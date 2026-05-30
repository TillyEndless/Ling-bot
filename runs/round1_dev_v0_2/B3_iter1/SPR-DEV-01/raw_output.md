## paper_card

| Field | Paper details |
|---|---|
| Source | *LoRA: Low-Rank Adaptation of Large Language Models*, arXiv:2106.09685, 26-page arXiv PDF. |
| Problem | Parameter-efficient adaptation of large pretrained language models, especially where full fine-tuning is expensive in trainable parameters, GPU memory, storage, and deployment overhead. `DIRECT_PACKET_EVIDENCE` |
| Core method | LoRA freezes pretrained weights and adds trainable low-rank decomposition matrices to selected dense weight matrices. The adapted weight is represented as `W0 + BA`, with `W0` frozen and `A`, `B` trainable; Section 4.1 states `Delta W = BA`. `DIRECT_PACKET_EVIDENCE` |
| Scope of method | Section 4.2 frames LoRA as generally applicable to dense weight matrices in neural networks, while the paper’s Transformer experiments focus on selected attention-module weight matrices. `DIRECT_PACKET_EVIDENCE` |
| Main hypothesis | The method is connected to the hypothesis that adaptation updates have low intrinsic rank. `DIRECT_PACKET_EVIDENCE` |
| Evaluated models | RoBERTa, DeBERTa, GPT-2, and GPT-3. `DIRECT_PACKET_EVIDENCE` |
| Evaluated tasks / benchmarks | GLUE for RoBERTa/DeBERTa; E2E NLG Challenge for GPT-2 medium/large; WikiSQL, MultiNLI-matched, and SAMSum for GPT-3 175B. `DIRECT_PACKET_EVIDENCE` |
| Baselines | Full fine-tuning and adapter-style methods are included in the described comparisons; exact full baseline list is unknown from the packet. |
| Metrics | Downstream task quality, trainable-parameter counts, GPU-memory requirements, training throughput, and inference latency. Exact task metrics are unknown from the packet. |
| Ablations / analyses | Section 7.1/Table 5 analyzes which attention matrices are adapted under an 18M-parameter budget in selected GPT-3 tasks. Section 7.2/Table 6 analyzes rank `r` on WikiSQL and MultiNLI in selected GPT-3 settings. `DIRECT_PACKET_EVIDENCE` |
| Reproducibility | The paper reports public code and checkpoints for several model families; appendices contain implementation details. Exact repository URL, checkpoint inventory, seeds, hyperparameters, and hardware are unknown from the packet. |
| Stated limitations | Batching inputs for different tasks can be nontrivial when different samples require different LoRA modules; no-latency deployment via merged weights complicates mixed-task batching. Footnote 6 cautions that small rank `r` should not be expected to work for every task or dataset. `DIRECT_PACKET_EVIDENCE` |

## claim_ledger

