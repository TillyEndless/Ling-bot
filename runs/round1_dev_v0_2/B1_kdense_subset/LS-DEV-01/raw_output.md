## corpus_coverage_table

| Source | Role in packet | Research problem | Method or artifact | Evidence type supplied | Limitations visible from packet | Use in synthesis |
|---|---|---|---|---|---|---|
| Efficient Transformers: A Survey | Survey / taxonomy source | Transformer time and memory cost, especially standard attention’s quadratic sequence-length dependence | Organizes efficient Transformer approaches | Source notes cite abstract, taxonomy sections, comparison tables, discussion/limitations | Packet does not provide detailed taxonomy entries or quantitative table values | Frames the corpus-level efficiency problem and confirms that multiple method families target time or memory reduction |
| Linformer | Core method paper | Reduce self-attention complexity with respect to sequence length | Projects keys and values along the sequence axis to lower dimension | Table 1 lists Linformer per-layer time complexity as `O(n)` vs quadratic standard self-attention; experiments include validation perplexity and downstream classification in reported settings | Linear claim depends on the paper’s assumptions; packet does not specify exact datasets, metrics, or all empirical numbers | Represents low-rank / projection-based approximate attention |
| Longformer | Core method paper | Enable Transformer processing of long documents | Local windowed attention plus task-motivated global attention | Claims linear scaling with sequence length; evaluates autoregressive language modeling and downstream long-document tasks; evidence locations include Figure 1, Table 1, Section 3, Tables 7-11, appendices | Packet does not provide exact task names, scores, hardware, or full ablations | Represents sparse / structured attention for long-document modeling |
| FlashAttention | Core method paper | Make attention faster and more memory-efficient on hardware while preserving exact attention | IO-aware exact attention using tiling to reduce GPU memory reads/writes; extension to block-sparse attention | Abstract and Section 3 describe exact IO-aware algorithm; p. 7 Section 4.1/Table 1 reports BERT-large training-time comparison; p. 8 Table 2 reports GPT-2 training-time comparison; theorem/complexity and experiment figures/tables noted | Packet does not provide exact speedups, memory values, hardware details, or sequence settings beyond noting they are stated in the paper | Represents hardware-aware exact attention, distinct from approximate or sparse attention |
| LoRA | Core method paper, adjacent efficiency line | Reduce adaptation cost for large pretrained models | Freezes pretrained weights and injects trainable low-rank update matrices | Abstract, Section 1, Section 4, Table 1, Table 2, GPT-3 discussion report reductions in trainable parameters and memory; evaluated on RoBERTa, DeBERTa, GPT-2, GPT-3 | It targets adaptation efficiency, not necessarily base inference or full pretraining attention complexity; packet does not provide exact parameter/memory numbers | Represents parameter-efficient fine-tuning rather than attention-kernel or sequence-length efficiency |

## literature_taxonomy

| Efficiency line | Papers in corpus | Paper claims from packet | Evidence support |
|---|---|---|---|
| Survey and taxonomy of efficient Transformers | Efficient Transformers survey | Transformer efficiency is motivated by standard attention’s quadratic dependence on sequence length; the paper organizes approaches for reducing time or memory | Directly supported by controlled notes: abstract, taxonomy sections, comparison tables, discussion/limitations |
| Low-rank / projection-based attention | Linformer | Projects keys and values to lower-dimensional sequence axis, making self-attention linear in sequence length under assumptions | Direct support: abstract, introduction, Section 3, Figure 2, Table 1; empirical support from validation perplexity and downstream classification discussion |
| Sparse / structured attention for long sequences | Longformer | Uses local windowed attention plus task-motivated global attention; claims linear scaling with sequence length | Direct support: abstract, Figure 1, Table 1, Section 3; empirical support from language modeling and long-document task tables |
| Hardware-aware exact attention | FlashAttention | Computes exact attention with IO-aware tiling, reducing HBM reads/writes and avoiding full attention-matrix materialization; also reports block-sparse extension | Direct support: p. 1 abstract, p. 4 Section 3, theorem/complexity discussion, p. 7 Table 1, p. 8 Table 2 |
| Parameter-efficient adaptation | LoRA | Freezes pretrained weights and trains low-rank update matrices, reducing trainable parameters and memory in adaptation | Direct support: abstract, Section 1, Section 4, Table 1, Table 2, GPT-3 discussion |

## method_difference_matrix

