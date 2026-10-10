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