| Claim | Claim type | Evidence-burden label | Source location | Supported scope |
|---|---|---|---|---|
| LoRA adapts models by freezing pretrained weights and training low-rank matrices whose product represents the update. | Method definition | `DIRECT_PACKET_EVIDENCE` | p. 1 Abstract/Figure 1; p. 4 Sections 4.1-4.2; Equation 3 | Method as described in the paper. |
| The adapted weight can be written as `W0 + BA`, with `W0` frozen and `A`, `B` trainable. | Method definition | `DIRECT_PACKET_EVIDENCE` | p. 4 Section 4.1; Equation 3 | Dense weight matrices selected for LoRA adaptation. |
| LoRA is motivated by the hypothesis that adaptation updates have low intrinsic rank. | Assumption / hypothesis | `DIRECT_PACKET_EVIDENCE` | p. 2 Introduction; p. 4 Sections 4.1-4.2 | Motivating hypothesis, not established as universally true. |
| LoRA can be applied generally to dense neural-network weight matrices, though experiments focus on selected Transformer attention matrices. | Method scope | `DIRECT_PACKET_EVIDENCE` | p. 4 Section 4.2 | General method framing; empirical evidence limited to reported model/task settings. |
| LoRA reduces trainable parameters and GPU memory in the GPT-3 175B adaptation setting. | Empirical/resource claim | `DIRECT_PACKET_EVIDENCE` | Abstract; p. 7 Table 4 | GPT-3 175B settings reported in the paper. |
| LoRA performs on par with or better than full fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3 in evaluated settings. | Empirical comparison | `DIRECT_PACKET_EVIDENCE` | Abstract; Section 5; Tables 2-4 | Only the paper’s evaluated models, tasks, and protocols. |
| LoRA introduces no additional inference latency relative to the corresponding fully fine-tuned weight path when updates are merged into `W0`. | Deployment/mechanism claim | `DIRECT_PACKET_EVIDENCE` | pp. 3-4 Section 4.1; Table 1 | Deployment path where LoRA weights are merged. |
| LoRA has a GPT-3 175B training-speed benefit relative to full fine-tuning with Adam in the paper’s stated setup. | Empirical/resource claim | `DIRECT_PACKET_EVIDENCE` | Paragraph before Section 5 | The stated GPT-3 175B setup only. |
| Choice of adapted attention matrices matters under a fixed 18M-parameter budget. | Ablation / analysis claim | `DIRECT_PACKET_EVIDENCE` | p. 9 Section 7.1; Table 5 | Selected GPT-3 tasks analyzed in that section. |
| Rank `r` affects performance, and small rank should not be assumed sufficient for every task or dataset. | Limitation / sensitivity claim | `DIRECT_PACKET_EVIDENCE` | p. 9 Section 7.2; Table 6; p. 10 footnote 6 | WikiSQL/MultiNLI selected GPT-3 settings plus author caution. |

## evidence_ledger

| Evidence object | What it supports | Evidence-burden label | Directness | Missing detail |
|---|---|---|---|---|
| p. 1 Abstract and Figure 1 | High-level method, claimed parameter/memory reductions, and performance summary. | `DIRECT_PACKET_EVIDENCE` | Direct summary evidence | Exact numerical values are not supplied in the packet. |
| p. 2 Introduction | Motivation and low-intrinsic-rank hypothesis. | `DIRECT_PACKET_EVIDENCE` | Direct for motivation; partial for validating the hypothesis | The packet does not provide full argument or empirical proof details. |
| p. 4 Sections 4.1-4.2, Equation 3 | Formal LoRA update `Delta W = BA`; frozen `W0`; trainable `A`, `B`; dense-matrix applicability. | `DIRECT_PACKET_EVIDENCE` | Direct | Initialization, scaling, optimizer, and implementation specifics are unknown from the packet. |
| Table 1, p. 3 | Inference latency comparison among adapter-style methods, LoRA, and full fine-tuning in GPT-2 medium setup. | `DIRECT_PACKET_EVIDENCE` | Direct for reported setup | Exact latency numbers and measurement protocol are unknown from the packet. |
| Section 4.1 no-additional-latency discussion, pp. 3-4 | LoRA updates can be merged into `W0` for deployment, avoiding added inference latency. | `DIRECT_PACKET_EVIDENCE` | Direct | Runtime details for dynamic multi-task serving are limited in the packet. |
| Section 5 | Downstream evaluations on RoBERTa, DeBERTa, GPT-2, GPT-3. | `DIRECT_PACKET_EVIDENCE` | Direct for existence of evaluations | Full setup, seeds, prompts, hyperparameters, and all metrics are unknown from the packet. |
| Table 2 | GLUE results for RoBERTa/DeBERTa adaptation methods. | `DIRECT_PACKET_EVIDENCE` | Direct for reported comparison | Exact scores, variance, and all compared methods are not supplied. |
| Table 3, p. 6 | GPT-2 medium/large results on E2E NLG Challenge. | `DIRECT_PACKET_EVIDENCE` | Direct for reported comparison | Exact metrics and values are unknown from the packet. |
| Table 4, p. 7 | GPT-3 175B results on WikiSQL, MultiNLI-matched, and SAMSum, including trainable-parameter comparisons. | `DIRECT_PACKET_EVIDENCE` | Direct | Exact numbers, uncertainty, and evaluation details are unknown from the packet. |
| Paragraph before Section 5 | GPT-3 175B training-speed benefit relative to full fine-tuning with Adam. | `DIRECT_PACKET_EVIDENCE` | Direct | Hardware, throughput numbers, and full optimizer setup are unknown from the packet. |
| Section 7.1/Table 5, p. 9 | Analysis of which attention matrices to adapt under an 18M-parameter budget. | `DIRECT_PACKET_EVIDENCE` | Direct | Generality beyond selected GPT-3 tasks is not established. |
| Section 7.2/Table 6, p. 9 | Effect of rank `r` on WikiSQL and MultiNLI in selected GPT-3 settings. | `DIRECT_PACKET_EVIDENCE` | Direct | Rank sensitivity across other tasks/models remains unknown. |
| Footnote 6, p. 10 | Warning that small rank `r` should not be expected to work for every task or dataset. | `DIRECT_PACKET_EVIDENCE` | Direct limitation | No universal rank-selection rule is provided in the packet. |
| Appendices | Implementation details. | `DIRECT_PACKET_EVIDENCE` | Direct existence only | Specific appendix contents are not included in the packet. |