| Dimension | Linformer | Longformer | FlashAttention | LoRA |
|---|---|---|---|---|
| Main target | Self-attention sequence-length complexity | Long-document attention scaling | GPU memory traffic and attention runtime | Fine-tuning/adaptation parameter and memory cost |
| Changes attention computation? | Yes | Yes | Yes, implementation/algorithmic schedule | No, not primarily from packet |
| Exact vs approximate | Packet implies approximation through projection under assumptions; exactness not established | Sparse pattern changes attention connectivity; exact equivalence to dense attention not established | Explicitly exact attention | Not an attention approximation method |
| Core mechanism | Low-dimensional projection of keys and values along sequence axis | Local windowed attention plus selected global attention | Tiling to reduce HBM reads/writes without materializing full attention matrix | Frozen pretrained weights plus trainable low-rank update matrices |
| Claimed scaling / savings | Table 1 lists `O(n)` per-layer time complexity | Claims linear scaling with sequence length | Reports speed and memory benefits under stated hardware/model/sequence settings | Reports large reductions in trainable parameters and memory for adaptation |
| Evidence in packet | Complexity table plus perplexity/classification experiments | Scaling claim plus language modeling and long-document downstream evaluations | BERT-large and GPT-2 training-time comparisons, complexity discussion, experiments | RoBERTa, DeBERTa, GPT-2, GPT-3 evaluations and parameter/memory tables |
| Main caveat from packet | Depends on assumptions; detailed assumptions and numbers not supplied | Exact task results and implementation details not included in packet | Exact speed/memory values and hardware settings not included in packet | Efficiency scope is adaptation, not general Transformer compute |

## core_paper_identification

| Core status | Paper | Reason |
|---|---|---|
| Framing source | Efficient Transformers survey | It supplies the packet’s broad problem framing and taxonomy: efficient Transformers are organized around reducing time or memory, especially due to quadratic standard attention |
| Core attention-efficiency method | Linformer | It directly modifies self-attention to reduce sequence-length complexity using low-rank sequence projection |
| Core attention-efficiency method | Longformer | It directly modifies attention structure for long-document processing through local and global sparse attention |
| Core systems-efficiency method | FlashAttention | It keeps attention exact but changes the hardware-aware computation schedule to reduce IO and memory use |
| Core adaptation-efficiency method | LoRA | It reduces the cost of adapting pretrained Transformers through trainable low-rank updates rather than changing base attention scaling |

## evidence_grounded_gap_list

| Gap visible within corpus | Evidence basis | Why it remains unresolved |
|---|---|---|
| No single directly comparable benchmark across all methods | Packet lists different evidence types: Linformer perplexity/classification, Longformer language modeling/long-document tasks, FlashAttention BERT/GPT-2 training-time comparisons, LoRA adaptation results | The packet does not provide a shared dataset, model, metric, hardware setup, or task suite |
| Approximate/sparse/exact methods are not directly ranked | Linformer, Longformer, and FlashAttention optimize different aspects of attention | The packet gives no controlled head-to-head comparison among these methods |
| Adaptation efficiency is separate from attention compute efficiency | LoRA targets trainable parameters and memory for downstream adaptation | The packet does not establish that LoRA reduces base attention runtime or long-sequence complexity |
| Hardware dependence is under-specified in the packet | FlashAttention evidence is tied to model, hardware, and sequence settings, but exact settings are not included in the packet | Cannot generalize speed or memory results beyond the stated-but-unspecified experimental settings |
| Claim scope for linear attention methods is incomplete | Linformer’s linearity is stated as holding “under its assumptions”; Longformer’s linearity depends on its attention pattern | The packet does not include the full assumptions, constants, approximation behavior, or failure cases |
| Survey taxonomy cannot be fully reconstructed | Survey notes mention taxonomy sections and comparison tables | The packet does not provide the actual taxonomy categories or table contents beyond broad framing |

## unsupported_synthesis_warnings

| Statement type | Status |
|---|---|
| “Linformer, Longformer, FlashAttention, and LoRA solve the same efficiency problem.” | Unsupported. The packet shows overlapping but distinct targets: sequence-length complexity, long-document sparsity, IO-aware exact attention, and adaptation cost. |
| “FlashAttention is better than Linformer or Longformer overall.” | Unsupported. The packet gives no global comparison or shared benchmark. |
| “Linformer preserves exact dense attention.” | Unsupported. The packet only states projection-based linear self-attention under assumptions. |
| “Longformer is universally linear for all Transformer workloads.” | Unsupported. The packet supports linear scaling for its attention pattern and long-document focus, not all workloads. |
| “LoRA improves inference speed or full pretraining efficiency.” | Not established by the packet. Supplied evidence concerns frozen-weight adaptation, trainable parameter reduction, and memory reduction in adaptation settings. |
| “The survey proves one dominant research direction.” | Unsupported. The survey is described as taxonomy/framing, not as evidence that one method family dominates. |
| “The corpus establishes field-wide gaps in transformer efficiency.” | Unsupported. Gaps listed here are visible only within the fixed packet, not the entire research field. |