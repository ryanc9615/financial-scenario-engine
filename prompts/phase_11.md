# Phase 11 — Scenario Updates, Deletion and Integrity

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 11 — Scenario Updates, Deletion and Integrity** of **Project 2: Financial Scenario Engine** (M4 — Scenario Persistence and CRUD).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Complete scenario PATCH and DELETE with correct partial semantics and referential integrity.

**Guide me through these build and learning activities:**
1. Explain PATCH versus PUT and difference between omitted fields and explicit zero.
2. Implement `PATCH /scenarios/{id}` with name and/or partial assumptions updates.
3. Validate the complete resulting assumptions set and preserve unchanged values.
4. Keep compound updates transactional and handle duplicate-name conflicts.
5. Implement `DELETE /scenarios/{id}` with 204 on success.
6. Inspect UPDATE, DELETE, FK cascade and handling of deleted assumptions.
7. Test zero updates, missing records, failed transactions and deletion integrity.

**Technical concepts to learn:** Partial updates, optional fields, idempotency, SQL UPDATE/DELETE, ORM dirty tracking, FK ON DELETE CASCADE.

**Business/financial concepts to reinforce:** Updating assumptions within an operating plan without corrupting other scenario values.

**Acceptance criteria (demonstrate rather than assume):**
- [ ] PATCH changes only named fields, including explicit zero where valid.
- [ ] DELETE removes scenario and its assumptions.
- [ ] Conflict and missing-resource errors are correct.
- [ ] Full scenario CRUD passes tests.

**Out of scope in this phase:** No scenario history, forecasting endpoint or versioning.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Start by comparing PATCH payload `{ "monthly_churn_rate": "0" }` with a payload omitting churn.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.
