# B0 Failure Profile

## Cross-Task Pattern

- B0 generally obeyed fixed-source constraints and avoided external retrieval or fabricated citations.
- Evidence traceability is the main residual weakness: outputs cite packet sources and tables but often do not consistently attach exact page/table anchors to every substantive claim.
- B0 is strong at conservative inference boundaries when the prompt asks for them, but it sometimes phrases recommendations from generic research judgment rather than explicitly tying each recommendation to packet evidence.
- Numeric extraction remains light: where packets mention tables, B0 often summarizes table roles rather than extracting concrete values.

## Task-Level Failure Modes

### `LS-DEV-01`
- evidence_traceability: Excellent taxonomy and correct FlashAttention exact/block-sparse distinction plus LoRA boundary treatment; evidence is mostly tied to packet source notes rather than exact page anchors in every claim.
- experimental_rigor: Appropriately avoids global ranking across incompatible protocols, but could more explicitly separate within-paper result settings for each reported efficiency claim.

### `SPR-DEV-01`
- evidence_traceability: Captures LoRA method definition, model families, efficiency dimensions, deployment limitation, and Tables 5-6 rank/matrix analyses, but some details remain summarized as packet-level rather than page/table-specific evidence.
- experimental_rigor: Good reproduction notes and boundary discipline; exact numeric magnitudes are sometimes marked unknown rather than extracted, which is acceptable under the packet but less complete.

### `MC-DEV-01`
- evidence_traceability: Correctly distinguishes DPO direct preference optimization, implicit reward framing, PPO-style RLHF pipeline, and PPO as a generic RL algorithm; evidence references are mostly section-level.
- experimental_rigor: Correctly treats DPO/PPO comparisons as setup-specific and avoids universal method ranking.

### `ERA-DEV-01`
- factual_accuracy: Captures eight environments, pinned 29-model version, heterogeneous metrics, weighted aggregation, and execution-outcome categories. Some proposed baselines/ablations go beyond packet evidence but are framed as audit recommendations.
- benchmark_validity: Strong construct-validity and aggregation critique; correctly treats contamination and prompt sensitivity as audit risks rather than established failures.

### `RL-DEV-01`
- factual_accuracy: Correctly separates offline training from simulator evaluation, behavior-policy/dataset issues, normalized score versus raw return, and conservative-value diagnostics. It does not explicitly restate the CQL Table 3 Atari role, but does not misuse it.
- rl_specific_correctness: Excellent RL-specific protocol framing, including static datasets, distribution shift, seeds, uncertainty, and offline-to-online claim boundaries.

### `PS-DEV-01`
- hypothesis_quality: Strong falsifiable hypotheses, controls, ablations, and proposal risk register. One causal-use falsification line is a little awkwardly phrased, but the overall boundary between recoverability and causal use is preserved.
- evidence_traceability: Accurately treats the local seed idea as motivation and separates packet facts, synthesis, and proposed hypotheses; source references are mostly source-level rather than exact page-level.
