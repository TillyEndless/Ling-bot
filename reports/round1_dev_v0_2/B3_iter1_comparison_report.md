# B3 Iter1 Comparison Report

Current best before Iter1: `B3_your_v1_revised`.

## Completion And Fairness

| Variant | Runs completed | Contamination | Hard-fail violations |
|---|---:|---|---|
| `B3_iter1` | 6/6 | passed static and execution-package audits | none observed |

## Average Scores By Dimension

| Variant | Factual | Traceability | Citation | Coverage | Fairness | Rigor | Benchmark | Boundary | Hypothesis | RL | Usefulness | Efficiency |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| `B0_base_agent` | 4.67 | 4 | 5 | 5 | 4.33 | 4.5 | 5 | 5 | 5 | 5 | 5 | 4.33 |
| `B1_kdense_subset` | 5 | 5 | 5 | 5 | 4.67 | 4.67 | 5 | 5 | 5 | 4 | 5 | 3.83 |
| `B2_orchestra_subset` | 5 | 5 | 5 | 5 | 5 | 4.83 | 5 | 5 | 5 | 5 | 5 | 3.67 |
| `B3_your_v1_original` | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 4.83 |
| `B3_your_v1_revised` | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 |
| `B3_iter1` | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 4.17 |

## Current Best Versus Iter1 Output Length

| Task | Current best words | Iter1 words | Delta |
|---|---:|---:|---:|
| `LS-DEV-01` | 1446 | 1592 | +146 |
| `SPR-DEV-01` | 1593 | 1667 | +74 |
| `MC-DEV-01` | 1119 | 1266 | +147 |
| `ERA-DEV-01` | 1201 | 1509 | +308 |
| `RL-DEV-01` | 1461 | 1321 | -140 |
| `PS-DEV-01` | 1382 | 1544 | +162 |

## Interpretation

Iter1 preserved factual accuracy, traceability, comparison fairness, rigor, RL correctness, and inference-boundary discipline. It did not produce a reliable improvement over the current best. The intended label-economy change shortened only the RL task and made five of six outputs longer, so the observed difference is not a useful general improvement.

## Acceptance Judgment

Reject Iter1 and keep `B3_your_v1_revised` as the current best.
