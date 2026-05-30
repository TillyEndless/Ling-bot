## paper_card

| Field | Content |
|---|---|
| Source | *LoRA: Low-Rank Adaptation of Large Language Models*, arXiv:2106.09685, 26-page arXiv PDF. |
| Topic | Parameter-efficient fine-tuning for large language models. |
| Core method | LoRA freezes pretrained weights and adds trainable low-rank matrices to selected dense weight matrices. The adapted weight is represented as `W0 + BA`, where `W0` is frozen and `A`, `B` are trainable. |
| Main hypothesis | Adaptation updates have low intrinsic rank. |
| Scope of experiments | RoBERTa, DeBERTa, GPT-2, and GPT-3 evaluated on downstream tasks reported in Section 5 and associated tables. |
| Main claimed benefits | Fewer trainable parameters, lower GPU memory use, competitive or better downstream performance versus full fine-tuning in evaluated settings, and no additional inference latency when LoRA weights are merged into the frozen weight path. |
| Deployment note | LoRA updates can be merged into `W0` for deployment, avoiding extra inference latency relative to the corresponding fully fine-tuned path. |
| Stated limitation | Batching inputs for different tasks can be nontrivial when different samples require different LoRA modules, especially when relying on merged weights for no-latency deployment. |
| Artifact availability | The paper reports public code and checkpoints for several model families. Exact repository, commit, environment, and checkpoint details are unknown from the packet. |

## claim_ledger

| Claim | Type | Provenance | Evidence burden | Supplied evidence | Support status | Allowed scope |
|---|---|---|---|---|---|---|
| LoRA freezes pretrained weights and trains low-rank update matrices. | Method description | source-derived | Clear method specification | Section 4.1 states `W0` is frozen, `A` and `B` are trainable, and `Delta W = BA`; Equation 3 is cited in the packet. | Supported | The method as described in the paper. |
| LoRA is generally applicable to dense weight matrices in neural networks. | Method-scope claim | source-derived | Method definition plus scope statement | Section 4.2 frames LoRA as applicable to dense weight matrices; experiments focus on selected Transformer attention matrices. | Partially supported | Conceptual applicability to dense matrices; empirical support mainly for selected Transformer attention matrices in the packet. |
| LoRA is motivated by the hypothesis that adaptation updates have low intrinsic rank. | Mechanism/hypothesis claim | source-derived | Hypothesis plus analyses or ablations | Packet says the paper connects LoRA to this hypothesis; Sections 7.1 and 7.2 analyze adapted matrices and rank effects. | Partially supported | Supported as a motivating hypothesis and explored empirically; not established as universally causal. |
| LoRA reduces trainable parameters in GPT-3 175B adaptation. | Efficiency improvement | source-derived | Direct comparison under compatible setup | Abstract reports trainable-parameter reductions; Table 4 includes GPT-3 175B trainable-parameter comparisons. | Supported | GPT-3 175B settings reported in the paper. |
| LoRA reduces GPU memory in GPT-3 175B adaptation. | Efficiency improvement | source-derived | Direct measurement or comparison | Abstract reports GPU-memory reductions in the GPT-3 175B adaptation setting. | Supported, but details limited | GPT-3 175B setting stated in the abstract; exact measurement protocol unknown from packet. |
| LoRA performs on par or better than full fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3. | Performance improvement/equivalence | source-derived | Direct baseline comparison with compatible tasks, metrics, and tuning | Abstract states this; Section 5 evaluates these model families; Tables 2-4 report task results. | Supported within evaluated settings | Only the paper’s evaluated tasks, models, metrics, and protocols. |
| LoRA has no additional inference latency after merging weights. | Deployment/efficiency claim | source-derived | Deployment mechanism plus latency comparison | Section 4.1 explains LoRA updates can be merged into `W0`; Table 1 compares inference latency for adapter-style methods and LoRA/full fine-tuning in GPT-2 medium. | Supported within specified deployment path | When LoRA weights are merged into the corresponding dense weight path. |
| LoRA improves GPT-3 175B training speed relative to full fine-tuning with Adam. | Efficiency improvement | source-derived | Direct comparison under same setup | Paragraph before Section 5 reports a training-speed benefit relative to full fine-tuning with Adam. | Supported, but scoped | GPT-3 175B setup described by the paper; exact setup details unknown from packet. |
| Small rank `r` should work for every task or dataset. | Generalization claim | source-derived as negated by paper | Broad heterogeneous evidence required | Footnote 6 cautions that small rank `r` should not be expected to work for every task or dataset. | Not supported; explicitly cautioned against | No universal claim about small-rank sufficiency. |
| LoRA is orthogonal to some prior efficient adaptation approaches. | Method-composability claim | source-derived | Conceptual compatibility or experiments combining methods | Packet says the paper describes the method as orthogonal to some prior efficient adaptation approaches. | Partially supported | Conceptual claim unless combination experiments are detailed; not enough packet evidence for broad empirical composability. |

## evidence_ledger

