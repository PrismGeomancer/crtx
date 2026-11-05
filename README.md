# CourtX

Static site (no build step).

## Publish on GitHub Pages
1. Push this folder to a GitHub repo.
2. Settings > Pages > Deploy from branch > main, folder / (root).
3. Open https://USERNAME.github.io/REPO/

Files: index.html (app), theme.css (shared styles), DATA.md (real-data spec).
All trials, bets and verdicts are sample data. See DATA.md to connect a backend.

## Brand and promo (folder `brand/`)
- courtx-logo.png (transparent, 1024), courtx-logo.svg, courtx-logo-navy.png
- courtx-wordmark.png, courtx-profile-400.png
- courtx-twitter-header.png (1500x500)
- courtx-promo-20s.mp4 (1920x1080, 30 fps, with sound)

## Wallet
Connect Wallet uses the Phantom, Solflare and Backpack browser extensions and reads the real SOL balance over public Solana RPC.
Bets are demo only: no transaction is sent.
