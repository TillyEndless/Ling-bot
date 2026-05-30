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
