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