| Evidence item | Location in packet/source | Supports | Directness | Notes |
|---|---|---|---|---|
| Abstract reports trainable-parameter and GPU-memory reductions for GPT-3 175B adaptation. | Abstract, p. 1 | Efficiency claims | Direct | Exact numbers are not included in the packet. |
| Abstract says LoRA performs on par or better than full fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3. | Abstract, p. 1 | Performance claim | Direct summary evidence | Needs table-level details for exact magnitude and task-by-task exceptions. |
| Figure 1 and introduction describe core LoRA idea. | p. 1 Figure 1; p. 2 Introduction | Method description | Direct | Packet gives conceptual description but not full figure contents. |
| Section 4.1 defines `W0`, `A`, `B`, and `Delta W = BA`. | p. 4 Section 4.1, Equation 3 | Method formalization | Direct | Strong support for the mathematical method claim. |
| Section 4.1 says updates can be merged into `W0` for deployment. | pp. 3-4 Section 4.1 | No-additional-latency deployment | Direct | Applies when using merged weights. |
| Section 4.2 frames applicability to dense matrices. | p. 4 Section 4.2 | Method-scope claim | Direct | Experiments still focus on selected Transformer attention matrices. |
| Table 1 compares inference latency of adapter-style methods and LoRA/full fine-tuning. | p. 3 Table 1 | Inference latency claim | Direct comparative evidence | GPT-2 medium setup only, according to packet. |
| Table 2 reports GLUE results for RoBERTa/DeBERTa adaptation methods. | Table 2 | Downstream performance | Direct | Exact metrics and values unknown from packet. |
| Table 3 reports GPT-2 medium and large results on E2E NLG Challenge. | p. 6 Table 3 | Downstream performance | Direct | Exact values unknown from packet. |
| Table 4 reports GPT-3 175B results on WikiSQL, MultiNLI-matched, and SAMSum, including trainable-parameter comparisons. | p. 7 Table 4 | GPT-3 performance and parameter efficiency | Direct | Supports only listed tasks. |
| Paragraph before Section 5 reports GPT-3 175B training-speed benefit relative to full fine-tuning with Adam. | Before Section 5 | Training speed | Direct | Exact magnitude and hardware details unknown from packet. |
| Section 7.1 and Table 5 analyze which attention matrices are adapted under an 18M-parameter budget. | p. 9 Section 7.1/Table 5 | Design choice and ablation evidence | Direct | Scope limited to selected GPT-3 tasks. |
| Section 7.2 and Table 6 analyze rank `r` effects on WikiSQL and MultiNLI. | p. 9 Section 7.2/Table 6 | Rank sensitivity | Direct | Scope limited to selected GPT-3 settings. |
| Footnote 6 cautions against expecting small rank to work everywhere. | p. 10 footnote 6 | Limitation/generalization boundary | Direct | Important negative evidence. |
| Appendices contain implementation details. | Appendices | Reproducibility | Indirect from packet | Specific details are unknown from packet. |
| Paper reports public code and checkpoints for several model families. | Reproducibility notes in packet | Artifact availability | Direct but incomplete | URL, versions, configs, and exact checkpoint coverage unknown. |

## reproducibility_notes

| Area | What is supplied | What remains unknown |
|---|---|---|
| Method specification | The update form `Delta W = BA`; `W0` frozen; `A` and `B` trainable; LoRA applied to selected dense matrices. | Initialization details, optimizer settings, learning rates, rank choices for every experiment, and exact module-selection configs are not specified in the packet. |
| Models | RoBERTa, DeBERTa, GPT-2, and GPT-3 are evaluated. | Exact model variants for all experiments, pretrained checkpoint identifiers, and tokenizer/config versions are unknown except where packet names GPT-2 medium/large and GPT-3 175B. |
| Tasks | GLUE, E2E NLG Challenge, WikiSQL, MultiNLI-matched, and SAMSum are mentioned. | Exact splits, preprocessing, prompts/templates, evaluation scripts, and task sampling are unknown. |
| Baselines | Full fine-tuning and adapter-style methods are compared in different settings. | Baseline tuning budgets, hyperparameter searches, compute parity, and implementation details are unknown. |
| Metrics | Tables report downstream task quality, inference latency, parameter counts, GPU memory, and training throughput. | Exact metric definitions, aggregation procedures, confidence intervals, variance, and number of seeds are unknown from the packet. |
| Artifacts | Paper reports public code and checkpoints for several model families. | Repository URL, commit hash, environment files, dependency versions, and full checkpoint inventory are unknown. |
| Ablations | Section 7.1 analyzes adapted attention matrices; Section 7.2 analyzes rank `r`. | Whether ablations cover all tasks, models, ranks, and module choices is unknown. |
| Deployment | LoRA weights can be merged into `W0` for no additional inference latency. | Operational details for multi-task serving, dynamic LoRA loading, and batching policies are not fully specified in the packet. |

## limitations_and_open_questions

| Limitation / question | Provenance | Why it matters |
|---|---|---|
| The strongest empirical claims are limited to the paper’s evaluated model families, tasks, metrics, and protocols. | agent-inferred from supplied evidence | The packet does not support unrestricted claims about all models, datasets, or fine-tuning scenarios. |
| Small rank `r` is not guaranteed to work for every task or dataset. | source-derived | Footnote 6 explicitly limits broad generalization about low-rank sufficiency. |
| No-latency deployment becomes harder when batching inputs requiring different LoRA modules. | source-derived | Merging task-specific LoRA weights into `W0` conflicts with heterogeneous task batches. |
| General applicability to dense matrices is broader than the main experimental focus. | cross-source synthesis | Section 4.2 frames generality, but experiments focus on selected Transformer attention matrices. |
| Exact reproducibility is under-specified in the packet. | agent-inferred | The packet mentions appendices, code, and checkpoints, but does not provide enough detail to reproduce results directly. |
| Variance, seeds, confidence intervals, and repeated-run stability are unknown. | unsupported by packet | Without these, robustness of reported improvements cannot be assessed from the packet alone. |
| Compute and tuning comparability with baselines is unknown. | unsupported by packet | Efficiency and quality comparisons require knowing whether baselines were equally tuned and run under compatible budgets. |
| The low-intrinsic-rank hypothesis is explored but not established as a universal causal explanation. | agent-inferred | Rank and module ablations support scoped analysis, but the packet does not establish a general causal mechanism across all adaptation settings. |