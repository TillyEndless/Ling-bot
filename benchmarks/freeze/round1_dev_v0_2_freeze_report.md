# Round 1 Dev v0.2 Freeze Report

- `benchmark_version`: `round1_dev_v0.2`
- `split`: `dev`
- `task_count`: 6
- `source_mode`: fixed source packets only
- `equal_inputs_across_variants`: true
- `dynamic_tools_allowed`: false
- `gold_visible_during_generation`: false

## Frozen Tasks

- `LS-DEV-01`: `expanded_and_sanitized_from_v0.1`
- `SPR-DEV-01`: `expanded_and_sanitized_from_v0.1`
- `MC-DEV-01`: `sanitized_from_v0.1_for_v0.2`
- `ERA-DEV-01`: `expanded_and_sanitized_from_v0.1`
- `RL-DEV-01`: `expanded_and_sanitized_from_v0.1`
- `PS-DEV-01`: `sanitized_from_v0.1_for_v0.2`

## Frozen File Classes

- Dev task YAML specifications.
- v0.2 effective packet manifests.
- v0.2 effective model input packets.
- Approved dev gold annotations.
- Common scoring rubric.
- Controlled run protocol.

## v0.1 Policy

`round1_dev_v0.1` is retained only as a benchmark-debugging run and must not be used for direct performance comparison with v0.2 runs.

## Variant State

Only `variants/README.md` exists. No `B1`, `B2`, `B3`, `B4`, or final research skill implementation exists in the benchmark workspace.

## Immutability Rule

Any change to a frozen task, packet, gold annotation, rubric, or run protocol requires a new benchmark version. Results from different benchmark versions must be reported separately and must not be silently mixed.
