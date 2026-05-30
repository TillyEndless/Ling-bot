## paper_card

| Field | Details |
|---|---|
| Source inventory | **LoRA: Low-Rank Adaptation of Large Language Models**, arXiv:2106.09685, 26-page arXiv PDF. Packet-provided evidence locations include Abstract/Figure 1, Introduction, Sections 4.1-4.2, Section 5, Section 7.1/Table 5, Section 7.2/Table 6, Tables 1-4, footnote 6, and appendices for implementation details. |
| Problem | The paper addresses parameter-efficient adaptation of large pretrained language models, where full fine-tuning is expensive in trainable parameters, optimizer state, GPU memory, and deployment/storage cost. |
| Core method | LoRA freezes pretrained weights and adds trainable low-rank decomposition matrices to selected dense weight matrices. Section 4.1 defines the adapted update as `Delta W = BA`, with frozen `W0` and trainable `A` and `B`, so the adapted weight path is commonly represented as `W0 + BA`. |
| Main hypothesis | The paper connects LoRA to the hypothesis that task adaptation updates have low intrinsic rank. |
| Scope of method | Section 4.2 frames LoRA as generally applicable to dense weight matrices in neural networks. The paper’s Transformer experiments focus on selected weight matrices in attention modules. |
| Evidence | Section 5 evaluates RoBERTa, DeBERTa, GPT-2, and GPT-3. Tables 2-4 report task quality results; Table 1 reports inference latency in a GPT-2 medium setup; Table 4 includes GPT-3 175B trainable-parameter comparisons; Section 7.1/Table 5 and Section 7.2/Table 6 provide analyses of adapted attention matrices and rank. |
| Baselines | Full fine-tuning and adapter-style efficient adaptation methods are mentioned in the packet. Exact baseline list, tuning details, and all compared methods are unknown from the packet except where tables are identified generally. |
| Metrics | Downstream task quality for GLUE, E2E NLG, WikiSQL, MultiNLI-matched, and SAMSum; trainable-parameter counts; GPU-memory requirements; training throughput/speed; inference latency. Exact metric definitions and numerical values are mostly not provided in the packet. |
| Ablations / analyses | Section 7.1/Table 5 analyze which attention weight matrices are adapted under an 18M-parameter budget in selected GPT-3 tasks. Section 7.2/Table 6 analyze rank `r` effects on WikiSQL and MultiNLI in selected GPT-3 settings. |
| Reproducibility | The paper reports public code and checkpoints for several model families. Appendices contain implementation details. The packet does not provide exact URLs, configs, seeds, hardware, hyperparameters, or full training recipes. |
| Limitations | The paper states that batching inputs for different tasks can be nontrivial when different samples require different LoRA modules. Footnote 6 cautions that a small rank `r` should not be expected to work for every task or dataset. |

## claim_ledger

| Claim | Claim type | Evidence-burden label | Source location | Supported scope |
|---|---|---|---|---|
| LoRA freezes pretrained weights and trains low-rank matrices for selected dense weight updates. | Method definition | DIRECT_PACKET_EVIDENCE | Section 4.1, Eq. 3; p. 1 Abstract/Figure 1 | LoRA method as described in the paper |
| LoRA represents the task-specific update as `Delta W = BA`, yielding an adapted weight `W0 + BA`. | Method definition | DIRECT_PACKET_EVIDENCE | Section 4.1, Eq. 3 | Dense matrices selected for LoRA adaptation |
| LoRA is generally applicable to dense weight matrices, though experiments focus on selected attention matrices in Transformers. | Method scope | DIRECT_PACKET_EVIDENCE | Section 4.2 | General framing plus paper’s Transformer experiments |
| The paper links LoRA to the hypothesis that adaptation updates have low intrinsic rank. | Assumption / hypothesis | DIRECT_PACKET_EVIDENCE | Abstract/Introduction and method notes | Hypothesis motivating LoRA, not universal proof |
| LoRA can be merged into `W0` for deployment, avoiding extra inference latency relative to the corresponding fully fine-tuned weight path. | Method/deployment claim | DIRECT_PACKET_EVIDENCE | Section 4.1; pp. 3-4 no-latency discussion | When LoRA weights are merged for a given task/module |
| LoRA performs on par or better than full fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3 in evaluated settings. | Empirical result | DIRECT_PACKET_EVIDENCE | Abstract; Section 5; Tables 2-4 | Only the paper’s reported settings and tasks |
| LoRA reduces trainable parameters and GPU memory in the GPT-3 175B adaptation setting. | Empirical/resource result | DIRECT_PACKET_EVIDENCE | Abstract; Table 4 | GPT-3 175B setting reported by the paper |
| LoRA provides a GPT-3 175B training-speed benefit relative to full fine-tuning with Adam in the stated setup. | Empirical/resource result | DIRECT_PACKET_EVIDENCE | Paragraph before Section 5 | The paper’s stated GPT-3 175B setup |
| Table 1 compares inference latency of adapter-style methods and LoRA/full fine-tuning in a GPT-2 medium setup. | Benchmark result | DIRECT_PACKET_EVIDENCE | p. 3 Table 1 | GPT-2 medium setup only |
| Small rank `r` should not be expected to work for every task or dataset. | Limitation | DIRECT_PACKET_EVIDENCE | p. 10 footnote 6 | Rank-selection generalization boundary |
| Batching inputs for different tasks is nontrivial when different samples require different LoRA modules. | Limitation | DIRECT_PACKET_EVIDENCE | p. 4 limitations paragraph before Section 5 | Multi-task serving/deployment with task-specific modules |
| Dynamic module selection remains possible when latency is not critical. | Deployment limitation/option | DIRECT_PACKET_EVIDENCE | p. 4 limitations paragraph before Section 5 | Cases where added latency is acceptable |

