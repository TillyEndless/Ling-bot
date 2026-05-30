# Validation Run Plan

Status: prepared only; do not execute until explicitly instructed.

## Variants To Compare

- `B0_base_agent`
- `B1_kdense_subset`
- `B2_orchestra_subset`
- `B3_final_for_validation`

## Conditions

- Use frozen validation task prompts and fixed source packets only.
- Use the same model, fresh context policy, and disabled-tool permissions across variants.
- Do not expose validation gold annotations, scoring notes, rubrics, or prior outputs during generation.
- Do not use dynamic retrieval, APIs, citation services, PDF parsers, executable upstream scripts, or experiment tools.
- Store outputs under a validation-specific run directory with per-task input snapshots, raw outputs, metadata, scorecards, and scoring notes.

## Scoring

Score only after generation against the frozen validation gold and rubric. Report by task category and dimension, preserving separate metrics for factual accuracy, evidence traceability, comparison fairness, experimental rigor, RL correctness, inference-boundary discipline, usefulness, and efficiency.

## Leakage Controls

- Runtime bundles must contain only the selected variant files, validation task prompts, validation model-input packets, and empty output directories.
- No dev scorecards or dev scoring notes should be present during validation generation.
- No validation gold should be inspected until generation is complete.
