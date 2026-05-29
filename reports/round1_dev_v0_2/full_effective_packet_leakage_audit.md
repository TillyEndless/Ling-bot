# Full Effective Packet Leakage Audit

Scope: complete effective `round1_dev_v0.2` model-input packet set before final sanitization.

Effective packet mapping audited:

- `LS-DEV-01`: `benchmarks/source_packets/dev_v0_2/LS-DEV-01/model_input_packet.md`
- `SPR-DEV-01`: `benchmarks/source_packets/dev_v0_2/SPR-DEV-01/model_input_packet.md`
- `ERA-DEV-01`: `benchmarks/source_packets/dev_v0_2/ERA-DEV-01/model_input_packet.md`
- `RL-DEV-01`: `benchmarks/source_packets/dev_v0_2/RL-DEV-01/model_input_packet.md`
- `MC-DEV-01`: carried-forward `benchmarks/source_packets/dev/MC-DEV-01/model_input_packet.md`
- `PS-DEV-01`: carried-forward `benchmarks/source_packets/dev/PS-DEV-01/model_input_packet.md`

## Problematic Packet-Level Guidance

| Task | Exact Phrase | Packet Location | Authorship | Classification | Proposed Action |
|---|---|---|---|---|---|
| `LS-DEV-01` | `Task: fixed-corpus literature mapping on transformer efficiency.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove from v0.2 packet. |
| `LS-DEV-01` | `Runtime rule: use only this packet and the task YAML. Do not retrieve external papers.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove from v0.2 packet; this belongs in task prompt/run protocol. |
| `LS-DEV-01` | `Use it as a taxonomy/background paper, not as an empirical proof that any one method is best.` | Efficient Transformers survey notes | agent-authored framing | `gold_or_rubric_leakage` | Replace with neutral source description of survey/taxonomy scope. |
| `LS-DEV-01` | `any claim about practical superiority must stay tied to those settings` | Linformer notes | agent-authored framing | `gold_or_rubric_leakage` | Replace with neutral statement that empirical discussion appears in reported settings. |
| `LS-DEV-01` | `It is a long-context architecture paper, not an exact-attention kernel paper.` | Longformer notes | agent-authored framing | `ambiguous_requires_human_review` | Replace with neutral source scope wording. |
| `LS-DEV-01` | `It is exact attention, not approximate/sparse attention.` | FlashAttention notes | agent-authored framing based on source | `ambiguous_requires_human_review` | Replace with neutral source claim: paper describes FlashAttention as exact attention. |
| `LS-DEV-01` | `Evidence about speed or memory must be tied to the reported hardware/model/sequence settings.` | FlashAttention notes | agent-authored framing | `gold_or_rubric_leakage` | Replace with neutral source-location statement. |
| `LS-DEV-01` | `It belongs in adaptation efficiency, not attention-computation efficiency.` | LoRA notes | agent-authored framing | `gold_or_rubric_leakage` | Replace with neutral source framing around adaptation. |
| `LS-DEV-01` | `Expected Literature-Mapping Boundaries` and all bullets below it | final section | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove section from packet. |
| `SPR-DEV-01` | `Task: structured deep reading of LoRA.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove from v0.2 packet. |
| `SPR-DEV-01` | `Runtime rule: use only this packet and the task YAML. Do not retrieve external papers.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove from v0.2 packet. |
| `SPR-DEV-01` | `but that does not prove compatibility in every later setting` | Reproducibility and limitations | agent-authored inference | `gold_or_rubric_leakage` | Remove inference clause. |
| `SPR-DEV-01` | `Required Boundaries` and all bullets below it | final section | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove section from packet. |
| `ERA-DEV-01` | `Task: experimental rigor audit of AgentBench-style agent evaluation.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove from v0.2 packet. |
| `ERA-DEV-01` | `Runtime rule: use only this packet and the task YAML. Do not retrieve external papers.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove from v0.2 packet. |
| `ERA-DEV-01` | `Audit focus` and all bullets below it | audit focus section | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove section from packet. |
| `ERA-DEV-01` | `Required Boundaries` and all bullets below it | final section | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove section from packet. |
| `RL-DEV-01` | `Task: RL-specific audit of an offline RL protocol.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove from v0.2 packet. |
| `RL-DEV-01` | `Runtime rule: use only this packet and the task YAML. Do not retrieve external papers.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove from v0.2 packet. |
| `RL-DEV-01` | `RL audit focus` and all directive bullets below it | audit focus section | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove directive bullets; keep neutral source note about distinct quantities. |
| `RL-DEV-01` | `Required Boundaries` and all bullets below it | final section | agent-authored framing | `belongs_in_task_prompt_not_packet` | Remove section from packet. |
| `MC-DEV-01` | `Task: compare DPO-style preference optimization and PPO-style RLHF under fixed sources.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Create v0.2 sanitized copy and remove. |
| `MC-DEV-01` | `Runtime rule: use only this packet and the task YAML. Do not retrieve external papers.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Create v0.2 sanitized copy and remove. |
| `MC-DEV-01` | `It is not itself a language-model preference optimization paper.` | PPO notes | agent-authored role interpretation | `ambiguous_requires_human_review` | Replace with neutral experiment-scope statement. |
| `MC-DEV-01` | `Required Comparison Boundaries` and all bullets below it | final section | agent-authored framing | `gold_or_rubric_leakage` | Create v0.2 sanitized copy and remove. |
| `PS-DEV-01` | `Task: evidence-grounded proposal support for representation probing.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Create v0.2 sanitized copy and remove. |
| `PS-DEV-01` | `Runtime rule: use only this packet and the task YAML. Do not retrieve external papers.` | top matter | agent-authored framing | `belongs_in_task_prompt_not_packet` | Create v0.2 sanitized copy and remove. |
| `PS-DEV-01` | `Use it as source-grounded context and methodological caution, not as a single empirical experiment.` | BERTology primer notes | agent-authored role instruction | `gold_or_rubric_leakage` | Replace with neutral survey-source description. |
| `PS-DEV-01` | `Develop a proposal that tests whether...` | Local seed idea | agent-authored imperative | `belongs_in_task_prompt_not_packet` | Replace with neutral source description of the local seed idea. |
| `PS-DEV-01` | `Required Boundaries` and all bullets below it | final section | agent-authored framing | `gold_or_rubric_leakage` | Create v0.2 sanitized copy and remove. |

## Acceptable Source-Evidence Phrases Flagged By Broad Scan

These terms were flagged by broad lexical scanning but are acceptable source evidence after human review because they describe paper content rather than packet instructions:

| Task | Phrase | Packet Location | Classification | Proposed Action |
|---|---|---|---|---|
| `SPR-DEV-01` | `Footnote 6 cautions that a small rank r should not be expected to work for every task or dataset.` | LoRA notes | `acceptable_source_evidence` | Keep. |
| `SPR-DEV-01` | `Table 1 compares inference latency...` | LoRA notes | `acceptable_source_evidence` | Keep. |
| `RL-DEV-01` | `unsupported or weakly supported by the offline dataset` | CQL notes | `acceptable_source_evidence` | Keep. |
| `LS-DEV-01` | `It claims linear scaling...` | Longformer notes | `acceptable_source_evidence` | Keep; describes paper claim. |

## Audit Decision

Residual problematic language exists in all six effective packets. `MC-DEV-01` and `PS-DEV-01` require v0.2 sanitized copies rather than edits to historical v0.1 files.
