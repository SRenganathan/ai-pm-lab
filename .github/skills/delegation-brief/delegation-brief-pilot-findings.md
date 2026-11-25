# Delegation Brief — Exploratory Pilot Findings

**Project:** AI PM Lab / `delegation-brief`  
**Status:** Exploratory; not a validation study  
**Compiled:** 26 November 2026  
**Source:** Four paired baseline / skill-v1 scenario transcripts supplied by the author in conversation, followed by two skill-v2 retests.  
**Important:** These are fictional, constrained-choice decisions. No purchases or bookings were authorized or executed.

## 1. Research question

When should an AI assistant ask for a consequential preference, when is a provisional or conditional recommendation sufficient, and can a structured delegation brief improve the decision process without displacing the user's requested answer?

This pilot explores behavior. It does **not** establish an improvement in preference accuracy, user trust, retention, safety, or commercial economics.

## 2. Test conditions

- **Baseline:** Model answered the task without invoking `delegation-brief`.
- **Skill v1:** Model answered with the original `delegation-brief` skill invoked.
- **Skill v2:** Revised instructions explicitly prioritize completing the user's requested task, clarify selectively, and distinguish advice from execution.
- **Scenarios:** Fictional product catalogues with predefined costs and attributes; only information inside the prompts was available for selection.
- **Samples:** One observed response per condition for each scenario; no repeated runs or randomized ordering.
- **Unverified control:** Whether the baseline and skill runs used exactly the same application, model, sampling settings and system context was not independently established. Treat causal attribution to skill instructions as tentative.

## 3. Observed results

| Scenario | Baseline (no skill) | Skill v1 | Skill v2 | Interpretation |
|---|---|---|---|---|
| **A. Headphones: work vs travel priorities unclear** | Explicitly recommended **EverydayBalance**; documented equal-weight assumption, alternatives and adjustable illustrative weights | Generated a delegation brief with preferences, assumption, alternatives and authority; **no explicit recommendation or clarification question** in the corrected transcript | Explicitly and **provisionally** recommended **EverydayBalance**, documented which preference would change the choice; **no clarification question** | v2 addressed answer omission. Neither skill version demonstrated discovery of the user's *hidden* strong preference for microphone quality |
| **B. Hotel: trip certainty unclear** | Offered **NearMeet if confirmed / FlexStay if plans may change**; no question | Asked how firm trip dates were; after the user said plans might change and cancellation mattered, recommended **FlexStay** | Not retested | Skill v1 elicited the decision-changing preference before recommending, but both baseline and skill reached FlexStay once given that preference |
| **C. Hotel: dates confirmed; proximity/reviews prioritized** | Directly recommended **NearMeet**, no question | Directly recommended **NearMeet**, no question; documented accepted non-refundable trade-off | Not retested | No unnecessary question from either condition; no outcome improvement observed |
| **D. Backpack: exploratory, low-stakes choice** | Provisionally recommended **RainTrail**, explained conditions for alternatives | Described criteria and assumptions, but omitted the requested initial recommendation | Explicitly and provisionally recommended **RainTrail**; no extra question | v2 addressed answer omission without observed extra clarification friction |

### Headphone v2 verbatim outcome excerpt

> **Recommendation: EverydayBalance — ₹9,200.** It’s within budget and offers a balanced mix for work and travel: good microphone, good noise cancellation, excellent comfort, and the longest return window (14 days).

> Your exact balance between calls and noise cancellation is unknown, so EverydayBalance is a provisional all-round choice.

> **Boundary:** This is a recommendation only. No purchase or payment is authorized.

### Clarification outcome in hotel v1

The skill asked whether trip dates were firm. After receiving the user's statement that the schedule might change and avoiding a non-refundable booking mattered more than proximity, it recommended FlexStay at ₹7,300/night and noted the ₹500/night premium.

## 4. Key observations (descriptive, not causal)

