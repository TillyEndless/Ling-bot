## paper_card

**Paper:** LoRA: Low-Rank Adaptation of Large Language Models  
**Source:** arXiv:2106.09685, 26-page arXiv PDF  
**Topic:** Parameter-efficient fine-tuning

**Core idea:** LoRA freezes pretrained model weights and adds trainable low-rank decomposition matrices to selected dense weight matrices. The adapted weight is represented as:

```text
W = W0 + BA
```

where `W0` is frozen, `A` and `B` are trainable, and the task-specific update is `Delta W = BA`.

**Main motivation:** The paper connects LoRA to the hypothesis that adaptation updates have low intrinsic rank, meaning full-rank fine-tuning updates may be overparameterized for many downstream tasks.

**Scope of method:** Section 4.2 frames LoRA as generally applicable to dense weight matrices in neural networks. In the paper’s Transformer experiments, LoRA is applied mainly to selected attention-module weight matrices.

**Evaluated model families:** RoBERTa, DeBERTa, GPT-2, and GPT-3.

**Key claimed benefits:**

- Fewer trainable parameters than full fine-tuning.
- Lower GPU memory requirements in large-model adaptation.
- Comparable or better downstream quality than full fine-tuning in evaluated settings.
- No additional inference latency when LoRA updates are merged into frozen weights for deployment.
- Training-speed benefit for GPT-3 175B relative to full fine-tuning with Adam in the paper’s setup.

---

## claim_ledger

| ID | Claim | Scope | Support in packet | Status |
|---|---|---|---|---|
| C1 | LoRA freezes pretrained weights and trains low-rank update matrices. | Method definition | Section 4.1, Equation 3 | Supported |
| C2 | The task-specific update is represented as `Delta W = BA`. | Method definition | Section 4.1 | Supported |
| C3 | LoRA can apply generally to dense weight matrices in neural networks. | General method framing | Section 4.2 | Supported |
| C4 | Transformer experiments focus on selected attention-module weight matrices. | Experimental scope | Controlled notes, Section 4.2/experiments | Supported |
| C5 | LoRA is motivated by the hypothesis that adaptation updates have low intrinsic rank. | Conceptual motivation | Controlled notes | Supported |
| C6 | LoRA reduces trainable parameters in GPT-3 175B adaptation. | GPT-3 175B setting | Abstract, Table 4 | Supported |
| C7 | LoRA reduces GPU memory requirements in GPT-3 175B adaptation. | GPT-3 175B setting | Abstract | Supported, exact figures unknown |
| C8 | LoRA performs on par with or better than full fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3 in evaluated settings. | Reported experiments only | Abstract, Section 5, Tables 2-4 | Supported |
| C9 | LoRA has no additional inference latency relative to the corresponding fully fine-tuned path when merged into `W0`. | Deployment/inference | Section 4.1 | Supported |
| C10 | LoRA improves GPT-3 175B training speed relative to full fine-tuning with Adam in the paper’s setup. | Stated GPT-3 setup | Paragraph before Section 5 | Supported, exact speedup unknown |
| C11 | Adapter-style methods can introduce inference latency, while LoRA/full fine-tuning avoid this in the GPT-2 medium comparison. | GPT-2 medium setup | Table 1 | Supported |
| C12 | Public code and checkpoints are reported for several model families. | Reproducibility | Controlled notes | Supported, exact URLs unknown |
| C13 | LoRA is orthogonal to some prior efficient adaptation methods. | Method relationship | Controlled notes | Supported |
| C14 | Small rank `r` should not be expected to work for every task or dataset. | Limitation/generalization | Footnote 6 | Supported |
| C15 | Batching inputs from different tasks can be nontrivial when different samples require different LoRA modules. | Deployment limitation | Limitations paragraph before Section 5 | Supported |

---

## evidence_ledger

