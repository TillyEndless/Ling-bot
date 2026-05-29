# LS-DEV-01 Model Input Packet

Task: fixed-corpus literature mapping on transformer efficiency.

Runtime rule: use only this packet and the task YAML. Do not retrieve external papers.

## Corpus

1. Efficient Transformers: A Survey, arXiv:2009.06732, 39-page arXiv PDF.
2. Linformer: Self-Attention with Linear Complexity, arXiv:2006.04768, 12-page arXiv PDF.
3. Longformer: The Long-Document Transformer, arXiv:2004.05150, 17-page arXiv PDF.
4. FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness, arXiv:2205.14135, 34-page arXiv PDF.
5. LoRA: Low-Rank Adaptation of Large Language Models, arXiv:2106.09685, 26-page arXiv PDF.

## Controlled Source Notes

Efficient Transformers survey:

- The survey frames transformer efficiency around the standard attention mechanism's quadratic dependence on sequence length and organizes many approaches for reducing time or memory.
- Use it as a taxonomy/background paper, not as an empirical proof that any one method is best.
- Relevant evidence locations: abstract; survey taxonomy sections; comparison tables; discussion/limitations.

Linformer:

- The paper proposes projecting keys and values to a lower-dimensional sequence axis to make self-attention linear in sequence length under its assumptions.
- Its Table 1 compares per-layer time complexity, listing Linformer as O(n) where standard self-attention is quadratic.
- Its empirical discussion includes validation perplexity and downstream classification evidence, but any claim about practical superiority must stay tied to those settings.
- Relevant evidence locations: abstract; introduction; Section 3 method; Figure 2; Table 1; experiment section.

Longformer:

- The paper proposes local windowed attention plus task-motivated global attention for long documents.
- It claims linear scaling with sequence length for its attention pattern and evaluates both autoregressive language modeling and downstream long-document tasks.
- It is a long-context architecture paper, not an exact-attention kernel paper.
- Relevant evidence locations: abstract; Figure 1; Table 1; Section 3; Tables 7-11; appendices on implementation details.

FlashAttention:

- The paper introduces an IO-aware exact attention algorithm that reduces memory reads/writes between GPU memory levels.
- It is exact attention, not approximate/sparse attention.
- Evidence about speed or memory must be tied to the reported hardware/model/sequence settings.
- Relevant evidence locations: abstract; algorithm/IO-awareness sections; theorem/complexity discussion; experiment tables and figures.

LoRA:

- The paper freezes pretrained model weights and injects trainable low-rank update matrices for adaptation.
- It belongs in adaptation efficiency, not attention-computation efficiency.
- It reports large reductions in trainable parameters and memory for adaptation settings and evaluates on RoBERTa, DeBERTa, GPT-2, and GPT-3.
- Relevant evidence locations: abstract; Section 1; Section 4; Table 1; Table 2; GPT-3 experiment discussion; limitations paragraph in Section 4.

## Expected Literature-Mapping Boundaries

- Coverage means accounting for all five supplied papers.
- External papers may be mentioned only as "not in packet" if needed to explain a coverage limitation.
- Do not infer that the corpus exhausts transformer efficiency.
- Do not compare reported speedups across papers as if they used the same hardware, models, or benchmarks unless the packet directly supports that comparison.

