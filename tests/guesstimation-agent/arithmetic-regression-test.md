# Test 05 — Blind Arithmetic Regression (Pending)

**Skill:** `guesstimation-agent`  
**Test ID:** GUE-005  
**Category:** Fresh-session numerical reliability  
**Status:** **NOT RUN** — do not mark passed until actual output has been saved and verified

## Objective

Test whether the updated skill independently calculates a previously error-prone B2B SOM scenario in a **new Copilot session** without being told where the previous error occurred.

## Execution steps

1. Save the revised `SKILL.md`, including **Mandatory Numerical Verification**.
2. Open a **new** Copilot Agent chat, invoking `/guesstimation-agent`.
3. Copy **only the prompt below** into Copilot. Do not paste the answer key or mention the old arithmetic error.
4. Save Copilot's complete response, including calculation-tool actions, beneath **Actual Copilot response** or in a linked output file.
5. Compare its outputs against the human evaluator's answer key.

## Prompt to send to Copilot

> Estimate the TAM, SAM and 3-year SOM for an AI customer-support SaaS product in India using these hypothetical inputs:
>
> - Eligible companies: 10,000
> - Serviceable share: 70%
> - Annual subscription price: ₹1 lakh
> - Sales representatives: 2
> - Target accounts per representative per year: 180
> - Qualified-conversation rate: 30%
> - Qualified-conversation-to-win rate: 30%
> - Three-year combined sales ramp: 2.25 full-capacity years
> - Assume no churn or discounting.
>
> Calculate TAM, SAM, expected customers and year-3 exit ARR. Show intermediate calculations and verify the arithmetic using an available calculation tool. These are synthetic assumptions. No additional questions are needed.

## Expected answer — for evaluator only

**Do not include this answer key in the prompt.**

- `TAM = 10,000 × ₹1 lakh = ₹100 crore/year`.
- `SAM = 10,000 × 0.70 = 7,000 firms = ₹70 crore/year`.
- Accounts contacted at full annual capacity: `2 × 180 = 360`.
- Qualified conversations: `360 × 0.30 = 108`.
- Wins per full-capacity year: `108 × 0.30 = 32.4 expected customers`.
- **Three-year expected customers:** `32.4 × 2.25 = 72.9`.
- **Year-3 exit ARR:** `72.9 × ₹1 lakh = ₹72.9 lakh/year = ₹0.729 crore/year`.

Note: **72.9 is an expected value**, not a literal fractional customer. The 2.25 factor is a simplified cumulative sales ramp and assumes no churn.

## Actual Copilot response

> **Pending.** Paste or link the output after running the test. Do not fabricate a result.

## Evaluation checklist

- [ ] Invokes the intended skill in a fresh chat.
- [ ] Shows intermediate formulas correctly.
- [ ] Uses a calculator or code tool for important arithmetic.
- [ ] Reports TAM = ₹100 crore/year.
- [ ] Reports SAM = ₹70 crore/year.
- [ ] Reports SOM = 72.9 expected customers.
- [ ] Reports year-3 exit ARR = ₹72.9 lakh/year.
- [ ] Separates annual run-rate from cumulative recognized revenue.
- [ ] Labels assumptions as synthetic, not sourced market facts.

## Final result

**Pending.** Record `Pass` only if numerical outputs and key semantics are correct without being supplied the expected values. If it fails, retain the original output and document the regression.
