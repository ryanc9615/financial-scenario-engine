# Phase 15 — Backend Reliability, Testing and Debugging

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 15 — Backend Reliability, Testing and Debugging** of **Project 2: Financial Scenario Engine** (M6 — Reliability and Debugging).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Harden the completed backend and learn evidence-based failure diagnosis.

**Guide me through these build and learning activities:**
1. Audit actual unit/API/DB test coverage, identify highest-value gaps.
2. Ensure DB tests use isolated, disposable databases or sound rollback fixtures.
3. Handle missing records, uniqueness conflicts, bad inputs and database connection failures predictably.
4. Add Python standard-library logging at relevant API/service boundaries without exposing credentials.
5. Inspect generated SQL and use EXPLAIN for scenario-list indexing intuition.
6. Diagnose deliberate calculation, validation and persistence failures with a repeatable workflow.
7. Demonstrate parameterized SQL and environment-based secrets.
8. Add focused regression tests and document discovered limitations.

**Technical concepts to learn:** Pytest isolation, errors across layers, structured debugging, logging, query plans, indexes, security basics.

**Business/financial concepts to reinforce:** Financial calculation trustworthiness and data integrity.

**Acceptance criteria (demonstrate rather than assume):**
- [ ] Important tests pass; unrun tests are not called passing.
- [ ] 422/409/500 differences explained.
- [ ] A failed transaction and SQL query can be inspected.
- [ ] A regression test demonstrates a fixed bug.
- [ ] Unsafe public exposure is explicitly avoided.

**Out of scope in this phase:** No full authentication, monitoring stack, complex CI/CD or Kubernetes.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Start with an audit of actual test files/results, not imagined coverage. Prioritise the largest verified gap.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.
