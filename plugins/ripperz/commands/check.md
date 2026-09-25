---
description: Read-only health check of the ripperZ Zcash service (database, manifest, worker, node)
allowed-tools: Read, Bash(npm --prefix summoning run check), Bash(npm --prefix summoning run preflight), Bash(npm.cmd --prefix summoning run check), Bash(npm.cmd --prefix summoning run preflight)
---

Run the read-only health checks of the ripperZ ressurrected Zcash service from the repository root and summarize what is ready and what blocks checkout. Run exactly these commands (on Windows use `npm.cmd` instead of `npm`):

1. `npm --prefix summoning run check` validates the database, manifest, frontend build, worker heartbeat and configuration.
2. `npm --prefix summoning run preflight` checks mainnet sync, the wallet and the shielded source addresses. It needs `.env.worker` at the repository root; if that file is missing, say so and skip this step.

Never add `--broadcast`, and never run `canary` or `anchor` from this command: they can spend real ZEC.

Summarize the result as a short checklist: each checkout safety gate (checkout switch, manifest, signing key, price, receiving address, RPC, delivery and proof addresses, fresh worker heartbeat) marked ready or blocked, with the reason for anything blocked.
