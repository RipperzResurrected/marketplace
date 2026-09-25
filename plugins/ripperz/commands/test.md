---
description: Run the ripperZ backend, browser and frontend checks and summarize the results
allowed-tools: Read, Bash(npm --prefix summoning test), Bash(npm --prefix summoning run test:browser), Bash(npm --prefix mint_page/react-app run lint), Bash(npm --prefix mint_page/react-app run build), Bash(npm.cmd --prefix summoning test), Bash(npm.cmd --prefix summoning run test:browser), Bash(npm.cmd --prefix mint_page/react-app run lint), Bash(npm.cmd --prefix mint_page/react-app run build)
---

Run every automated check of the ripperZ ressurrected project from the repository root and report the results. Run exactly these commands (on Windows use `npm.cmd` instead of `npm`):

1. Backend tests: `npm --prefix summoning test`
2. Browser tests: `npm --prefix summoning run test:browser`
3. Frontend lint: `npm --prefix mint_page/react-app run lint`
4. Frontend build: `npm --prefix mint_page/react-app run build`

Report pass/fail counts for each step. For every failure, show the failing test name and the relevant error lines, and point to the file and line most likely responsible. Do not modify code unless the user asks you to fix something.
