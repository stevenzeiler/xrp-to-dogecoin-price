# Status

Last reviewed: 2026-11-20 (github-audit pass 02, docs only).

## What works

Nothing was run in this pass. From reading the code, the converter chains two HTTP lookups and returns `{ xrp, dog }`.

## What's broken or unknown

- Cryptsy (`pubapi.cryptsy.com`) has shut down, so the DOGE price step cannot succeed. **(inference from Cryptsy's public closure; not tested)**
- The Ripple Charts endpoint used (`api.ripplecharts.com/api/exchange_rates`) may have changed or gone.
- Errors are not passed on: if the second lookup fails, the returned promise never settles, and a failure in the first step is not caught.
- `bin/btc_to_dog` only validates its argument and does nothing else.
- mocha is not a declared dependency, and the only test hits the live APIs.
- `package.json` has an empty description and author.

## What's next

1. Decide whether to keep this as a read-only showcase or archive it (Steven's decision).
2. If keeping it: swap in a live price source, propagate errors, stub the HTTP calls in tests.

## Not yet from the standard

- CONTRIBUTING.md
- SECURITY.md
- .editorconfig
- .github issue and pull request templates
- Dependabot configuration
- `ci.yml` with gitleaks
- Rename `master` to `main`
- CloudEvents catalog
- Product one-pager
