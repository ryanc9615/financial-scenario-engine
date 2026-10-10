# Staged Conversation Prompts — Financial Scenario Engine

These are **copy-ready conversation starters**, one per new ChatGPT Project conversation, in phase order. The same prompts are available individually under `prompts/phase_00.md` through `prompts/phase_16.md`.

Use the original scope, engineering spec, roadmap and tutor protocol as shared references. The source of actual progress is repository code/tests plus `docs/PROJECT_STATE.md`—never assume a planned feature already exists.

---

# Phase 00 — Project Setup and Development Workflow

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 00 — Project Setup and Development Workflow** of **Project 2: Financial Scenario Engine** (M1 — Python Financial Engine).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Create and understand a clean Python development environment and a reproducible Git workflow before adding domain logic.

**Guide me through these build and learning activities:**

1. Inspect the actual operating system, editor, terminal, Python and Git setup; do not assume their versions.
2. Create a virtual environment; understand activation, interpreter choice, package isolation and dependency management.
3. Create the smallest runnable Python package and project structure; introduce `pyproject.toml` only as needed.
4. Configure `.gitignore`, `.env.example`, README and source-control practices.
5. Review the existing repository files; do not overwrite documentation or rebuild the repository without need.
6. Run a trivial Python entry point, commit the meaningful change and update `docs/PROJECT_STATE.md`.

**Technical concepts to learn:** Python interpreters, virtual environments, modules/packages/imports, dependencies, terminals, Git commits, branches and project layout.

**Business/financial concepts to reinforce:** Why a reliable development environment and reproducible workflow matter for professional software.

**Acceptance criteria (demonstrate rather than assume):**

- [ ] A Python entry point runs in the project environment.
- [ ] The user can explain which interpreter and environment are active.
- [ ] A meaningful source change is committed and working tree status is understood.
- [ ] PROJECT_STATE accurately describes evidence and remaining tasks.

**Out of scope in this phase:** No database, FastAPI, ORM, financial implementation, pre-generated giant codebase or unnecessary tooling.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Help me inspect my current local environment and repository first. Then teach the first setup concept and guide one step at a time.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.

---

# Phase 01 — Financial Domain Modelling in Python

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 01 — Financial Domain Modelling in Python** of **Project 2: Financial Scenario Engine** (M1 — Python Financial Engine).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Model the 12 financial inputs and structured calculation outputs before implementing formulas.

**Guide me through these build and learning activities:**

1. Distinguish business concepts from Python dictionaries, dataclasses and classes.
2. Define exactly the 12 V1 financial assumptions in the engineering specification.
3. Choose types for counts, decimal money and rates; introduce `Decimal` and rounding.
4. Design a monthly result and 12-month forecast data representation.
5. Separate source assumptions from derived outputs.
6. Write small tests that construct domain objects and exercise key invariants.

**Technical concepts to learn:** Python dataclasses, classes, immutability, fields, type hints, modules, constructors, `Decimal`, imports and test assertions.

**Business/financial concepts to reinforce:** Business assumptions, financial precision, model inputs versus outputs and reproducible scenarios.

**Acceptance criteria (demonstrate rather than assume):**

- [ ] Assumptions and result objects can be constructed and inspected.
- [ ] The 12 agreed inputs and their type/range intent are explicit.
- [ ] No database or HTTP imports are needed.
- [ ] The user can explain why domain objects differ from API and ORM models.

**Out of scope in this phase:** Do not add extra financial inputs or introduce calculation, API, database or ORM code.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Have me compare a dictionary versus a dataclass for the same financial assumptions before choosing an implementation.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.

---

# Phase 02 — Customer Economics and Calculation Logic

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 02 — Customer Economics and Calculation Logic** of **Project 2: Financial Scenario Engine** (M1 — Python Financial Engine).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Implement and test the 12-month customer opening, churn, acquisition and closing calculations.

**Guide me through these build and learning activities:**

1. Translate opening → churned → new → closing customer movements into deterministic functions.
2. Use opening customers to calculate churn, cap churn to opening customers, and round customer flows with `Decimal` + `ROUND_HALF_UP`.
3. Compute new customers from sales reps × opportunities per rep × win rate.
4. Roll closing customers to next month opening, producing 12 results.
5. Keep functions pure and outputs deterministic.
6. Write tests for base case, zero churn, 100% churn, zero sales staff, month roll-forward and never-negative closing customers.

**Technical concepts to learn:** Functions, scope, parameters, return values, control flow, iteration, `Decimal`, numeric rounding, pytest.

**Business/financial concepts to reinforce:** Customer acquisition, churn, net customer movement and growth dynamics.

**Acceptance criteria (demonstrate rather than assume):**

- [ ] For the base case, month 1 has 2 churned, 4 acquired and 102 closing customers.
- [ ] A 12-month customer series is produced without API/database.
- [ ] Boundary-case tests pass and results are explainable by hand.

