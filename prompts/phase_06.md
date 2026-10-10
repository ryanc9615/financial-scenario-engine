# Phase 06 — API Contracts, Pydantic and Validation

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 06 — API Contracts, Pydantic and Validation** of **Project 2: Financial Scenario Engine** (M2 — HTTP and APIs).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Define and test robust request/response contracts for the stateless forecast endpoint.

**Guide me through these build and learning activities:**
1. Explain Python type hints versus runtime Pydantic validation.
2. Define Pydantic inputs for the 12 approved assumptions and outputs for monthly forecasts and summaries.
3. Make exact Decimal string representation in JSON explicit.
4. Reject missing fields, negative price, churn > 1, invalid rate/headcount types and unsupported collection lag.
5. Inspect OpenAPI/Swagger generated docs and HTTP 200/422 behavior.
6. Write happy- and failure-path API tests; map validated inputs to domain objects.

**Technical concepts to learn:** Pydantic v2 schemas, validators, serialization, API contracts, HTTP status codes, OpenAPI, test client.

**Business/financial concepts to reinforce:** Financial assumption integrity and consistent results for external consumers.

**Acceptance criteria (demonstrate rather than assume):**
- [ ] Forecast API produces the complete documented JSON shape.
- [ ] Invalid inputs produce expected 422 errors.
- [ ] The domain engine remains independent of FastAPI/Pydantic.
- [ ] OpenAPI documentation correctly describes the input/output rules.

**Out of scope in this phase:** No company/scenario database endpoints yet.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Explain type hints versus runtime validation with one small example before touching the existing endpoint.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.
