## corpus_coverage_table

| Source | Role in Corpus | Efficiency Target | Main Paper Claim | Evidence Provided in Packet | Evidence-Burden Label | Coverage Boundary |
|---|---|---:|---|---|---|---|
| Efficient Transformers: A Survey | Survey / taxonomy | Transformer time and memory, especially attention scaling | Standard attention has quadratic dependence on sequence length; many approaches reduce time or memory | Abstract, taxonomy sections, comparison tables, discussion/limitations | `DIRECT_PACKET_EVIDENCE` | Packet gives only controlled notes, not the full taxonomy tables or exact categories |
| Linformer | Method paper | Self-attention sequence-length complexity | Projects keys and values along the sequence axis to make self-attention linear in sequence length under assumptions | Abstract, introduction, Section 3, Figure 2, Table 1, experiments; Table 1 lists Linformer as `O(n)` versus quadratic standard attention | `DIRECT_PACKET_EVIDENCE` | Assumptions are mentioned but not fully specified in packet; empirical details are summarized only |
| Longformer | Method paper | Long-document attention scaling | Uses local windowed attention plus task-motivated global attention; claims linear scaling with sequence length | Abstract, Figure 1, Table 1, Section 3, Tables 7-11, appendices | `DIRECT_PACKET_EVIDENCE` | Packet does not provide exact task names, metrics, scores, or global-attention configurations |
| FlashAttention | Systems / algorithm paper | GPU memory traffic and exact attention runtime/memory | IO-aware exact attention algorithm reduces HBM reads/writes using tiling without materializing full attention matrix | Abstract p.1, Section 3 p.4, Section 4.1 p.7, Table 1, Table 2, theorem/complexity discussion, experiments | `DIRECT_PACKET_EVIDENCE` | Packet does not provide exact numerical speedups, memory values, hardware details beyond “stated model, hardware, and sequence settings” |
| LoRA | Adaptation-efficiency method paper | Fine-tuning trainable parameters and memory | Freezes pretrained weights and injects trainable low-rank update matrices for downstream adaptation | Abstract, Section 1, Section 4, Table 1, Table 2, GPT-3 discussion, Section 4 limitations paragraph | `DIRECT_PACKET_EVIDENCE` | Not primarily an attention-computation method; evidence concerns adaptation efficiency, not base pretraining/inference attention complexity |

## literature_taxonomy

| Research Line | Papers | Efficiency Mechanism | Claimed Efficiency Benefit | Evidence in Packet | Boundary |
|---|---|---|---|---|---|
| Survey-level organization of efficient Transformer methods | Efficient Transformers survey | Taxonomizes approaches for reducing Transformer time or memory | Frames the field around quadratic standard attention and efficiency approaches | Survey abstract, taxonomy sections, comparison tables, discussion/limitations | `DIRECT_PACKET_EVIDENCE`; packet does not expose the complete taxonomy |
| Low-rank / projection-based attention approximation | Linformer | Projects keys and values to a lower-dimensional sequence axis | Linear self-attention complexity in sequence length under assumptions | Section 3, Figure 2, Table 1, experiment section | `DIRECT_PACKET_EVIDENCE`; exact assumptions and numerical results are not supplied |
| Sparse / structured attention for long contexts | Longformer | Local windowed attention plus task-motivated global attention | Linear scaling with sequence length for long-document attention pattern | Abstract, Figure 1, Table 1, Section 3, Tables 7-11 | `DIRECT_PACKET_EVIDENCE`; global attention choices are task-motivated but exact protocol details are absent |
| IO-aware exact attention | FlashAttention | Tiling to reduce memory reads/writes between GPU memory levels; avoids full attention matrix materialization | Faster and more memory-efficient exact attention | Abstract p.1, Section 3 p.4, Section 4.1 p.7, Tables 1-2, theorem/complexity discussion | `DIRECT_PACKET_EVIDENCE`; setup-specific speed/memory claims only |
| Parameter-efficient adaptation | LoRA | Frozen pretrained weights plus trainable low-rank update matrices | Reduces trainable parameters and adaptation memory | Abstract, Section 1, Section 4, Tables 1-2, GPT-3 experiment discussion | `DIRECT_PACKET_EVIDENCE`; not evidence of lower core attention complexity |

## method_difference_matrix

