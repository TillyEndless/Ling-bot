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
