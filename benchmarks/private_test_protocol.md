# Private Test Protocol

The private test is a future final evaluation split. It is not implemented in this repository at this stage.

## Purpose

The private test should estimate how candidate research-skill variants generalize after development and validation have already shaped the system.

## Storage

Private-test assets should live outside the skill-development workspace, for example:

```text
research-skill-private-evaluator/
  tasks/
  source_packets/
  gold_annotations/
  run_metadata/
  scorecards/
```

The development repository may contain this protocol but must not contain private-test prompts, packets, gold annotations, or scorecards.

## Creation Timing

Private-test tasks and gold annotations should be created or finalized only after candidate variants are frozen, or by an evaluator who has not used them during skill design.

## Execution Requirements

Before private-test execution:

- Freeze variant commits or file hashes.
- Freeze model and reasoning settings.
- Freeze source-packet checksums.
- Freeze tool permissions.
- Confirm no private-test artifacts are present in the development workspace.
- Confirm no variant-specific tuning has occurred against private-test materials.

## Recording

Each private-test run must record:

- Evaluation ID.
- Variant ID.
- Variant commit or file-hash manifest.
- Task ID.
- Source packet ID and checksums.
- Model and reasoning settings.
- Tool permissions.
- Loaded skill/reference files.
- Raw output.
- Scorecard.
- Reviewer identity or reviewer code.
- Hard-fail flags.

## Reporting

Private-test reporting should distinguish:

- Dev calibration performance.
- Validation-cycle performance.
- Private-test performance.

Do not use private-test results to make further changes and then reuse the same private-test score as final evidence.

