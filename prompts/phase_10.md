# Phase 10 — Scenario Retrieval, Listing and SQL JOINs

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 10 — Scenario Retrieval, Listing and SQL JOINs** of **Project 2: Financial Scenario Engine** (M4 — Scenario Persistence and CRUD).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Retrieve a scenario with assumptions and list scenarios by company while learning JOINs.

**Guide me through these build and learning activities:**
1. Implement `GET /scenarios/{id}` with the saved assumptions in its response.
2. Implement `GET /companies/{id}/scenarios` with list summaries ordered sensibly.
3. Write and run equivalent SQL SELECT JOIN and ORDER BY queries in PostgreSQL.
4. Compare INNER JOIN versus LEFT JOIN and ORM relationship loads.
5. Use GROUP BY/COUNT to count scenarios by company as a direct SQL exercise.
6. Handle missing company/scenario and invalid IDs correctly.
7. Write API and PostgreSQL integration tests.

**Technical concepts to learn:** GET routes, object serialization, relational joins, ORM retrieval behavior, ordering, aggregation, response contracts.

**Business/financial concepts to reinforce:** Identifying operating plans, listing alternatives per business.

**Acceptance criteria (demonstrate rather than assume):**
- [ ] A saved scenario returns all 12 assumptions.
- [ ] Company list returns only its scenarios.
- [ ] SQL JOIN equivalent is understood and demonstrable.
- [ ] Missing records yield 404 and relevant tests pass.

**Out of scope in this phase:** No PATCH, DELETE, forecast comparison or extra endpoints.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Ask me to propose the raw SQL join before showing SQLAlchemy retrieval.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.
