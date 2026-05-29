# B0 Failure Profile

## Cross-Task Pattern

- Strong compliance with the closed-packet rule: no observed dynamic retrieval or external-source use.
- Good inference-boundary discipline on most tasks.
- Evidence traceability is mostly coarse: outputs cite packet notes, paper sections, or tables broadly, not exact approved page/table anchors.
- The biggest issue is benchmark-input incompleteness after human review. Several approved gold facts are not present in the frozen model packets.

## By Task

### LS-DEV-01

- Strong fixed-corpus organization and correct LoRA boundary treatment.
- Correctly treats FlashAttention as exact attention, but misses the approved block-sparse-extension distinction because the frozen model packet did not expose it.
- Evidence traceability is to packet notes rather than exact approved page/table anchors.

### SPR-DEV-01

- Captures LoRA core mechanism, evaluated model families, and broad efficiency dimensions.
- Misses the approved matrix-choice/rank ablation entry from Tables 5-6 and the footnote caveat because the model packet did not include those details.
- Overly marks many details unknown, which is safe but makes the output less useful for deep reading.

### MC-DEV-01

- Correctly distinguishes DPO direct preference optimization from PPO-style RLHF.
- Correctly avoids universal DPO-over-RLHF claims and separates direct from indirect comparisons.
- Implicit-reward nuance is present but not as explicitly tied to DPO policy parameterization as the approved gold.

### ERA-DEV-01

- Good generic rigor audit and appropriate caution about general agency claims.
- Misses approved AgentBench-specific anchors: pinned-version model-count sensitivity, heterogeneous metric set, weighted aggregation procedure, and observed execution-outcome categories.
- These misses trace partly to the model packet, which did not expose the F1/reward/game-progress/step-SR details or Table 4 category specifics.

### RL-DEV-01

- Strong general offline-RL protocol audit with fixed-data, behavior-policy, metric, seed, and online-claim boundaries.
- Does not capture approved CQL table-role corrections, four-seed reporting detail, or the precise lower-bound/table distinction.
- Uses a simplified OOD-action formulation and treats Atari-style experiments too loosely relative to the approved D4RL/CQL gold.

### PS-DEV-01

- Strong separation of packet facts, synthesis, and hypotheses.
- Correctly treats probing evidence as non-causal and proposes falsifiable controls.
- Evidence locations are coarse packet-note references rather than exact approved page locations; local seed is handled as motivation rather than literature evidence.

## Dimension-Level Weaknesses

- `evidence_traceability`: weakest repeated dimension because the B0 input packets often expose only summary notes and broad evidence locations.
- `experimental_rigor`: strong in generic audits, weaker where task-specific paper/table details are needed.
- `benchmark_validity`: ERA output identified generic risks but missed pinned AgentBench aggregation and failure-category specifics.
- `rl_specific_correctness`: RL output found offline-RL protocol risks but missed approved table-role distinctions and used a simplified CQL description.
- `output_usefulness`: good structure overall, but insufficient source detail in packets caused over-conservative `unknown` entries in SPR and missed gold anchors in ERA/RL.
