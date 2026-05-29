## `corpus_coverage_table`

| Paper | Role in Corpus | Efficiency Target | Core Method Claim From Packet | Evidence Scope / Limits |
|---|---:|---|---|---|
| Efficient Transformers: A Survey | Taxonomy/background | Transformer time and memory efficiency, especially quadratic attention cost | Frames efficient transformer work around reducing the standard attention mechanism’s quadratic dependence on sequence length; organizes many approach families | Use as taxonomy and framing only, not empirical proof that one method is best |
| Linformer | Core method paper | Attention complexity with respect to sequence length | Projects keys and values to a lower-dimensional sequence axis to make self-attention linear in sequence length under its assumptions | Table 1 lists Linformer per-layer complexity as `O(n)` versus quadratic standard self-attention; practical claims must remain tied to its validation perplexity and downstream classification settings |
| Longformer | Core method paper | Long-document sequence modeling | Uses local windowed attention plus task-motivated global attention; claims linear scaling with sequence length for its attention pattern | Evaluated on autoregressive language modeling and downstream long-document tasks; it is not an exact-attention kernel paper |
| FlashAttention | Core method paper | Exact attention speed and memory on GPUs | Introduces IO-aware exact attention that reduces reads/writes between GPU memory levels | Speed or memory claims must be tied to the reported hardware, model, and sequence settings; not approximate or sparse attention |
| LoRA | Core method paper | Parameter- and memory-efficient adaptation/fine-tuning | Freezes pretrained weights and injects trainable low-rank update matrices | Reports large reductions in trainable parameters and memory for adaptation on RoBERTa, DeBERTa, GPT-2, and GPT-3; not attention-computation efficiency |

## `literature_taxonomy`

| Taxonomy Branch | Included Corpus Papers | Efficiency Mechanism | What Is Supported |
|---|---|---|---|
| Survey-level taxonomy of efficient transformers | Efficient Transformers survey | Organizes approaches that reduce transformer time or memory, especially around quadratic attention | Supported as a map of approach families, not as a ranking |
| Low-rank / projected attention | Linformer | Projects keys and values along sequence dimension to reduce attention complexity | Supported claim: linear sequence-length complexity under Linformer assumptions |
| Sparse / structured long-context attention | Longformer | Combines sliding local windows with selected global attention | Supported claim: linear scaling for its attention pattern and suitability for long documents in evaluated settings |
| IO-aware exact attention kernels | FlashAttention | Reorders exact attention computation to reduce GPU memory traffic | Supported claim: exact attention with improved IO behavior; empirical claims are setting-bound |
| Parameter-efficient adaptation | LoRA | Freezes base model and trains low-rank update matrices | Supported claim: adaptation efficiency through fewer trainable parameters and reduced memory in evaluated model families |

## `method_difference_matrix`

| Dimension | Linformer | Longformer | FlashAttention | LoRA |
|---|---|---|---|---|
| Primary efficiency problem | Quadratic self-attention sequence cost | Long-document attention scalability | GPU memory traffic and attention kernel efficiency | Fine-tuning/adaptation parameter and memory cost |
| Changes attention pattern? | Yes, via low-rank sequence projection of keys/values | Yes, via local window plus global attention | No; remains exact attention | No; changes adaptation parameterization |
| Exact standard attention? | Not supported as exact standard attention in packet | No; sparse/structured attention pattern | Yes | Not applicable |
| Complexity claim in packet | Linear in sequence length under assumptions; Table 1 lists `O(n)` per-layer | Linear scaling with sequence length for its attention pattern | IO-aware exact attention with reduced memory reads/writes; complexity discussion tied to paper | Large reduction in trainable parameters and adaptation memory |
| Main empirical scope | Validation perplexity and downstream classification | Autoregressive LM and long-document downstream tasks | Reported hardware/model/sequence settings | RoBERTa, DeBERTa, GPT-2, GPT-3 adaptation |
| Best interpreted as | Approximate/low-rank efficient attention architecture | Long-context sparse attention architecture | Systems/kernel method for exact attention | Parameter-efficient fine-tuning method |
| Not supported to claim | Universally best attention method | Exact-attention kernel improvement | Approximate/sparse attention method | Faster long-context attention computation |

