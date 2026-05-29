# B0 Base Agent Input Snapshot

- benchmark_version: round1_dev_v0.1
- variant: B0_base_agent
- task_id: PS-DEV-01
- split: dev
- evaluation_mode: closed_source
- dynamic_tools: disabled

## User-Facing Task Prompt

Using only the provided source packet, turn the seed idea into a small research proposal.
Produce scoped research questions, evidence-grounded hypotheses, falsification criteria, required experiments, baselines, ablations, and a risk register.
Clearly separate facts from the packet, synthesis, and your own proposed hypotheses.

## Required Outputs

- `scoped_research_questions`
- `hypothesis_table`
- `evidence_map`
- `experiment_plan`
- `risk_register`

## Source-Use Rule

Use only the frozen model input packet supplied with this task. Do not use external retrieval, citation databases, APIs, scripts, or prior outside knowledge as evidence. Mark packet-unsupported facts as unknown or speculative.
