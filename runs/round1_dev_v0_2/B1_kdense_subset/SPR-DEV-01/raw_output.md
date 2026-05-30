## paper_card

| Field | Content |
|---|---|
| Source | *LoRA: Low-Rank Adaptation of Large Language Models*, arXiv:2106.09685, 26-page arXiv PDF |
| Topic | Parameter-efficient fine-tuning / adaptation of large language models |
| Core method | Freeze pretrained weights and add trainable low-rank matrices to selected dense weight matrices. The adapted weight is represented as `W0 + BA`, where `W0` is frozen and `A`, `B` are trainable. |
| Main technical location | Section 4.1, Equation 3; Section 4.2 |
| Central hypothesis | Adaptation updates have low intrinsic rank, so task-specific changes can be represented by low-rank updates. |
| Experimental scope | RoBERTa, DeBERTa, GPT-2, and GPT-3; downstream tasks reported in Section 5 and Tables 2-4. |
| Main claimed advantages | Fewer trainable parameters, lower GPU memory, better or comparable downstream quality, no added inference latency after merging LoRA weights, and training-speed benefits in a stated GPT-3 175B setup. |
| Deployment mechanism | LoRA updates can be merged into the frozen weight path, giving no additional inference latency relative to the corresponding fully fine-tuned weight path. |
| Stated limitation | Batching inputs from different tasks is nontrivial when samples require different LoRA modules, especially when merged no-latency deployment is desired. |

## claim_ledger

| Claim | Source location supplied | Support status | Notes |
|---|---:|---|---|
| LoRA freezes pretrained weights and trains low-rank update matrices. | p. 1 Abstract/Figure 1; p. 4 Sections 4.1-4.2; Equation 3 | Direct | Core method is explicitly described as `W0 + BA`, with `W0` frozen and `A`, `B` trainable. |
| LoRA is generally applicable to dense weight matrices in neural networks. | Section 4.2 | Direct | Experiments focus on selected Transformer attention matrices, so broad applicability is method-framing, not exhaustively tested in packet. |
| LoRA is motivated by the hypothesis that adaptation updates have low intrinsic rank. | Core method notes; Section 7.2/Table 6; footnote 6 | Direct/partial | Rank analyses support selected GPT-3 settings, but footnote 6 cautions that small rank should not be expected to work for every task or dataset. |
| LoRA reduces trainable parameters in GPT-3 175B adaptation. | Abstract; Table 4 | Direct | Table 4 includes trainable-parameter comparisons for GPT-3 175B on WikiSQL, MultiNLI-matched, and SAMSum. Exact numeric values are not provided in the packet. |
| LoRA reduces GPU memory in the GPT-3 175B adaptation setting. | Abstract | Direct but limited granularity | Packet states the abstract reports GPU-memory reductions, but no exact memory numbers are included. |
| LoRA performs on par with or better than full fine-tuning in evaluated settings. | Abstract; Section 5; Tables 2-4 | Direct/partial | Supported for the paper’s evaluated RoBERTa, DeBERTa, GPT-2, and GPT-3 settings. Not established beyond those settings. |
| LoRA has no additional inference latency after merging weights. | pp. 3-4 Section 4.1 discussion; Table 1 for latency comparison | Direct | Applies relative to corresponding fully fine-tuned weight path when LoRA updates are merged into `W0`. |
| LoRA improves GPT-3 175B training speed relative to full fine-tuning with Adam in the stated setup. | Paragraph before Section 5 | Direct but setup-specific | Packet does not give exact throughput numbers or hardware/config details. |
| Which attention matrices to adapt matters under a fixed parameter budget. | p. 9 Section 7.1/Table 5 | Direct | Evidence comes from selected GPT-3 tasks under an 18M-parameter budget. |
| Rank `r` affects performance, but small rank is not universally guaranteed. | p. 9 Section 7.2/Table 6; p. 10 footnote 6 | Direct | Packet explicitly includes a caution against expecting small `r` to work for every task or dataset. |
| Public code and checkpoints are available for several model families. | Reproducibility notes in packet | Direct but limited | Packet states availability, but does not provide repository URL, checkpoint list, or exact model coverage. |

## evidence_ledger

