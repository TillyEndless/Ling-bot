# B0 Base Agent Input Snapshot

- benchmark_version: round1_dev_v0.1
- variant: B0_base_agent
- task_id: LS-DEV-01
- split: dev
- evaluation_mode: closed_source
- dynamic_tools: disabled

## User-Facing Task Prompt

Produce a fixed-corpus literature map on transformer efficiency for AI/ML research.
Use only the provided source packet. Do not perform external retrieval.
Return a corpus coverage table, taxonomy of efficiency approaches, method-difference matrix, evidence-grounded synthesis, unsupported-synthesis warnings, and research gaps visible within the corpus.
Distinguish paper claims from your synthesis. If a method, metric, or conclusion is not supported by the packet, mark it as unsupported.

## Required Outputs

- `corpus_coverage_table`
- `literature_taxonomy`
- `method_difference_matrix`
- `core_paper_identification`
- `evidence_grounded_gap_list`
- `unsupported_synthesis_warnings`

## Source-Use Rule

Use only the frozen model input packet supplied with this task. Do not use external retrieval, citation databases, APIs, scripts, or prior outside knowledge as evidence. Mark packet-unsupported facts as unknown or speculative.
