# AGENTS.md — Logia Insights / LOGIA BRIDGE

Rules for AI coding agents working in this repository.

## Product context

- Product: **Logia Insights**
- Public site: https://logiainsights.com
- This repo (`logia-bridge`) is the collaboration / engineering workspace

## Non-negotiables

1. **Do not invent secrets.** Never commit `.env`, API tokens, DB URLs, or DigitalOcean credentials.
2. **Do not create billable infrastructure** (Droplets, App Platform apps, managed DBs, reserved IPs) unless a human explicitly asks and confirms cost.
3. **Do not create or rewrite the git remote** unless a human explicitly asks. Remote is intentionally unset for now.
4. Prefer **Django + DigitalOcean App Platform + Managed PostgreSQL** when proposing hosting — see [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).
5. Keep changes small. Document decisions in `docs/` when they affect collaborators.
6. Read this file and [CONTRIBUTING.md](CONTRIBUTING.md) before large refactors.

## Preferred stack defaults

- Python via `uv` / `pyproject.toml`
- Django for the web app (when scaffolded)
- PostgreSQL in production; SQLite only for local throwaway experiments
- Environment variables for config (`DJANGO_SECRET_KEY`, `DATABASE_URL`, `ALLOWED_HOSTS`, etc.)
- App Platform `app.yaml` / App Spec when deploy is ready — not Droplet DIY unless required

## Documentation duty

When you change how collaborators build, run, or deploy:

- Update `README.md` and the relevant file under `docs/`
- Leave `_TBD_` markers only for decisions the team has not made yet — do not invent owner/org/region/plan values
