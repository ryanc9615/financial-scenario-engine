# Financial Scenario Engine — Engineering Specification

**Project:** Technical Apprenticeship, Project 2\
**Status:** Agreed V1 design; implementation not started\
**Last reviewed:** 2026-10-10\
**Priority:** Learn backend engineering through an end-to-end, independently explainable application.

> **Source of truth:** This document is the implementation contract distilled from the initial project scope and engineering-planning conversation. If an implementation choice needs to change, explain the trade-off and record the decision in `docs/DECISIONS.md`; do not silently enlarge scope. The original user-provided brief is preserved in `docs/ORIGINAL_SCOPE.md`.

## 1. Product definition

The **Financial Scenario Engine** is a Python backend service for a fictional B2B SaaS business. A client can create a company; create, retrieve, edit and delete named sets of operating assumptions; calculate a deterministic 12-month monthly financial forecast; and compare alternative saved scenarios. It exposes HTTP/JSON APIs and persists source data in PostgreSQL. Its primary outcome is competence with HTTP, Python application structure, validation, SQL, relational databases, transactions, persistence and testing—not a polished frontend or a production SaaS product.

**Initial client:** Swagger UI, cURL, Python or API-test client. Integrating the Project 1 frontend is optional and must not dominate V1.

**Pipeline to master:** client → HTTP request → API route → validation → application service → domain calculation and/or persistence → SQLAlchemy → SQL → PostgreSQL → result mapping → response serialization → HTTP/JSON. Not every request traverses every layer; an unsaved forecast does not touch PostgreSQL, while a saved-scenario creation need not calculate a forecast.

## 2. Scope and design principles

### In scope

- One fictional B2B SaaS company model, 12 monthly forecast periods, GBP only.
- Company creation/retrieval; scenario creation, read/list, partial update and delete.
- Pure Python financial engine with customer movements, MRR/ARR, revenue, COGS, gross profit, payroll, marketing, EBITDA and simplified operating cash bridge.
- Stateless forecasts from submitted assumptions and from saved scenarios; comparison of 2–4 scenarios from the same company.
- PostgreSQL source-data persistence, constraints, transactions, raw SQL exercises, SQLAlchemy ORM and Alembic migration.
- Unit, API, integration and direct database tests, basic error handling, logging and documentation.

### PARK FOR LATER

Authentication, authorisation, user accounts, OAuth, payments, true three-statement accounting, tax, capex, financing, multi-currency, SaaS pricing tiers, deferred revenue, annual contracts, historical scenario versioning, queues, microservices, advanced cloud/CI/CD, elaborate frontend, external integrations, LLMs, RAG, agents and ML.

### Invariants

1. **Source assumptions are persisted; financial outputs are recalculated.**
2. **Calculation logic is pure Python**, independent of HTTP and SQLAlchemy.
3. **SQL remains visible and teachable** even though an ORM is used.
4. **Do not build abstractions without a concrete need.**
5. **No unauthenticated write API exposed publicly.** Demonstrate locally or in protected development infrastructure.
6. Every completed phase has working functionality, observed tests and a knowledge check.

## 3. Domain model

- `Company`: business identity, name, fixed GBP currency, creation timestamp.
- `Scenario`: one company's named alternative operating plan, creation timestamp.
- `Assumptions`: exactly twelve inputs associated with one scenario (also accepted in the unsaved forecast endpoint).
- `MonthlyResult` and `Forecast`: calculated Python domain values, **not** database tables.
- `Comparison`: a calculated API result, **not** a database table.

**Three distinct representations:**

- Domain objects express financial rules (`Assumptions`, `Forecast`).
- API schemas express input/output contracts (Pydantic).
- ORM models map persisted records to SQL tables (SQLAlchemy).

A converter/map between domain, API and ORM may be necessary. Avoid making one type serve all three roles merely for convenience.

## 4. Financial model — V1 contract

### 4.1 Input assumptions and example case

