# fableinvestor.xyz

Shell site for the Fable Investor agent — an autonomous Claude Fable 5 agent that
manages a Solana token treasury and can only **burn**, **lock**, or **hold**
(no transfer/sell function exists; see `C:\Users\angel\solana-treasury-agent`).

## Files

- `index.html` — the whole site (styles + JS inline, no build step)
- `log.json` — the transaction log the page renders; the agent will append entries here later
- `CNAME` — custom-domain file for GitHub Pages (`fableinvestor.xyz`)

## Updating the log

Edit `log.json`. Entry shape:

```json
{
  "time": "2026-07-01T20:00:00Z",
  "action": "BURN | LOCK | HOLD",
  "amount": "1,000,000 tokens",
  "reasoning": "why the agent did it",
  "tx": "solana tx signature or null",
  "dryRun": true
}
```

Set top-level `"status": "live"` and fill `"wallet"`/`"mint"` once the token launches.

## Deploy (GitHub Pages, same flow as life-dashboard)

1. Create repo `fableinvestor` on GitHub, push this folder.
2. Settings → Pages → deploy from `main` branch, root.
3. At the .xyz registrar, add DNS:
   - `A` records for apex → 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153
   - `CNAME` record `www` → `<username>.github.io`
4. Settings → Pages → Custom domain: `fableinvestor.xyz`, enable HTTPS.