## `core_paper_identification`

| Core Paper | Why Core |
|---|---|
| Linformer | Represents low-rank/projection-based reduction of attention sequence complexity |
| Longformer | Represents sparse/structured attention for long-document transformers |
| FlashAttention | Represents IO-aware exact attention acceleration and memory reduction |
| LoRA | Represents parameter-efficient adaptation rather than attention-computation efficiency |
| Efficient Transformers survey | Core background paper for taxonomy, but not a primary empirical method comparison |

## `evidence_grounded_gap_list`

1. **Cross-method empirical comparability is limited.**  
   The packet does not support direct ranking of Linformer, Longformer, FlashAttention, and LoRA because their hardware, models, tasks, and efficiency targets differ.

2. **Attention-efficiency and adaptation-efficiency are only loosely connected in the corpus.**  
   LoRA addresses adaptation cost, while Linformer, Longformer, and FlashAttention address attention computation or memory. The packet does not establish a unified benchmark across these categories.

3. **Exact versus approximate/sparse attention boundaries matter.**  
   FlashAttention is exact attention, while Linformer and Longformer alter the attention computation pattern. The corpus does not support treating all “efficient attention” methods as interchangeable.

4. **Long-context evidence is method-specific.**  
   Longformer has long-document task evidence; Linformer has perplexity and classification evidence; FlashAttention reports setting-bound speed/memory results. The packet does not support a universal conclusion about best long-context performance.

5. **The survey broadens the map but does not resolve winners.**  
   Efficient Transformers can organize the landscape, but the packet explicitly says not to use it as empirical proof that any method is best.

6. **Missing corpus areas are unknown, not absent from the field.**  
   The packet does not allow external retrieval, so gaps relative to methods not included in the packet must be marked as corpus coverage gaps rather than field-level absences.

## `unsupported_synthesis_warnings`

| Unsupported Claim | Status |
|---|---|
| “Linformer is better than Longformer overall.” | Unsupported by packet |
| “FlashAttention is always faster than sparse attention.” | Unsupported; speed evidence must be tied to reported settings |
| “LoRA improves attention computation complexity.” | Unsupported; LoRA is adaptation efficiency |
| “Longformer is an exact-attention implementation.” | Unsupported; packet identifies it as local plus global attention, not exact-attention kernel work |
| “The five-paper corpus exhausts transformer efficiency research.” | Unsupported |
| “Reported speedups or memory savings can be compared directly across all papers.” | Unsupported unless same hardware/model/benchmark is directly established, which the packet does not provide |
| “The survey proves one method is best.” | Unsupported; survey is taxonomy/background |
| “Linformer’s practical superiority generalizes beyond its evaluated settings.” | Unsupported |
| “FlashAttention is approximate or sparse attention.” | Unsupported; packet says it is exact attention |
| “LoRA’s parameter savings imply better task quality in all settings.” | Unsupported |

## Evidence-Grounded Synthesis

The packet supports a taxonomy in which transformer efficiency is not one problem but several distinct ones. Linformer and Longformer target attention scaling with sequence length, but they do so differently: Linformer uses low-rank projections of keys and values, while Longformer uses a sparse local/global attention pattern for long documents. FlashAttention targets a different layer of the stack: it keeps attention exact but improves memory movement between GPU memory levels. LoRA is separate again, reducing the cost of adapting pretrained models by freezing base weights and training low-rank updates.

A careful synthesis is therefore: the corpus shows transformer efficiency spanning architectural approximation or sparsity, systems-level exact-attention optimization, and parameter-efficient adaptation. These approaches should not be collapsed into a single leaderboard without shared tasks, models, hardware, sequence lengths, and metrics.