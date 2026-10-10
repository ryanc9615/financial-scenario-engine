# Phase 08 — SQLAlchemy and Company Persistence

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 08 — SQLAlchemy and Company Persistence** of **Project 2: Financial Scenario Engine** (M3 — Relational Persistence).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Connect FastAPI to PostgreSQL and build persistent create/get company operations.

**Guide me through these build and learning activities:**
1. Explain PostgreSQL vs psycopg driver vs SQLAlchemy SQL toolkit vs SQLAlchemy ORM.
2. Introduce SQLAlchemy 2.x models for the **three** agreed app tables.
3. Set up Alembic baseline migration and verify actual generated schema.
4. Configure synchronous DB engine and scoped session dependency using secrets from environment.
5. Create `POST /companies` and `GET /companies/{id}` with appropriate Pydantic contracts.
6. Inspect INSERT/SELECT SQL emitted and query the row directly using psql.
7. Write API+DB tests with isolated test database and persistence across new sessions.

**Technical concepts to learn:** ORM mapping, schema migrations, sessions, connections, SQL statements, DI where useful, persistence layer.

**Business/financial concepts to reinforce:** Stable company identity and persistence across API calls.

**Acceptance criteria (demonstrate rather than assume):**
- [ ] A company created through HTTP exists in PostgreSQL.
- [ ] Retrieve works in a new session and after app restart.
- [ ] All three tables exist through Alembic migration.
- [ ] User explains what SQLAlchemy abstracts and can inspect its SQL.

**Out of scope in this phase:** No actual scenario endpoint yet; no async infrastructure or complex repository interfaces.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Ask me to explain a raw SQL INSERT from Phase 07 and compare it to an ORM save.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.
