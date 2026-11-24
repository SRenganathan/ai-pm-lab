# Test 01 — Consumer Finance TAM / SAM / SOM

**Skill:** `guesstimation-agent`  
**Test ID:** GUE-001  
**Category:** Consumer subscription market sizing  
**Status:** Initial conversational and modeling test completed; market inputs unverified

## Objective

Check whether the skill asks for the user's known assumptions before modeling a consumer opportunity, distinguishes assumptions from evidence, and produces transparent TAM, SAM, and SOM estimates.

## Initial user prompt

> I want to estimate the TAM, SAM and SOM for an AI-powered personal finance assistant in India.
>
> Help me build a realistic market-sizing estimate.
>
> Start by understanding my problem and asking me for the assumptions I already know. Don't jump directly into calculations. Guide me through the process step by step.

## Conversation behavior observed

- **Confirmed by tester:** Copilot asked for questions and assumptions before calculating.
- The complete intervening questions and user answers were **not archived** in the supplied test record. Do not infer which input values came from the user versus Copilot merely from the final output.
- Copilot explicitly classified the numerical assumptions as illustrative and low-confidence, not verified market statistics.

## Final model reported by Copilot

### Illustrative base-case assumptions

| Variable | Value | Basis in available record |
|---|---:|---|
| India population | 1.45 billion | Illustrative / not independently verified |
| Adult proportion | 70% | Illustrative / not independently verified |
| Urban proportion | 37% | Illustrative / not independently verified |
| Smartphone access | 80% | Illustrative / not independently verified |
| Willingness to pay | 10% | Illustrative / not validated |
| Realized price | ₹999 per year | Used in model; origin not independently established |
| Serviceable share | 60% of potential paid users | Illustrative, not derived from explicit fit filters |
| Year-1 / Year-2 / Year-3 prospects reached | 0.5m / 1m / 2m | Illustrative sales funnel |
| Trial rate / trial-to-paid rate | 10% / 10% | Illustrative conversion rates |
| Annual renewal | 70% | Illustrative retention assumption |

### Reproducible base-case calculations

- Eligible adults with assumed access: `1,450,000,000 × 0.70 × 0.37 × 0.80 = 300,440,000`.
- Potential paid users: `300,440,000 × 0.10 = 30,044,000`.
- **TAM:** `30,044,000 × ₹999 = ₹30,013,956,000 = ₹3,001.40 crore/year`.
- Serviceable paid users: `30,044,000 × 0.60 = 18,026,400`.
- **SAM:** `18,026,400 × ₹999 = ₹18,008,373,600 = ₹1,800.84 crore/year`.
- New paying subscribers by cohort: `5,000`, `10,000`, `20,000`.
- **Year-3 active subscribers:** `5,000 × 0.70² + 10,000 × 0.70 + 20,000 = 29,450`.
- **Year-3 exit ARR:** `29,450 × ₹999 = ₹29,420,550 = ₹2.94 crore`.

| Metric | Copilot's rounded answer | Verification |
|---|---:|---|
| TAM | ₹3,001 crore/year | Pass |
| SAM | ₹1,801 crore/year | Pass |
| Year-3 SOM | 29,450 active subscribers | Pass |
| Year-3 exit ARR | ₹2.94 crore | Pass |

Copilot also reported assumption-driven conservative and optimistic scenarios. Their full input tables are not present in the available response, so they are **not independently validated here**.

## Evaluation

| Criterion | Result | Evidence / qualification |
|---|---|---|
| Asks for assumptions before calculating | Pass (tester-confirmed) | Full discovery transcript unavailable |
| Chooses a meaningful model | Pass | Customer pool × willingness to pay × realized price; cohort-based SOM |
| Shows reproducible base calculations | Pass | Arithmetic verified above |
| Distinguishes sourced facts from assumptions | Pass | Final response calls inputs illustrative and low confidence |
| Explains serviceable market | Partial | 60% SAM filter not operationally substantiated |
| Documents scenario input changes | Partial | Only base-case inputs shared |
| Distinguishes revenue vs. ARR | Pass | SOM labeled year-3 **exit ARR**, not revenue booked over three years |

## Findings and improvements

1. **SAM needs explicit eligibility filters.** Replace the unsubstantiated 60% serviceability ratio with segment, language, product coverage, distribution, and payment constraints where feasible.
2. **Scenario tables need input transparency.** Display changed assumptions for conservative/base/optimistic cases, not just their results.
3. **Verify population intersections.** Applying nationwide adult, urban, and smartphone percentages sequentially is a simplifying assumption, not observed joint distribution.
4. **Clarify realized revenue.** State whether the annual figure reflects discounts, taxes, refunds, and collections.

## Verdict

**Passed initial consumer-market modeling test with limitations.** This is evidence of structured guesstimation behavior, not evidence that the Indian market estimate is empirically correct.
