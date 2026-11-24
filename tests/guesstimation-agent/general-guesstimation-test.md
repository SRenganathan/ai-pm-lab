# Test 04 — Bengaluru Daily Coffee Consumption

**Skill:** `guesstimation-agent`  
**Test ID:** GUE-004  
**Category:** Non-commercial, Fermi-style estimation  
**Status:** Passed initial methodology and arithmetic checks

## Objective

Verify that the skill handles a general quantity-estimation question without forcing TAM/SAM/SOM, asks appropriate boundary questions, builds a reproducible model and discloses uncertain inputs.

## Test prompt

> Estimate how many cups of coffee are consumed in Bengaluru every day.
>
> I don't have any numerical assumptions yet.
>
> Help me structure the problem and ask me relevant questions before calculating.
>
> Use a bottom-up estimation approach, explain your assumptions, show the calculations, and provide conservative, base, and optimistic estimates.
>
> Do not use TAM, SAM, or SOM unless they are genuinely relevant.

## Discovery behavior

Copilot asked two relevant boundary questions:

1. Bengaluru **urban area**, residents only, or wider metro; whether to count commuters and visitors.
2. All coffee servings (home, office, cafés) or only out-of-home servings.

The analysis used **Bengaluru urban area including residents, commuters and visitors**, and **all coffee settings**. The precise geographic boundary remained unspecified.

## Model and illustrative inputs

`Cups/day = unique people present during day × adult share × share of adults drinking coffee that day × cups consumed locally per drinker/day`.

| Input | Conservative | Base | Optimistic |
|---|---:|---:|---:|
| Unique people present | 10 million | 13 million | 16 million |
| Adult share | 75% | 75% | 75% |
| Adult daily coffee drinkers | 30% | 40% | 50% |
| Cups per drinking adult per day | 1.0 | 1.3 | 1.6 |

**All figures are illustrative, low-confidence inputs—not verified Bengaluru statistics.**

## Verified calculations

| Scenario | Formula | Cups/day |
|---|---|---:|
| Conservative | `10m × 0.75 × 0.30 × 1.0` | **2.25 million** |
| Base | `13m × 0.75 × 0.40 × 1.3` | **5.07 million** |
| Optimistic | `16m × 0.75 × 0.50 × 1.6` | **9.60 million** |

Copilot reported about **2.3m**, **5.1m**, and **9.6m** cups/day, consistent with rounding above, and identified the assumed population and coffee-drinker share as major uncertainties.

## Evaluation

| Criterion | Result | Notes |
|---|---|---|
| Asks useful boundary questions | Pass | Geography and meaning of “cup” |
| Uses appropriate bottom-up decomposition | Pass | Population × participation × frequency |
| Avoids inappropriate TAM/SAM/SOM | Pass | Direct cups/day output |
| Computes scenario arithmetic correctly | Pass | Tool-based calculation shown |
| Labels assumptions clearly | Pass | Low confidence / illustrative |
| Aligns modeled population with scope | Partial | Asked for **all** servings but omitted children |
| Defines geographic coverage precisely | Partial | Urban area remained approximate |
| Quantifies independent sensitivities | Partial | Identified drivers, did not rank numerically |

## Improvement actions

1. If the request includes all servings, model children's contributions separately or state explicitly that the result is **adult-only**.
2. Define geographic boundaries consistently for population inputs.
3. Distinguish unique people present over a day from simultaneous population, and avoid double-counting commuters or visitors.
4. Quantify key sensitivity drivers when sufficient assumptions are available.

## Verdict

**Passed initial general-guesstimation test.** Mathematical structure and transparency were good; scope completeness needs refinement.