| API/domain field | Example | Type and rule |
| --- | --- | --- |
| `starting_customers` | 100 | integer, >= 0 |
| `monthly_price` | £200.00 | Decimal, > 0 |
| `monthly_churn_rate` | 0.02 | Decimal in \[0,1\] |
| `sales_reps` | 2 | integer, >= 0 |
| `qualified_opportunities_per_rep` | 20 | integer, >= 0 |
| `win_rate` | 0.10 | Decimal in \[0,1\] |
| `monthly_marketing_spend` | £3,000.00 | Decimal, >= 0 |
| `other_fte` | 3 | integer, >= 0 |
| `monthly_fully_loaded_cost_per_fte` | £4,000.00 | Decimal, >= 0 |
| `gross_margin` | 0.80 | Decimal in \[0,1\] |
| `cash_collection_lag_months` | 0 | integer, 0 or 1 |
| `starting_cash` | £150,000.00 | Decimal, >= 0 |

Monetary values and rates are `Decimal` inside Python. In JSON, decimal monetary/rate values are represented by **strings** so precision is explicit (example: `"monthly_price": "200.00"`). Counts remain JSON integers. Reject invalid or out-of-range inputs at the API boundary and guard financial-domain invariants; database CHECK constraints protect persisted data as well.

### 4.2 Month-by-month calculations

For months `t=1..12`, define `opening_customers[1] = starting_customers`. The new/churned customer flows take effect at the start of the period. Customers are billed for the full month after those changes; there is no proration.

```text
churned_t        = min(opening_customers_t, round_half_up(opening_customers_t * monthly_churn_rate))
new_t            = round_half_up(sales_reps * qualified_opportunities_per_rep * win_rate)
ending_customers = opening_customers_t - churned_t + new_t
opening_customers_(t+1) = ending_customers_t

MRR_t          = ending_customers_t * monthly_price
exit_ARR_t     = 12 * MRR_t
revenue_t      = MRR_t
COGS_t         = revenue_t * (1 - gross_margin)
gross_profit_t = revenue_t - COGS_t
payroll_t      = (sales_reps + other_fte) * monthly_fully_loaded_cost_per_fte
EBITDA_t       = gross_profit_t - payroll_t - monthly_marketing_spend

receipts_t = revenue_t                    if cash_collection_lag_months == 0
receipts_t = revenue_(t-1) for t >= 2     if cash_collection_lag_months == 1
receipts_1 = 0                           if cash_collection_lag_months == 1
operating_cash_flow_t = receipts_t - COGS_t - payroll_t - monthly_marketing_spend
opening_cash_1 = starting_cash
ending_cash_t = opening_cash_t + operating_cash_flow_t
opening_cash_(t+1) = ending_cash_t
```

- Round customer flows to whole persons with `Decimal` + `ROUND_HALF_UP`.
- Round financial results to 2 decimal places with a documented consistent `Decimal` policy, with intermediate quantization where appropriate. Tests must reflect the chosen order of calculations.
- Sales productivity and spending are constant each month; no seasonality, customer expansion or sales pipeline carryover.
- Employee delivery costs are represented by COGS/gross margin; sales and other headcount are operating payroll. Do not double count.
- Assume monthly subscriptions invoiced during service month, with revenue equal to billings. The cash collection lag changes cash **not** recognised revenue or EBITDA.
- With lag 1, initial receivables are assumed zero, so there are no month-1 receipts.
- Cash balances may go below zero to show a funding shortfall. A negative balance is a forecast warning, not an automatic calculation error.

**Monthly output fields:** month number; opening/churned/new/ending customers; MRR; exit ARR; revenue; COGS; gross profit; payroll; marketing; EBITDA; opening cash; receipts; operating cash movement; closing cash.

**Forecast summary fields:** 12-month revenue sum; 12-month EBITDA sum; ending MRR; exit ARR; ending cash; first month with closing cash <= 0, or `null` if none. A full debt/tax/capex balance sheet is not supplied. ARR is a run rate (`12 × MRR`), never the annual total revenue.

