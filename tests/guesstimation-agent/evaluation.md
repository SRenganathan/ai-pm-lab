# Guesstimation Agent — Evaluation Summary

**Project:** `ai-pm-lab`  
**Skill:** `.github/skills/guesstimation-agent/SKILL.md`  
**Evaluation type:** Manual functional testing, arithmetic checks, and model-behavior review  
**Overall status:** Promising prototype; **fresh arithmetic regression still pending**

## 1. Evaluation objective

Assess whether the skill can:

1. Ask for the user's problem and known assumptions before estimating.
2. Choose an appropriate market-sizing or Fermi framework.
3. Distinguish observed data, user-provided inputs, and illustrative assumptions.
4. Calculate TAM, SAM, SOM, or direct quantity estimates transparently.
5. Preserve existing assumptions across follow-up questions.
6. Check numerical accuracy and maintain consistent units/time periods.
7. Explain uncertainty, business implications, and trade-offs.

## 2. Test matrix

| ID | Test | Evidence | Result |
|---|---|---|---|
| GUE-001 | Consumer AI finance assistant TAM/SAM/SOM | [consumer-finance-test.md](consumer-finance-test.md) | **Pass with limitations** |
| GUE-002 | Renewal sensitivity (70% → 50%) | [sensitivity-test.md](sensitivity-test.md) | **Pass** |
| GUE-003 | B2B AI support SaaS market sizing | [b2b-saas-test.md](b2b-saas-test.md) | **Initial arithmetic failure** |
| GUE-003B | Prompted B2B arithmetic correction | [b2b-saas-test.md](b2b-saas-test.md) | **Correction passed** |
| GUE-004 | Bengaluru coffee cups/day | [general-guesstimation-test.md](general-guesstimation-test.md) | **Pass with limitations** |
| GUE-005 | Fresh-session B2B regression | [arithmetic-regression-test.md](arithmetic-regression-test.md) | **Not run** |

## 3. Observed strengths

### Interactive discovery

In consumer, B2B, and general estimation tests, the agent asked clarifying questions rather than immediately returning unsupported market-size numbers. The complete consumer discovery exchange was not archived; its conversational behavior was confirmed by the tester.

### Framework selection

The skill used **population × demand × monetization** for consumer finance, **company counts × price plus a direct-sales funnel** for B2B SaaS, and **population × participation × consumption** for daily coffee cups. It did not force TAM/SAM/SOM into the non-commercial coffee problem.

### Multi-turn consistency

When annual renewal changed from 70% to 50%, the agent correctly recomputed year-3 customers (`29,450 → 26,250`) and exit ARR (`₹2.94 crore → ₹2.62 crore`) without modifying TAM or SAM.

### Transparent uncertainty

The agent repeatedly disclosed that market populations, conversion rates, market shares, and scenario figures were illustrative—not validated research findings.

## 4. Critical failure and correction

In the first B2B SaaS output, optimistic SOM was **145.8** customers, whereas the stated formula yields **72.9**:

`180 accounts/rep/year × 2 reps × 30% meeting rate × 30% win rate × 2.25 ramp years = 72.9 expected customers`.

The initial answer therefore overstated optimistic exit ARR by 2× (`₹1.458 crore` instead of `₹0.729 crore`).

After an explicit verification request, Copilot used PowerShell calculations and corrected the figures. This demonstrates **correctability**, not yet proven **automatic error prevention**. The fresh blind regression is pending.

## 5. Remaining limitations

| Area | Observation | Action |
|---|---|---|
| SAM justification | Consumer model assumed 60% serviceability; B2B scenarios assumed 50–70% without measured filters | Ground serviceability in explicit product-fit and eligibility filters |
| Scenario provenance | Consumer conservative/optimistic input changes were not fully documented in the shared output | Require a complete scenario input table |
| Sensitivity ranking | Agent named major drivers but did not quantitatively rank comparable changes | Add one-at-a-time perturbation analysis |
| Population scope | Coffee estimate modeled adult consumption despite an all-servings question | Include other segments or explicitly narrow scope |
| Numerical reliability | One serious B2B multiplication error occurred | Require tool-based calculation and fresh regression |
| Commercial definitions | Some estimates rely on simplified no-churn or full-price assumptions | Label run-rate vs. recognized revenue and caveats |

## 6. Skill improvements to retain

Add or preserve these directives in `SKILL.md`:

- Verify each major numerical scenario with a calculation tool where available.
- Reconcile assumption tables, intermediate steps, and final summary outputs.
- Test percentage, time-period, lakh/crore, and revenue-vs-GMV conversions.
- Distinguish qualitative influential variables from quantitatively demonstrated sensitivity.
- Match the population actually modeled to the scope of the question.
- Identify proposed inputs as assumptions until independently validated.

These are intended instructions; **their effectiveness must be tested**, rather than assumed from their inclusion.

## 7. Release-readiness view

**Suitable as a public experimental Agent Skill with transparent limitations.** Not yet justified to claim reliable, production-grade financial forecasting or validated market research. Never present illustrative TAM/SAM/SOM estimates as externally verified facts.

### Remaining test before describing arithmetic reliability as verified

- [ ] Run GUE-005 in a new conversation **without showing the answer key**.
- [ ] Confirm tool-backed calculations and correct numerical outputs.
- [ ] Record actual output and update the regression verdict.
- [ ] If necessary, repeat across multiple independent problems/models.

## 8. Traceability

These reports were drafted from the actual Copilot responses and tester confirmations shared during development. They include **summaries and selected values**, not complete archived chat transcripts. For full reproducibility, save unedited Copilot outputs (and tool logs where available) alongside these files or link to them from each test report.

## 9. Next iteration

1. Complete the blind numerical regression test.
2. Confirm the skill's updated instructions are committed.
3. Add a fully recorded user-assumption interview test with all inputs traceable.
4. Test a marketplace model that distinguishes **GMV from platform revenue**.
5. Re-run earlier cases after future skill changes to detect regressions.
