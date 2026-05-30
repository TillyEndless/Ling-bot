# B3 Iter1 Revision Plan

Current best: `B3_your_v1_revised`.

## Targeted Weaknesses

1. Evidence-burden label overhead in proposal-support and long audit outputs.
   - Prior support: `B3_revision_failure_profile.md` notes that evidence-burden labels add a small amount of structural overhead, especially in proposal-support tasks.
   - General mechanism: instruct the skill to label major/substantive claims, not every sentence or low-level detail.
   - Not benchmark-specific: applies to any fixed-source AI/ML/RL analysis task.
   - Expected improvement dimensions: efficiency, output usefulness, readability.
   - Possible side effect: too few labels if the instruction becomes overly restrictive.

2. Source inventory placement can be inconsistent under constrained task formats.
   - Prior support: `B3_revision_failure_profile.md` notes that the inventory can appear inside the first requested section rather than as a separate compact heading.
   - General mechanism: make the inventory a compact preface or first table row only when the requested format leaves no room for a separate heading.
   - Not benchmark-specific: applies to arbitrary task prompts and source packets.
   - Expected improvement dimensions: source inventory quality, evidence traceability, output usefulness.
   - Possible side effect: extra heading can add mild verbosity if not kept short.

3. Evidence labels should not crowd method-comparison matrices.
   - Prior support: the comparison report says revised B3 improved evidence-burden labeling, but the residual risk is structural overhead.
   - General mechanism: allow one label per row or per major claim, and avoid repeating the same label in prose when already shown in a table.
   - Not benchmark-specific: a generic table-efficiency rule.
   - Expected improvement dimensions: efficiency, concision, comparison fairness preservation.
   - Possible side effect: less granular provenance for very dense comparisons.

## Revision Scope

Apply minimal edits to the current best B3 guidance:

- `SKILL.md`: make source inventory explicitly short and allow compact placement.
- `references/evidence_traceability.md`: add label-use economy guidance.
- `references/workflow_modes.md`: clarify compact inventory placement.
- `references/comparative_analysis_schema.md`: avoid duplicate labels in comparison prose.
- `references/inference_boundary_policy.md`: keep unsupported/speculative labels on substantive claims.

No task-specific facts, paper-specific conclusions, page/table answers, dynamic tools, scripts, APIs, retrieval, or validation assumptions will be added.

## Stop Criteria After Iter1

Accept only if it preserves the current best's factual accuracy and boundary discipline while improving or maintaining efficiency and readability. If gains are marginal or only stochastic, stop the loop and freeze the current best rather than pursuing further dev tuning.
