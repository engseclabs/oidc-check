# oidc-check

Test harness for **Lab 01 — Authentication** of the Floe AWS security training.

A scheduled GitHub Action reads `handles.txt` and, for each student handle, tries
to assume `floe-training-<handle>` in account `997880307006` over GitHub OIDC and
read the shared lab bucket. A static results page (GitHub Pages, served from
`docs/`) lets a student enter their handle and see green (their trust policy
works) or red (it doesn't), reading the public Actions results with no token.

This repo holds **no secrets** — OIDC means the Action proves its identity with a
short-lived token, not a stored credential.

| File | What it is |
|---|---|
| `.github/workflows/oidc-check.yml` | Scheduled + dispatchable matrix job, one job per handle. |
| `handles.txt` | One student handle per line. Maintained by the instructor. |
| `docs/index.html` | The results page (GitHub Pages). |

> Managed by Terraform in the training repo (`labs/lab-01-github/`). Edit the
> sources there and re-apply rather than committing here directly.
