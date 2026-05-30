# Variant Runtime Instructions

You are running benchmark variant `B0_base_agent`. No research skill is loaded. Use only the task prompt and supplied source packet. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Task

- Task ID: `SPR-VAL-01`
- Split: `validation`
- Task type: `single_paper_deep_reading`
- Topic: world models
- Research question: What does the provided Dreamer-style world-model paper claim, and what evidence in the paper supports or limits those claims?

## Input Prompt

Read only the provided source packet. Produce a structured paper card, claim ledger, evidence ledger, experiment summary, reproducibility notes, and limitation summary.
Do not use external retrieval. Mark absent details as unknown.


## Required Outputs

- paper_card
- claim_ledger
- evidence_ledger
- experiment_summary
- reproducibility_notes
- limitations_and_open_questions

# Source Packet

# SPR-VAL-01 Model Input Packet
## Sources
- Mastering Diverse Domains through World Models (arXiv:2301.04104; 2023). Local file: `hafner_2023_mastering_diverse_domains_through_world_models.pdf`. Included evidence: Abstract; method/objective; domains; baselines; experiments; limitations.

## Controlled Source Notes
- DreamerV3 paper: presents a world-model agent intended to work across diverse domains and reports benchmark performance across multiple environments.
- Evidence objects: abstract, method/objective sections, experiment sections, baseline/result tables, ablations if supplied, reproducibility details, and limitations.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.

