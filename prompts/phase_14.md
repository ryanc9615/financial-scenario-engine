# Phase 14 — Database Migrations and Schema Evolution

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 14 — Database Migrations and Schema Evolution** of **Project 2: Financial Scenario Engine** (M6 — Reliability and Debugging).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Evolve the populated PostgreSQL database intentionally using Alembic.

**Guide me through these build and learning activities:**
1. Explain why editing an ORM class does not change an already-created PostgreSQL table.
2. Review Alembic baseline schema and current revision.
3. Add nullable `description TEXT` to `scenarios` as intentional V2 schema change.
4. Autogenerate candidate migration, read and review upgrade/downgrade SQL.
5. Apply against a database with existing sample rows and confirm preservation.
6. Extend relevant ORM, API and tests to expose description correctly.
7. Trial downgrade only in a disposable database, then reapply and rerun checks.
8. Document the real consequences of dropping a column.

**Technical concepts to learn:** Schema change, Alembic, DDL, ALTER TABLE, migration scripts, backwards compatibility, data-preserving evolution.

**Business/financial concepts to reinforce:** Preserving existing scenario data when requirements evolve.

**Acceptance criteria (demonstrate rather than assume):**
- [ ] Existing records survive migration.
- [ ] New/old scenarios work with optional descriptions.
- [ ] Upgrade/downgrade mechanics can be described.
- [ ] No populated development database destroyed.

**Out of scope in this phase:** No additional scenario versioning or complex migrations.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Ask what happens if only Python models change while the PostgreSQL schema remains the same.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.
