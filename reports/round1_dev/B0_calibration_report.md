# B0 Calibration Report

- `variant`: `B0_base_agent`
- `benchmark_version`: `round1_dev_v0.1`
- `run_count`: 6
- `model`: `gpt-5.5`
- `agent_environment`: `Codex CLI v0.133.0-alpha.1`
- `tool_access`: `none_dynamic`
- `generation_mode`: fixed source packets only; no retrieval, plugins, shell tool, browser, APIs, citation databases, PDF parsers, or experiment execution.

## Run Completion

- `LS-DEV-01` completed; raw output SHA-256 `20d9f5fce41cdb5f75cb3623089dd63da3fea49b1978c509f929841e768c99c5`.
- `SPR-DEV-01` completed; raw output SHA-256 `ac10a4e69c01b532bae6844f891eca328bf795b2bf4b445cc5001f5501134595`.
- `MC-DEV-01` completed; raw output SHA-256 `a6bd82d49db24920104f9013aedc0d669831244c151aba14935b641538ab6a66`.
- `ERA-DEV-01` completed; raw output SHA-256 `833156197aa7294a71658fcec8dd35c6f9daf5f57eecf5f658ebe328a3bc76de`.
- `RL-DEV-01` completed; raw output SHA-256 `ca4cff082857994ad276272b1ac70eed17de7106c299e83c042fc085e96c0e62`.
- `PS-DEV-01` completed; raw output SHA-256 `aa20f7e673787a03d075733ec0998b630b9856b8cf7125b21845d965058e4563`.

## Draft Scores

| Task | Factual | Traceability | Coverage/Comparison/Rigor | Boundary | Usefulness | Main note |
|---|---:|---:|---:|---:|---:|---|
| `LS-DEV-01` | 4 | 3 | 3.7 | 5 | 4 | Strong fixed-corpus organization and correct LoRA boundary treatment. |
| `SPR-DEV-01` | 3 | 3 | 2.0 | 4 | 3 | Captures LoRA core mechanism, evaluated model families, and broad efficiency dimensions. |
| `MC-DEV-01` | 4 | 3 | 4.5 | 5 | 4 | Correctly distinguishes DPO direct preference optimization from PPO-style RLHF. |
| `ERA-DEV-01` | 3 | 3 | 3.3 | 4 | 4 | Good generic rigor audit and appropriate caution about general agency claims. |
| `RL-DEV-01` | 3 | 3 | 3.8 | 4 | 4 | Strong general offline-RL protocol audit with fixed-data, behavior-policy, metric, seed, and online-claim boundaries. |
| `PS-DEV-01` | 4 | 3 | 4.5 | 5 | 4 | Strong separation of packet facts, synthesis, and hypotheses. |

## Calibration Finding

B0 completed successfully and generally obeyed the fixed-source/no-dynamic-tools constraint. However, calibration revealed a benchmark defect: several frozen `model_input_packet.md` files do not contain enough detail to support the newly approved gold annotations. This makes some misses ambiguous between baseline weakness and input-packet insufficiency.

The affected anchors include FlashAttention block-sparse-extension handling, LoRA Tables 5-6 matrix/rank analysis, AgentBench heterogeneous metric/weighted-aggregation and execution-outcome details, and CQL/D4RL table-role and four-seed protocol details.
