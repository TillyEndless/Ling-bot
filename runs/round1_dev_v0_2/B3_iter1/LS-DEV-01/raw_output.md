## corpus_coverage_table

| Source | Corpus role | Efficiency target | Core paper claim | Evidence provided in packet | Evidence-burden label | Coverage boundary |
|---|---|---|---|---|---|---|
| Efficient Transformers: A Survey | Survey / taxonomy | Transformer time and memory, especially attention cost | Standard attention has quadratic dependence on sequence length; many methods reduce time or memory | Abstract; taxonomy sections; comparison tables; discussion/limitations | `DIRECT_PACKET_EVIDENCE` | Packet gives no specific table values or full taxonomy details beyond controlled notes |
| Linformer | Method paper | Attention complexity with respect to sequence length | Projects keys and values along the sequence axis to make self-attention linear in sequence length under its assumptions | Abstract; intro; Section 3; Figure 2; Table 1; experiments with validation perplexity and downstream classification | `DIRECT_PACKET_EVIDENCE` | Empirical setup details, exact datasets, numbers, seeds, and uncertainty are not supplied |
| Longformer | Method paper | Long-document attention | Uses local windowed attention plus task-motivated global attention; claims linear scaling with sequence length | Abstract; Figure 1; Table 1; Section 3; Tables 7-11; appendices on implementation | `DIRECT_PACKET_EVIDENCE` | Packet does not provide exact scores, baselines, seed counts, or task list details |
| FlashAttention | Systems / algorithm paper | Attention runtime and memory movement on GPUs | IO-aware exact attention uses tiling to reduce HBM reads/writes without materializing full attention matrix | Abstract p.1; Section 3 p.4; Section 4.1 p.7; Table 1 BERT-large; Table 2 GPT-2; theorem/complexity discussion; experiment figures/tables | `DIRECT_PACKET_EVIDENCE` | Packet does not include exact speedups, hardware specs beyond “stated model, hardware, and sequence settings,” or all experiment values |
| LoRA | Adaptation-efficiency method paper | Fine-tuning trainable parameters and memory | Freezes pretrained weights and injects trainable low-rank update matrices for downstream adaptation | Abstract; Section 1; Section 4; Tables 1-2; GPT-3 discussion; Section 4 limitations paragraph | `DIRECT_PACKET_EVIDENCE` | Not a primary attention-complexity method; packet does not give exact parameter/memory numbers |

## literature_taxonomy

| Research line | Papers | Efficiency mechanism | Main measured or claimed benefit | Evidence status | Boundary |
|---|---|---|---|---|---|
| Attention approximation / projection | Linformer | Low-rank projection of keys and values along sequence dimension | Per-layer attention complexity listed as `O(n)` versus quadratic standard attention | `DIRECT_PACKET_EVIDENCE` from Table 1 and Section 3 notes | Linear claim is under Linformer’s assumptions; packet does not establish universal accuracy preservation |
| Sparse / structured attention for long context | Longformer | Local sliding-window attention plus selected global attention | Linear scaling with sequence length for long-document processing | `DIRECT_PACKET_EVIDENCE` from abstract, Figure 1, Table 1, Section 3 | Best supported for long-document settings reported by the paper, not all transformer workloads |
| IO-aware exact attention | FlashAttention | Tiling and memory hierarchy-aware computation; avoids materializing full attention matrix | Faster and more memory-efficient exact attention in reported BERT-large and GPT-2 settings | `DIRECT_PACKET_EVIDENCE` from p.1 abstract, p.4 Section 3, p.7 Table 1, p.8 Table 2 | Evidence is hardware/model/sequence-setting dependent; packet does not support broad hardware-general claims |
| Parameter-efficient adaptation | LoRA | Freeze pretrained weights; train low-rank update matrices | Large reductions in trainable parameters and memory for adaptation on RoBERTa, DeBERTa, GPT-2, GPT-3 | `DIRECT_PACKET_EVIDENCE` from abstract, Sections 1/4, Tables 1-2 | Improves adaptation efficiency, not necessarily pretraining or inference attention cost |
| Survey-level organization | Efficient Transformers survey | Taxonomizes efficient Transformer approaches | Frames efficiency around quadratic attention and organizes reduction strategies | `DIRECT_PACKET_EVIDENCE` | Useful for map structure, but packet does not provide enough detail to reconstruct the full survey taxonomy |

## method_difference_matrix