| Evidence ID | Location | What it supports |
|---|---|---|
| E1 | Abstract, p. 1 | Reports trainable-parameter and GPU-memory reductions in GPT-3 175B adaptation; reports comparable or better performance than full fine-tuning across RoBERTa, DeBERTa, GPT-2, and GPT-3 settings. |
| E2 | Figure 1, p. 1 | Illustrates the LoRA setup of frozen pretrained weights plus trainable low-rank update. |
| E3 | Introduction, p. 2 | Motivates parameter-efficient adaptation and low-rank update framing. |
| E4 | Section 4.1, p. 4, Equation 3 | Defines `W0` as frozen, `A` and `B` as trainable, and `Delta W = BA`. |
| E5 | Section 4.1, pp. 3-4 | Explains that LoRA weights can be merged into `W0` for deployment, giving no additional inference latency relative to the equivalent fine-tuned weight path. |
| E6 | Section 4.2, p. 4 | Frames LoRA as applicable to dense weight matrices, while experiments focus on selected Transformer attention weights. |
| E7 | Table 1, p. 3 | Compares inference latency for adapter-style methods and LoRA/full fine-tuning in a GPT-2 medium setup. |
| E8 | Paragraph before Section 5 | Reports GPT-3 175B training-speed benefit relative to full fine-tuning with Adam in the stated setup. |
| E9 | Section 5 | Provides downstream evaluation setup for RoBERTa, DeBERTa, GPT-2, and GPT-3. |
| E10 | Table 2 | Reports GLUE results for RoBERTa and DeBERTa adaptation methods. |
| E11 | Table 3, p. 6 | Reports GPT-2 medium and large results on the E2E NLG Challenge. |
| E12 | Table 4, p. 7 | Reports GPT-3 175B results on WikiSQL, MultiNLI-matched, and SAMSum, including trainable-parameter comparisons. |
| E13 | Section 7.1 and Table 5, p. 9 | Analyze which attention weight matrices are adapted under an 18M-parameter budget in selected GPT-3 tasks. |
| E14 | Section 7.2 and Table 6, p. 9 | Analyze the effect of rank `r` on WikiSQL and MultiNLI in selected GPT-3 settings. |
| E15 | Footnote 6, p. 10 | Cautions that small rank `r` should not be expected to work for every task or dataset. |
| E16 | Appendices | Contain implementation details; exact content unknown from packet. |

---

## reproducibility_notes

**Available reproducibility signals from the packet:**

- The paper reports public code and checkpoints for several model families.
- Appendices include implementation details.
- The method is mathematically specified in Section 4.1 via the low-rank update `Delta W = BA`.
- Experiments are organized by model family and task:
  - RoBERTa/DeBERTa on GLUE in Table 2.
  - GPT-2 medium/large on E2E NLG Challenge in Table 3.
  - GPT-3 175B on WikiSQL, MultiNLI-matched, and SAMSum in Table 4.
- Section 7.1/Table 5 analyze adapted attention matrices under an 18M-parameter budget.
- Section 7.2/Table 6 analyze rank `r` effects on selected GPT-3 tasks.

**Unknown from the packet:**

- Exact hyperparameters.
- Exact optimizer settings beyond the mention of full fine-tuning with Adam in one GPT-3 comparison.
- Exact trainable-parameter counts except that Table 4 includes comparisons.
- Exact GPU-memory numbers.
- Exact training-throughput numbers.
- Exact random seeds.
- Dataset preprocessing details.
- Code/checkpoint URLs.
- Hardware configuration.
- Whether all reported experiments are fully reproducible from released artifacts.

---

## limitations_and_open_questions

**Stated limitations:**

- Batching inputs from different tasks is nontrivial when different samples require different LoRA modules.
- No-latency deployment depends on merging LoRA weights into the frozen weights. If different tasks require different merged LoRA modules, mixed-task batching is not straightforward.
- Dynamic module selection remains possible when latency is not critical.
- Footnote 6 cautions that a small rank `r` should not be expected to work for every task or dataset.

**Scope limitations visible from the packet:**

- Although LoRA is framed as generally applicable to dense weight matrices, the Transformer experiments focus on selected attention-module matrices.
- Rank sensitivity is analyzed only for selected GPT-3 settings on WikiSQL and MultiNLI.
- Matrix-selection analysis is reported under an 18M-parameter budget in selected GPT-3 tasks, not necessarily all tasks or models.

**Open questions not answered by the packet:**

- How LoRA performs on domains or tasks outside those evaluated.
- How robust the method is across many random seeds.
- How to choose rank `r` systematically for a new task.
- How to choose which dense matrices to adapt in architectures beyond the evaluated Transformer settings.
- Whether the reported memory and speed benefits hold across other hardware, batch sizes, optimizers, and training systems.
- How LoRA interacts empirically with other efficient adaptation methods, despite being described as orthogonal.