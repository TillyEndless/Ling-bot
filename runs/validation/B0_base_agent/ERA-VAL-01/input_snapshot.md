# Variant Runtime Instructions

You are running benchmark variant `B0_base_agent`. No research skill is loaded. Use only the task prompt and supplied source packet. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Task

- Task ID: `ERA-VAL-01`
- Split: `validation`
- Task type: `experimental_rigor_audit`
- Topic: LLM benchmark contamination
- Research question: Does the provided LLM evaluation evidence support the claimed model capability, given possible benchmark contamination and protocol issues?

## Input Prompt

Audit the provided LLM evaluation excerpt or proposal for experimental rigor.
Focus on contamination risk, benchmark saturation, prompt protocol, baseline selection, statistical reporting, evaluation leakage, and claim scope.
Return severity-ranked findings and a corrected evaluation protocol.


## Required Outputs

- rigor_audit_findings
- contamination_and_leakage_risk_table
- baseline_and_metric_review
- claim_scope_assessment
- corrected_protocol

# Source Packet

# ERA-VAL-01 Model Input Packet
## Sources
- Language Models are Few-Shot Learners (arXiv:2005.14165; 2020). Local file: `brown_2020_language_models_are_few_shot_learners.pdf`. Included evidence: Abstract; evaluation/benchmark descriptions; contamination discussion; limitations.
- Measuring Massive Multitask Language Understanding (arXiv:2009.03300; 2021). Local file: `hendrycks_2021_measuring_massive_multitask_language_understanding.pdf`. Included evidence: Abstract; benchmark/task design; evaluation protocol; limitations.

## Controlled Source Notes
- GPT-3 paper: reports few-shot, one-shot, and zero-shot benchmark evaluation across many NLP tasks and includes a contamination analysis discussion for test-set overlap risk.
- MMLU paper: introduces a multitask benchmark for measuring knowledge and reasoning across many subjects and reports model results under defined evaluation settings.
- Evidence objects: GPT-3 abstract, evaluation sections, contamination analysis appendix/section, benchmark result tables; MMLU abstract, benchmark construction sections, evaluation protocol, result tables, limitations.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.

