# MC-DEV-01 Review Log

## 2026-05-29 Human Review Decision

Status: `approved_with_minor_notes`

Eligibility: `eligible_for_scoring: true`

Reviewer corrections applied:

- Preserved the DPO direct-policy-training finding while adding the implicit-reward interpretation.
- Replaced broad evidence locations with reviewed page, section, equation, figure, and table anchors.
- Clarified that DPO's own PPO comparisons are direct but setup-specific.
- Clarified that InstructGPT is a separate PPO-based RLHF pipeline source, not a DPO comparison.
- Clarified that the PPO paper is an algorithmic foundation/boundary source, with continuous-control and Atari evidence outside LLM preference-learning settings.
- Added allowed claims for setup-specific DPO-over-PPO statements and prohibited universal DPO-over-RLHF generalization.
- Replaced the outside-corpus hard-fail rule with a graded outside-corpus policy.
- Added corpus-role records for all three sources.

Remaining minor note:

- Scorers should enforce the distinction between DPO's direct within-paper PPO comparisons and unsupported cross-paper universal rankings.

