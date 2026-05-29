# SPR-DEV-01 Model Input Packet

## Source

LoRA: Low-Rank Adaptation of Large Language Models, arXiv:2106.09685, 26-page arXiv PDF.

## Controlled Source Notes

Core method:

- The paper proposes Low-Rank Adaptation, or LoRA.
- It freezes pretrained weights and adds trainable rank-decomposition matrices to represent updates to selected dense weight matrices.
- The method expresses an adapted weight as the frozen pretrained weight plus a low-rank update, commonly written as W0 + BA.
- Section 4.1 gives the trainable low-rank update form: W0 is frozen, A and B are trainable, and the task-specific update is represented as Delta W = BA.
- Section 4.2 frames LoRA as generally applicable to dense weight matrices in neural networks, while the paper's Transformer experiments focus on selected weight matrices in attention modules.
- The paper connects this to the hypothesis that adaptation updates have low intrinsic rank.
- Relevant evidence locations: p. 1 Abstract and Figure 1; p. 2 Introduction; p. 4 Sections 4.1-4.2, including Equation 3.

Claims and evidence:

- The abstract reports reductions in trainable parameters and GPU memory in the GPT-3 175B adaptation setting.
- The abstract says LoRA performs on par or better than full fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3 in the paper's evaluated settings.
- Section 5 evaluates downstream task performance on RoBERTa, DeBERTa, GPT-2, and GPT-3.
- Table 1 compares inference latency of adapter-style methods and LoRA/full fine-tuning in a GPT-2 medium setup.
- Table 2 reports GLUE results for RoBERTa/DeBERTa adaptation methods.
- Table 3 reports GPT-2 medium and large results on the E2E NLG Challenge.
- Table 4 reports GPT-3 175B results on WikiSQL, MultiNLI-matched, and SAMSum, including trainable-parameter comparisons.
- The paper reports evidence concerning trainable-parameter counts, GPU-memory requirements, training throughput, inference latency, and downstream task quality in different sections and experimental settings.
- The paragraph before Section 5 reports a GPT-3 175B training-speed benefit relative to full fine-tuning with Adam in the paper's stated setup.
- Section 4.1 explains that LoRA updates can be merged into W0 for deployment so that inference has no additional latency relative to the corresponding fully fine-tuned weight path.

Reproducibility and limitations:

- The paper reports public code and checkpoints for several model families.
- The method is described as orthogonal to some prior efficient adaptation approaches.
- A stated limitation is that batching inputs for different tasks can be nontrivial when different samples require different LoRA modules.
- When no-latency deployment depends on merged LoRA weights, batching inputs from different tasks that require different LoRA modules is not straightforward; the paper notes dynamic module selection remains possible when latency is not critical.
- Section 7.1 and Table 5 analyze which attention weight matrices are adapted under an 18M-parameter budget in selected GPT-3 tasks.
- Section 7.2 and Table 6 analyze the effect of rank r on WikiSQL and MultiNLI in selected GPT-3 settings.
- Footnote 6 cautions that a small rank r should not be expected to work for every task or dataset.
- Relevant evidence locations: abstract; p. 3 Table 1; pp. 3-4 Section 4.1 no-additional-inference-latency discussion; p. 4 limitations paragraph before Section 5; Section 5 experiment setup; p. 6 Table 3; p. 7 Table 4; p. 9 Section 7.1/Table 5; p. 9 Section 7.2/Table 6; p. 10 footnote 6; appendices for implementation details.
