# Phase 09 — Scenario Creation and Database Transactions

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 09 — Scenario Creation and Database Transactions** of **Project 2: Financial Scenario Engine** (M4 — Scenario Persistence and CRUD).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Save a scenario and its assumptions atomically as linked rows.

**Guide me through these build and learning activities:**
1. Review 1-to-many company/scenarios and 1-to-1 scenario/assumptions relationships.
2. Implement `POST /companies/{id}/scenarios` including company existence and duplicate-name validation.
3. Map API assumption input to ORM rows without calculating the forecast.
4. Write scenario and assumptions within one transaction; inspect `flush`, `commit` and `rollback`.
5. Handle uniqueness violations even when an application-level check exists (race condition).
6. Inspect generated INSERT SQL.
7. Deliberately fail the second insert and verify no partial rows remain.

**Technical concepts to learn:** Application services, ORM relations, transactions, atomicity, flush vs commit, rollback, SQL exception translation.

**Business/financial concepts to reinforce:** A scenario is a named assumption snapshot; calculation outputs are derived on demand.

**Acceptance criteria (demonstrate rather than assume):**
- [ ] Valid scenario + assumptions save together.
- [ ] Missing company 404, invalid assumptions 422, duplicate scenario 409.
- [ ] Failed two-row transaction rolls back both operations.
- [ ] User can explain atomicity and show actual SQL.

**Out of scope in this phase:** No saved forecast outputs, retrieval/list/update/delete or comparison yet.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** First ask me to predict the database state if scenario INSERT succeeds but assumption INSERT fails outside one transaction.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.
