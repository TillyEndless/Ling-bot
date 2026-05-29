# B0 Calibration Report

- `variant`: `B0_base_agent`
- `benchmark_version`: `round1_dev_v0.2`
- `run_count`: 6
- `model`: `gpt-5.5`
- `agent_environment`: `Codex CLI v0.133.0-alpha.1`
- `tool_access`: `none_dynamic`
- `generation_mode`: fixed source packets only; no retrieval, plugins, shell tool, browser, APIs, citation databases, PDF parsers, or experiment execution.

## Run Completion

- `LS-DEV-01` completed; raw output SHA-256 `388f7201dc8e7ca2a2c2e772e83427d3ffb4cb7513cd0fc05b5199cfd9fab7ee`.
- `SPR-DEV-01` completed; raw output SHA-256 `45a9165866921a6332b76e0a3d2f5352a1ad628c40b587d558eae62e4d6906eb`.
- `MC-DEV-01` completed; raw output SHA-256 `9e3cd7d1d0ab368ef70a1b377739f6ef5a2d027dbfee9fa5d34b4abd91446a81`.
- `ERA-DEV-01` completed; raw output SHA-256 `41f27d92712ff53a4f6175d97ce052c6c73c490efffe61a73053abb2931fab5c`.
- `RL-DEV-01` completed; raw output SHA-256 `e689f4d269a6a09591b7b8456e8faacc25cec0a07f2163b05df8b499e3611851`.
- `PS-DEV-01` completed; raw output SHA-256 `9e22431d8e3e9e74e93a2fda1f3d7e240fe33fbefbe475cfcd03f4da3f0c5e1a`.

## Draft Scores

| Task | Factual | Traceability | Task-specific rigor/coverage | Boundary | Usefulness | Main note |
|---|---:|---:|---:|---:|---:|---|
| `LS-DEV-01` | 5 | 4 | 5 | 5 | 5 | Strong fixed-corpus literature map. v0.2 evidence additions resolved the v0.1 ambiguity around FlashAttention and LoRA boundary handling. |
| `SPR-DEV-01` | 5 | 4 | 4 | 5 | 5 | Strong single-paper reading. The v0.2 additions made the matrix/rank ablation and efficiency-dimension anchors scorable. |
| `MC-DEV-01` | 5 | 4 | 5 | 5 | 5 | Very strong method comparison with the central universal-ranking boundary intact. |
| `ERA-DEV-01` | 4 | 4 | 4 | 5 | 5 | Strong experimental-rigor audit. v0.2 packet additions fixed the previous metric/aggregation and failure-category evidence gap. |
| `RL-DEV-01` | 4 | 4 | 4 | 5 | 5 | Strong RL-specific audit. v0.2 packet additions resolved the v0.1 D4RL/CQL protocol and table-role coverage problem. |
| `PS-DEV-01` | 5 | 4 | 4 | 5 | 5 | Strong evidence-grounded proposal support. The sanitized v0.2 packet remains source-only while preserving enough evidence for scoring. |

## Calibration Finding

B0 completed successfully on all six `round1_dev_v0.2` tasks under the fixed-source/no-dynamic-tools condition. The v0.2 packet revisions resolved the v0.1 benchmark-design defect: approved gold anchors are now supported by the effective model input packets, and remaining misses are interpretable as baseline capability or output-calibration gaps rather than packet coverage failures.

No hard-fail conditions were triggered in the draft scoring pass. Scores should be treated as calibration scores for baseline characterization, not as a substitute for later human comparative review.
