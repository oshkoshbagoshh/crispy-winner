# Collaboration — Logia Insights

How we work together on this project.

## People & access

| Role | Who | Access |
| --- | --- | --- |
| Product / owner | _TBD_ | Site: [logiainsights.com](https://logiainsights.com) |
| Engineering | _TBD_ | GitHub repo: _TBD_ |
| DigitalOcean team | _TBD_ | MCP / control panel: _TBD_ |

## Communication

| Channel | Use for |
| --- | --- |
| _TBD_ (Slack / email / etc.) | Day-to-day |
| GitHub Issues / PRs | _TBD once remote exists_ |
| This `docs/` folder | Durable decisions |

## Working agreement

1. **Docs first for shared decisions** — architecture, hosting, and access changes land in `docs/` so nobody relies on chat memory.
2. **No surprise billing** — DigitalOcean creates/resizes need an explicit OK and a cost note.
3. **No surprise remotes** — git hosting (GitHub org/user, visibility) is decided by the team before `origin` is added.
4. **Small PRs** — easier review, fewer conflicts.
5. **Secrets stay out of git** — use local `.env` / DO App Platform env vars.

## Open decisions

Track blanks here until filled:

- [ ] Git host + org/user + repo name + visibility
- [ ] Add `git remote add origin …`
- [ ] DigitalOcean team / region
- [ ] App Platform vs Droplet (default recommendation: **App Platform**)
- [ ] Managed PostgreSQL plan size
- [ ] Custom domain wiring for app subdomain vs apex (`logiainsights.com`)
- [ ] Who can approve deploys and spend

## Onboarding (when remote exists)

1. Get invited to the GitHub repo and DigitalOcean team.
2. Clone, `uv sync`, copy `.env.example` → `.env` (file to be added with Django scaffold).
3. Read [ARCHITECTURE.md](ARCHITECTURE.md) before changing deploy config.
