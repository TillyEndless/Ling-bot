# Variant Runtime Instructions

You are running benchmark variant `B3_your_v1_revised` for the `literature_analysis_and_research_rigor` module. Follow only the variant skill/reference content included below. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Variant Skill And References

## Variant File: variant/ai_ml_rl_literature_analysis/SKILL.md

---
name: ai-ml-rl-literature-analysis-and-research-rigor
description: Revised instruction-only skill for AI/ML/RL literature mapping, paper reading, method comparison, benchmark audit, RL protocol analysis, and evidence-grounded proposal support.
license: project-original
---

# AI/ML/RL Literature Analysis And Research Rigor

Use this skill for fixed-source research analysis in artificial intelligence, machine learning, and reinforcement learning. It is a literature-analysis and research-rigor module only. It does not schedule projects, manage repositories, execute experiments, monitor runs, retrieve papers, call APIs, parse PDFs, or maintain persistent state.

## Non-Negotiable Rules

1. Use only the task prompt and supplied source packet.
2. Do not import facts, citations, identifiers, numbers, or conclusions from memory.
3. Separate source-stated claims, extracted evidence, cross-source synthesis, proposed hypotheses, and unsupported speculation.
4. Prefer page, section, figure, table, appendix, or excerpt-level grounding when the packet provides it.
5. Label the evidence burden for important claims using the vocabulary in `references/evidence_traceability.md`.
6. Extract experimental details before interpreting results: task, data, model, baseline, metric, protocol, seed/run count, uncertainty, ablation, compute or hardware when supplied, and limitations.
7. Do not infer global method superiority from incompatible setups.
8. For RL, distinguish dataset collection, behavior policy, offline or online training, policy evaluation, reward/environment details, distribution shift, and deployment claims.
9. For representation or mechanism proposals, distinguish information recoverability, correlation, intervention evidence, causal use, and mechanism claims.

## Mode Selection

Choose the closest mode from the task:

- literature mapping
- single-paper structured reading
- method comparison
- benchmark or experimental rigor audit
- RL protocol analysis
- evidence-grounded proposal support

Load the relevant reference file and then produce the requested output sections. If the task requests a format, honor it while applying the evidence rules.

## Default Work Pattern

1. Source inventory: before analysis, concisely identify supplied source titles, paper versions when provided, sections, tables, figures, appendices, and other evidence objects. Keep this short; it supports the analysis but does not replace it.
2. Claim extraction: list major claims before synthesis.
3. Evidence ledger: attach each important claim to the most specific available source location and an evidence-burden label.
4. Rigor pass: check baselines, metrics, protocol, ablations, variability, reproducibility, and scope.
5. Boundary pass: label unsupported, speculative, or out-of-packet claims.
6. Final answer: concise, structured, and directly useful for research decisions.

Reference files:

- `references/workflow_modes.md`
- `references/evidence_traceability.md`
- `references/paper_reading_schema.md`
- `references/comparative_analysis_schema.md`
- `references/benchmark_and_experiment_audit.md`
- `references/rl_analysis_guidance.md`
- `references/inference_boundary_policy.md`


## Variant File: variant/ai_ml_rl_literature_analysis/references/benchmark_and_experiment_audit.md

# Benchmark And Experiment Audit

## Benchmark Validity

Assess whether the benchmark supports the intended claim.

| Audit area | Questions |
|---|---|
| Construct | What capability or property is the benchmark supposed to measure? |
| Task coverage | Are tasks representative or narrow? |
| Metric alignment | Do metrics measure the claimed property? |
| Aggregation | Are heterogeneous metrics combined transparently and defensibly? |
| Baselines | Are baseline systems relevant, strong, and fairly tuned? |
| Protocol | Are prompts, data splits, sampling, environment versions, and evaluation rules clear? |
| Leakage | Could train/test contamination, public benchmark exposure, or prompt leakage affect results? |
| Uncertainty | Are repeated runs, seeds, confidence intervals, or variance reported? |
| Reproducibility | Are artifacts, scripts, configs, model versions, data, and raw outputs available or specified? |