**Out of scope in this phase:** No P&L, cash, HTTP or SQL implementation.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Ask me to derive and calculate the month-1 customer movement on paper, then translate one rule at a time to Python.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.

---

# Phase 03 — Revenue, Gross Profit and EBITDA

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 03 — Revenue, Gross Profit and EBITDA** of **Project 2: Financial Scenario Engine** (M1 — Python Financial Engine).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Extend monthly customer movements into deterministic financial revenue and profit calculations.

**Guide me through these build and learning activities:**

1. Use month-end/post-flow customers to calculate monthly recurring revenue.
2. Explain MRR versus exit ARR (12×MRR), and recognised monthly revenue equals billings for V1.
3. Calculate COGS, gross profit, operating payroll, marketing and EBITDA.
4. Compose financial logic using existing customer results rather than duplicating those calculations.
5. Apply consistent financial cent rounding with Decimal.
6. Write independent unit tests for the golden month 1 and edge conditions.

**Technical concepts to learn:** Function composition, intermediate variables, pure arithmetic, data transformation, structured financial outputs and tests.

**Business/financial concepts to reinforce:** SaaS subscription economics, gross margin, payroll, EBITDA, operating leverage, ARR run-rate versus annual revenue.

**Acceptance criteria (demonstrate rather than assume):**

- [ ] Month 1 base case: 102 customers, £20,400 revenue, £4,080 COGS, £16,320 gross profit, £20,000 payroll, £3,000 marketing and -£6,680 EBITDA.
- [ ] Revenue and profit are correctly generated for each of 12 periods.
- [ ] Tests derive expectations independently from source code.

**Out of scope in this phase:** Do not add cash, database, API or full three-statement accounting.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Ask me to calculate month-1 MRR, ARR, gross profit and EBITDA manually before coding.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.

---

# Phase 04 — Cash Flow, Forecast Summary and Financial Testing

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 04 — Cash Flow, Forecast Summary and Financial Testing** of **Project 2: Financial Scenario Engine** (M1 — Python Financial Engine).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Complete and test the standalone 12-month Python financial forecasting engine.

**Guide me through these build and learning activities:**

1. Introduce cash receipts with a zero- or one-month collection delay; opening receivables equal zero.
2. Explain why cash receipts differ from recognised revenue/EBITDA under collection lag.
3. Compute operating cash movement, opening and closing cash balances monthly.
4. Add 12-month summary: revenue sum, EBITDA sum, ending MRR, exit ARR, ending cash and first non-positive closing cash month (or null).
5. Integrate domain calculation into one simple callable function.
6. Use independent golden cases, boundary cases, parametrised tests, arithmetic reconciliations and repeated-run determinism.
7. Create a runnable example without any API framework.

**Technical concepts to learn:** Pure functions, module organisation, `Decimal` rounding, pytest fixtures, parametrisation, debugging and deterministic calculations.

**Business/financial concepts to reinforce:** Cash conversion, working capital timing, earnings vs cash, cash runway warning and limitations of a simplified cash bridge.

**Acceptance criteria (demonstrate rather than assume):**

- [ ] Immediate-collection base case month 1 EBITDA/operating cash -£6,680 and closing cash £143,320.
- [ ] Lag=1 month 1 receipts zero and EBITDA unchanged.
- [ ] Twelve periods plus summary are produced; important unit tests pass.
- [ ] The user can explain why this is not a GAAP/IFRS full cash-flow statement.

**Out of scope in this phase:** No FastAPI, PostgreSQL, deferred revenue, tax, financing or balance-sheet model.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** First ask me to predict how moving from zero-month to one-month collection changes revenue, EBITDA and closing cash.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.

---

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

---

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

---

# Phase 07 — Relational Databases, PostgreSQL and Raw SQL

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 07 — Relational Databases, PostgreSQL and Raw SQL** of **Project 2: Financial Scenario Engine** (M3 — Relational Persistence).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Learn relational storage and write SQL by hand before depending on the ORM.

**Guide me through these build and learning activities:**

1. Introduce persistence and compare SQL language with PostgreSQL database software.
2. Install/start PostgreSQL and connect using `psql` or a suitable client.
3. Reason through the proposed three-table schema, keys, foreign keys, checks and relationships.
4. Create a **disposable practice schema** (not the real application schema) with sample records.
5. Practice CREATE TABLE, INSERT, SELECT, WHERE, ORDER BY, UPDATE, DELETE, JOIN, GROUP BY/COUNT and EXISTS.
6. Explain what should persist versus what should be recalculated.
7. Demonstrate constraint failures and inspect stored data directly.

**Technical concepts to learn:** SQL syntax, relational concepts, PostgreSQL CLI, datatypes, constraints, identity keys, normalization and referential integrity.

