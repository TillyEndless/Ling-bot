# B0 Base Agent Input Snapshot

- benchmark_version: round1_dev_v0.1
- variant: B0_base_agent
- task_id: MC-DEV-01
- split: dev
- evaluation_mode: closed_source
- dynamic_tools: disabled

## User-Facing Task Prompt

Using only the provided source packet, compare DPO-style preference optimization and PPO-style RLHF.
Produce a comparison matrix covering objectives, assumptions, data requirements, optimization dynamics, baselines, evaluation protocols, and evidence limits.
Mark any claim not supported by the packet as unknown or speculative.

## Required Outputs

- `method_comparison_matrix`
- `assumptions_table`
- `evidence_strength_summary`
- `fairness_caveats`
- `scoped_conclusions`

## Source-Use Rule

Use only the frozen model input packet supplied with this task. Do not use external retrieval, citation databases, APIs, scripts, or prior outside knowledge as evidence. Mark packet-unsupported facts as unknown or speculative.
