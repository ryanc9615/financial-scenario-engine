# Engineering Decision Log

Record decisions that affect scope, domain rules, API/database contracts or engineering approach. Reference the phase, reasoning and trade-offs. Avoid entries for tiny formatting choices.

| ID | Status | Decision | Why | Revisit when |
|---|---|---|---|---|
| D-001 | Accepted | One fictional GBP B2B SaaS model, 12 fixed monthly periods | Keeps financial complexity subordinate to backend learning | Later projects |
| D-002 | Accepted | Pure Python deterministic financial engine; persist assumptions, not forecast rows | Testability and no stale derived results | If explicit historical snapshot requirements arise |
| D-003 | Accepted | P&L and simplified cash bridge; no full three statements | Teaches cash vs earnings without large accounting subsystem | Separate accounting-focused project |
| D-004 | Accepted | Three relational tables for companies, scenarios, assumptions | Teaches keys, constraints and joins; keeps V1 small | If domain genuinely expands |
| D-005 | Accepted | Synchronous FastAPI + Pydantic + PostgreSQL/psycopg + SQLAlchemy + Alembic + pytest | Well-defined teaching path; avoids unnecessary concurrency complexity | After V1 |
| D-006 | Accepted | Decimal values as JSON strings; money/rates held as Decimal, NUMERIC in DB | Precision and consistent API contract | If clients require another representation |
| D-007 | Accepted | No production auth; demo locally or behind external access control | Auth is outside scope and unauthenticated writes are unsafe publicly | Full-stack/security project |
| D-008 | Accepted | Base case uses ending monthly customers for full-month MRR, revenue and billings | Explicit, deterministic simplified SaaS rules | Future realism work |
| D-009 | Accepted | Scenario comparison baseline is first requested scenario; 2–4 unique IDs | Simple, predictable V1 comparison contract | Later analytics project |
| D-010 | Accepted | Initial schema via Alembic; intentional `description` migration in Phase 14 | Makes migration concepts concrete | After executing migration |

## New decision template

```markdown
### D-011 — Short title
- **Phase/date:**
- **Status:** Proposed / Accepted / Superseded
- **Context:**
- **Decision:**
- **Consequences/trade-offs:**
- **Scope effect:** In V1 / PARK FOR LATER
```
