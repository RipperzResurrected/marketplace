---
name: zcash-safety
description: Safety rules for working in the ripperZ ressurrected Zcash codebase (summoning service, mint page, marketplace). Use whenever editing or running code that touches Zcash payments, shielded deliveries, the worker, production CLI commands (preflight, canary, anchor), environment files, deployment, or git push.
---

# ripperZ Zcash safety rules

This project moves real ZEC on Zcash mainnet. Follow these rules in addition to normal coding practice.

## Never without explicit approval in the current conversation

- Run `canary`, `anchor` or any command with `--broadcast`. Dry runs (without `--broadcast`) are fine.
- Call a spending RPC method (`z_sendmany`) against a real node.
- `git push`, force-push, or change a remote branch. Commit locally only when asked.
- Deploy, restart production services, or edit DNS.

## Never commit or publish

- `.env`, `.env.app`, `.env.worker` or any file holding RPC credentials, operator tokens or `OWNERSHIP_PRIVATE_KEY_B64`.
- `provenance-private.json`, `production-selection.private.json`, SQLite databases or their backups.
- Wallet keys, seed phrases or spending keys. Viewing keys are public only when the user says so.

## Invariants to preserve in code

- Payments and deliveries need at least 10 confirmations and a check that the block is still on the active chain.
- A shielded send is claimed before `z_sendmany`. If its outcome is unknown (timeout, crash, lost operation), the job goes to `held` and is never resent automatically.
- Amounts are integer zatoshi strings. Never use floating point for money.
- User-facing failures throw `Problem(status, message, code)` so the API returns a useful status instead of a generic 500.
- The app has read-only RPC access; only the worker holds the spending RPC.

## Before finishing a change

Run the backend tests in `summoning/` (`npm test`). If the frontend changed, also run `npm run lint` and `npm run build` in `mint_page/react-app/`. Report failures honestly.
