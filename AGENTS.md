# AGENTS.md

Guidance for AI agents working in this repo. Humans: see `README.md`.

## What this is

`xrp-to-dogecoin-price` is a tiny dormant 2014 npm module (v1.0.1) that converts XRP to DOGE using Ripple Charts and Cryptsy. Treat it as a historical showcase.

## Stack

- Node.js, CommonJS, no build step. `index.js` uses `const`, so it needs a Node that supports it (io.js or Node 4 and later).
- Dependencies: `superagent ^0.18.2`, `bluebird ^2.3.1`.
- Tests: mocha (`mocha -R spec test/ --timeout 10000`), not listed as a dependency.
- Default branch: `master`.

## Layout

- `index.js`: the converter (the whole library).
- `bin/btc_to_dog`: unfinished CLI stub.
- `test/convert_xrp_to_dog.js`: the one test, hits live APIs.
- `docs/STATUS.md`: current state and gap to the repo standard.

## Commands

- Install: `npm install` (not verified on a current Node).
- Test: `npm install --no-save mocha && npm test`. Known not to pass today, because Cryptsy is gone and the test calls the live APIs.
- Run: there is no server. Use `require('./index.js')` from a script.

## Rules

- Add or update tests with every code change. Prefer tests that stub the HTTP calls.
- Never commit secrets. There are none in the repo today.
- Use Conventional Commits.
- Keep `docs/STATUS.md` current.

## What agents may and may not do

- May: improve docs, fix clear bugs, add stubbed tests, open pull requests.
- May not: archive the repo, publish to npm, rewrite git history, or rename the default branch without Steven's say-so.
