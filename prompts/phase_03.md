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
