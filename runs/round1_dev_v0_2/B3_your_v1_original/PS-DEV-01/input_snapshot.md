# Variant Runtime Instructions

You are running benchmark variant `B3_your_v1_original` for the `literature_analysis_and_research_rigor` module. Follow only the variant skill/reference content included below. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Variant Skill And References

## Variant File: variant/ai_ml_rl_literature_analysis/SKILL.md

---
name: ai-ml-rl-literature-analysis-and-research-rigor
description: Original instruction-only skill for AI/ML/RL literature mapping, paper reading, method comparison, benchmark audit, RL protocol analysis, and evidence-grounded proposal support.
license: project-original
---

# AI/ML/RL Literature Analysis And Research Rigor

Use this skill for fixed-source research analysis in artificial intelligence, machine learning, and reinforcement learning. It is a literature-analysis and research-rigor module only. It does not schedule projects, manage repositories, execute experiments, monitor runs, retrieve papers, call APIs, parse PDFs, or maintain persistent state.

## Non-Negotiable Rules

1. Use only the task prompt and supplied source packet.
2. Do not import facts, citations, identifiers, numbers, or conclusions from memory.
3. Separate source-stated claims, extracted evidence, cross-source synthesis, proposed hypotheses, and unsupported speculation.
4. Prefer page, section, figure, table, appendix, or excerpt-level grounding when the packet provides it.
5. Extract experimental details before interpreting results: task, data, model, baseline, metric, protocol, seed/run count, uncertainty, ablation, compute or hardware when supplied, and limitations.
6. Do not infer global method superiority from incompatible setups.
7. For RL, distinguish dataset collection, behavior policy, offline or online training, policy evaluation, reward/environment details, distribution shift, and deployment claims.
8. For representation or mechanism proposals, distinguish information recoverability, correlation, intervention evidence, causal use, and mechanism claims.

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

1. Source inventory: identify every supplied source and what kind of evidence it contributes.
2. Claim extraction: list major claims before synthesis.
3. Evidence ledger: attach each important claim to the most specific available source location.
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


## Variant File: variant/ai_ml_rl_literature_analysis/references/comparative_analysis_schema.md

# Comparative Analysis Schema

## Method Comparison Matrix

| Dimension | Method or source A | Method or source B | Comparable as stated? | Evidence | Boundary |
|---|---|---|---|---|---|

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

## Output Checks

- Have all methods/sources been represented fairly?
- Are assumptions visible?
- Are incompatible protocols called out?
- Are claims limited to supported settings?


## Variant File: variant/ai_ml_rl_literature_analysis/references/evidence_traceability.md

# Evidence Traceability

## Claim-Evidence Ledger

Use a ledger whenever the task has more than one substantive claim.

| Claim | Claim type | Source location | Evidence directness | Supported scope | Missing detail |
|---|---|---|---|---|---|

Claim types include method definition, assumption, empirical result, benchmark result, comparison, limitation, mechanism claim, causal claim, reproducibility claim, and proposal hypothesis.

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

- Source fact: directly stated in supplied material.
- Extracted observation: result or detail read from supplied evidence.
- Cross-source synthesis: relation among supplied sources.
- Proposed hypothesis: new testable idea grounded in supplied evidence.
- Speculation: plausible but not established by supplied material.
- Unsupported claim: not justified by the packet.

## Boundary Rules

- Mark unsupported synthesis explicitly.
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

## Literature Mapping

Goal: organize a fixed corpus into research lines and evidence boundaries.

Minimum steps:

1. Account for every source in the packet.
2. Assign source role using evidence only: method paper, survey, benchmark, empirical study, theory, systems artifact, boundary case, or motivation.
3. Group by technical mechanism, research question, evidence type, and evaluation target.
4. Compare claims only where setup compatibility is clear.
5. List unsupported syntheses and corpus coverage limits.

## Single-Paper Structured Reading

Goal: recover exactly what the paper claims and what supports it.

Minimum steps: method definition, author motivation, assumptions, experiment setup, baselines, metrics, ablations, limitations, reproducibility details, and unknowns.

## Method Comparison

Goal: compare methods without laundering setup differences into universal rankings.

Minimum steps: objectives, assumptions, data, optimization, baselines, metrics, evaluation protocols, evidence strength, and fair scope.

