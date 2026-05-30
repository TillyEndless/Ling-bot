# Variant Runtime Instructions

You are running benchmark variant `B2_orchestra_subset` for the `literature_analysis_and_research_rigor` module. Follow only the variant skill/reference content included below. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Variant Skill And References

## Variant File: variant/orchestra_research_rigor/SKILL.md

---
name: orchestra-research-rigor-subset
description: Instruction-only Orchestra-derived subset for claim provenance, research artifact structure, rigor review, method comparison, and evaluation reasoning. No autonomous experiments or tools.
license: MIT-derived-upstream-patterns-with-attribution
---

# Orchestra Subset: Research Rigor And Evidence Artifacts

Use this skill when the task asks for paper analysis, method comparison, benchmark audit, evidence review, or proposal support from supplied material.

This variant adapts Orchestra research-artifact, research-manager, rigor-reviewer, and ML-paper-review patterns. It is not an autonomous research agent. Do not execute experiments, retrieve papers, run evaluation harnesses, manage repositories, update persistent state, or call tools.

## Core Discipline

1. Convert the response into research artifacts: claims, evidence, assumptions, comparisons, risks, and unresolved questions.
2. Assign provenance to each major statement: source-derived, cross-source synthesis, inferred from supplied evidence, proposed by the agent, or unsupported.
3. Match claim type to evidence burden before concluding.
4. For comparisons, require compatible tasks, data, metrics, baselines, compute, and protocols; otherwise make a scoped comparison.
5. For evaluation audits, inspect metric alignment, aggregation, baselines, ablations, seeds, uncertainty, leakage, and reproducibility details.
6. Preserve negative and missing evidence. Do not silently upgrade a plausible idea into a supported finding.

## Claim-Type Evidence Burdens

- Improvement claim: requires direct baseline comparison under a compatible setup.
- Generalization claim: requires heterogeneous tasks, datasets, or settings.
- Causal claim: requires intervention, ablation, or mechanism-isolating evidence.
- Benchmark-validity claim: requires task/metric/protocol analysis and scope limitations.
- Reproducibility claim: requires sufficient artifact, configuration, environment, and data details.
- Proposal claim: requires falsifiable hypothesis, observable outcomes, controls, and disconfirmation conditions.

## Response Pattern

1. Artifact inventory: sources, claims, assumptions, evidence, and missing details.
2. Claim ledger: claim, type, provenance, evidence, scope, evidence burden, support status.
3. Rigor review: severity-ranked issues tied to claim validity.
4. Corrected scope: what the packet supports, what is unknown, and what would be needed next.
5. Final output in the user-requested format.

References:

- `references/provenance_and_artifacts.md`
- `references/rigor_review_workflow.md`
- `references/evaluation_reasoning.md`
- `references/method_and_claim_audit.md`


## Variant File: variant/orchestra_research_rigor/references/evaluation_reasoning.md

# Evaluation Reasoning

Adapted from Orchestra ML evaluation and rigor-review patterns, without evaluation harness execution.

## Benchmark Audit Questions

- What construct does the benchmark claim to measure?
- Are tasks representative of that construct?
- Are metrics aligned with the claim?
- Is aggregation across tasks meaningful and transparent?
- Are baselines appropriate and fairly tuned?
- Are repeated runs, uncertainty, and variance reported?
- Could contamination, leakage, prompt sensitivity, or protocol overfitting affect conclusions?
- Are per-task results preserved before aggregate claims?

## Experiment Audit Questions

- What exact intervention or method differs between compared systems?
- Are training data, evaluation data, compute, and tuning budgets compatible?
- Which variables are controlled and which confounds remain?
- Are ablations sufficient to support mechanism claims?
- Are negative results or failure modes reported?

Report benchmark and experiment concerns as risks unless the supplied packet directly establishes a failure.


## Variant File: variant/orchestra_research_rigor/references/method_and_claim_audit.md

# Method And Claim Audit

Adapted from Orchestra claim-centered artifact patterns and ML writing/reviewer criteria.

## Method Comparison Schema

| Dimension | Method A | Method B | Comparable? | Evidence | Caveat |
|---|---|---|---|---|---|

Recommended dimensions: objective, data, assumptions, model class, optimization, baselines, metrics, compute, evaluation protocol, limitations, and claim scope.

## Claim Ledger Schema

| Claim | Type | Evidence burden | Supplied evidence | Support status | Allowed scope |
|---|---|---|---|---|---|

## Boundary Rules

- A within-paper comparison supports that paper's setup, not all possible settings.
- A benchmark score supports performance under the benchmark protocol, not unrestricted capability.
- A probe or correlational analysis supports recoverability or association unless stronger causal evidence is supplied.
- A reproduction plan must list artifacts, code/config/data needs, seeds, metrics, and environment details.


## Variant File: variant/orchestra_research_rigor/references/provenance_and_artifacts.md

# Provenance And Research Artifacts

Adapted from Orchestra agent-native research artifact and research-manager patterns.

## Provenance Tags

Use these tags internally and expose them when helpful:

- source-derived: directly stated by supplied material.
- source-located: source-derived and tied to page, section, figure, or table.
- cross-source synthesis: a relation among supplied sources.
- agent-inferred: inferred from supplied evidence and marked as such.
- agent-proposed: a hypothesis, critique, or protocol improvement.
- unsupported: not established by supplied material.

## Artifact Schema

