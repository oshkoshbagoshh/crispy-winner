# Contributing — Logia Insights

Thanks for helping build Logia Insights.

## Before you start

1. Read [README.md](README.md) and [docs/COLLABORATION.md](docs/COLLABORATION.md).
2. Confirm the git remote is set (currently **TBD**). Until then, work locally and share patches / branches however the team agrees.
3. Do not push secrets or create DigitalOcean resources without an explicit team decision.

## Branching (once remote exists)

Suggested defaults — adjust when the team picks a workflow:

| Branch | Purpose |
| --- | --- |
| `main` | Stable / deployable |
| `feat/<short-name>` | Features |
| `fix/<short-name>` | Bug fixes |
| `docs/<short-name>` | Documentation only |

Open a PR for review before merging to `main`.

## Commit messages

Use short, imperative subjects focused on **why**:

```text
Add collaboration docs for Logia Insights bootstrap
```

## Code expectations

- Python 3.14+, typed where practical
- Django best practices when the app lands (settings split, no secrets in repo, migrations in VCS)
- Prefer clarity over cleverness
- Update docs when behavior or setup changes

## Local checklist

```bash
uv sync
uv run logia-bridge
# Later: Django test / lint commands will live here
```

## Questions

Capture open decisions in [docs/COLLABORATION.md](docs/COLLABORATION.md) under **Open decisions** instead of scattering them in chat.