## Experimental Rigor

For experiments, extract:

- independent variable or intervention;
- controlled variables;
- datasets or environments;
- baselines;
- metrics;
- ablations;
- statistical or multi-run reporting;
- missing information;
- claim boundaries.

## Audit Language

State risks as risks unless the packet directly establishes a flaw. A missing detail weakens support; it is not proof that the original study failed to do the thing.

Use evidence-burden labels in audit findings:

- `DIRECT_PACKET_EVIDENCE` for source-stated design choices, metrics, reported results, and limitations.
- `WITHIN_PACKET_SYNTHESIS` for relations among packet-supplied tasks, metrics, baselines, or result tables.
- `LIMITED_CRITIQUE` for grounded audit concerns inferred from packet evidence or missing protocol detail.
- `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW` for claims about contamination, reproducibility, deployment robustness, or external validity that require evidence beyond the packet.


## Variant File: variant/ai_ml_rl_literature_analysis/references/comparative_analysis_schema.md

# Comparative Analysis Schema

## Method Comparison Matrix

| Dimension | Method or source A | Method or source B | Comparable as stated? | Evidence-burden label | Evidence | Boundary |
|---|---|---|---|---|---|---|

Recommended dimensions:

- objective;
- input data and supervision;
- optimization procedure;
- model or policy class;
- assumptions;
- baselines;
- datasets, environments, or tasks;
- metrics;
- compute or hardware when available;
- ablations;
- limitations and failure modes.

## Fairness Rules

- Compare within the same experimental setup when possible.
- If comparisons cross papers, state differences in data, model size, metrics, training budget, implementation, and evaluation protocol.
- A method can be better in a reported setup without being universally better.
- A result from one domain does not automatically transfer to another domain.
- If a source is an algorithmic foundation rather than a direct comparison, use it for mechanism/objective explanation, not direct empirical ranking.
- Label setup-specific comparisons as direct evidence only for the reported setup.
- Label cross-paper relations as synthesis unless the packet contains a direct shared evaluation.

## Output Checks

- Have all methods/sources been represented fairly?
- Are assumptions visible?
- Are incompatible protocols called out?
- Are claims limited to supported settings?
- Are unsupported ranking or transfer claims explicitly marked as needing external review?


## Variant File: variant/ai_ml_rl_literature_analysis/references/evidence_traceability.md

# Evidence Traceability

## Claim-Evidence Ledger

Use a ledger whenever the task has more than one substantive claim.

| Claim | Claim type | Evidence-burden label | Source location | Evidence directness | Supported scope | Missing detail |
|---|---|---|---|---|---|---|

Claim types include method definition, assumption, empirical result, benchmark result, comparison, limitation, mechanism claim, causal claim, reproducibility claim, and proposal hypothesis.

## Evidence-Burden Labels

Use these labels to make provenance and uncertainty visible:

- `DIRECT_PACKET_EVIDENCE`: directly stated in the provided source packet.
- `WITHIN_PACKET_SYNTHESIS`: synthesized from multiple packet-provided sources.
- `METHOD_BACKGROUND`: general method context from the provided materials.
- `LIMITED_CRITIQUE`: critique grounded in packet evidence but not directly stated by the source.
- `SPECULATIVE_PROPOSAL`: proposed hypothesis or future work, explicitly not established fact.
- `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`: claim requiring literature search or external evidence beyond the packet.

Prefer the narrowest label that fits. A claim may be useful even when it is not direct evidence, but its burden must be visible.

## Source Location Granularity

Use the most precise available location:

1. page plus section/table/figure/appendix;
2. section/table/figure/appendix without page;
3. source note or excerpt name;
4. source-level citation only when no finer location is supplied.

If the packet supplies exact locations, use them. If it does not, state that the packet does not provide finer grounding.

## Evidence Directness

