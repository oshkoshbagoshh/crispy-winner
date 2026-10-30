# Logia Insights (LOGIA BRIDGE)

Collaboration workspace for **Logia Insights**.

- **Product site:** [https://logiainsights.com](https://logiainsights.com)
- **Local project name:** `logia-bridge`
- **Git remote:** _TBD — not configured yet_
- **Hosting:** _TBD — DigitalOcean (Django / App Platform planned)_

## Goal

Build and ship Logia Insights together with a clear Django + DigitalOcean foundation, without locking infra choices until the team is ready.

## Stack (planned)

| Layer | Choice | Status |
| --- | --- | --- |
| Language | Python 3.14+ | Local stub present |
| Framework | Django | Not scaffolded yet |
| Package / env | `uv` + `pyproject.toml` | Started |
| Hosting | DigitalOcean App Platform | TBD |
| Database | DigitalOcean Managed PostgreSQL | TBD |
| Domain | logiainsights.com | External site live |

## Repo layout

```text
.
├── README.md
├── AGENTS.md
├── CONTRIBUTING.md
├── pyproject.toml
├── hello_money.py          # scratch / local experiments
├── src/logia_bridge/       # Python package entrypoint
└── docs/
    ├── ARCHITECTURE.md
    └── COLLABORATION.md
```

## Quick start (local)

```bash
# From repo root
uv sync
uv run logia-bridge
```

Django project bootstrap, env files, and deploy steps will be filled in once the remote and DigitalOcean team are decided.

## Documentation

- [Collaboration](docs/COLLABORATION.md) — how we work together
- [Architecture](docs/ARCHITECTURE.md) — Django + DigitalOcean target design
- [Contributing](CONTRIBUTING.md) — PR / branch expectations
- [AGENTS.md](AGENTS.md) — rules for AI coding agents in this repo

## Status

Early bootstrap. Prefer small, reviewable changes. Do not create billable DigitalOcean resources or a git remote until the team explicitly decides.
# crispy-winner
