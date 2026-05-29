# LS-DEV-01 Model Input Packet

## Corpus

1. Efficient Transformers: A Survey, arXiv:2009.06732, 39-page arXiv PDF.
2. Linformer: Self-Attention with Linear Complexity, arXiv:2006.04768, 12-page arXiv PDF.
3. Longformer: The Long-Document Transformer, arXiv:2004.05150, 17-page arXiv PDF.
4. FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness, arXiv:2205.14135, 34-page arXiv PDF.
5. LoRA: Low-Rank Adaptation of Large Language Models, arXiv:2106.09685, 26-page arXiv PDF.

## Controlled Source Notes

Efficient Transformers survey:

- The survey frames transformer efficiency around the standard attention mechanism's quadratic dependence on sequence length and organizes many approaches for reducing time or memory.
- The paper presents itself as a survey and taxonomy of efficient Transformer approaches.
- Relevant evidence locations: abstract; survey taxonomy sections; comparison tables; discussion/limitations.

Linformer:

- The paper proposes projecting keys and values to a lower-dimensional sequence axis to make self-attention linear in sequence length under its assumptions.
- Its Table 1 compares per-layer time complexity, listing Linformer as O(n) where standard self-attention is quadratic.
- Its empirical discussion includes validation perplexity and downstream classification evidence in the paper's reported settings.
- Relevant evidence locations: abstract; introduction; Section 3 method; Figure 2; Table 1; experiment section.

Longformer:

- The paper proposes local windowed attention plus task-motivated global attention for long documents.
- It claims linear scaling with sequence length for its attention pattern and evaluates both autoregressive language modeling and downstream long-document tasks.
- The paper focuses on long-document Transformer architecture and attention patterns.
- Relevant evidence locations: abstract; Figure 1; Table 1; Section 3; Tables 7-11; appendices on implementation details.

FlashAttention:

- The paper introduces an IO-aware exact attention algorithm that reduces memory reads/writes between GPU memory levels.
- The paper describes FlashAttention as an exact attention algorithm.
- The abstract states that FlashAttention is an IO-aware exact attention algorithm and also reports an extension to block-sparse attention.
- Section 3 describes an IO-aware attention algorithm using tiling to reduce HBM reads and writes while computing exact attention without materializing the full attention matrix.
- Reported speed and memory evidence appears in experiment tables and figures with stated model, hardware, and sequence settings.
- Relevant evidence locations: p. 1 Abstract; p. 4 Section 3; p. 7 Section 4.1 and Table 1 for BERT-large training-time comparison; p. 8 Table 2 for GPT-2 training-time comparison; theorem/complexity discussion; experiment tables and figures.

LoRA:

- The paper freezes pretrained model weights and injects trainable low-rank update matrices for adaptation.
- The paper frames LoRA around downstream adaptation with frozen pretrained weights and trainable low-rank update matrices.
- It reports large reductions in trainable parameters and memory for adaptation settings and evaluates on RoBERTa, DeBERTa, GPT-2, and GPT-3.
- Relevant evidence locations: abstract; Section 1; Section 4; Table 1; Table 2; GPT-3 experiment discussion; limitations paragraph in Section 4.
