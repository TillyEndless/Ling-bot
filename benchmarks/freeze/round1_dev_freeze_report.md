# Round 1 Dev Freeze Report

- `benchmark_version`: `round1_dev_v0.1`
- `split`: `dev`
- `task_count`: 6
- `source_mode`: fixed source packets only
- `dynamic_tools_allowed`: false
- `gold_visible_during_generation`: false

## Frozen Tasks

- `LS-DEV-01`
- `SPR-DEV-01`
- `MC-DEV-01`
- `ERA-DEV-01`
- `RL-DEV-01`
- `PS-DEV-01`

## Frozen File Classes

- Dev task YAML specifications.
- Dev model input packets.
- Approved dev gold annotations.
- Common scoring rubric.
- Controlled run protocol.

## Variant State

Only `variants/README.md` exists. No `B1`, `B2`, `B3`, `B4`, or final research skill implementation exists in the benchmark workspace.

## Immutability Rule

Any change to a frozen task, packet, gold annotation, rubric, or run protocol requires a new benchmark version. Results from different benchmark versions must be reported separately and must not be silently mixed.
