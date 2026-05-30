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