| Evidence item | Location supplied | Evidence type | Supports | Caveat |
|---|---:|---|---|---|
| Abstract and Figure 1 introduce LoRA and report parameter/memory reductions. | p. 1 | Method summary and headline empirical claim | Core method; parameter efficiency; GPU memory reduction | Exact values are not included in the packet. |
| Introduction motivates low-rank adaptation. | p. 2 | Conceptual framing | Low intrinsic-rank hypothesis | Motivation is not by itself proof of universal low rank. |
| Trainable low-rank update formula `Delta W = BA`; `W0` frozen. | p. 4 Section 4.1; Equation 3 | Formal method definition | LoRA mechanism | Packet does not include full derivation or implementation details. |
| LoRA applicability to dense matrices, with Transformer experiments on attention modules. | Section 4.2 | Scope statement | General method applicability | Experiments are narrower than the stated generality. |
| Adapter-style latency comparison versus LoRA/full fine-tuning. | p. 3 Table 1 | Latency comparison | No added inference latency claim | Specific to GPT-2 medium setup. |
| Mergeability of LoRA updates into `W0`. | pp. 3-4 Section 4.1 | Deployment argument | No additional inference latency | Complicates batching across tasks needing different LoRA modules. |
| GLUE results for RoBERTa/DeBERTa adaptation methods. | Table 2 | Benchmark comparison | Comparable/better task quality | Exact tasks, scores, variance, and baselines are not provided in packet. |
| GPT-2 medium/large E2E NLG Challenge results. | p. 6 Table 3 | Benchmark comparison | Task quality under NLG setting | Packet does not include full metric details. |
| GPT-3 175B results on WikiSQL, MultiNLI-matched, and SAMSum with parameter comparisons. | p. 7 Table 4 | Benchmark and parameter comparison | Quality and trainable-parameter reduction | Limited to these tasks and reported settings. |
| Training-speed benefit versus full fine-tuning with Adam. | Paragraph before Section 5 | Runtime comparison | Training efficiency | Setup-specific; exact setup details unavailable in packet. |
| Attention-matrix adaptation analysis under 18M-parameter budget. | p. 9 Section 7.1/Table 5 | Ablation | Which matrices to adapt | Selected GPT-3 tasks only. |
| Rank `r` analysis on WikiSQL and MultiNLI. | p. 9 Section 7.2/Table 6 | Ablation | Effect of rank | Footnote 6 limits generalization. |
| Footnote caution about small rank. | p. 10 footnote 6 | Author caveat | Limits rank-generalization claim | Directly weakens any universal “small rank always works” interpretation. |
| Appendices contain implementation details. | Appendices | Reproducibility support | Implementation clarity | Packet does not specify which exact details are included. |

## reproducibility_notes

The packet establishes that the paper reports public code and checkpoints for several model families, but the repository location, checkpoint list, exact versions, and coverage are unknown from the packet.

The method itself is reproducible at a high level from the supplied description: freeze `W0`, add trainable matrices `A` and `B`, represent the task-specific update as `Delta W = BA`, and optionally merge `BA` into `W0` for deployment.

Important missing reproducibility details from the packet include exact hyperparameters, random seeds, optimizer settings, training schedules, hardware, dataset preprocessing, prompt or input formatting for generative tasks, and full metric definitions. The packet says appendices contain implementation details, but their contents are not provided here.

## limitations_and_open_questions

| Limitation or open question | Evidence location | Severity for claims | Notes |
|---|---:|---|---|
| Generality beyond evaluated models/tasks is not established by the packet. | Section 5; Tables 2-4 | Medium | Evidence covers RoBERTa, DeBERTa, GPT-2, and GPT-3 in reported settings only. |
| General applicability to dense matrices is broader than the experimental focus. | Section 4.2 | Medium | The method is framed generally, but Transformer experiments focus on selected attention matrices. |
| Small rank `r` is not guaranteed for every task/dataset. | p. 10 footnote 6 | High for rank-generalization claims | The paper itself cautions against universal small-rank conclusions. |
| Multi-task batching is difficult when different samples require different LoRA modules. | p. 4 limitations paragraph before Section 5 | Practical deployment limitation | Dynamic module selection remains possible when latency is not critical. |
| No-latency inference depends on merging LoRA weights. | pp. 3-4 Section 4.1 | Medium | This creates a tension with serving mixed tasks requiring different merged modules. |
| Exact quantitative results are unavailable in the packet. | Tables 1-6 referenced but not numerically reproduced | Medium | Claims can be attributed, but exact effect sizes cannot be audited here. |
| Statistical reliability is unknown from the packet. | Not established | Unknown | Seeds, variance, confidence intervals, and aggregation details are not supplied. |
| Baseline fairness cannot be fully assessed from the packet. | Not established | Unknown | The packet names comparisons but does not provide enough setup detail to judge fairness. |
| Memory and throughput claims are setup-specific. | Abstract; paragraph before Section 5 | Medium | Hardware, optimizer configuration, and measurement details are not supplied. |

Overall, the packet supports the claim that LoRA is a low-rank, parameter-efficient adaptation method with strong reported results in the paper’s evaluated settings. The packet does not support broader claims that LoRA is always superior, that low rank always suffices, or that the reported efficiency gains transfer unchanged to all models, tasks, deployment regimes, or serving setups.