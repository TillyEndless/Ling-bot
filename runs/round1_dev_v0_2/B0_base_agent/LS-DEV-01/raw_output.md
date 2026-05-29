## corpus_coverage_table

| Paper | Efficiency target | Main method line | Evidence provided in packet | Scope limits visible from packet |
|---|---:|---|---|---|
| Efficient Transformers: A Survey | Attention time/memory, especially quadratic sequence-length scaling | Survey taxonomy of efficient Transformer approaches | Frames standard attention as quadratic in sequence length; organizes methods for reducing time or memory; includes taxonomy, comparison tables, discussion/limitations | It is secondary literature, not a new method evaluation paper in this packet |
| Linformer | Self-attention sequence-length complexity | Low-rank projection of keys and values along the sequence axis | Claims linear self-attention under its assumptions; Table 1 lists Linformer per-layer complexity as `O(n)` versus quadratic standard self-attention; reports validation perplexity and downstream classification results | Linear claim depends on paper assumptions; packet does not provide detailed numeric results |
| Longformer | Long-sequence / long-document attention | Sparse attention pattern: local windowed attention plus task-driven global attention | Claims linear scaling with sequence length for its attention pattern; evaluates autoregressive language modeling and downstream long-document tasks; evidence in Figure 1, Table 1, Section 3, Tables 7-11, appendices | Focused on long-document Transformer architecture, not general dense attention acceleration |
| FlashAttention | GPU memory traffic and attention runtime/memory | IO-aware exact attention using tiling; avoids materializing full attention matrix | Abstract calls it IO-aware exact attention; Section 3 describes tiling to reduce HBM reads/writes while computing exact attention; reports speed and memory evidence for BERT-large and GPT-2 training settings; also reports block-sparse extension | Evidence is tied to stated hardware, model, and sequence settings |
| LoRA | Fine-tuning/adaptation parameter and memory cost | Freeze pretrained weights; add trainable low-rank update matrices | Reports large reductions in trainable parameters and memory for adaptation; evaluates RoBERTa, DeBERTa, GPT-2, and GPT-3; evidence in abstract, Sections 1 and 4, Tables 1-2, GPT-3 discussion | Addresses adaptation efficiency, not base Transformer attention computation during pretraining/inference |

## literature_taxonomy

| Research line | Papers | Core idea | Paper claims | Synthesis from packet |
|---|---|---|---|---|
| Survey/taxonomic framing | Efficient Transformers survey | Organize efficient Transformer methods around time and memory reduction | Transformer efficiency is motivated by quadratic standard attention dependence on sequence length | This paper provides the map into which the other methods can be placed |
| Low-rank attention approximation | Linformer | Project keys and values to a lower-dimensional sequence axis | Self-attention can be made linear in sequence length under Linformer assumptions | This line trades full attention structure for a projected representation intended to preserve task performance |
| Sparse/local/global attention patterns | Longformer | Restrict most tokens to local windows while allowing selected global attention | Attention pattern scales linearly with sequence length and supports long-document tasks | This line changes the connectivity pattern rather than computing dense attention |
| IO-aware exact attention | FlashAttention | Reorder exact attention computation with tiling to reduce GPU memory traffic | Computes exact attention without materializing the full attention matrix; improves speed and memory in reported settings | This line keeps the mathematical attention result exact while improving implementation efficiency |
| Parameter-efficient adaptation | LoRA | Freeze base weights and train low-rank update matrices | Reduces trainable parameters and memory for downstream adaptation across several model families | This is a different efficiency axis: adaptation cost rather than attention complexity |

## method_difference_matrix