1. **Answer completion:** In the two v1 cases subsequently retested, v1 omitted an explicit requested recommendation; v2 supplied one in both retests. This is encouraging for the narrow failure mode, not proof of robustness.
2. **Clarification is selective in observed samples:** Skill v1 asked a question in the ambiguous hotel case but not in the ambiguous headphones case. The reasons for this difference are not independently established.
3. **Final choice accuracy was not improved in the hotel comparison:** When both conditions received the user's cancellation preference, both recommended FlexStay.
4. **Baseline already showed useful uncertainty handling:** It explained assumptions, offered conditional alternatives, and sometimes provided an interactive preference adjustment. The skill cannot be credited for inventing those capabilities.
5. **All observed responses respected stated no-purchase/no-booking limits.** This is a descriptive observation, not evidence that the skill enforces permission boundaries against tools or malicious prompts.

## 5. Most important unresolved issue

In the headphone example, the fictional user's intended hidden priority was several hours of work calls from noisy places and rare flights. With that information, **ClearCall** would be a plausible preferred choice, given the catalog's 'excellent microphone' attribute. Neither the baseline nor skill-v2 learned that priority from the initial prompt; both offered EverydayBalance provisionally.

This is **not** a proven error when preferences are genuinely absent. The test demonstrates ambiguity and the limits of proceeding under assumptions; it does not show which intervention produces better user outcomes.

## 6. Product-design hypotheses worth testing next

- **H1 — Materiality:** Asking a targeted question is more worthwhile when different plausible preferences would materially change a consequential decision.
- **H2 — Stage of delegation:** For exploration, reversible recommendations with explicit assumptions can be more efficient than mandatory clarification.
- **H3 — Outcome completion:** A decision-support layer should not substitute a well-formatted decision brief for a concrete recommendation explicitly requested by the user.
- **H4 — Authority:** Advising, preparing an action, and executing a paid or irreversible action should remain separate permission states.

These are **hypotheses**, not measured conclusions.

## 7. Recommended next evaluation (before claiming a skill improvement)

1. **Freeze v2.** Record its exact `SKILL.md` version/commit. Do not tune it mid-test.
2. **Control the environment.** Use the same app, model, settings, prompt/catalogue, and fresh-session procedure for all comparisons. Record the app/model and versions.
3. **Repeat paired runs.** For each of four scenarios, run baseline and v2 at least three times each, if resources permit, rather than relying on a single sample. Alternate run order when practical.
4. **Record simple outcomes:** `answer_given`, `decision_pivot_identified`, `material_question_asked`, `unnecessary_question_asked`, `assumption_disclosed`, `authority_respected`, and `extra_turns`.
5. **Add counterfactual user-priority variants** to ambiguous scenarios: for headphones, 'calls-first' vs 'travel-first'; for hotels, 'dates firm' vs 'dates uncertain'. Ask the same follow-up to both conditions where necessary. Evaluate whether the result matches the **stated** preference, not an undisclosed ground truth.
6. **Report all runs and failures**, not only favorable examples. Keep fictional scenarios clearly labeled.

## 8. What a LinkedIn article can responsibly claim

**Supported by this pilot:** We observed a trade-off between structured preference documentation and answer completion in a tiny set of fictional decisions; v2 addressed two observed answer omissions. The hotel case showed a difference between clarification and a conditional answer, while both paths produced the same final choice after clarification.

**Not supported:** The skill improves recommendation accuracy, user trust, conversion, cost-to-serve, agent reliability, or commercial viability; the sample is too small and these outcomes were not measured.

**Possible central insight:** *Understanding decision pivots, choosing when to ask, and actually fulfilling the user's request are separate product capabilities. Optimizing one can accidentally weaken another.*

## 9. Publication and repository handling

Suggested repository location:

`experiments/delegation-brief/pilot-findings.md`

Keep the skill instructions in `.github/skills/delegation-brief/SKILL.md`, and link from the skill README to this pilot report. The write-up should describe v2 as **experimental** until it is evaluated more rigorously.
