# Variant Runtime Instructions

You are running benchmark variant `B0_base_agent`. No research skill is loaded. Use only the task prompt and supplied source packet. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Task

- Task ID: `SPR-VAL-02`
- Split: `validation`
- Task type: `single_paper_deep_reading`
- Topic: sequence modeling for reinforcement learning
- Research question: What does the provided Decision-Transformer-style paper demonstrate, and where are its evidence boundaries?

## Input Prompt

Read only the provided source packet. Produce a structured paper card, claim ledger, evidence ledger, baseline/metric summary, reproducibility notes, and limitation summary.
Do not use external retrieval. If the packet does not contain a detail, say so.


## Required Outputs

- paper_card
- claim_ledger
- evidence_ledger
- baseline_metric_summary
- reproducibility_notes
- limitations_and_open_questions

# Source Packet

# SPR-VAL-02 Model Input Packet
## Sources
- Decision Transformer: Reinforcement Learning via Sequence Modeling (arXiv:2106.01345; 2021). Local file: `chen_2021_decision_transformer.pdf`. Included evidence: Abstract; method formulation; datasets/environments; baselines; experiments; limitations.

## Controlled Source Notes
- Decision Transformer paper: formulates offline reinforcement learning as conditional sequence modeling over trajectories and returns.
- Evidence objects: abstract, method formulation, datasets/environments, baseline/metric sections, experiments, reproducibility details, and limitations.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.