### 4.3 Golden test — month 1

For the example assumptions: churn 2, new 4, ending customers 102, revenue/MRR £20,400.00, exit ARR £244,800.00, COGS £4,080.00, gross profit £16,320.00, operating payroll £20,000.00, marketing £3,000.00, EBITDA **-£6,680.00**, immediate-collection operating cash flow **-£6,680.00**, ending cash **£143,320.00**. Verify independently before implementing.

### 4.4 Why not three statements?

V1 is **P&L + simplified operating cash bridge**. It deliberately excludes receivables/balance-sheet accounting, deferred revenue, debt, taxes, capex and depreciation; do not describe this as GAAP/IFRS-compliant three-statement reporting.

## 5. API contract (ten endpoints)

| Method | Path | Request | Success | Main expected errors |
| --- | --- | --- | --- | --- |
| POST | `/forecasts` | complete assumptions | `200` 12-month forecast | `422` invalid body |
| POST | `/companies` | name, currency | `201` created company | `422` invalid values |
| GET | `/companies/{id}` | path ID | `200` company | `404`, `422` |
| POST | `/companies/{id}/scenarios` | name, assumptions | `201` scenario with assumptions | `404`, `409`, `422` |
| GET | `/companies/{id}/scenarios` | company ID | `200` scenario summaries | `404`, `422` |
| GET | `/scenarios/{id}` | scenario ID | `200` scenario with assumptions | `404`, `422` |
| PATCH | `/scenarios/{id}` | changed name and/or assumption fields | `200` updated scenario | `404`, `409`, `422` |
| DELETE | `/scenarios/{id}` | scenario ID | `204` no body | `404`, `422` |
| GET | `/scenarios/{id}/forecast` | scenario ID | `200` calculated forecast | `404`, `422` |
| GET | `/companies/{id}/scenario-comparison` | repeated `scenario_ids` query values (2–4) | `200` comparison | `400` cross-company, `404` unknown, `422` invalid |

**HTTP design:** GET for read-only retrieval; POST for resource creation and the stateless `/forecasts` calculation with a request body; PATCH for partial updates; DELETE for scenario removal. No separate PUT endpoint. GET requests never mutate saved records.

**Validation and error policy:**

- All IDs positive integers. Malformed IDs → 422, well-formed absent IDs → 404.
- Company `currency` fixed to GBP in V1; company and scenario names must be nonblank and <= 120 chars.
- Scenario names unique per company, case-sensitive. Conflicts → 409, including unique violations caused by races.
- Scenario PATCH requires at least one field; omission is different from an explicit zero. Revalidate the complete resulting assumption set before saving.
- Comparison: 2–4 **distinct** saved scenario IDs, all associated with the specified company; baseline is the first input scenario. Return absolute deltas and nullable percentage deltas if baseline is zero.
- API responses serialize decimals consistently as strings and timestamps as timezone-aware ISO 8601 strings.
- Expected application errors use a consistent small error body, e.g. `{"error":{"code":"SCENARIO_NAME_CONFLICT","message":"..."}}`; FastAPI built-in 422 `detail` format may remain standard.
- Unhandled infrastructure failures are logged internally and returned as sanitised 500 (or controlled 503) errors.

**Response schema concepts:** `CompanyCreate`, `CompanyResponse`, `AssumptionsCreate`, `AssumptionsPatch`, `ScenarioCreate`, `ScenarioPatch`, `ScenarioResponse`, `ScenarioSummary`, `MonthlyFinancialResult`, `ForecastResponse`, `ComparisonResponse`.

## 6. Data model and constraints

```text
companies (1) -------- (*) scenarios (1) -------- (1) scenario_assumptions
  PK id                  PK id                          PK + FK scenario_id
  name                   FK company_id                  12 financial inputs
  currency               name
  created_at             created_at

Forecast + comparison = derived in Python; NOT stored tables.
```

