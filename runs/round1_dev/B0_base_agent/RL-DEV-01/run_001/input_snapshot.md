# B0 Base Agent Input Snapshot

- benchmark_version: round1_dev_v0.1
- variant: B0_base_agent
- task_id: RL-DEV-01
- split: dev
- evaluation_mode: closed_source
- dynamic_tools: disabled

## User-Facing Task Prompt

Review the provided offline RL protocol using only the source packet.
Audit dataset coverage, behavior policy assumptions, train/eval separation, environment details, metrics, baselines, seeds, uncertainty reporting, and offline-to-online claim boundaries.
Return an RL-specific risk register and a revised protocol.

## Required Outputs

- `rl_protocol_audit`
- `dataset_and_environment_checklist`
- `baseline_and_metric_review`
- `claim_scope_assessment`
- `revised_protocol`

## Source-Use Rule

Use only the frozen model input packet supplied with this task. Do not use external retrieval, citation databases, APIs, scripts, or prior outside knowledge as evidence. Mark packet-unsupported facts as unknown or speculative.
