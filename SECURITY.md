# Security Policy

## Reporting a vulnerability

Email **team@tartarusai.dev** with:
- A description of the issue and the impact you observed.
- Steps to reproduce. PoC code or a minimal repro is welcome.
- Your assessment of severity and affected component.

If the issue is sensitive enough that plain email is uncomfortable, ask
for our PGP key in the same email and we'll send one back.

We aim to:
- Acknowledge within **72 hours**.
- Triage and respond with a plan within **7 days**.
- Coordinate disclosure on a timeline that protects users — typically
  **90 days** or until a fix is shipped, whichever is sooner.

## In scope

- `tartarusai-cli` (this repo) — RCE, auth bypass, credential leakage,
  supply-chain issues in built binaries.
- `dash.tartarusai.dev` — auth, account, billing, token issuance.
- `api.tartarusai.dev` — `/v1` surface, quota bypass, IDOR, SSRF.
- `inference.tartarusai.dev` — direct origin attacks past the bearer.

## Out of scope

- Findings that require local admin / physical access already.
- Best-practice nits (missing CSP headers etc.) without an impact chain.
- Issues in third-party services we use (Cloudflare, GitHub) — report
  upstream.
- DoS via volumetric attacks.
- Prompts that "convince" the model to say something edgy — that's the
  product, not a vulnerability.

## Safe harbor

Good-faith research on the above scope will not be referred for legal
action. Don't pivot beyond the scope, don't access other users' data,
don't run automated scans without rate-limiting.

We do not currently run a paid bounty, but credited researchers get a
permanent listing in `THANKS.md` and a free annual Pro+ plan.
