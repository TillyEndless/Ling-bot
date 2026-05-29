# Benchmark Split Policy

The benchmark uses three split concepts.

## `dev`

Visible tasks for:

- Source-packet construction.
- Gold annotation drafting.
- Rubric calibration.
- Variant debugging.
- Early failure analysis.

Dev tasks may be inspected during skill development. Dev gold annotations may be used for calibration only after they are human-reviewed and marked `eligible_for_scoring: true`.

## `validation`

Internal fixed-comparison tasks used after candidate variants are frozen for a development cycle.

The current 12 non-dev tasks are validation tasks because their task shells were created in this development workspace and may be visible during later skill implementation.

Validation task shells may remain in this repository, but validation source packets, gold annotations, scorecards, and reviewer notes should be stored outside the skill-development workspace or access-controlled before formal validation runs.

Validation results may guide development after a frozen comparison cycle, but they are not a strict private final test set.

## `private_test`

Future final evaluation split.

Private-test tasks, source packets, gold annotations, scorecards, and reviewer notes must be created or stored outside the skill-development workspace after candidate variants are frozen.

Private-test materials must not be visible during:

- Skill design.
- Variant prompt/reference editing.
- Dev gold annotation drafting.
- Validation analysis.

Private-test results should be used only for final reporting or release gating.

## Split Hygiene Rules

- Do not call validation tasks a private or strict blind test set.
- Do not tune a variant against validation results and then report the same validation result as final generalization evidence.
- Do not expose private-test task details in development-facing docs.
- Freeze variant file hashes before validation and private-test execution.
- Increment the benchmark version if validation or private-test task shells change after formal runs begin.
