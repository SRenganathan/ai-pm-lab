# Test 02 — Consumer Subscription Retention Sensitivity

**Skill:** `guesstimation-agent`  
**Test ID:** GUE-002  
**Category:** Multi-turn assumption revision  
**Status:** Passed arithmetic and model-state checks

## Objective

Determine whether the agent can change one assumption in an existing TAM/SAM/SOM model, preserve other inputs, recompute only affected results, and explain the business implication.

## Test prompt (sent in the existing consumer-finance conversation)

> Let's challenge the assumptions in your base-case estimate.
>
> Reduce annual renewal from 70% to 50%, keeping every other assumption unchanged.
>
> Recalculate the year-3 SOM and explain the impact on active subscribers and exit ARR.
>
> Show the original and revised cohort calculations. Do not recalculate TAM or SAM unless they are affected.
>
> Also identify the three assumptions that have the greatest influence on year-3 SOM.

## Preserved assumptions

- New paying subscribers: Year 1 `5,000`, Year 2 `10,000`, Year 3 `20,000`.
- Annual realized subscription price: `₹999`.
- Original renewal: `70%`; revised renewal: `50%`.
- All market-size and acquisition assumptions unchanged.

## Verified calculations

| Cohort | Original: 70% renewal | Revised: 50% renewal |
|---|---:|---:|
| Year 1 retained into Year 3 | `5,000 × 0.70² = 2,450` | `5,000 × 0.50² = 1,250` |
| Year 2 retained into Year 3 | `10,000 × 0.70 = 7,000` | `10,000 × 0.50 = 5,000` |
| New Year 3 subscribers | `20,000` | `20,000` |
| **Year-3 active subscribers** | **29,450** | **26,250** |
| **Year-3 exit ARR** | **₹2.942055 crore** | **₹2.622375 crore** |

- Difference: `3,200` fewer active subscribers.
- Revenue run-rate decrease: `3,200 × ₹999 = ₹3,196,800 = ₹31.968 lakh`.
- Relative decline: `3,200 / 29,450 ≈ 10.87%`.
- **TAM and SAM remain unchanged** because renewal affects retained customers, not the defined addressable population.

## What Copilot actually reported

Copilot reported **26,250 subscribers**, **₹2.62 crore exit ARR**, **3,200 fewer subscribers**, and approximately **10.9% decline**, all consistent with the arithmetic above. It preserved TAM/SAM and the acquisition funnel.

Copilot identified three influential SOM levers:

1. Qualified prospect reach.
2. Trial and paid conversion rates.
3. Annual renewal.

It also correctly noted that price changes exit ARR but not subscriber count.

## Evaluation

| Criterion | Result |
|---|---|
| Preserves unchanged model assumptions | Pass |
| Recalculates retained cohorts | Pass |
| Computes ARR and delta correctly | Pass |
| Keeps TAM/SAM unchanged | Pass |
| Explains causal business impact | Pass |
| **Quantitatively ranks** assumptions by sensitivity | Partial — qualitative lever identification only |

## Recommended improvement

When asked what drives SOM most, perform comparable one-at-a-time changes (for example, ±10% where meaningful), recompute outputs, and **rank by measured effect**. Label qualitative rankings as hypotheses, not measured sensitivity.

## Verdict

**Passed sensitivity-recalculation test.** Quantified ranking of competing assumptions remains an improvement opportunity.