- Direct: the source explicitly states the claim.
- Indirect: the claim follows from supplied details but is not directly stated.
- Partial: evidence supports only part of the claim.
- Comparative: evidence supports a relation between methods under a specific setup.
- Absent: the packet does not establish the claim.

## Citation Hygiene

Do not invent missing metadata. Do not cite absent papers. Do not use external memory as evidence. A citation is valid only if the supplied source supports the statement being made.


## Variant File: variant/ai_ml_rl_literature_analysis/references/inference_boundary_policy.md

# Inference Boundary Policy

## Claim Classes

- Source fact: directly stated in supplied material; usually `DIRECT_PACKET_EVIDENCE`.
- Extracted observation: result or detail read from supplied evidence; usually `DIRECT_PACKET_EVIDENCE`.
- Cross-source synthesis: relation among supplied sources; usually `WITHIN_PACKET_SYNTHESIS`.
- Method background: general method context supplied by the packet; usually `METHOD_BACKGROUND`.
- Grounded critique: audit concern based on packet evidence but not directly stated by the source; usually `LIMITED_CRITIQUE`.
- Proposed hypothesis: new testable idea grounded in supplied evidence; usually `SPECULATIVE_PROPOSAL`.
- Speculation: plausible but not established by supplied material; usually `SPECULATIVE_PROPOSAL` or `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`.
- Unsupported claim: not justified by the packet; use `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`.

## Boundary Rules

- Mark unsupported synthesis explicitly.
- Use evidence-burden labels to distinguish direct evidence, synthesis, grounded critique, proposal, and unsupported claims.
- Do not infer a field-wide literature gap from a small packet.
- Do not infer causality from correlation, probing, association, or representation recoverability alone.
- Do not infer mechanism from performance unless intervention or ablation evidence supports it.
- Do not infer deployment robustness from benchmark performance alone.
- Do not infer global superiority from setup-specific comparisons.
- Do not fill absent numbers, versions, metrics, seeds, or tables from memory.

## Proposal Rules

A useful proposal must state:

- a falsifiable hypothesis;
- observable outcomes that would support it;
- observations that would count against it;
- controls and baselines;
- feasibility and reproducibility requirements;
- the evidence still needed before making stronger claims.


## Variant File: variant/ai_ml_rl_literature_analysis/references/paper_reading_schema.md

# Paper Reading Schema

## Paper Card

| Field | Notes |
|---|---|
| Problem | What question or bottleneck the paper addresses. |
| Core method | Exact intervention or algorithmic idea. |
| Assumptions | Modeling, data, optimization, or evaluation assumptions. |
| Evidence | Experiments, theory, analysis, or benchmarks supplied. |
| Baselines | What the paper compares against. |
| Metrics | What outcomes are measured and how. |
| Ablations | Components, settings, or mechanisms tested separately. |
| Reproducibility | Code, configs, seeds, datasets, hardware, prompts, or missing details. |
| Limitations | Author-stated and evidence-implied boundaries. |

## Reading Order

1. Identify the paper's own contribution claim.
2. Extract the method definition before interpreting results.
3. Extract each evidence table or figure by role: main result, ablation, analysis, resource cost, failure mode, or limitation.
4. Separate what is demonstrated in the paper from what is plausible beyond it.
5. Mark absent details as unknown.

## Experimental Detail Checklist

- Models or systems evaluated.
- Datasets, tasks, environments, prompts, or benchmark suites.
- Baselines and whether they are strong and comparable.
- Metrics and aggregation.
- Number of seeds, runs, samples, trials, or evaluation episodes.
- Variability or uncertainty.
- Hyperparameters and tuning budget.
- Compute, hardware, or implementation details when supplied.
- Ablations and sensitivity analyses.


## Variant File: variant/ai_ml_rl_literature_analysis/references/rl_analysis_guidance.md

# RL Analysis Guidance

Use this reference for reinforcement learning and sequential-decision tasks.

## Core Distinctions

