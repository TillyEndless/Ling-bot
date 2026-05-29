# AI/ML/RL Research Skill Benchmark

This directory defines a frozen, controlled evaluation package for comparing instruction/reference-based research skill variants. It is intentionally created before implementing `B3_your_v1_original` so the skill can be evaluated against predeclared tasks, rubrics, and run controls.

The benchmark compares variants such as:

- `B0_base_agent`
- `B1_kdense_subset`
- `B2_orchestra_subset`
- `B3_your_v1_original`

It does not yet include `B4_your_v1_integrated`; that variant should be created only after the first controlled comparison identifies which upstream components actually improve research quality.

## Directory Layout

```text
benchmarks/
  README.md
  tasks/
    dev/
    validation/
    private_test/   # not stored here; future external evaluator split
  source_packets/
  gold_annotations/
  rubrics/
    scoring_rubric.md
  run_protocol.md
  readiness_checklist.md
  source_packet_requirements.md
  gold_annotation_template.md
```

## Splits

- `dev`: visible tasks for iteration, debugging, and rubric calibration.
- `validation`: internal fixed comparison tasks used after candidate variants are frozen for a development cycle. The current validation task shells are visible in this repository, so they are not a strict private final test set.
- `private_test`: future final evaluation tasks, source packets, and gold annotations stored outside the skill-development workspace.

Each of the six task categories has exactly one development task and two validation tasks.

See `split_policy.md` and `private_test_protocol.md`.

## Task Categories

- Literature survey.
- Single-paper deep reading.
- Method comparison.
- Experimental rigor audit.
- RL-specific analysis.
- Evidence-grounded proposal support.

## Round 1 Evaluation Mode

Round 1 uses only `closed_source` tasks. The agent must answer using fixed source packets supplied with the task. These tasks test structured reading, fixed-corpus literature mapping, comparison, evidence discipline, rigor review, RL-specific analysis, and bounded proposal reasoning.

Open retrieval is deferred to `future_rounds/retrieval_enabled_evaluation.md`.

## Current Status

The six dev source packets have been materialized with canonical sources, model-input packets, and packet manifests. Dev gold annotations are agent-drafted and remain `eligible_for_scoring: false` until human review.
