# Financial Scenario Engine

**Project 2 — Technical Apprenticeship**\
Status: **Documentation/reference setup; Phase 00 not yet started**

A deliberately small Python backend for managing B2B SaaS financial scenarios, generating deterministic 12-month forecasts and comparing alternatives. The goal is practical mastery of Python, HTTP, FastAPI, SQL, PostgreSQL, SQLAlchemy, persistence, transactions and testing.

## Read this first

1. `docs/ORIGINAL_SCOPE.md` — full original project brief and boundaries.
2. `docs/ENGINEERING_SPEC.md` — agreed product, financial formulas, ten API endpoints, database and test contract.
3. `docs/PHASE_ROADMAP.md` — staged sequence with completion gates.
4. `docs/TUTOR_PROTOCOL.md` — how AI should tutor and assess, rather than autogenerate the entire system.
5. `docs/PROJECT_STATE.md` — current verified status and handoff between conversations.
6. `docs/DECISIONS.md` — accepted trade-offs and changes.
7. `prompts/` — individual copy-ready prompts for Phases 00–16.

**Start at:** `prompts/phase_00.md` in a new conversation in the existing ChatGPT Project.

## Delivery strategy

| Milestone | Phases | End result |
| --- | --- | --- |
| 1 — Python engine | 00–04 | Independently tested 12-month forecast |
| 2 — HTTP API | 05–06 | Stateless `POST /forecasts` and validation |
| 3 — Relational persistence | 07–08 | PostgreSQL and company API |
| 4 — Scenario CRUD | 09–11 | Persisted scenarios, transactions and integrity |
| 5 — Integrated calculations | 12–13 | Saved forecasts and 2–4-scenario comparisons |
| 6 — Reliability | 14–15 | Migration, error handling and debugging |
| 7 — Final mastery | 16 | Repeatable demonstration and technical examination |

## Getting started

This repository deliberately contains no application source files or installed dependencies yet. The first phase is to learn and perform Python setup in a guided way. **Do not skip it by generating the entire scaffold.**

When app development begins, replace this section with verified installation, database, migration, run and test instructions. Never publish a public write-enabled API without authentication or an independent access boundary.

## GitHub remote setup (one time)

For complete extraction, creation, authentication and verification steps, see `docs/GITHUB_SETUP.md`.

If creating a new GitHub repository from this existing local Git history:

1. In GitHub create a **private, empty** repository named `financial-scenario-engine` under your own account. **Do not** initialise it with a README, licence or `.gitignore`, because those files already exist here.
2. From the extracted project directory run:

```bash
git remote add origin https://github.com/ryanc9615/financial-scenario-engine.git
git push -u origin main
```

If you use SSH, substitute the SSH URL. Authenticate with the GitHub CLI, credential manager or your usual Git setup; never put personal access tokens in documents or chats. If your chosen repository name/owner differs, change the remote URL accordingly.

Check publication with `git remote -v` and the GitHub repository website. A local commit alone does **not** mean files have reached GitHub.