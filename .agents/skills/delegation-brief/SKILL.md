---
name: delegation-brief
description: Prepare or review a concrete delegation brief so an AI agent can represent a user's preferences, trade-offs, and authority before researching, recommending, or acting.
---

# Delegation brief

Help a user delegate one concrete decision or task without mistaking plausible assumptions for their preferences. Use the task, context and available evidence; this skill guides decisions and cannot enforce permissions or guarantee alignment.

1. Identify the decision, who benefits, time horizon, and what action is requested. Separate explicit requirements from inferred preferences and unknowns; quote or point to the user's actual evidence for consequential assumptions. Do not assume a preference belongs to the current user when buying for someone else or reuse stale memories without checking relevance. Minimize collection of sensitive information.
2. Identify material decision pivots: missing information or trade-offs likely to change the shortlist, recommendation, or authorized action. Separate hard constraints, soft preferences, and conditions of authority; mark unknowns rather than filling them in. Consider total price, practical fit, reversibility, timing, and privacy as relevant, not as a mandatory checklist.
3. Ask the smallest useful number of questions, prioritizing high-impact uncertainty. Prefer a concrete choice between plausible alternatives to a broad preference survey. If a low-stakes, reversible task can progress safely, present provisional options with assumptions and let the user correct them; do not block on irrelevant detail. If a material constraint, authorization, or consequential preference is unknown, clarify before the dependent decision.
4. Return a compact editable brief: objective, verified requirements, preferences and their trade-offs, assumptions and evidence, unresolved issues, authorized actions, and stopping/confirmation boundary. Distinguish research, recommendation, and execution; a preference is not purchase authorization. If asked to evaluate options, cite or label evidence and unknowns, compare options that make the main trade-off visible, and do not invent prices, availability, or product properties. Ask for approval before purchases or other consequential external actions unless explicitly authorized for the specific action and consistent with applicable controls.
5. Where appropriate, propose a lightweight check: compare two or more genuinely different options and ask which the user prefers and why. Do not claim such a check establishes alignment, assign fabricated numerical confidence, or equate approval of an option with proof that hidden preferences were understood. Revise the brief when the user corrects it; do not persist sensitive preferences or make them permanent without permission.

For a worked example read [references/example.md](references/example.md). For research and the limits of the design read [references/evidence.md](references/evidence.md).
