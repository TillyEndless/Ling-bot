## paper_card

| Field | Reading |
|---|---|
| Problem | The paper addresses parameter-efficient adaptation of large pretrained language models, especially the cost of full fine-tuning in settings such as GPT-3 175B adaptation. |
| Core method | LoRA freezes pretrained weights and adds trainable low-rank matrices to selected dense weight matrices. Section 4.1 defines the adapted update as `Delta W = BA`, with frozen `W0` and trainable `A` and `B`, so the adapted weight path is commonly represented as `W0 + BA`. |
| Main hypothesis | The method is connected to the hypothesis that task adaptation updates have low intrinsic rank. |
| Applicability claim | Section 4.2 frames LoRA as generally applicable to dense weight matrices in neural networks, while the reported Transformer experiments focus on selected attention-module weight matrices. |
| Evidence | Section 5 evaluates RoBERTa, DeBERTa, GPT-2, and GPT-3. Tables 2-4 report downstream quality results. Table 1 reports inference latency in a GPT-2 medium setup. Other reported evidence covers trainable parameters, GPU memory, training throughput, and deployment latency. |
| Baselines | Full fine-tuning and adapter-style methods are included in the supplied notes. Exact baseline list, tuning procedures, and all compared variants are unknown from the packet except where specific tables are named. |
| Metrics | Downstream task quality metrics are reported in Tables 2-4, but the packet does not specify exact metrics per task. It also notes trainable-parameter counts, GPU-memory requirements, training throughput, and inference latency. |
| Ablations | Section 7.1/Table 5 analyze which attention matrices are adapted under an 18M-parameter budget in selected GPT-3 tasks. Section 7.2/Table 6 analyze rank `r` on WikiSQL and MultiNLI in selected GPT-3 settings. |
| Reproducibility | The paper reports public code and checkpoints for several model families. Appendices contain implementation details. Exact configs, seeds, hardware, raw outputs, and complete hyperparameter details are unknown from the packet. |
| Limitations | A stated limitation is that batching different tasks can be nontrivial when samples require different LoRA modules, especially when no-latency deployment relies on merged weights. Footnote 6 cautions that small rank `r` should not be expected to work for every task or dataset. |

## claim_ledger

| Claim | Claim type | Source location | Evidence directness | Supported scope | Missing detail |
|---|---|---|---|---|---|
| LoRA freezes pretrained weights and trains low-rank decomposition matrices for selected dense weight updates. | Method definition | p. 4 Sections 4.1-4.2, Equation 3 | Direct | Method definition as described in the paper | Exact initialization, scaling, and implementation details are not in the packet |
| The adapted weight can be represented as `W0 + BA`, where `W0` is frozen and `A`, `B` are trainable. | Method definition | p. 4 Section 4.1, Equation 3 | Direct | Selected dense weight matrices | Exact dimensions are not provided in the packet |
| LoRA is motivated by the hypothesis that adaptation updates have low intrinsic rank. | Assumption / hypothesis | p. 1 Abstract/Figure 1; p. 2 Introduction; p. 4 Sections 4.1-4.2 | Direct | Motivating hypothesis for parameter-efficient adaptation | Packet does not establish this as universally true |
| LoRA can be applied to dense weight matrices generally, though experiments focus on selected Transformer attention matrices. | Scope claim | p. 4 Section 4.2 | Direct | General method framing; experimental support limited to evaluated Transformer settings | Evidence for non-Transformer or all dense-matrix use is not supplied |
| LoRA reduces trainable parameters and GPU memory in GPT-3 175B adaptation. | Empirical result | Abstract; Table 4 for trainable-parameter comparisons | Direct / partial | Paper’s GPT-3 175B adaptation setting | Exact reduction values are not in the packet |
| LoRA performs on par or better than full fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3 in evaluated settings. | Empirical result | Abstract; Section 5; Tables 2-4 | Direct | Only the evaluated models, tasks, and protocols | Exact scores, variance, and task metrics are not in the packet |
| LoRA has no additional inference latency relative to the corresponding fully fine-tuned weight path when updates are merged into `W0`. | Deployment / efficiency claim | pp. 3-4 Section 4.1; Table 1 for latency comparison | Direct | Inference path where LoRA weights are merged | Operational constraints for serving multiple task modules remain |
| LoRA gives a GPT-3 175B training-speed benefit relative to full fine-tuning with Adam in the stated setup. | Empirical result | Paragraph before Section 5 | Direct | GPT-3 175B setup described by the paper | Exact speedup value and hardware details are not in the packet |
| The paper analyzes attention-matrix choices under an 18M-parameter budget. | Ablation / analysis | p. 9 Section 7.1/Table 5 | Direct | Selected GPT-3 tasks | Exact task list and results are not in the packet |
| The paper analyzes rank `r` on WikiSQL and MultiNLI in selected GPT-3 settings. | Ablation / sensitivity | p. 9 Section 7.2/Table 6 | Direct | WikiSQL and MultiNLI selected GPT-3 settings | Exact ranks and scores are not in the packet |
| Small rank `r` should not be expected to work for every task or dataset. | Limitation | p. 10 footnote 6 | Direct | Rank-selection caution across tasks/datasets | Conditions where small rank fails are not specified in the packet |

