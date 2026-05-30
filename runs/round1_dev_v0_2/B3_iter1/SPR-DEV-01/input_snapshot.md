# Variant Runtime Instructions

You are running benchmark variant `B3_iter1` for the `literature_analysis_and_research_rigor` module. Follow only the variant skill/reference content included below. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

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

1. Source inventory: before analysis, concisely identify supplied source titles, paper versions when provided, sections, tables, figures, appendices, and other evidence objects. Keep this to a short preface or compact first table; it supports the analysis but does not replace it.
2. Claim extraction: list major claims before synthesis.
3. Evidence ledger: attach each important claim to the most specific available source location and an evidence-burden label. Label major claims and table rows; avoid repeating labels for every sentence.
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
- In matrices, one evidence-burden label per row is usually enough; avoid duplicating the same label again in adjacent prose unless the claim changes.

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

Prefer the narrowest label that fits. A claim may be useful even when it is not direct evidence, but its burden must be visible. Use labels for substantive claims, ledger rows, and major proposal hypotheses; do not add repetitive labels to every sentence when a nearby table or bullet already carries the burden.

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
- Use evidence-burden labels to distinguish direct evidence, synthesis, grounded critique, proposal, and unsupported claims. Prioritize labels for claims that affect conclusions, rankings, critique severity, or proposed hypotheses.
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

Begin every mode with a concise source inventory: source titles, versions when supplied, sections, tables, figures, appendices, and other packet-provided evidence objects. Use a short preface or compact first table when the task format is constrained. The inventory prevents missing sources; it should not become a long preliminary report.

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

variant_id: B3_iter1
module_scope: literature_analysis_and_research_rigor
implementation_type: instruction_reference_only
runtime_tools_enabled: false
external_services_enabled: false
dynamic_retrieval_enabled: false
scripts_enabled: false
originality: project-original general AI/ML/RL research-analysis guidance
skill_directory: variants/B3_iter1/ai_ml_rl_literature_analysis
revision_scope:
  - concise source inventory discipline
  - evidence-burden labeling for provenance and uncertainty
  - general comparison, audit, and inference-boundary refinements
  - label-use economy and compact source-inventory placement
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
Task ID: SPR-DEV-01
Task type: single_paper_deep_reading
Topic: parameter-efficient fine-tuning
Evaluation mode: closed_source

## Research Question

What exactly does the provided LoRA-style paper claim, what evidence supports those claims, and what limitations remain?

## User Prompt

Read only the provided source packet. Produce a structured paper card, claim ledger, evidence ledger, reproducibility notes, and limitation summary.
Do not use external retrieval. If a fact is not in the packet, mark it as unknown.


## Required Output Sections

- paper_card
- claim_ledger
- evidence_ledger
- reproducibility_notes
- limitations_and_open_questions

## Output Constraint

Use only the source packet provided below. Do not use external retrieval or dynamic tools.

# Frozen Model Input Packet

# SPR-DEV-01 Model Input Packet

## Source

LoRA: Low-Rank Adaptation of Large Language Models, arXiv:2106.09685, 26-page arXiv PDF.

## Controlled Source Notes

Core method:

- The paper proposes Low-Rank Adaptation, or LoRA.
- It freezes pretrained weights and adds trainable rank-decomposition matrices to represent updates to selected dense weight matrices.
- The method expresses an adapted weight as the frozen pretrained weight plus a low-rank update, commonly written as W0 + BA.
- Section 4.1 gives the trainable low-rank update form: W0 is frozen, A and B are trainable, and the task-specific update is represented as Delta W = BA.
- Section 4.2 frames LoRA as generally applicable to dense weight matrices in neural networks, while the paper's Transformer experiments focus on selected weight matrices in attention modules.
- The paper connects this to the hypothesis that adaptation updates have low intrinsic rank.
- Relevant evidence locations: p. 1 Abstract and Figure 1; p. 2 Introduction; p. 4 Sections 4.1-4.2, including Equation 3.

Claims and evidence:

- The abstract reports reductions in trainable parameters and GPU memory in the GPT-3 175B adaptation setting.
- The abstract says LoRA performs on par or better than full fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3 in the paper's evaluated settings.
- Section 5 evaluates downstream task performance on RoBERTa, DeBERTa, GPT-2, and GPT-3.
- Table 1 compares inference latency of adapter-style methods and LoRA/full fine-tuning in a GPT-2 medium setup.
- Table 2 reports GLUE results for RoBERTa/DeBERTa adaptation methods.
- Table 3 reports GPT-2 medium and large results on the E2E NLG Challenge.
- Table 4 reports GPT-3 175B results on WikiSQL, MultiNLI-matched, and SAMSum, including trainable-parameter comparisons.
- The paper reports evidence concerning trainable-parameter counts, GPU-memory requirements, training throughput, inference latency, and downstream task quality in different sections and experimental settings.
- The paragraph before Section 5 reports a GPT-3 175B training-speed benefit relative to full fine-tuning with Adam in the paper's stated setup.
- Section 4.1 explains that LoRA updates can be merged into W0 for deployment so that inference has no additional latency relative to the corresponding fully fine-tuned weight path.

Reproducibility and limitations:

- The paper reports public code and checkpoints for several model families.
- The method is described as orthogonal to some prior efficient adaptation approaches.
- A stated limitation is that batching inputs for different tasks can be nontrivial when different samples require different LoRA modules.
- When no-latency deployment depends on merged LoRA weights, batching inputs from different tasks that require different LoRA modules is not straightforward; the paper notes dynamic module selection remains possible when latency is not critical.
- Section 7.1 and Table 5 analyze which attention weight matrices are adapted under an 18M-parameter budget in selected GPT-3 tasks.
- Section 7.2 and Table 6 analyze the effect of rank r on WikiSQL and MultiNLI in selected GPT-3 settings.
- Footnote 6 cautions that a small rank r should not be expected to work for every task or dataset.
- Relevant evidence locations: abstract; p. 3 Table 1; pp. 3-4 Section 4.1 no-additional-inference-latency discussion; p. 4 limitations paragraph before Section 5; Section 5 experiment setup; p. 6 Table 3; p. 7 Table 4; p. 9 Section 7.1/Table 5; p. 9 Section 7.2/Table 6; p. 10 footnote 6; appendices for implementation details.