| Dimension | Linformer | Longformer | FlashAttention | LoRA | Comparable as Stated? | Evidence-Burden Label | Boundary |
|---|---|---|---|---|---|---|---|
| Primary objective | Reduce self-attention sequence complexity | Enable long-document Transformer attention | Make exact attention faster and more memory-efficient via IO awareness | Reduce adaptation parameters and memory | Partly | `WITHIN_PACKET_SYNTHESIS` | They target different bottlenecks |
| Attention type | Approximate/projection-based attention implied by lower-dimensional K/V projection | Sparse structured attention: local plus global | Exact attention | Does not change attention mechanism as stated; changes adaptation parameterization | No direct empirical comparison | `WITHIN_PACKET_SYNTHESIS` | Do not rank these as universally better/worse |
| Complexity claim | Table 1 lists Linformer as `O(n)` versus standard quadratic attention | Claims linear scaling with sequence length | Reduces IO and avoids full attention matrix materialization while computing exact attention | Reduces trainable parameters/memory for adaptation | Partly | `DIRECT_PACKET_EVIDENCE` | Complexity dimensions differ: asymptotic attention, IO cost, adaptation memory |
| Main evidence type | Complexity table plus validation perplexity and downstream classification evidence | Language modeling and downstream long-document tasks | Training-time comparisons for BERT-large and GPT-2 plus experiments under stated hardware/sequence settings | Experiments on RoBERTa, DeBERTa, GPT-2, GPT-3 | Partly | `DIRECT_PACKET_EVIDENCE` | Metrics and tasks are not fully specified in packet |
| Best-supported claim scope | Reported settings for linearized self-attention and downstream evaluations | Reported long-document architecture/task settings | Reported model/hardware/sequence settings for exact attention | Reported downstream adaptation settings | Setup-specific only | `LIMITED_CRITIQUE` | Packet does not support global superiority claims |
| Main missing audit details in packet | Exact assumptions, metrics, scores, seeds, uncertainty | Exact metrics, task protocols, global attention design details, uncertainty | Exact numerical speed/memory results, hardware configs, seeds/variance | Exact parameter/memory values, training protocol, uncertainty | N/A | `LIMITED_CRITIQUE` | Missing from packet, not necessarily missing from papers |

## core_paper_identification

| Core Paper | Why It Is Core Within This Corpus | Claim Type | Evidence-Burden Label |
|---|---|---|---|
| Efficient Transformers survey | Provides the corpus-level framing: efficient Transformer work is organized around reducing time or memory, especially the quadratic sequence-length cost of standard attention | Survey framing | `DIRECT_PACKET_EVIDENCE` |
| Linformer | Represents projection/low-rank-style reduction of attention sequence complexity | Method definition and complexity claim | `DIRECT_PACKET_EVIDENCE` |
| Longformer | Represents sparse/structured long-context attention with local and global patterns | Method definition and benchmark evidence | `DIRECT_PACKET_EVIDENCE` |
| FlashAttention | Represents hardware-aware exact attention, separating algorithmic exactness from memory-system efficiency | Method definition, systems efficiency evidence | `DIRECT_PACKET_EVIDENCE` |
| LoRA | Represents parameter-efficient adaptation rather than faster attention computation | Method definition and adaptation-efficiency evidence | `DIRECT_PACKET_EVIDENCE` |

## evidence_grounded_gap_list

| Gap Visible Within Corpus | Grounding | Evidence-Burden Label | Why It Matters |
|---|---|---|---|
| The corpus mixes different notions of “efficiency”: asymptotic attention complexity, long-context feasibility, GPU IO efficiency, and adaptation memory | Linformer, Longformer, FlashAttention, and LoRA target different bottlenecks | `WITHIN_PACKET_SYNTHESIS` | A single ranking would be misleading without a common metric and protocol |
| Cross-paper empirical comparability is weak in the packet | Packet lists different tasks/models: classification/perplexity, long-document tasks, BERT/GPT-2 training time, RoBERTa/DeBERTa/GPT-2/GPT-3 adaptation | `LIMITED_CRITIQUE` | The packet supports taxonomy, not universal method superiority |
| Reproducibility details are sparse in the packet | Seeds, uncertainty, exact metrics, scores, configs, and full protocols are mostly not included in controlled notes | `LIMITED_CRITIQUE` | Missing packet detail limits audit strength |
| Exactness versus approximation is an important axis | FlashAttention is explicitly exact; Linformer changes attention via K/V projection; Longformer changes attention pattern | `WITHIN_PACKET_SYNTHESIS` | Efficiency gains may have different quality or fidelity tradeoffs |
| Adaptation efficiency is distinct from base Transformer computation efficiency | LoRA freezes weights and trains low-rank updates; packet does not state that it reduces core attention complexity | `WITHIN_PACKET_SYNTHESIS` | LoRA should not be grouped as an attention-speed method without qualification |
| Hardware-aware efficiency appears only through FlashAttention in the packet | FlashAttention centers IO between GPU memory levels and reports model/hardware/sequence-specific experiments | `DIRECT_PACKET_EVIDENCE` | The packet has limited coverage of systems-level optimization beyond this paper |

## unsupported_synthesis_warnings

| Warning | Status |
|---|---|
| “Linformer is better than Longformer” | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`; packet provides different mechanisms and settings, not a shared decisive comparison |
| “FlashAttention is universally faster than all efficient attention methods” | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`; packet supports reported setup-specific speed/memory evidence only |
| “LoRA improves attention computation efficiency” | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`; packet supports adaptation parameter/memory efficiency, not core attention computation reduction |
| “Sparse attention is always less accurate than exact attention” | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`; packet does not provide that conclusion |
| “The survey’s taxonomy is complete for the field” | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`; packet says it is a survey/taxonomy but does not establish complete field coverage |
| “Linear scaling claims imply equal wall-clock speedups across hardware and implementations” | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`; packet distinguishes asymptotic claims and FlashAttention’s hardware-aware IO evidence but does not support this transfer |
| “Benchmark performance establishes deployment robustness” | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW`; packet contains benchmark/task evidence, not deployment evidence |