| Table | Columns and PostgreSQL types | Important constraints |
| --- | --- | --- |
| `companies` | `id BIGINT IDENTITY`, `name VARCHAR(120)`, `currency CHAR(3)`, `created_at TIMESTAMPTZ` | PK `id`; NOT NULL; trimmed name nonblank; currency = `GBP` |
| `scenarios` | `id BIGINT IDENTITY`, `company_id BIGINT`, `name VARCHAR(120)`, `created_at TIMESTAMPTZ` | PK `id`; FK company; UNIQUE(`company_id`, `name`); NOT NULL; trimmed name nonblank |
| `scenario_assumptions` | `scenario_id BIGINT`; `starting_customers INTEGER`; `monthly_price NUMERIC(14,2)`; `monthly_churn_rate NUMERIC(7,6)`; `sales_reps INTEGER`; `qualified_opportunities_per_rep INTEGER`; `win_rate NUMERIC(7,6)`; `monthly_marketing_spend NUMERIC(14,2)`; `other_fte INTEGER`; `monthly_fully_loaded_cost_per_fte NUMERIC(14,2)`; `gross_margin NUMERIC(7,6)`; `cash_collection_lag_months SMALLINT`; `starting_cash NUMERIC(14,2)` | `scenario_id` PK+FK `ON DELETE CASCADE`; all NOT NULL; numeric checks parallel API rules |

Use server-generated creation timestamps (UTC-aware). `companies` deletion is not part of V1. Each scenario has exactly one assumptions row after a successful create transaction. Constraints enforce at most one assumptions row; application transaction ensures required row is created.

**Indexes:** implicit PK indexes; unique `(company_id, name)` index; `(company_id, created_at DESC)` for sorted list. Inspect real query plans before adding more.

## 7. Stack and architectural boundaries

- Python; synchronous FastAPI; Pydantic v2; PostgreSQL; psycopg; SQLAlchemy 2.x; Alembic; pytest; Git/GitHub. Docker only if it materially aids later setup.
- `Decimal` for financial data; PostgreSQL `NUMERIC` for persisted financial data.
- No async database layer in V1: synchronous operations keep transactions comprehensible.

```text
app/
  main.py               # FastAPI app setup
  api/
    routes.py            # HTTP handling
    schemas.py           # Pydantic request / response contracts
  domain/
    financial_engine.py  # pure Python domain calculations
  services/
    scenarios.py         # workflows and domain/service errors
  db/
    models.py            # SQLAlchemy tables and ORM relations
    session.py           # engine, sessions, configuration
    queries.py           # database queries / persistence functions
  config.py              # environment-based config

tests/
  conftest.py
  test_financial_engine.py
  test_api.py
  test_database.py
migrations/
alembic.ini
pyproject.toml
.env.example
.gitignore
README.md
```

**This is a TARGET structure, not a directive to create empty modules during Phase 00.** Split modules only when implementation requires them. Avoid formal repository interfaces, dependency-injection containers, CQRS, microservices or similar abstractions.

**Main path:** API schemas validate, service orchestrates, domain calculates, DB layer queries. Domain calculation does not import FastAPI or SQLAlchemy. SQLAlchemy constructs/executes SQL through the driver; PostgreSQL executes SQL and enforces constraints.

## 8. SQL learning checklist tied to features

1. SELECT/WHERE: fetch a company by primary key.
2. JOIN/ORDER BY: list scenarios with saved assumptions.
3. LEFT JOIN/GROUP BY/COUNT: count scenarios for every company, including those with zero.
4. EXISTS/subquery: find companies with high-churn scenarios.
5. INSERT ... RETURNING: create a company; inspect ID generation.
6. UPDATE ... RETURNING: change churn for one scenario.
7. DELETE ... RETURNING: delete a scenario and examine `ON DELETE CASCADE`.
8. Explicit transaction: scenario + assumptions insertion; cause second insert to fail and verify rollback.
9. EXPLAIN (ANALYZE, BUFFERS): assess a company scenario-listing query and indexes.