## Benchmark Or Experimental Rigor Audit

Goal: decide whether a protocol supports a stated claim.

Minimum steps: construct validity, metric alignment, task selection, aggregation, baselines, ablations, uncertainty, leakage, reproducibility, and claim scope.

## RL Protocol Analysis

Goal: audit sequential decision evidence.

Minimum steps: environment, reward, behavior policy, data collection, train/eval separation, policy evaluation, return metric, stochasticity, distribution shift, seeds, and deployment boundaries.

## Evidence-Grounded Proposal Support

Goal: convert a vague idea into testable hypotheses without inventing field-wide novelty.

Minimum steps: packet facts, synthesis, hypotheses, predictions, disconfirming observations, experiments, controls, baselines, ablations, risks, and evidence needed for stronger claims.


## Variant File: variant/variant_manifest.yaml

variant_id: B3_your_v1_original
module_scope: literature_analysis_and_research_rigor
implementation_type: instruction_reference_only
runtime_tools_enabled: false
external_services_enabled: false
dynamic_retrieval_enabled: false
scripts_enabled: false
originality: project-original guidance written for general AI/ML/RL research analysis
skill_directory: variants/B3_your_v1_original/ai_ml_rl_literature_analysis
supported_modes:
  - literature_mapping
  - single_paper_structured_reading
  - method_comparison
  - benchmark_experimental_rigor_audit
  - rl_protocol_analysis
  - evidence_grounded_proposal_support
runtime_exclusions:
  - no upstream text copied
  - no benchmark-specific paper names
  - no task identifiers
  - no expected answer content
  - no dynamic tools
  - no Research OS orchestration


# Benchmark Task Input

Benchmark version: round1_dev_v0.2
Task ID: PS-DEV-01
Task type: evidence_grounded_proposal_support
Topic: representation learning
Evaluation mode: closed_source

## Research Question

Can a vague representation-probing idea be turned into evidence-grounded, testable research hypotheses?

## User Prompt

Using only the provided source packet, turn the seed idea into a small research proposal.
Produce scoped research questions, evidence-grounded hypotheses, falsification criteria, required experiments, baselines, ablations, and a risk register.
Clearly separate facts from the packet, synthesis, and your own proposed hypotheses.


## Required Output Sections

- scoped_research_questions
- hypothesis_table
- evidence_map
- experiment_plan
- risk_register

## Output Constraint

Use only the source packet provided below. Do not use external retrieval or dynamic tools.

# Frozen Model Input Packet

# PS-DEV-01 Model Input Packet

## Corpus

1. BERT Rediscovers the Classical NLP Pipeline, arXiv:1905.05950, 9-page arXiv PDF.
2. A Primer in BERTology: What we know about how BERT works, arXiv:2002.12327, 23-page arXiv PDF.
3. A Structural Probe for Finding Syntax in Word Representations, ACL Anthology N19-1419 PDF, 10 pages.
4. Local seed idea brief: representation probing.

## Controlled Source Notes

BERT Rediscovers:

- The paper uses edge-probing tasks and layer analysis to investigate where linguistic information appears in BERT representations.
- It explicitly warns that inspection/probing has limitations: observing a pattern does not necessarily show how the model uses that information.
- Evidence locations: abstract; Section 2 probing tasks; Section 3 scalar mixing/cumulative scoring; Figures 1-3; limitations paragraph.

BERTology primer:

- The primer surveys work on BERT representations, attention, probing, and what is known about how BERT works.
- The primer is a survey source covering BERT representations, attention, probing, and methodological cautions.
- Evidence locations: survey sections on probing and representations; methodological cautions and discussion.

Structural Probe:

- The paper proposes a structural probe that learns a linear transformation under which squared distances or norms correspond to parse-tree distances or depths.
- It evaluates contextual representations such as ELMo and BERT and includes baselines.
- The paper discusses limitations of probing tasks and the tradeoff between probe complexity, probe task, and hypothesis.
- Evidence locations: abstract; Section 2; Table 1; Figures 1-5; limitations discussion around probing tasks.

Local seed idea:

- The local seed idea concerns whether probing results reveal stable representational structure or reflect probe capacity, dataset artifacts, and analysis choices.