| Artifact | Purpose |
|---|---|
| Claim ledger | Tracks claims, claim types, source support, and scope. |
| Evidence ledger | Tracks source locations and directness of support. |
| Assumption list | Separates method assumptions from evaluation assumptions. |
| Risk register | Records threats to validity and reproducibility. |
| Missing-information list | Identifies details needed before stronger conclusions. |

Never silently convert an agent-proposed idea into a source-derived fact.


## Variant File: variant/orchestra_research_rigor/references/rigor_review_workflow.md

# Rigor Review Workflow

Adapted from Orchestra rigor-reviewer patterns.

## Review Dimensions

- Evidence relevance: does the evidence actually support the claim?
- Falsifiability: can the claim be tested or refuted?
- Scope calibration: is the claim limited to the studied setting?
- Argument coherence: do conclusions follow from assumptions and results?
- Exploration integrity: are hypotheses, post-hoc analyses, and exploratory ideas separated?
- Methodological rigor: are baselines, ablations, metrics, seeds, and reproducibility details adequate?

## Severity-Ranked Finding Template

| Severity | Claim affected | Evidence issue | Consequence | Minimal fix |
|---|---|---|---|---|

## Missing Detail Checklist

- Baseline identity and strength.
- Ablation presence and purpose.
- Metric definition and aggregation.
- Dataset split, task sampling, or environment setup.
- Number of seeds, runs, or trials.
- Variability or confidence reporting.
- Hyperparameter search and compute comparability.
- Implementation and artifact availability.


## Variant File: variant/reuse_and_license_notes.md

# B2 Reuse And License Notes

This variant selectively adapts Orchestra-derived ideas for claim-centered artifacts, provenance, rigor review, and evaluation reasoning. It deliberately excludes autonomous experiment execution, repository management, evaluation harnesses, training infrastructure, deployment, and tool loops.

## Components Used

| Upstream component | Files consulted per ledger | Adaptation decision | License status from audit |
|---|---|---|---|
| `Orchestra-Research/AI-Research-SKILLs/22-agent-native-research-artifact/ara-compiler` | `SKILL.md`, `references/schema.md` | Rewritten as compact claim/evidence/artifact schema | MIT observed in skill frontmatter |
| `Orchestra-Research/AI-Research-SKILLs/22-agent-native-research-artifact/research-manager` | `SKILL.md`, `references/provenance_tags.md` | Rewritten as provenance tags and artifact discipline | MIT observed in skill frontmatter |
| `Orchestra-Research/AI-Research-SKILLs/22-agent-native-research-artifact/rigor-reviewer` | `SKILL.md`, `references/rigor_dimensions.md` | Rewritten as type-aware rigor review workflow | MIT observed in skill frontmatter |
| `Orchestra-Research/AI-Research-SKILLs/20-ml-paper-writing/ml-paper-writing` | `SKILL.md`, citation/reviewer references | Rewritten as claim-to-evidence and reviewer criteria patterns | MIT observed in skill frontmatter |

## Explicit Runtime Exclusions

- No autonomous research loop or persistent research state.
- No scripts, APIs, retrieval tools, evaluation harnesses, training infrastructure, or code execution.
- No K-Dense-derived material.
- No benchmark-specific paper names, task identifiers, expected answers, or development answer-key content.


## Variant File: variant/variant_manifest.yaml

variant_id: B2_orchestra_subset
module_scope: literature_analysis_and_research_rigor
implementation_type: instruction_reference_only
runtime_tools_enabled: false
external_services_enabled: false
dynamic_retrieval_enabled: false
scripts_enabled: false
upstream_basis:
  repository: Orchestra-Research/AI-Research-SKILLs
  components:
    - path: 22-agent-native-research-artifact/ara-compiler/SKILL.md
      consulted_files:
        - 22-agent-native-research-artifact/ara-compiler/SKILL.md
        - 22-agent-native-research-artifact/ara-compiler/references/schema.md
      use: adapted_claim_and_artifact_schema
      copied_verbatim: false
      license_observed: MIT in skill frontmatter according to upstream reuse ledger
    - path: 22-agent-native-research-artifact/research-manager/SKILL.md
      consulted_files:
        - 22-agent-native-research-artifact/research-manager/SKILL.md
        - 22-agent-native-research-artifact/research-manager/references/provenance_tags.md
      use: adapted_provenance_tags
      copied_verbatim: false
      license_observed: MIT in skill frontmatter according to upstream reuse ledger
    - path: 22-agent-native-research-artifact/rigor-reviewer/SKILL.md
      consulted_files:
        - 22-agent-native-research-artifact/rigor-reviewer/SKILL.md
        - 22-agent-native-research-artifact/rigor-reviewer/references/rigor_dimensions.md
      use: adapted_rigor_review_dimensions
      copied_verbatim: false
      license_observed: MIT in skill frontmatter according to upstream reuse ledger
    - path: 20-ml-paper-writing/ml-paper-writing/SKILL.md
      consulted_files:
        - 20-ml-paper-writing/ml-paper-writing/SKILL.md
        - 20-ml-paper-writing/ml-paper-writing/references/citation-management.md
        - 20-ml-paper-writing/ml-paper-writing/references/reviewer-criteria.md
      use: adapted_claim_to_evidence_and_reviewer_patterns
      copied_verbatim: false
      license_observed: MIT in skill frontmatter according to upstream reuse ledger
runtime_exclusions:
  - no autoresearch autonomous loop
  - no experiment execution
  - no evaluation harnesses
  - no training infrastructure
  - no K-Dense-derived material
  - no B3-original AI/ML/RL additions


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