- Data collection policy versus learned policy.
- Offline training from fixed data versus online interaction.
- Simulator evaluation versus real-world deployment.
- Reward function, return metric, success metric, and normalized benchmark score.
- Behavior-policy support and learned-policy distribution shift.
- Environment version, wrappers, stochasticity, horizon, termination, and evaluation episodes.
- Policy value estimates versus actual rollout returns.

## Offline RL Checklist

| Item | What to extract |
|---|---|
| Dataset identity | Task, domain, version, collection regime, size if supplied. |
| Behavior policy | Known, unknown, mixture, expert, suboptimal, scripted, human, or generated. |
| Training mode | Fixed dataset only, online rollouts, model-based augmentation, or unclear. |
| Evaluation mode | Simulator rollout, logged-policy evaluation, off-policy estimate, real deployment, or unclear. |
| Metrics | Raw return, normalized score, success, regret, value estimate, or other. |
| Baselines | Behavior cloning, offline RL methods, online RL, random, expert, or task-specific baselines. |
| Variability | Seeds, runs, episodes, confidence intervals, or missing uncertainty. |
| Claim boundary | Benchmark performance, algorithmic property, deployment robustness, or generalization. |

## RL Failure Modes

- Treating trajectories as independent supervised examples while ignoring policy evaluation.
- Ignoring action-distribution shift or support mismatch.
- Equating normalized benchmark scores with universal absolute performance.
- Using offline value estimates as if they were verified returns.
- Generalizing simulator results to deployment without evidence.


## Variant File: variant/ai_ml_rl_literature_analysis/references/workflow_modes.md

# Workflow Modes

Begin every mode with a concise source inventory: source titles, versions when supplied, sections, tables, figures, appendices, and other packet-provided evidence objects. Use the inventory to avoid missing sources, not as a substitute for analysis.

## Literature Mapping

Goal: organize a fixed corpus into research lines and evidence boundaries.

Minimum steps:

1. Account for every source in the packet.
2. Assign source role using evidence only: method paper, survey, benchmark, empirical study, theory, systems artifact, boundary case, or motivation.
3. Group by technical mechanism, research question, evidence type, and evaluation target.
4. Compare claims only where setup compatibility is clear.
5. List unsupported syntheses and corpus coverage limits.
6. Mark broad synthesis or coverage claims with evidence-burden labels.

## Single-Paper Structured Reading

Goal: recover exactly what the paper claims and what supports it.

Minimum steps: method definition, author motivation, assumptions, experiment setup, baselines, metrics, ablations, limitations, reproducibility details, and unknowns.

## Method Comparison

Goal: compare methods without laundering setup differences into universal rankings.

Minimum steps: objectives, assumptions, data, optimization, baselines, metrics, evaluation protocols, evidence strength, and fair scope.

Label direct within-source comparisons separately from cross-source synthesis or limited critique.

## Benchmark Or Experimental Rigor Audit

Goal: decide whether a protocol supports a stated claim.

Minimum steps: construct validity, metric alignment, task selection, aggregation, baselines, ablations, uncertainty, leakage, reproducibility, and claim scope.

Separate source-stated protocol details from audit risks inferred from missing or incomplete details.

## RL Protocol Analysis

Goal: audit sequential decision evidence.

Minimum steps: environment, reward, behavior policy, data collection, train/eval separation, policy evaluation, return metric, stochasticity, distribution shift, seeds, and deployment boundaries.

## Evidence-Grounded Proposal Support

Goal: convert a vague idea into testable hypotheses without inventing field-wide novelty.

Minimum steps: packet facts, synthesis, hypotheses, predictions, disconfirming observations, experiments, controls, baselines, ablations, risks, and evidence needed for stronger claims.

Label new hypotheses as proposals and mark field-wide novelty claims as needing external review unless the packet directly supports them.


## Variant File: variant/ai_ml_rl_literature_analysis/variant_manifest.yaml

