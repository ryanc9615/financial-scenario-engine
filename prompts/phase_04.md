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
