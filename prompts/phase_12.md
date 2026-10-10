# Phase 12 — Calculating Saved Financial Scenarios

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 12 — Calculating Saved Financial Scenarios** of **Project 2: Financial Scenario Engine** (M5 — Integrated Scenario Engine).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Combine saved assumptions with the pre-existing pure financial engine.

**Guide me through these build and learning activities:**
1. Implement `GET /scenarios/{id}/forecast`.
2. Load scenario plus assumptions without changing state.
3. Convert ORM values to domain objects and call the existing financial function.
4. Convert domain outputs to Pydantic response schema and JSON.
5. Compare derived output to independently expected values.
6. PATCH an assumption and show next GET forecast changes without a stored forecast row.
7. Trace one complete read request through HTTP → SQLAlchemy/SQL/PostgreSQL → domain engine → JSON.
8. Write end-to-end integration/API tests.

**Technical concepts to learn:** Layer boundaries, domain mapping, read-only operations, service orchestration, serialization and end-to-end tracing.

**Business/financial concepts to reinforce:** How saved operating assumptions become recalculated projections.

**Acceptance criteria (demonstrate rather than assume):**
- [ ] Saved forecast endpoint returns all 12 months and summary.
- [ ] Changes to assumptions recalculate results.
- [ ] No forecast rows persisted or commits needed for read-only operation.
- [ ] User can explain every layer traversed.

**Out of scope in this phase:** No forecast result persistence or comparison endpoint yet.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Ask me to predict the full order of operations, noting when DB access occurs and when financial engine is called.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.
