# Variant Runtime Instructions

You are running benchmark variant `B0_base_agent`. No research skill is loaded. Use only the task prompt and supplied source packet. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Task

- Task ID: `PS-VAL-02`
- Split: `validation`
- Task type: `evidence_grounded_proposal_support`
- Topic: mechanistic interpretability
- Research question: Can the provided mechanistic-interpretability claim be turned into a cautious, testable research proposal?

## Input Prompt

Using only the provided source packet, develop a small proposal to test the mechanistic-interpretability claim.
Produce scoped research questions, evidence-grounded hypotheses, causal tests or interventions, controls, falsification criteria, alternative explanations, and a risk register.
Do not treat correlational evidence as causal proof.


## Required Outputs

- scoped_research_questions
- hypothesis_table
- evidence_map
- causal_test_plan
- alternative_explanations
- risk_register

# Source Packet

# PS-VAL-02 Model Input Packet
## Sources
- Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 small (arXiv:2211.00593; 2022). Local file: `wang_2022_interpretability_in_the_wild_ioi.pdf`. Included evidence: Abstract; circuit analysis; interventions/ablations; limitations.
- Locating and Editing Factual Associations in GPT (arXiv:2202.05262; 2022). Local file: `meng_2022_locating_and_editing_factual_associations.pdf`. Included evidence: Abstract; causal tracing; editing intervention; scope.
- local_mech_interp_claim.md (local_seed_brief; 2026). Local file: `local_mech_interp_claim.md`. Included evidence: User/evaluator-provided seed idea or claim brief for proposal construction.

## Controlled Source Notes
- IOI circuit paper: analyzes a circuit for indirect-object identification in a language model and reports mechanistic evidence including intervention/ablation-style analyses.
- ROME paper: studies localization and editing of factual associations in language models using causal tracing and model editing experiments.
- Local claim brief: asks for a cautious test of whether a localized internal circuit or representation is responsible for a behavior.
- Evidence objects: abstracts, method sections, causal/intervention sections, result tables/figures, and limitations.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.

