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
