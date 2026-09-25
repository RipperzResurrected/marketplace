---
description: Run the ripperZ backend, browser and frontend checks and summarize the results
allowed-tools: Bash, Read
---

Run every automated check of the ripperZ ressurrected project from the repository root and report the results.

1. Backend tests: `npm test` in `summoning/`.
2. Browser tests: `npm run test:browser` in `summoning/`.
3. Frontend: `npm run lint` and `npm run build` in `mint_page/react-app/`.

On Windows use `npm.cmd` if `npm` is not resolvable.

Report pass/fail counts for each step. For every failure, show the failing test name and the relevant error lines, and point to the file and line most likely responsible. Do not modify code unless the user asks you to fix something.