## evidence_ledger

| Evidence object | What it supports | Evidence-burden label | Evidence directness | Missing detail |
|---|---|---|---|---|
| Abstract and Figure 1 | Main LoRA idea; trainable-parameter/GPU-memory reductions; performance on par or better than full fine-tuning in evaluated settings | DIRECT_PACKET_EVIDENCE | Direct | Exact numbers are not included in the packet |
| p. 2 Introduction | Motivation and low-rank adaptation framing | DIRECT_PACKET_EVIDENCE | Direct | Full argument and citations unavailable in packet |
| Section 4.1, Eq. 3 | Formal update `Delta W = BA`; `W0` frozen; `A` and `B` trainable | DIRECT_PACKET_EVIDENCE | Direct | Initialization, scaling, optimizer details not specified in packet |
| Section 4.1 no-additional-latency discussion | LoRA weights can be merged into `W0` for deployment | DIRECT_PACKET_EVIDENCE | Direct | Practical serving details and module-switching overhead not fully specified |
| Section 4.2 | Applicability to dense matrices; Transformer experiments focus on attention modules | DIRECT_PACKET_EVIDENCE | Direct | Which non-attention dense matrices were or were not evaluated is only partially specified |
| Table 1 | Inference latency comparison among adapter-style methods, LoRA, and full fine-tuning in GPT-2 medium | DIRECT_PACKET_EVIDENCE | Direct | Exact latency values, hardware, batching, and measurement protocol are not provided in packet |
| Table 2 | GLUE results for RoBERTa/DeBERTa adaptation methods | DIRECT_PACKET_EVIDENCE | Direct | Exact scores, tasks, variance, and tuning details are not provided in packet |
| Table 3 | GPT-2 medium/large results on E2E NLG Challenge | DIRECT_PACKET_EVIDENCE | Direct | Exact scores and decoding/evaluation settings are not provided in packet |
| Table 4 | GPT-3 175B results on WikiSQL, MultiNLI-matched, and SAMSum, including trainable-parameter comparisons | DIRECT_PACKET_EVIDENCE | Direct | Exact values, prompt/evaluation setup, seeds, and variance are not provided in packet |
| Paragraph before Section 5 | GPT-3 175B training-speed benefit relative to full fine-tuning with Adam | DIRECT_PACKET_EVIDENCE | Direct | Exact speedup, hardware, optimizer state accounting, and run protocol unknown |
| Section 7.1/Table 5 | Which attention weight matrices are adapted under an 18M-parameter budget in selected GPT-3 tasks | DIRECT_PACKET_EVIDENCE | Direct | Generality beyond selected GPT-3 tasks unknown |
| Section 7.2/Table 6 | Effect of rank `r` on WikiSQL and MultiNLI in selected GPT-3 settings | DIRECT_PACKET_EVIDENCE | Direct | Rank behavior on other datasets/tasks unknown |
| Footnote 6 | Small rank `r` is not guaranteed for every task or dataset | DIRECT_PACKET_EVIDENCE | Direct | No universal rank-selection rule supplied |
| Appendices | Implementation details | DIRECT_PACKET_EVIDENCE | Partial | Packet does not provide the appendix contents |

## reproducibility_notes

The packet states that the paper reports public code and checkpoints for several model families, and that appendices contain implementation details. This is direct packet evidence for some reproducibility support.

Important unknowns remain from the supplied packet: exact code/checkpoint links, commit/version identifiers, model checkpoints, preprocessing, prompts, hyperparameters, optimizer settings, learning rates, rank/scaling settings, hardware, batch sizes, training steps, seeds, number of runs, confidence intervals, raw outputs, and full evaluation scripts are not provided here.

Rigor assessment: the packet identifies multiple tables, tasks, and analyses, but does not provide enough detail to audit variance, statistical reliability, tuning fairness, leakage risk, or exact reproducibility. These are `LIMITED_CRITIQUE` concerns based on missing packet detail, not established flaws.

## limitations_and_open_questions

LoRA’s no-additional-inference-latency claim depends on merging LoRA weights into the frozen weight path. The paper itself notes a deployment limitation: batching inputs for different tasks can be nontrivial when different samples require different LoRA modules. Dynamic module selection is possible when latency is not critical.

The rank assumption is bounded. Footnote 6 cautions that a small rank `r` should not be expected to work for every task or dataset. Therefore, the packet supports LoRA’s effectiveness in the reported settings, but not a universal claim that low-rank updates are sufficient for all adaptations.

The empirical superiority claim is setup-specific. The packet says LoRA performs on par or better than full fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3 in evaluated settings, but it does not support a global claim that LoRA is always better than full fine-tuning or other parameter-efficient methods.

Open questions from the packet: exact numerical results, variance across seeds, tuning budgets, full baseline strength, hardware-dependent throughput and latency behavior, task contamination risk, behavior on non-attention matrices, rank selection rules, and generalization to tasks outside the reported evaluations are unknown or need external review.