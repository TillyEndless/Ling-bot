# SPR-DEV-01 Model Input Packet

Task: structured deep reading of LoRA.

Runtime rule: use only this packet and the task YAML. Do not retrieve external papers.

## Source

LoRA: Low-Rank Adaptation of Large Language Models, arXiv:2106.09685, 26-page arXiv PDF.

## Controlled Source Notes

Core method:

- The paper proposes Low-Rank Adaptation, or LoRA.
- It freezes pretrained weights and adds trainable rank-decomposition matrices to represent updates to selected dense weight matrices.
- The method expresses an adapted weight as the frozen pretrained weight plus a low-rank update, commonly written as W0 + BA.
- The paper connects this to the hypothesis that adaptation updates have low intrinsic rank.
- Relevant evidence locations: abstract; Section 1; Section 4; Figure 1.

Claims and evidence:

- The abstract reports reductions in trainable parameters and GPU memory in the GPT-3 175B adaptation setting.
- The abstract says LoRA performs on par or better than full fine-tuning on RoBERTa, DeBERTa, GPT-2, and GPT-3 in the paper's evaluated settings.
- Section 5 evaluates downstream task performance on RoBERTa, DeBERTa, GPT-2, and GPT-3.
- Table 1 compares inference latency of adapter-style methods and LoRA/full fine-tuning in a GPT-2 medium setup.
- Table 2 reports GLUE results for RoBERTa/DeBERTa adaptation methods.

Reproducibility and limitations:

- The paper reports public code and checkpoints for several model families.
- The method is described as orthogonal to some prior efficient adaptation approaches, but that does not prove compatibility in every later setting.
- A stated limitation is that batching inputs for different tasks can be nontrivial when different samples require different LoRA modules.
- Relevant evidence locations: abstract; Section 4 limitations paragraph; Section 5 experiment setup; appendices for implementation details.

## Required Boundaries

- Distinguish trainable-parameter reduction, GPU memory reduction, inference latency, and task quality.
- Do not claim LoRA is universally better than full fine-tuning.
- Mark any missing implementation detail as missing rather than inferring it.

