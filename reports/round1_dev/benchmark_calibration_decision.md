# Benchmark Calibration Decision

Decision: `benchmark_revision_required_before_variants`

## Rationale

All six B0 runs completed under the isolated no-skill protocol, but the frozen `round1_dev_v0.1` development benchmark should not yet be used to compare `B1`, `B2`, or `B3`.

Minimum defect: several model input packets are too compressed relative to the approved gold annotations. The benchmark would unfairly penalize variants for missing facts that were not actually supplied at generation time.

## Required Minimum Fix Before Variant Implementation

Create `round1_dev_v0.2` with model input packets updated to expose the approved gold-relevant source facts without exposing the gold annotations themselves. At minimum:

- `LS-DEV-01`: include FlashAttention block-sparse approximate extension as distinct from the core exact algorithm.
- `SPR-DEV-01`: include LoRA Tables 5-6 matrix-choice/rank analysis and the footnote caveat about small rank not working for every task/dataset.
- `ERA-DEV-01`: include pinned AgentBench v3 version marker, heterogeneous metric list, weighted aggregation procedure, and execution-outcome categories.
- `RL-DEV-01`: include CQL/D4RL table-role distinctions, four-seed reporting detail, and clearer lower-bound-analysis versus benchmark-ranking separation.

After updating packets, recompute packet hashes, create a new freeze manifest, rerun B0, and score again. Do not begin `B1`, `B2`, or `B3` until the calibration decision becomes `benchmark_ready_for_variant_implementation`.