| Dimension | Linformer | Longformer | FlashAttention | LoRA | Comparable as stated? | Evidence-burden label | Boundary |
|---|---|---|---|---|---|---|---|
| Primary objective | Reduce self-attention complexity | Enable long-document Transformer processing | Make exact attention faster and more memory-efficient on GPU | Reduce adaptation trainable parameters and memory | Partly | `WITHIN_PACKET_SYNTHESIS` | All are “efficiency” methods, but target different bottlenecks |
| Attention output | Approximate/assumption-based linear attention via projection | Sparse structured attention pattern | Exact attention computation | Does not primarily change attention computation | No direct ranking | `DIRECT_PACKET_EVIDENCE` | FlashAttention exactness should not be equated with same objective as sparse/projection methods |
| Efficiency axis | Sequence-length complexity | Sequence-length scaling for long documents | IO and memory reads/writes between GPU memory levels | Fine-tuning parameter and memory cost | Partly | `WITHIN_PACKET_SYNTHESIS` | Metrics are not interchangeable |
| Main architectural intervention | Project keys/values to lower sequence dimension | Local windows plus global tokens | Tiled attention algorithm, avoids full attention matrix materialization | Low-rank trainable update matrices in frozen pretrained model | Yes, descriptively | `DIRECT_PACKET_EVIDENCE` | Packet supports method descriptions, not implementation equivalence |
| Evidence type | Complexity table plus perplexity/classification experiments | Scaling claim plus language modeling and downstream long-document tasks | Theorem/complexity discussion plus BERT-large and GPT-2 timing tables | Parameter/memory reductions plus RoBERTa, DeBERTa, GPT-2, GPT-3 evaluations | Partly | `DIRECT_PACKET_EVIDENCE` | Empirical numbers are absent from packet |
| Baseline visibility | Standard self-attention in Table 1 | Implied comparison to standard attention; downstream task baselines not specified in packet | BERT-large and GPT-2 training-time comparisons in Tables 1-2 | Adaptation baselines in Tables 1-2 not specified by packet | Limited | `LIMITED_CRITIQUE` | Baseline strength cannot be audited fully from the packet |
| Metrics visible in packet | Per-layer time complexity; validation perplexity; downstream classification | Scaling; autoregressive LM; downstream long-document task performance | Training time; memory-related IO behavior; speed/memory evidence | Trainable parameters; memory; downstream task performance | Limited | `DIRECT_PACKET_EVIDENCE` | Exact metric definitions and values mostly absent |
| Reproducibility details visible | Relevant experiment section named | Appendices on implementation details named | Model, hardware, and sequence settings stated in experiments | Sections/tables named; limitations paragraph named | Limited | `LIMITED_CRITIQUE` | Packet does not provide seeds, configs, raw outputs, or exact hyperparameters |

## core_paper_identification

| Core role | Paper | Why it is core within this packet | Evidence-burden label |
|---|---|---|---|
| Corpus organizer | Efficient Transformers survey | It explicitly frames the problem as quadratic attention cost and provides a taxonomy of efficient Transformer approaches | `DIRECT_PACKET_EVIDENCE` |
| Canonical projection-based efficient attention paper | Linformer | It directly proposes low-dimensional key/value sequence projection and reports linear per-layer complexity in Table 1 | `DIRECT_PACKET_EVIDENCE` |
| Canonical sparse long-context architecture paper | Longformer | It targets long documents with local plus global attention and evaluates long-document tasks | `DIRECT_PACKET_EVIDENCE` |
| Core exact-attention systems paper | FlashAttention | It improves exact attention through IO-aware tiling rather than changing the mathematical attention result | `DIRECT_PACKET_EVIDENCE` |
| Core adaptation-efficiency paper | LoRA | It shifts efficiency from attention computation to downstream fine-tuning cost via low-rank trainable updates | `DIRECT_PACKET_EVIDENCE` |

## evidence_grounded_gap_list

| Visible gap | Grounding | Evidence-burden label | Why it matters |
|---|---|---|---|
| Cross-paper empirical ranking is not supported by the packet | The methods target different bottlenecks: attention complexity, long-context sparsity, GPU IO, and adaptation memory | `LIMITED_CRITIQUE` | A single “best efficient Transformer method” conclusion would collapse incompatible objectives and protocols |
| Exact numerical comparisons are unavailable in the packet | Notes identify tables and metrics but omit most values | `LIMITED_CRITIQUE` | Magnitude of gains, tradeoffs, and statistical reliability cannot be reconstructed |
| Variance, seeds, and uncertainty are not visible | Packet does not mention repeated runs, confidence intervals, or seed counts for any paper | `LIMITED_CRITIQUE` | Reported empirical stability cannot be audited from supplied evidence |
| Baseline strength cannot be fully assessed | Packet names some comparison contexts but not detailed baseline tuning or implementation parity | `LIMITED_CRITIQUE` | Efficiency claims may depend on baseline implementation quality |
| Hardware dependence is especially relevant for FlashAttention but not fully auditable | Packet says speed/memory evidence uses stated model, hardware, and sequence settings, but does not give all details | `LIMITED_CRITIQUE` | IO-aware gains may vary across devices and kernels; broader claims need external review |
| Adaptation efficiency and attention efficiency are both present but distinct | LoRA reduces trainable parameters/memory for adaptation; other papers address attention computation or long-context processing | `WITHIN_PACKET_SYNTHESIS` | The corpus covers multiple efficiency meanings, not one unified benchmark |
| Deployment robustness is not established | Packet reports benchmark/task evidence but no deployment evidence | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW` | Real-world efficiency and quality under production constraints require evidence outside the packet |

## unsupported_synthesis_warnings

| Warning | Status |
|---|---|
| “FlashAttention is universally better than Linformer or Longformer.” | Unsupported. Packet supports FlashAttention as exact and IO-aware in reported settings, but not universal superiority. |
| “Linformer, Longformer, and FlashAttention solve the same problem.” | Unsupported. They all concern attention efficiency, but use different mechanisms and optimize different constraints. |
| “LoRA is an efficient attention method.” | Unsupported as stated. Packet supports LoRA as parameter- and memory-efficient adaptation, not as a primary attention-computation method. |
| “Linear complexity guarantees better downstream accuracy.” | Unsupported. Packet reports some empirical evidence for Linformer and Longformer, but does not establish a general accuracy guarantee. |
| “The survey proves which efficiency family is best.” | Unsupported. Packet describes the survey as a taxonomy and comparison source, not as establishing a global winner. |
| “The corpus covers all major transformer efficiency research lines.” | Unsupported. The packet is a fixed five-source corpus; field-wide coverage requires external review. |