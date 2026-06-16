# oidc-check

Test harness for a hands-on AWS authentication lab.

A scheduled GitHub Action reads `handles.txt` and, for each participant handle,
tries to assume `oidc-lab-<handle>` in the lab AWS account over GitHub OIDC and
read a shared lab bucket. A static results page (GitHub Pages, served from
`docs/`) lets a participant enter their handle and see green (their trust policy
works) or red (it doesn't), reading the public Actions results with no token.

This repo holds **no secrets** — OIDC means the Action proves its identity with a
short-lived token, not a stored credential.

| File | What it is |
|---|---|
| `.github/workflows/oidc-check.yml` | Scheduled + dispatchable matrix job, one job per handle. |
| `handles.txt` | One participant handle per line. Maintained by the instructor. |
| `docs/index.html` | The results page (GitHub Pages). |

> This repo's contents are generated; edit the sources and re-apply rather than
> committing here directly.