variant_id: B3_your_v1_revised
module_scope: literature_analysis_and_research_rigor
implementation_type: instruction_reference_only
runtime_tools_enabled: false
external_services_enabled: false
dynamic_retrieval_enabled: false
scripts_enabled: false
originality: project-original general AI/ML/RL research-analysis guidance
skill_directory: variants/B3_your_v1_revised/ai_ml_rl_literature_analysis
revision_scope:
  - concise source inventory discipline
  - evidence-burden labeling for provenance and uncertainty
  - general comparison, audit, and inference-boundary refinements
supported_modes:
  - literature_mapping
  - single_paper_structured_reading
  - method_comparison
  - benchmark_experimental_rigor_audit
  - rl_protocol_analysis
  - evidence_grounded_proposal_support
runtime_exclusions:
  - no upstream repository text copied
  - no task identifiers
  - no expected answer content
  - no dynamic tools
  - no Research OS orchestration


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

# Frozen Model Input Packet

# LS-DEV-01 Model Input Packet

## Corpus

1. Efficient Transformers: A Survey, arXiv:2009.06732, 39-page arXiv PDF.
2. Linformer: Self-Attention with Linear Complexity, arXiv:2006.04768, 12-page arXiv PDF.
3. Longformer: The Long-Document Transformer, arXiv:2004.05150, 17-page arXiv PDF.
4. FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness, arXiv:2205.14135, 34-page arXiv PDF.
5. LoRA: Low-Rank Adaptation of Large Language Models, arXiv:2106.09685, 26-page arXiv PDF.

## Controlled Source Notes

Efficient Transformers survey:

- The survey frames transformer efficiency around the standard attention mechanism's quadratic dependence on sequence length and organizes many approaches for reducing time or memory.
- The paper presents itself as a survey and taxonomy of efficient Transformer approaches.
- Relevant evidence locations: abstract; survey taxonomy sections; comparison tables; discussion/limitations.

Linformer:

- The paper proposes projecting keys and values to a lower-dimensional sequence axis to make self-attention linear in sequence length under its assumptions.
- Its Table 1 compares per-layer time complexity, listing Linformer as O(n) where standard self-attention is quadratic.
- Its empirical discussion includes validation perplexity and downstream classification evidence in the paper's reported settings.
- Relevant evidence locations: abstract; introduction; Section 3 method; Figure 2; Table 1; experiment section.

Longformer:

- The paper proposes local windowed attention plus task-motivated global attention for long documents.
- It claims linear scaling with sequence length for its attention pattern and evaluates both autoregressive language modeling and downstream long-document tasks.
- The paper focuses on long-document Transformer architecture and attention patterns.
- Relevant evidence locations: abstract; Figure 1; Table 1; Section 3; Tables 7-11; appendices on implementation details.

FlashAttention:

- The paper introduces an IO-aware exact attention algorithm that reduces memory reads/writes between GPU memory levels.
- The paper describes FlashAttention as an exact attention algorithm.
- The abstract states that FlashAttention is an IO-aware exact attention algorithm and also reports an extension to block-sparse attention.
- Section 3 describes an IO-aware attention algorithm using tiling to reduce HBM reads and writes while computing exact attention without materializing the full attention matrix.
- Reported speed and memory evidence appears in experiment tables and figures with stated model, hardware, and sequence settings.
- Relevant evidence locations: p. 1 Abstract; p. 4 Section 3; p. 7 Section 4.1 and Table 1 for BERT-large training-time comparison; p. 8 Table 2 for GPT-2 training-time comparison; theorem/complexity discussion; experiment tables and figures.

LoRA:

- The paper freezes pretrained model weights and injects trainable low-rank update matrices for adaptation.
- The paper frames LoRA around downstream adaptation with frozen pretrained weights and trainable low-rank update matrices.
- It reports large reductions in trainable parameters and memory for adaptation settings and evaluates on RoBERTa, DeBERTa, GPT-2, and GPT-3.
- Relevant evidence locations: abstract; Section 1; Section 4; Table 1; Table 2; GPT-3 experiment discussion; limitations paragraph in Section 4.

