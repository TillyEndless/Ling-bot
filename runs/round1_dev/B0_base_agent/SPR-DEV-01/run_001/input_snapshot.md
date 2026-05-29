# B0 Base Agent Input Snapshot

- benchmark_version: round1_dev_v0.1
- variant: B0_base_agent
- task_id: SPR-DEV-01
- split: dev
- evaluation_mode: closed_source
- dynamic_tools: disabled

## User-Facing Task Prompt

Read only the provided source packet. Produce a structured paper card, claim ledger, evidence ledger, reproducibility notes, and limitation summary.
Do not use external retrieval. If a fact is not in the packet, mark it as unknown.

## Required Outputs

- `paper_card`
- `claim_ledger`
- `evidence_ledger`
- `reproducibility_notes`
- `limitations_and_open_questions`

## Source-Use Rule

Use only the frozen model input packet supplied with this task. Do not use external retrieval, citation databases, APIs, scripts, or prior outside knowledge as evidence. Mark packet-unsupported facts as unknown or speculative.
