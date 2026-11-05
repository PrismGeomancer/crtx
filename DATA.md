# CourtX: real data spec

The page runs on sample data now. To switch to real data, set this before the page script:

```html
<script>window.COURTX_CONFIG = { api: "https://api.yourdomain.com" }</script>
```

If `api` is set, the page calls `GET {api}/trials` and falls back to sample data with a toast if the call fails.

## GET /trials

```json
[
  {
    "id": "0xA2",
    "defender": { "handle": "@vc_bro", "text": "post text", "url": "https://x.com/vc_bro/status/..." },
    "roaster":  { "handle": "@anon_sage", "text": "reply text", "url": "https://x.com/anon_sage/status/..." },
    "defenderPct": 38,
    "pot": 48.9,
    "closesAt": "2026-11-05T12:00:00Z"
  }
]
```

When `url` is present the exhibit card shows a "View on X" link.

## Records the backend needs

| Record | Fields | Source |
|---|---|---|
| Trial | id, original post id, reply post id, opens_at, closes_at, status | Bot that watches X for replies tagging @CourtX_project |
| Post snapshot | post id, text, author, likes, reposts, replies, views, taken_at, hash | X API (paid) or a data provider; taken at open and at close |
| Pool and bet | trial id, wallet, side, amount, tx signature | Solana program or indexer |
| Jury vote | trial id, X user id, vote (held / landed) | Backend database, one per verified account |
| Verdict | trial id, winner, score, open hash, close hash, payout tx | Settlement job plus on-chain record |
| User | X handle, wallet, wins, SOL won, XP, avatar | Backend database |

## Endpoints the UI would call next

- `GET /trials/:id` trial detail, backers, jury tally
- `POST /trials/:id/bets` signed bet from the wallet
- `POST /trials/:id/votes` jury vote (requires X sign-in)
- `GET /verdicts` recent verdicts (replaces the sample log)
- `GET /leaderboard` Hall of Burns
- `GET /me` profile and open bets

## Needs a decision before launch

- Scoring weights (the page says 60% engagement, 30% jury, 10% anti-spam) are placeholders.
- Protocol fee (3%) is a placeholder.
- X API cost and rate limits decide how often metrics can be read.
