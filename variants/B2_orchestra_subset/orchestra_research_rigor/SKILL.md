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
