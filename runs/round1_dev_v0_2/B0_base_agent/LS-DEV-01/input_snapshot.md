# Benchmark Task Input

Benchmark version: round1_dev_v0.2
Task ID: LS-DEV-01
Task type: literature_mapping
Topic: transformer efficiency
Evaluation mode: closed_source

## Research Question

Within the fixed source packet, what are the main research lines for making transformer computation more efficient, and what evidence does each paper provide?

## User Prompt

Produce a fixed-corpus literature map on transformer efficiency for AI/ML research.
Use only the provided source packet. Do not perform external retrieval.
Return a corpus coverage table, taxonomy of efficiency approaches, method-difference matrix, evidence-grounded synthesis, unsupported-synthesis warnings, and research gaps visible within the corpus.
Distinguish paper claims from your synthesis. If a method, metric, or conclusion is not supported by the packet, mark it as unsupported.


## Required Output Sections

- corpus_coverage_table
- literature_taxonomy
- method_difference_matrix
- core_paper_identification
- evidence_grounded_gap_list
- unsupported_synthesis_warnings

## Output Constraint

Use only the source packet provided below. Do not use external retrieval or dynamic tools.
