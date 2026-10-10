# Phase 05 — HTTP Fundamentals and First FastAPI Endpoint

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 05 — HTTP Fundamentals and First FastAPI Endpoint** of **Project 2: Financial Scenario Engine** (M2 — HTTP and APIs).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Expose the independently tested financial engine as an HTTP JSON service.

**Guide me through these build and learning activities:**
1. Teach request/response anatomy, client-server separation, methods, URLs, headers, body, JSON and status codes.
2. Install FastAPI and the minimal local app server only when needed.
3. Create an app and `POST /forecasts` endpoint that calls the domain function.
4. Use Swagger UI and cURL to submit sample assumptions and examine the returned forecast.
5. Keep the route free of embedded financial calculations.
6. Write a first API smoke test and inspect the actual request/response bytes where practical.

**Technical concepts to learn:** HTTP, JSON, request/response, route decorators, web servers, FastAPI, serialisation, client-server boundaries.

**Business/financial concepts to reinforce:** An existing financial capability becomes a reusable backend service, independent of UI.

**Acceptance criteria (demonstrate rather than assume):**
- [ ] An HTTP POST returns correct 12-month JSON output.
- [ ] The original Python engine tests still pass.
- [ ] The user can explain route selection, data flow and HTTP response components.

**Out of scope in this phase:** No PostgreSQL, saved companies/scenarios or giant API scaffold.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Start with a raw HTTP request example and ask me to identify method, path, headers and body.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.
