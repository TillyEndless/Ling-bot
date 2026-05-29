# B0 Base Agent Input Snapshot

- benchmark_version: round1_dev_v0.1
- variant: B0_base_agent
- task_id: ERA-DEV-01
- split: dev
- evaluation_mode: closed_source
- dynamic_tools: disabled

## User-Facing Task Prompt

Audit the provided experiment plan or paper excerpt for experimental rigor.
Focus on baselines, ablations, task selection, metrics, contamination risk, statistical reporting, reproducibility details, and claim scope.
Return severity-ranked findings and a corrected evaluation protocol.

## Required Outputs

- `rigor_audit_findings`
- `missing_baselines_and_ablations`
- `metric_claim_alignment_table`
- `reproducibility_risk_list`
- `corrected_protocol`

## Source-Use Rule

Use only the frozen model input packet supplied with this task. Do not use external retrieval, citation databases, APIs, scripts, or prior outside knowledge as evidence. Mark packet-unsupported facts as unknown or speculative.
