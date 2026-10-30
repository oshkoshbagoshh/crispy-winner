# Architecture — Logia Insights (target)

Target design for a Django app on DigitalOcean. **Nothing below is provisioned yet.**

Public marketing / product site today: [https://logiainsights.com](https://logiainsights.com).

## Recommended shape

```text
Internet
   │
   ▼
DigitalOcean App Platform  ── Django (gunicorn / uvicorn)
   │
   ├── Managed PostgreSQL
   ├── App Platform env vars (secrets)
   └── Domain / TLS  (_TBD mapping to logiainsights.com_)
```

### Why App Platform (not a raw Droplet) for v1

- Builds from git when the remote exists; less server babysitting
- Managed TLS, scaling knobs, and component logs out of the box
- Clean pairing with Managed PostgreSQL
- Fits a collaboration repo: infra is declarative (`app.yaml` / App Spec) instead of snowflake SSH

Use a Droplet only if you need long-lived custom system packages, unusual networking, or GPU/specialized workloads.

## Django practices we will follow

When the app is scaffolded:

1. **Split settings** — `settings/base.py`, `local.py`, `production.py` (or equivalent env-driven config).
2. **12-factor config** — `SECRET_KEY`, `DEBUG`, `ALLOWED_HOSTS`, `DATABASE_URL`, `CSRF_TRUSTED_ORIGINS` from env.
3. **No secrets in git** — `.env` gitignored; `.env.example` documents keys only.
4. **Migrations in VCS** — never hand-edit production schema.
5. **Static files** — WhiteNoise or DO Spaces + collectstatic for App Platform.
6. **HTTPS-aware** — `SECURE_*` settings on when `DEBUG=False`.
7. **One web process** — gunicorn (or uvicorn if ASGI) as the App Platform run command.
8. **Health check** — simple `/healthz/` (or similar) for platform probes.

## DigitalOcean pieces (TBD)

| Resource | Intent | Status |
| --- | --- | --- |
| App Platform app | Serve Django | Not created |
| Managed PostgreSQL | Primary DB | Not created |
| App Spec / `app.yaml` | Declarative deploy | Not added |
| Domain / DNS | Tie to logiainsights.com | Not configured |
| Uptime / alerts | Basic monitoring | Not configured |

Region, size, and monthly cost: fill in after the team picks a plan. Creating these resources starts billing immediately.

## Local vs production

| Concern | Local | Production (planned) |
| --- | --- | --- |
| App | `uv` + Django runserver / similar | App Platform |
| DB | SQLite or local Postgres | Managed PostgreSQL |
| Secrets | `.env` | App Platform encrypted env |
| Static | Django static serving | WhiteNoise or Spaces |

## References (DigitalOcean)

- [App Platform](https://docs.digitalocean.com/products/app-platform/)
- [Python buildpack](https://docs.digitalocean.com/products/app-platform/reference/buildpacks/python/)
- [Sample Django-style multi-component flow](https://docs.digitalocean.com/products/app-platform/getting-started/deploy-rss-reader/)

## Out of scope for bootstrap

- Creating the git remote
- Provisioning DO resources
- Scaffolding the full Django project tree

Those land in follow-up work once open decisions in [COLLABORATION.md](COLLABORATION.md) are closed.