## reproducibility_notes

The packet states that the paper reports public code and checkpoints for several model families. It also states that appendices provide implementation details. These are positive reproducibility signals. `DIRECT_PACKET_EVIDENCE`

However, from the supplied packet, the following details are unknown: exact code URL, checkpoint list, dataset preprocessing, prompts, seeds, number of runs, confidence intervals or variance, hyperparameters, tuning budget, hardware, environment versions, exact latency measurement protocol, and raw output availability. These missing details weaken the ability to independently audit or reproduce the reported results from the packet alone. `LIMITED_CRITIQUE`

The packet identifies several reproducibility-relevant evidence objects: Table 1 for latency, Tables 2-4 for task results, Table 5 for adapted-matrix analysis, Table 6 for rank analysis, and appendices for implementation details. Exact values and procedures are not provided in the packet, so they must be treated as unknown here.

## limitations_and_open_questions

The main stated limitation is serving or batching complexity across tasks: when different samples require different LoRA modules, batching can be nontrivial. This is especially relevant when no-latency deployment depends on merging LoRA weights into the base weights. The packet also notes that dynamic module selection remains possible when latency is not critical. `DIRECT_PACKET_EVIDENCE`

A second stated limitation is rank sensitivity. Footnote 6 cautions that a small rank `r` should not be expected to work for every task or dataset, and Section 7.2/Table 6 only analyze selected GPT-3 settings on WikiSQL and MultiNLI. `DIRECT_PACKET_EVIDENCE`

Open questions from the packet:

| Open question | Evidence-burden label | Why it remains open |
|---|---|---|
| How robust are LoRA gains across tasks not evaluated in the paper? | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW` | The packet only supports claims for reported RoBERTa, DeBERTa, GPT-2, and GPT-3 settings. |
| What rank-selection rule should be used for new tasks? | `LIMITED_CRITIQUE` | The packet reports rank analysis but also cautions that small rank may not work universally. |
| How fair and complete are the baseline comparisons? | `LIMITED_CRITIQUE` | Baseline categories are described, but exact tuning and full protocol details are not supplied. |
| How much uncertainty is present in reported performance? | `LIMITED_CRITIQUE` | The packet does not provide seeds, repeated-run counts, confidence intervals, or variance. |
| Does low-rank adaptation explain the mechanism of successful fine-tuning? | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW` | The packet states a low-intrinsic-rank hypothesis, but mechanism-level causal evidence is not established here. |
| How well does merged-weight deployment handle high-throughput multi-task serving? | `LIMITED_CRITIQUE` | The packet directly notes mixed-task batching difficulty, but does not provide a full serving-system evaluation. |