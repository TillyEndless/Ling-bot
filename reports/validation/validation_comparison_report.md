# Validation Comparison Report

Created: 2026-05-30T15:43:04

All 48 validation generations completed with the approved bundled Codex.app CLI runner. Scoring was performed post-generation only, using frozen validation gold annotations, frozen scoring rubric, and the frozen agent-review decision layer. Generation inputs did not include gold, rubric, or review reports.

## Overall Means

| Variant | Overall | Hard fails | Factual | Evidence | Grounding/Citation | Comparison | Rigor | Benchmark | Boundary | RL | Usefulness | Efficiency |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| `B0_base_agent` | 3.915 | 0 | 3.75 | 3.25 | 3.857 | 3.9 | 3.909 | 3.889 | 4.167 | 3.833 | 4.083 | 4.333 |
| `B1_kdense_subset` | 4.158 | 0 | 3.75 | 3.75 | 3.857 | 4 | 4.091 | 3.889 | 4.583 | 3.833 | 4.25 | 4.667 |
| `B2_orchestra_subset` | 4.257 | 0 | 4 | 3.667 | 3.857 | 4.3 | 4.273 | 4.222 | 4.583 | 4 | 4.583 | 4.5 |
| `B3_final_for_validation` | 4.437 | 0 | 4.083 | 4.667 | 3.875 | 4.3 | 4.455 | 4.333 | 5 | 4.167 | 4.667 | 4.083 |

## By Task Category

| Category | B0 | B1 | B2 | B3_final | Winner |
|---|---:|---:|---:|---:|---|
| experimental_rigor_audit | 3.88 | 4.06 | 4.375 | 4.625 | `B3_final_for_validation` |
| literature_mapping | 4.165 | 4.53 | 4.47 | 4.58 | `B3_final_for_validation` |
| method_comparison | 3.945 | 4.055 | 4.39 | 4.435 | `B3_final_for_validation` |
| proposal_support | 4.0 | 4.705 | 4.355 | 4.78 | `B3_final_for_validation` |
| rl_specific_analysis | 4.3 | 4.4 | 4.65 | 4.65 | `B2_orchestra_subset` |
| single_paper_reading | 3.2 | 3.2 | 3.3 | 3.55 | `B3_final_for_validation` |

## Dimension Winners

- `factual_accuracy`: `B3_final_for_validation` (4.083)
- `evidence_traceability`: `B3_final_for_validation` (4.667)
- `citation_validity`: `B3_final_for_validation` (3.875)
- `literature_coverage`: tie, `B1_kdense_subset` and `B3_final_for_validation` (5)
- `comparison_fairness`: tie, `B2_orchestra_subset` and `B3_final_for_validation` (4.3)
- `experimental_rigor`: `B3_final_for_validation` (4.455)
- `benchmark_validity`: `B3_final_for_validation` (4.333)
- `inference_boundary_discipline`: `B3_final_for_validation` (5)
- `hypothesis_quality`: `B1_kdense_subset` (5)
- `rl_specific_correctness`: `B3_final_for_validation` (4.167)
- `output_usefulness`: `B3_final_for_validation` (4.667)
- `efficiency`: `B1_kdense_subset` (4.667)

## Interpretation

- `B3_final_for_validation` is the strongest overall validation performer in this scored pass, with the best average score and no hard fails.
- `B2_orchestra_subset` remains competitive on benchmark/risk/audit-heavy dimensions, especially where provenance and rigor framing help.
- `B1_kdense_subset` remains useful for literature/source coverage discipline but is less consistently strong than B3 on comparison and boundary control.
- `B0_base_agent` is capable but less consistent on source inventory, burden-of-evidence labels, and explicit inference boundaries.

## Runner Caveat

Validation used `/Applications/Codex.app/Contents/Resources/codex` (`codex-cli 0.133.0-alpha.1`) because the PATH-resolved Homebrew/Cask runner exited with signal-kill behavior. This matches the CLI version recorded in prior dev metadata, but the validation command explicitly used `--ignore-user-config`, `--ignore-rules`, `--ephemeral`, `--sandbox read-only`, and `model_reasoning_effort="none"`; comparisons should be interpreted as results under this frozen validation runner.
