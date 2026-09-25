---
description: Read-only health check of the ripperZ Zcash service (database, manifest, worker, node)
allowed-tools: Bash, Read
---

Run the read-only health checks of the ripperZ ressurrected Zcash service from `summoning/` and summarize what is ready and what blocks checkout.

1. `npm run check` validates the database, manifest, frontend build, worker heartbeat and configuration.
2. `npm run preflight` checks mainnet sync, the wallet and the shielded source addresses. It needs `../.env.worker`; if that file is missing, say so and skip this step.

Never add `--broadcast`, and never run `canary` or `anchor` from this command: they can spend real ZEC.

Summarize the result as a short checklist: each checkout safety gate (checkout switch, manifest, signing key, price, receiving address, RPC, delivery and proof addresses, fresh worker heartbeat) marked ready or blocked, with the reason for anything blocked.
