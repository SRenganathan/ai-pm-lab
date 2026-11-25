---
name: delegation-brief
description: Prepare or review a concrete delegation brief so an AI agent can represent a user's preferences, trade-offs, and authority before researching, recommending, or acting.
---

# Delegation brief

Help a user delegate one concrete decision or task without mistaking plausible assumptions for their preferences. Use the task, context and available evidence; this skill guides decisions and cannot enforce permissions or guarantee alignment.

1. Identify the decision, who benefits, time horizon, and what action is requested. Separate explicit requirements from inferred preferences and unknowns; quote or point to the user's actual evidence for consequential assumptions. Do not assume a preference belongs to the current user when buying for someone else or reuse stale memories without checking relevance. Minimize collection of sensitive information.
2. Identify material decision pivots: missing information or trade-offs likely to change the shortlist, recommendation, or authorized action. Separate hard constraints, soft preferences, and conditions of authority; mark unknowns rather than filling them in. Consider total price, practical fit, reversibility, timing, and privacy as relevant, not as a mandatory checklist.
3. Ask the smallest useful number of questions, prioritizing high-impact uncertainty. Ask a focused clarification when its answer is likely to change the recommendation **and** proceeding without it could lead to a consequential or hard-to-reverse mistake; first consider whether a transparent conditional recommendation would suffice. Do not assume a recommendation is as consequential as carrying out a purchase: distinguish advice, selection, and execution. If a low-stakes or exploratory task can progress safely, give a provisional answer with assumptions and let the user correct it. When a hard constraint or necessary authority for a requested *action* is unknown, clarify before that action. Never manufacture uncertainty to justify a question.
4. **Answer the user's requested task, not merely document it.** If asked to recommend an option and no decision-blocking uncertainty remains, explicitly name a recommendation and briefly explain why; for exploratory requests label the recommendation provisional. If a consequential missing preference prevents a responsible recommendation, ask one focused question and wait, or provide conditional choices if that meets the user's request. Then return a compact editable delegation brief as useful: objective, verified requirements, preferences and trade-offs, assumptions, unresolved issues, authorized actions, and confirmation boundary. The brief must not replace a recommendation the user requested. Distinguish research, recommendation, and execution; a preference is not purchase authorization. If asked to evaluate options, cite or label evidence and unknowns, compare options that expose the material trade-off, and do not invent prices, availability, product properties, or numerical suitability scores. Ask for approval before purchases or other consequential external actions unless explicitly authorized for the specific action and consistent with applicable controls.
5. Where appropriate, propose a lightweight check: compare two or more genuinely different options and ask which the user prefers and why. Do not claim such a check establishes alignment, assign fabricated numerical confidence, or equate approval of an option with proof that hidden preferences were understood. Revise the brief when the user corrects it; do not persist sensitive preferences or make them permanent without permission.

## Before responding: quick quality check

- Did I actually answer the user's request (e.g., name a product when asked for an initial recommendation)?
- If I am asking a question, can I explain exactly how the answer could materially change the outcome, and why a provisional or conditional recommendation is insufficient?
- Did I label assumptions and accepted trade-offs without presenting them as confirmed preferences?
- Did I keep authorization for purchases and external actions separate from the recommendation itself?

For a worked example read [references/example.md](references/example.md). For research and the limits of the design read [references/evidence.md](references/evidence.md).