## evidence_ledger

| Evidence item | Location | What it supports | Boundary |
|---|---|---|---|
| Abstract and Figure 1 | p. 1 | High-level LoRA method, parameter/memory reduction claims, and on-par-or-better performance claim | Abstract-level claims require table-level details for exact magnitudes |
| Introduction | p. 2 | Motivation for low-rank adaptation and efficient fine-tuning | Motivation does not prove universal low-rank structure |
| Equation 3 and Section 4.1 | p. 4 | Formal update `Delta W = BA`; frozen `W0`; trainable `A`, `B`; mergeability for no additional inference latency | Does not by itself establish empirical performance |
| Section 4.2 | p. 4 | General applicability to dense matrices; Transformer experiments focus on attention matrices | Empirical evidence in packet is limited to listed model/task settings |
| Table 1 | p. 3 | Inference latency comparison among adapter-style methods and LoRA/full fine-tuning in GPT-2 medium | Latency result is setup-specific |
| Section 5 | Section 5 | Downstream evaluation on RoBERTa, DeBERTa, GPT-2, GPT-3 | Exact protocol details are unknown from packet |
| Table 2 | Section 5 | GLUE results for RoBERTa/DeBERTa adaptation methods | Exact metrics, scores, variance, and baseline tuning details are not supplied |
| Table 3 | p. 6 | GPT-2 medium and large results on E2E NLG Challenge | Exact scores and evaluation metrics are not in packet |
| Table 4 | p. 7 | GPT-3 175B results on WikiSQL, MultiNLI-matched, and SAMSum, including trainable-parameter comparisons | Does not establish results outside these tasks/settings |
| Paragraph before Section 5 | Before Section 5 | GPT-3 175B training-speed benefit relative to full fine-tuning with Adam | Exact speedup, hardware, and full training setup are unknown |
| Section 7.1/Table 5 | p. 9 | Which attention weight matrices are adapted under an 18M-parameter budget | Limited to selected GPT-3 tasks and the fixed budget |
| Section 7.2/Table 6 | p. 9 | Effect of rank `r` on WikiSQL and MultiNLI in selected GPT-3 settings | Does not imply one rank works across all tasks |
| Footnote 6 | p. 10 | Caution against expecting small rank `r` to work for every task/dataset | Limitation is stated, but failure cases are not detailed in packet |
| Appendices | Appendices | Implementation details | Specific appendix contents are not included in the packet |

## reproducibility_notes

The packet states that the paper reports public code and checkpoints for several model families, and that appendices contain implementation details. That supports a positive reproducibility claim at the artifact-availability level.

Unknown from the packet: exact random seeds, run counts, uncertainty estimates, hardware, full hyperparameter grids, tuning budgets, data preprocessing, exact prompts if any, raw outputs, and complete model-version details. The packet also does not specify whether all experiments in Tables 1-6 are reproducible from the released artifacts.

The paper reports several experiment types: downstream task quality, trainable-parameter counts, GPU-memory requirements, training throughput, inference latency, attention-matrix ablations, and rank sensitivity. However, the packet does not provide exact numeric results, so the strength of individual empirical claims cannot be independently audited beyond the described source locations.

## limitations_and_open_questions

LoRA’s strongest supported claims are setup-bound: parameter efficiency, memory savings, latency behavior, and downstream quality are supported only for the evaluated RoBERTa, DeBERTa, GPT-2, and GPT-3 settings described in the paper.

The low intrinsic-rank idea is presented as a motivating hypothesis and is probed through rank analysis, but the packet does not establish it as a universal mechanism of adaptation. Footnote 6 explicitly cautions that small rank `r` should not be expected to work for every task or dataset.

The no-additional-latency claim depends on merging LoRA updates into the frozen weights. The paper states a serving limitation: batching inputs from different tasks is nontrivial when samples require different LoRA modules. Dynamic module selection remains possible when latency is not critical, but that weakens the simple no-latency deployment story for multi-task serving.

Open details not resolved by the packet include exact scores, confidence intervals, seed counts, full baseline tuning fairness, hardware, complete implementation settings, and whether results transfer to architectures, tasks, or deployment regimes outside those reported.