**Business/financial concepts to reinforce:** Company identity, scenario assumptions as source data, derived forecast outputs.

**Acceptance criteria (demonstrate rather than assume):**

- [ ] The user can write a basic SQL query without AI.
- [ ] Tables/relations can be drawn and described.
- [ ] A bad FK or CHECK constraint fails as expected.
- [ ] No learning SQL work disrupts the future Alembic-managed app schema.

**Out of scope in this phase:** Do not treat SQLAlchemy as a substitute for understanding raw SQL. Do not create live application schema by hand.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Ask me to sketch companies → scenarios → assumptions and explain what happens if a scenario references a missing company.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.

---

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

---

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

---

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

---

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

---

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

---

# Phase 13 — Financial Scenario Comparison

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 13 — Financial Scenario Comparison** of **Project 2: Financial Scenario Engine** (M5 — Integrated Scenario Engine).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Compare 2–4 saved forecasts from one company against a selected baseline.

**Guide me through these build and learning activities:**

1. Define useful output metrics: annual revenue, annual EBITDA, exit ARR and ending cash.
2. Create sample Base, Upside and Downside scenarios.
3. Implement `GET /companies/{id}/scenario-comparison` with repeated `scenario_ids` query values.
4. Validate 2–4 distinct scenarios and same-company membership.
5. Calculate forecasts using existing engine; baseline is first supplied ID.
6. Compute absolute deltas and nullable percentage deltas where baseline is zero.
7. Test missing/duplicated IDs, cross-company selection, count bounds and arithmetic.
8. Demonstrate one end-to-end scenario comparison with raw JSON.

**Technical concepts to learn:** Query params, multi-record fetch, data aggregation, response contracts, separation of comparison from persistence.

**Business/financial concepts to reinforce:** Base/upside/downside planning, changes in revenue, profitability and cash risk.

**Acceptance criteria (demonstrate rather than assume):**

- [ ] Three named scenarios can be saved, forecast and compared.
- [ ] Comparison metrics reconcile to standalone forecasts.
- [ ] Invalid selections have deterministic 400/404/422 handling.
- [ ] No new finance tables required.

**Out of scope in this phase:** No frontend, scenario version history, advanced sensitivity or batch analytics.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Ask which financial KPIs best communicate scenarios and why, then introduce the agreed four V1 metrics.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.

---

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

---

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

---

# Phase 16 — Final Integration and Technical Mastery Examination

**Copy the prompt below into a NEW conversation within the Financial Scenario Engine ChatGPT Project.**

---

I am beginning **Phase 16 — Final Integration and Technical Mastery Examination** of **Project 2: Financial Scenario Engine** (M7 — Completion).

Act as my interactive engineering tutor. Follow the project's original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md` and the current `docs/PROJECT_STATE.md`.

**Phase objective:** Verify the finished backend from a clean environment and independently demonstrate technical mastery.

**Guide me through these build and learning activities:**

1. Audit all ten API endpoints, data model and financial assumptions against engineering specification.
2. Create a fresh test database, run Alembic revisions and all real tests.
3. Walk through company → scenario → PATCH → forecast → comparison → DELETE using real HTTP requests.
4. Complete README: setup, environment, commands, migration/test instructions, ER diagram, architecture and limitation notes.
5. Demonstrate the API locally or behind external access controls, not an open unauthenticated public writer.
6. Conduct interactive questioning about HTTP, Python, Pydantic, SQLAlchemy, SQL, PostgreSQL, transactions and tests.
7. Complete an independently implemented small change spanning two layers plus a test.
8. Document unresolved gaps, make final `PROJECT_STATE.md` handoff and assess readiness for next project.

**Technical concepts to learn:** End-to-end request tracing, maintainability, repeatability, independent implementation and debugging.

**Business/financial concepts to reinforce:** Interpretation and reliability of commercial scenario forecasts.

**Acceptance criteria (demonstrate rather than assume):**

- [ ] Full acceptance checklist met or explicit remaining items recorded.
- [ ] Fresh setup and demo verified.
- [ ] User can predict, alter, test and debug behavior without AI.
- [ ] Architecture and ER diagrams and known simplifications documented.

**Out of scope in this phase:** No additional unscoped production features, cloud platform build or elaborate frontend.

**Working method:** First inspect actual files and prior verified test results when accessible; distinguish planning from implementation. Explain concepts before or alongside small changes. Let me write/modify and test one meaningful increment at a time. Ask me to predict and explain behavior. Do not dump the entire solution or advance prematurely. If you cannot inspect local files, tell me exactly what to share.

**Begin with this action:** Begin with a repository-backed audit of the acceptance checklist; do not automatically declare completion.

Before closing, perform a 3–5-question knowledge check, review observed tests, determine COMPLETE or NOT YET COMPLETE, and update the PROJECT_STATE handoff with actual evidence.