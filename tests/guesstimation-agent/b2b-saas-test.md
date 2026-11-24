# Test 03 / 03B — B2B SaaS Market Sizing and Error Correction

**Skill:** `guesstimation-agent`  
**Test IDs:** GUE-003 (initial), GUE-003B (prompted correction)  
**Category:** B2B subscription sales-funnel sizing  
**Status:** Initial calculation failed; corrected after explicit verification request

## Objective

Evaluate TAM/SAM/SOM for a direct-sales B2B AI support platform, including ability to define the company segment, disclose assumptions, use sales capacity for SOM, and check arithmetic.

## Initial test prompt

> I want to estimate the TAM, SAM, and SOM for an AI customer-support platform targeting mid-sized e-commerce companies in India.
>
> The platform automates customer queries, order tracking, returns, and support ticket resolution.
>
> Here are the assumptions I currently know:
> - Target market: Indian mid-sized e-commerce companies
> - Pricing: ₹1 lakh per customer per year
> - Supported languages: English and Hindi
> - Sales model: Direct B2B sales
> - SOM horizon: 3 years
>
> I don't know the number of eligible companies, likely adoption rates, or expected sales conversion.
>
> Help me build this estimate interactively. Ask me relevant questions before calculating. Where information is unavailable, explicitly identify illustrative assumptions rather than inventing market statistics. Show the calculations and explain the key business implications.

## Discovery behavior

Copilot asked for (1) the meaning of *mid-sized*, (2) serviceable-scope filters, and (3) three-year sales capacity. It proceeded with explicitly **illustrative**, not sourced, company counts and sales-funnel assumptions.

## Assumptions from Copilot's model

| Input | Conservative | Base | Optimistic |
|---|---:|---:|---:|
| Eligible companies (illustrative) | 2,000 | 5,000 | 10,000 |
| Serviceable share (illustrative) | 50% | 60% | 70% |
| Price per customer per year | ₹1 lakh | ₹1 lakh | ₹1 lakh |
| Sales reps | 1 | 1 | 2 |
| Accounts targeted per rep/year | 80 | 120 | 180 |
| Target account → qualified conversation | 15% | 20% | 30% |
| Qualified conversation → win | 20% | 25% | 30% |
| Combined three-year ramp | 2.25 full-capacity years | 2.25 | 2.25 |
| Churn / discounting | None | None | None |

## Correct model

- `TAM = eligible companies × ₹1 lakh/year`.
- `SAM = eligible companies × serviceable share × ₹1 lakh/year`.
- `Expected customers by Year 3 = reps × accounts targeted per rep/year × meeting rate × win rate × 2.25`.
- `Exit ARR = expected customers × ₹1 lakh/year`.

| Scenario | TAM/year | SAM/year | Expected Year-3 customers | Exit ARR |
|---|---:|---:|---:|---:|
| Conservative | ₹20 crore | ₹10 crore | 5.4 | ₹5.4 lakh/year |
| Base | ₹50 crore | ₹30 crore | 13.5 | ₹13.5 lakh/year |
| Optimistic | ₹100 crore | ₹70 crore | **72.9** | **₹72.9 lakh/year** |

### Error observed in initial output

Initial optimistic SOM was reported as **145.8 customers / ₹1.458 crore exit ARR**. But:

`180 × 2 × 0.30 × 0.30 × 2.25 = 72.9`, **not 145.8**.

The initial optimistic SOM was overstated by **2×**. TAM and SAM were correct.

### Prompted correction (Test 03B)

The tester asked Copilot to independently recalculate each scenario, show intermediate multiplication, identify errors, and use a calculation tool if available. Copilot ran a PowerShell calculation and correctly returned **72.9 customers / ₹72.9 lakh exit ARR**, acknowledging that its earlier optimistic SOM was doubled.

## Evaluation

| Criterion | Result | Notes |
|---|---|---|
| Asks relevant B2B clarifying questions | Pass | Company size, product fit and sales capacity |
| Uses appropriate TAM/SAM definitions | Pass with assumptions | Firm count and serviceability filters unverified |
| Derives SOM from sales execution | Pass | Funnel and ramp model rather than arbitrary share |
| Labels uncertainty | Pass | All unsupported counts and rates called illustrative |
| Initial scenario arithmetic | **Fail** | Optimistic SOM overstated by 100% |
| Corrects error when challenged | Pass | PowerShell verification plus acknowledgment |
| Prevents the error in a fresh blind run | **Not yet tested** | See `arithmetic-regression-test.md` |

## Root-cause hypothesis and fix

The original output included an unchecked or incorrectly evaluated multiplication. This observation alone does not reveal the model's internal mechanism.

**Skill improvement:** Require calculator/code-based verification of each scenario, plus consistency checks between assumption tables, intermediate arithmetic and summary numbers.

## Verdict

**Conditional pass for methodology; initial numerical-accuracy failure.** Prompted correction succeeded. A fresh, unhinted regression test is needed before claiming the arithmetic safeguard is effective.
