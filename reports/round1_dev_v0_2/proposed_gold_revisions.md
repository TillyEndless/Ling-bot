# Proposed Gold Revisions For Round 1 Dev v0.2

No gold annotation revisions are proposed at this stage.

The gold-to-packet coverage audit found that the accepted gold annotations remain methodologically appropriate. The v0.1 calibration defect is that several `model_input_packet.md` files did not expose enough source-facing evidence for already-approved central anchors.

## Decision

- Keep existing approved dev gold annotations unchanged.
- Do not change `human_review_status` or `eligible_for_scoring` on any gold annotation.
- Treat v0.2 work as draft packet expansion only.

## Tasks

| Task | Gold Revision Needed? | Rationale |
|---|---:|---|
| `LS-DEV-01` | No | FlashAttention exact-core/block-sparse-extension distinction is central and should be supported by packet evidence. |
| `SPR-DEV-01` | No | LoRA Tables 5-6, rank caveat, and efficiency-dimension separation are central to deep reading. |
| `MC-DEV-01` | No | v0.1 packet already supports the approved method-comparison anchors. |
| `ERA-DEV-01` | No | Heterogeneous metrics, weighting, versioning, and execution outcomes are central to benchmark-validity audit. |
| `RL-DEV-01` | No | D4RL/CQL protocol and table-role distinctions are central to RL-specific rigor. |
| `PS-DEV-01` | No | v0.1 packet already supports the approved proposal-support anchors and local seed role. |

If human review later determines any newly added packet detail is too leading or not faithful to the source, revise the packet wording and keep gold unchanged unless the reviewer explicitly requests a gold change.