Practice raw SQL in a disposable learning schema in Phase 07. Use Alembic-managed schema for the actual application from Phase 08 onward.

## 9. Migrations and schema evolution

- Baseline Alembic revision creates all three application tables.
- Intentional follow-on migration in Phase 14 adds `scenarios.description TEXT NULL`.
- Review generated migration, apply against populated test data, inspect actual DDL, test downgrade only on a disposable copy, reapply, and verify existing data preserved.
- Never recreate an inhabited database as a substitute for a migration.

## 10. Error ownership and testing

| Failure | Expected owner | Outcome |
| --- | --- | --- |
| Missing field, negative price, churn >100%, invalid collection lag | Pydantic + domain safeguards + DB CHECK | 422 from API |
| Missing company / scenario | Service | 404 |
| Duplicate scenario name | UNIQUE constraint + service translation | 409 |
| Comparison includes scenarios from another company | Service | 400 |
| Connection failure, unhandled calculation failure | Infrastructure boundary with internal logs | Sanitised 500/503 |

**Unit tests:** independent goldens; 12-month roll forwards; no negative customer counts; zero/100% churn; zero sales; gross margin edge; rounding; lag zero vs lag one; cash reconciliation; deterministic repeats.

**API tests:** happy paths and 422/404/409; JSON contracts; PATCH zero vs absent; comparison limits; no persistence from forecasts.

**Integration/database tests:** create/read after new session; update recalculates; foreign key, CHECK, UNIQUE; atomic transaction rollback; cascade; migration and fresh setup. Use disposable PostgreSQL test database, not a live developer data store.

**Debugging workflow:** reproduce → identify status/layer → inspect traceback/logs/generated SQL/data → form hypothesis → small fix → regression test. Deliberately inject one calculation, one validation and one persistence bug.

**Basic security:** prepared/parameterized queries, secrets in environment variables, `.env` excluded from Git, limited database user, sanitised error responses, no unauthenticated writable API exposed publicly. Production auth is PARK FOR LATER.

## 11. Delivery sequence

Seven milestones, split into seventeen tutor conversations (Phases 00–16). See `docs/PHASE_ROADMAP.md` and `prompts/`. **Build incrementally and require an acceptance gate at each milestone**.

- Milestone 1: Phases 00–04 — Python financial engine.
- Milestone 2: Phases 05–06 — HTTP and FastAPI.
- Milestone 3: Phases 07–08 — PostgreSQL and company persistence.
- Milestone 4: Phases 09–11 — scenario CRUD and transactions.
- Milestone 5: Phases 12–13 — saved forecasts and comparison.
- Milestone 6: Phases 14–15 — schema migration and reliability.
- Milestone 7: Phase 16 — repeatable demonstration and technical examination.

## 12. Final acceptance

- [ ] 12-month financial engine correct, tested, deterministic and separate from API/database.
- [ ] Ten documented HTTP endpoints function with expected response codes and validation.
- [ ] Three-table PostgreSQL schema with sensible constraints and relationships.
- [ ] Company and scenario persistence, CRUD and atomic transaction rollback verified.
- [ ] Saved forecasts and 2–4-scenario comparison agree with independently expected results.
- [ ] Raw SQL exercises performed, SQLAlchemy-generated SQL understood and query plan inspected.
- [ ] Initial and follow-on Alembic migrations work without deleting data.
- [ ] Unit, API and PostgreSQL integration tests pass in isolated environments.
- [ ] Secrets/config/errors handled at a secure-development baseline.
- [ ] Fresh setup steps, README, ER diagram and architecture are documented.
- [ ] A complete workflow can be demonstrated safely to another person.
- [ ] Learner can trace, change, test and debug the application **without AI**.