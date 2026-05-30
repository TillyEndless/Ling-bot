# Variant Runtime Instructions

You are running benchmark variant `B0_base_agent`. No research skill is loaded. Use only the task prompt and supplied source packet. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Task

- Task ID: `ERA-VAL-02`
- Split: `validation`
- Task type: `experimental_rigor_audit`
- Topic: generative model evaluation
- Research question: Does the provided generative-model evaluation section justify its quality and diversity claims?

## Input Prompt

Audit the provided generative-model experiment section using only the source packet.
Focus on metrics, baselines, dataset splits, sample selection, human evaluation if present, ablations, compute, and claim scope.
Return severity-ranked findings and a corrected evaluation protocol.


## Required Outputs

- rigor_audit_findings
- metric_claim_alignment_table
- baseline_and_ablation_review
- reproducibility_risk_list
- corrected_protocol

# Source Packet

# ERA-VAL-02 Model Input Packet
## Sources
- Denoising Diffusion Probabilistic Models (arXiv:2006.11239; 2020). Local file: `ho_2020_denoising_diffusion_probabilistic_models.pdf`. Included evidence: Abstract; experiments; sample quality/likelihood discussion; limitations.
- Improved Denoising Diffusion Probabilistic Models (arXiv:2102.09672; 2021). Local file: `nichol_2021_improved_ddpm.pdf`. Included evidence: Abstract; evaluation metrics; precision/recall; sampling speed; ablations.

## Controlled Source Notes
- DDPM paper: presents diffusion probabilistic models and evaluates sample quality and likelihood-related quantities on image-generation benchmarks.
- Improved DDPM paper: studies modifications to diffusion models, reports likelihood/sample-quality metrics, precision/recall style evaluation, and faster sampling settings.
- Evidence objects: abstracts, experiment sections, metric tables/figures, sample-quality comparisons, sampling-speed discussions, and ablations where supplied.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.

