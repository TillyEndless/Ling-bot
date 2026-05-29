# PS-DEV-01 Review Log

## 2026-05-29 Initial Human Review Decision

Status: `revisions_required`

Eligibility: `eligible_for_scoring: false`

Reviewer corrections applied:

- Revised PS1 to distinguish BERT Rediscovers edge-probing/layer-wise evidence from causal-use claims.
- Revised PS2 to treat BERTology as a survey and methodological context source, with explicit limitations and inference-time reliance concerns.
- Revised PS3 to focus Structural Probe on its specific geometric hypothesis.
- Moved the proposal-quality criterion out of `must_capture` into `proposal_quality_requirements`.
- Revised PS5 so the general causal-use warning is directly attributed to BERT Rediscovers and BERTology, with Structural Probe used only as a contextual example of a bounded structural hypothesis.
- Revised PS-E1 and PS-E2, including allowed claims for packet-local limitations and broader gaps requiring external review.
- Preserved PS-E3 while adding allowed claims about extractability and future causal-use tests.
- Replaced PS-E4 with a graded outside-corpus policy.
- Expanded inference-boundary requirements and optional high-value findings.
- Added corpus-role record for `local_seed_idea_representation_probing.md`.

Remaining blocker:

- The user must manually inspect and approve `local_seed_idea_representation_probing.md` as an appropriate task input and scoring reference before this task can be marked eligible for scoring.

## 2026-05-29 Acceptance Update

Status: `approved_with_minor_notes`

Eligibility: `eligible_for_scoring: true`

Acceptance correction applied:

- Treated `local_seed_idea_representation_probing.md` as `user_provided_research_motivation`.
- Set its scoring use to `context_only_not_authoritative_evidence`.
- Confirmed that it may constrain proposal relevance, but must not be used to score literature facts, literature gaps, or causal claims.

Remaining minor note:

- Scorers must keep proposal-quality requirements separate from packet-grounded paper findings.
