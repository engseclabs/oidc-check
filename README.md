# oidc-check

Test harness for a hands-on AWS authentication lab.

A participant enters their handle on the results page (GitHub Pages, served from
`docs/`). That triggers a one-shot GitHub Action that tries to assume
`oidc-lab-<handle>` in the lab AWS account over GitHub OIDC and read a shared lab
bucket. The page then shows green (their trust policy works) or red (it doesn't),
reading the public Actions results with no token.

This repo holds **no secrets** — OIDC means the Action proves its identity with a
short-lived token, not a stored credential. Triggering a run needs `actions:write`,
which is **not** in this repo or the page; a small external proxy holds that token
and dispatches only this workflow.

| File | What it is |
|---|---|
| `.github/workflows/oidc-check.yml` | One-shot job, dispatched per handle (`workflow_dispatch` with a `handle` input). |
| `docs/index.html` | The results page (GitHub Pages). |

> This repo's contents are generated; edit the sources and re-apply rather than
> committing here directly.
