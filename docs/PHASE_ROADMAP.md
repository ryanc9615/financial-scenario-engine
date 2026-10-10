# Phased Build Roadmap — Financial Scenario Engine

**Status:** Planning complete; implementation starts at Phase 00.  
**Format:** Seven milestones broken into **17 separate guided tutor conversations**, Phases 00–16. A phase can require multiple work sessions. Schedule by **acceptance evidence**, not the calendar.

**Source of scope:** [`ORIGINAL_SCOPE.md`](ORIGINAL_SCOPE.md).  
**Technical contract:** [`ENGINEERING_SPEC.md`](ENGINEERING_SPEC.md).  
**Tutor method:** [`TUTOR_PROTOCOL.md`](TUTOR_PROTOCOL.md).  
**Project handoff:** [`PROJECT_STATE.md`](PROJECT_STATE.md).

## Milestones and gates

| Milestone | Phases | Delivery gate |
|---|---|---|
| 1 — Python Financial Engine | 00–04 | Pure Python 12-month forecast, tested without HTTP or DB |
| 2 — HTTP and APIs | 05–06 | Documented validated POST /forecasts endpoint |
| 3 — Relational Database | 07–08 | PostgreSQL schema and company persistence |
| 4 — Scenario Persistence & CRUD | 09–11 | Linked scenario/assumption CRUD and transaction safety |
| 5 — Integrated Forecasting | 12–13 | Saved scenario forecasts and comparisons |
| 6 — Reliability | 14–15 | Migration, controlled errors and robust tests |
| 7 — Final Integration & Mastery | 16 | Clean environment demo and technical examination |

## Ordered phase plan

| Phase | Conversation focus | Tangible result | Dependency |
|---|---|---|---|
| [00](../prompts/phase_00.md) | Project Setup and Development Workflow | Create and understand a clean Python development environment and a reproducible Git workflow before adding domain logic | — |
| [01](../prompts/phase_01.md) | Financial Domain Modelling in Python | Model the 12 financial inputs and structured calculation outputs before implementing formulas | Phase 00 completed |
| [02](../prompts/phase_02.md) | Customer Economics and Calculation Logic | Implement and test the 12-month customer opening, churn, acquisition and closing calculations | Phase 01 completed |
| [03](../prompts/phase_03.md) | Revenue, Gross Profit and EBITDA | Extend monthly customer movements into deterministic financial revenue and profit calculations | Phase 02 completed |
| [04](../prompts/phase_04.md) | Cash Flow, Forecast Summary and Financial Testing | Complete and test the standalone 12-month Python financial forecasting engine | Phase 03 completed |
| [05](../prompts/phase_05.md) | HTTP Fundamentals and First FastAPI Endpoint | Expose the independently tested financial engine as an HTTP JSON service | Phase 04 completed |
| [06](../prompts/phase_06.md) | API Contracts, Pydantic and Validation | Define and test robust request/response contracts for the stateless forecast endpoint | Phase 05 completed |
| [07](../prompts/phase_07.md) | Relational Databases, PostgreSQL and Raw SQL | Learn relational storage and write SQL by hand before depending on the ORM | Phase 06 completed |
| [08](../prompts/phase_08.md) | SQLAlchemy and Company Persistence | Connect FastAPI to PostgreSQL and build persistent create/get company operations | Phase 07 completed |
| [09](../prompts/phase_09.md) | Scenario Creation and Database Transactions | Save a scenario and its assumptions atomically as linked rows | Phase 08 completed |
| [10](../prompts/phase_10.md) | Scenario Retrieval, Listing and SQL JOINs | Retrieve a scenario with assumptions and list scenarios by company while learning JOINs | Phase 09 completed |
| [11](../prompts/phase_11.md) | Scenario Updates, Deletion and Integrity | Complete scenario PATCH and DELETE with correct partial semantics and referential integrity | Phase 10 completed |
| [12](../prompts/phase_12.md) | Calculating Saved Financial Scenarios | Combine saved assumptions with the pre-existing pure financial engine | Phase 11 completed |
| [13](../prompts/phase_13.md) | Financial Scenario Comparison | Compare 2–4 saved forecasts from one company against a selected baseline | Phase 12 completed |
| [14](../prompts/phase_14.md) | Database Migrations and Schema Evolution | Evolve the populated PostgreSQL database intentionally using Alembic | Phase 13 completed |
| [15](../prompts/phase_15.md) | Backend Reliability, Testing and Debugging | Harden the completed backend and learn evidence-based failure diagnosis | Phase 14 completed |
| [16](../prompts/phase_16.md) | Final Integration and Technical Mastery Examination | Verify the finished backend from a clean environment and independently demonstrate technical mastery | Phase 15 completed |

## Milestone completion gates

1. **Python engine (00–04):** Correct, deterministic customer/revenue/profit/cash forecasts; independent unit tests; no FastAPI or ORM needed.
2. **HTTP (05–06):** Stateless `POST /forecasts` serves complete JSON output with documented Pydantic validation and observed API tests.
3. **Relational database (07–08):** Three-table schema created by Alembic; company API persists across sessions; raw SQL and ORM SQL understood.
4. **Scenario CRUD (09–11):** Linked scenario + assumptions rows saved atomically; read/list/PATCH/DELETE, constraints, rollback and API tests verified.
5. **Integrated scenarios (12–13):** Persisted assumptions feed pure calculations; 2–4 scenario comparison reconciles to individual forecasts.
6. **Reliability (14–15):** Safe schema evolution, error-handling, logs, SQL inspection and multi-level tests proven.
7. **Mastery (16):** Reproducible new environment, documented API, full demo and independent technical examination.

## Repeatable conversation protocol

1. Open a **new chat in the same ChatGPT Project** and paste that phase's prompt.
2. Provide the latest `docs/PROJECT_STATE.md` and relevant code/test output if the tutor cannot directly read the repo.
3. Work one meaningful step at a time. Answer prediction questions, write or edit code and run tests locally.
4. Before finishing, use [`prompts/_end_phase_review.md`](../prompts/_end_phase_review.md). A phase is **COMPLETE** only with working evidence **and** understanding.
5. Save updated project-state record and commit relevant files. Open the next conversation.

If a chat becomes unwieldy, start a new one with [`prompts/_resume_phase.md`](../prompts/_resume_phase.md) and the current state. Never restart the phase from assumptions or skip prerequisites.

## Scope guardrails

No production user authentication, paid billing, LLMs, RAG, agents, complex frontend, true 3-statement financial reporting, data pipelines, distributed systems, microservices, Kubernetes or advanced cloud engineering. Label proposals in these domains **PARK FOR LATER**. A local Swagger demo is adequate; don't publish writable endpoints without access control.

## What must be demonstrated to advance

- Working feature with tangible input/output.
- Relevant tests actually executed (failure states too).
- Source code understood and accessible, not just generated.
- The learner can explain the mechanics and at least one meaningful trade-off.
- `PROJECT_STATE.md` updated with evidence and remaining problems.

**Rough effort only:** Earlier estimates for the original seven milestones totalled 67–101 focused hours; the 17-phase subdivision is for manageable tutoring, not 17 calendar days. Actual duration depends on baseline knowledge, environment and time spent debugging.
