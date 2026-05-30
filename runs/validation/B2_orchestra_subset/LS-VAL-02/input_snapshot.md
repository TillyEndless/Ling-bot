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


# Task

- Task ID: `LS-VAL-02`
- Split: `validation`
- Task type: `literature_mapping`
- Topic: latent reasoning in language models
- Research question: Within the fixed source packet, what literature supports or challenges the idea that language models perform useful latent or internal reasoning?

## Input Prompt

Produce a balanced fixed-corpus literature map on latent or internal reasoning in language models.
Use only the provided source packet. Do not perform external retrieval.
Return a corpus coverage table, taxonomy of evidence types, representative papers, skeptical counter-evidence, unsupported-synthesis warnings, and open gaps visible within the corpus.
Treat latent reasoning as one possible topic, not as an assumed fact.


## Required Outputs

- corpus_coverage_table
- evidence_type_taxonomy
- representative_paper_table
- counter_evidence_summary
- unsupported_synthesis_warnings
- gap_and_hypothesis_list

# Source Packet

# LS-VAL-02 Model Input Packet
## Sources
- Chain-of-Thought Prompting Elicits Reasoning in Large Language Models (arXiv:2201.11903; 2022). Local file: `wei_2022_chain_of_thought_prompting.pdf`. Included evidence: Abstract; prompting/evaluation results; limitations.
- Large Language Models are Zero-Shot Reasoners (arXiv:2205.11916; 2022). Local file: `kojima_2022_large_language_models_are_zero_shot_reasoners.pdf`. Included evidence: Abstract; zero-shot reasoning prompt; experiments.
- Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting (arXiv:2305.04388; 2023). Local file: `turpin_2023_unfaithful_explanations_cot.pdf`. Included evidence: Abstract; unfaithfulness experiments; discussion.
- Measuring Faithfulness in Chain-of-Thought Reasoning (arXiv:2307.13702; 2023). Local file: `lanham_2023_measuring_faithfulness_cot.pdf`. Included evidence: Abstract; faithfulness tests; intervention/ablation evidence; limitations.

## Controlled Source Notes
- Chain-of-Thought Prompting: reports that chain-of-thought exemplars can improve reasoning performance in large language models on selected tasks.
- Zero-Shot Reasoners: reports that a simple reasoning prompt can elicit step-by-step reasoning behavior without task-specific examples in selected settings.
- Unfaithful Explanations in Chain-of-Thought Prompting: studies cases where generated rationales can be unfaithful to the model behavior or influenced by biases.
- Measuring Faithfulness in Chain-of-Thought Reasoning: proposes tests for faithfulness of chain-of-thought rationales and studies interventions/perturbations in selected settings.
- Evidence objects: abstracts, method/evaluation sections, result tables/figures, and discussion/limitations.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.