| Dimension | Linformer | Longformer | FlashAttention | LoRA |
|---|---|---|---|---|
| Primary efficiency bottleneck | Quadratic self-attention over sequence length | Long-document sequence length | GPU memory reads/writes and attention materialization | Fine-tuning parameter and memory cost |
| Main intervention | Low-rank projection of keys/values | Sparse local window plus global attention | IO-aware tiled exact attention | Low-rank trainable adapters with frozen base weights |
| Attention result | Approximate or assumption-dependent reduction | Modified sparse attention pattern | Exact attention | Does not primarily modify attention computation |
| Claimed complexity/effect | Linear in sequence length per Table 1 | Linear scaling with sequence length | Faster and more memory-efficient exact attention in reported settings | Large reductions in trainable parameters and adaptation memory |
| Evidence type | Complexity table; perplexity; classification experiments | Scaling claim; language modeling; long-document downstream tasks | Algorithm analysis; BERT-large and GPT-2 training-time tables; memory/speed figures | Parameter/memory tables; RoBERTa, DeBERTa, GPT-2, GPT-3 adaptation results |
| Best characterized as | Architectural attention approximation | Sparse long-context architecture | Systems/kernel-level attention algorithm | Parameter-efficient fine-tuning method |

## core_paper_identification

| Role in corpus | Paper | Reason |
|---|---|---|
| Framing paper | Efficient Transformers survey | Provides the high-level taxonomy and identifies quadratic attention as the central efficiency problem |
| Representative low-rank attention paper | Linformer | Directly targets self-attention complexity by projecting keys and values |
| Representative sparse long-context paper | Longformer | Directly targets long-document computation with local/global sparse attention |
| Representative exact systems optimization paper | FlashAttention | Improves attention implementation while preserving exact attention |
| Representative adaptation-efficiency paper | LoRA | Moves efficiency focus from attention computation to trainable-parameter and memory cost during adaptation |

## evidence_grounded_gap_list

| Gap visible within corpus | Grounding |
|---|---|
| The corpus mixes different efficiency objectives, making direct comparison difficult | Linformer and Longformer target sequence scaling; FlashAttention targets GPU IO/runtime/memory; LoRA targets adaptation parameters/memory |
| The packet does not provide a unified benchmark across all methods | Evidence is paper-specific: Linformer reports perplexity/classification, Longformer reports long-document tasks, FlashAttention reports BERT/GPT-2 training speed/memory, LoRA reports adaptation results |
| Approximate/sparse/exact methods are not evaluated under one shared accuracy-efficiency tradeoff | Linformer changes attention via projection; Longformer changes attention pattern; FlashAttention preserves exact attention |
| Hardware dependence is visible but not normalized across corpus | FlashAttention evidence is explicitly tied to model, hardware, and sequence settings; packet does not provide comparable hardware detail for all papers |
| Adaptation efficiency is underconnected to attention efficiency | LoRA is included but addresses fine-tuning cost rather than the main quadratic-attention bottleneck emphasized by the survey |
| Long-sequence effectiveness beyond reported settings is not established in the packet | Linformer and Longformer claims are supported by their reported experiments, but the packet does not supply broad cross-domain evidence |

## unsupported_synthesis_warnings

| Statement type | Status |
|---|---|
| “FlashAttention is always faster than sparse or low-rank attention.” | Unsupported by packet |
| “Linformer preserves accuracy for all Transformer tasks.” | Unsupported by packet |
| “Longformer is the best method for all long-context applications.” | Unsupported by packet |
| “LoRA reduces inference compute for standard Transformer forward passes.” | Unsupported by packet |
| “All methods are directly comparable on one benchmark.” | Unsupported by packet |
| “The corpus proves one dominant efficiency approach.” | Unsupported by packet |
| “Block-sparse FlashAttention results generalize to every sparse attention pattern.” | Unsupported by packet |
| “The survey’s taxonomy exhausts all transformer-efficiency research after its publication.” | Unsupported by packet |

Overall synthesis: within this fixed corpus, transformer efficiency splits into at least four main lines: reduce attention complexity through low-rank projection, reduce attention connectivity through sparse/local/global patterns, preserve exact attention while improving hardware IO behavior, and reduce downstream adaptation cost through low-rank trainable updates. The packet supports this taxonomy, but it does not support a single overall ranking across papers.