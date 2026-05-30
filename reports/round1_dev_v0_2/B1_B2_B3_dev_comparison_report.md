# B1/B2/B3 Dev Comparison Report

Benchmark: `round1_dev_v0.2`  
Run set: B0 plus B1/B2/B3 on six frozen dev tasks  
Runtime condition: fixed source packets, no dynamic tools, fresh contexts, same model/settings.

## Completion And Fairness

| Variant | Runs completed | Runtime package contamination | Hard-fail violations |
|---|---:|---|---|
| `B0_base_agent` | 6/6 | baseline scan passed | none observed |
| `B1_kdense_subset` | 6/6 | passed | none observed |
| `B2_orchestra_subset` | 6/6 | passed | none observed |
| `B3_your_v1_original` | 6/6 | passed | none observed |

## Average Scores By Dimension

| Variant | Factual | Traceability | Citation | Fairness | Rigor | Benchmark | Boundary | Hypothesis | RL | Usefulness | Efficiency |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| `B0_base_agent` | 4.67 | 4.0 | 5.0 | 4.33 | 4.5 | 5.0 | 5.0 | 5.0 | 5.0 | 5.0 | 4.33 |
| `B1_kdense_subset` | 5.0 | 5.0 | 5.0 | 4.67 | 4.67 | 5.0 | 5.0 | 5.0 | 4.0 | 5.0 | 3.83 |
| `B2_orchestra_subset` | 5.0 | 5.0 | 5.0 | 5.0 | 4.83 | 5.0 | 5.0 | 5.0 | 5.0 | 5.0 | 3.67 |
| `B3_your_v1_original` | 5.0 | 5.0 | 5.0 | 5.0 | 5.0 | 5.0 | 5.0 | 5.0 | 5.0 | 5.0 | 4.83 |

## Task Winners

| Task | Best variant(s) | Rationale |
|---|---|---|
| `LS-DEV-01` | `B3_your_v1_original` | Best balance of taxonomy, method differences, experimental-detail gaps, and concise unsupported synthesis. |
| `SPR-DEV-01` | `B3_your_v1_original` | Captured all key LoRA reading anchors with the best efficiency. |
| `MC-DEV-01` | `B2_orchestra_subset`, `B3_your_v1_original` | B2 had the strongest evidence-burden schema; B3 matched quality more concisely. |
| `ERA-DEV-01` | `B2_orchestra_subset`, `B3_your_v1_original` | B2 was strongest on artifact-style benchmark critique; B3 matched core audit content with better concision. |
| `RL-DEV-01` | `B3_your_v1_original` | RL-specific guidance improved dataset/behavior-policy/train-eval/metric distinctions. |
| `PS-DEV-01` | `B3_your_v1_original` | Strongest concise separation of packet facts, synthesis, hypotheses, falsification, and causal-use boundaries. |

## Main Findings

- All three variants improve on B0 evidence traceability by consistently using claim/evidence ledgers or location-rich tables.
- B1 contributes useful K-Dense-style literature coverage and citation discipline, especially for fixed-corpus mapping and source-accounting tasks.
- B2 contributes the clearest provenance, claim-type, evidence-burden, and rigor-review structure; it is strongest for method comparison and benchmark audits but can be verbose.
- B3 best addresses the original B0 weaknesses while staying concise: page/table grounding, extraction of ablations and missing experimental details, comparison fairness, RL protocol boundaries, and proposal causality boundaries.
- No variant accessed dynamic tools, external retrieval, gold annotations, scoring rubrics during generation, benchmark audit reports, validation materials, or other variants.
