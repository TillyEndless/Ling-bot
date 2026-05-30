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
