## corpus_coverage_table

| Source | Source role | Efficiency target stated in packet | Main method/claim from paper notes | Evidence provided in packet | Key boundary |
|---|---|---|---|---|---|
| Efficient Transformers: A Survey | Survey / taxonomy | Time and memory costs of standard attention, especially quadratic dependence on sequence length | Organizes efficient Transformer approaches for reducing time or memory | Abstract; taxonomy sections; comparison tables; discussion/limitations | Survey evidence maps methods but does not itself establish one method as best |
| Linformer | Method paper | Self-attention sequence-length complexity | Projects keys and values to a lower-dimensional sequence axis to make self-attention linear in sequence length under assumptions | Abstract; introduction; Section 3; Figure 2; Table 1; experiment section with validation perplexity and downstream classification evidence | Linear complexity claim is tied to the paper’s assumptions and reported settings |
| Longformer | Method paper | Long-document attention cost | Uses local windowed attention plus task-motivated global attention; claims linear scaling with sequence length | Abstract; Figure 1; Table 1; Section 3; Tables 7-11; appendices on implementation | Evidence is for long-document architecture and tasks, not all Transformer workloads |
| FlashAttention | Method / systems algorithm paper | Attention speed and memory movement on GPU | IO-aware exact attention algorithm using tiling to reduce HBM reads/writes without materializing full attention matrix; also reports block-sparse extension | p. 1 abstract; p. 4 Section 3; theorem/complexity discussion; p. 7 Section 4.1 and Table 1 for BERT-large; p. 8 Table 2 for GPT-2; experiment tables/figures | Exact attention efficiency is hardware/memory-hierarchy sensitive; reported results depend on stated model, hardware, and sequence settings |
| LoRA | Method paper | Efficient downstream adaptation of large pretrained models | Freezes pretrained weights and injects trainable low-rank update matrices | Abstract; Section 1; Section 4; Table 1; Table 2; GPT-3 discussion; limitations paragraph in Section 4 | Targets adaptation efficiency, not reducing base pretraining or inference attention complexity unless packet says so, which it does not |

## literature_taxonomy

| Research line | Papers in corpus | Efficiency mechanism | What computation/resource is reduced | Paper-stated evidence |
|---|---|---|---|---|
| Survey-level organization of efficient Transformers | Efficient Transformers survey | Taxonomy and comparison of approaches | Frames the problem around quadratic attention time/memory | Survey taxonomy sections and comparison tables |
| Low-rank / projected attention over sequence dimension | Linformer | Projects keys and values to lower-dimensional sequence axis | Per-layer self-attention complexity, with Linformer listed as `O(n)` versus quadratic standard attention | Table 1 complexity comparison; validation perplexity and downstream classification experiments |
| Sparse / structured attention for long sequences | Longformer | Local windowed attention plus selected global attention | Attention scaling for long documents, claimed linear with sequence length | Architecture figure/table; language modeling and long-document downstream task evidence |
| IO-aware exact attention kernels | FlashAttention | Tiling and memory-aware computation across GPU memory levels | HBM reads/writes and memory use, while preserving exact attention | Section 3 algorithm; theorem/complexity discussion; BERT-large and GPT-2 training-time tables |
| Parameter-efficient adaptation | LoRA | Frozen pretrained weights plus trainable low-rank update matrices | Trainable parameters and adaptation memory | Tables 1-2; GPT-3 experiment discussion; evaluations on RoBERTa, DeBERTa, GPT-2, GPT-3 |

## method_difference_matrix

| Dimension | Linformer | Longformer | FlashAttention | LoRA | Comparable as stated? | Evidence / boundary |
|---|---|---|---|---|---|---|
| Primary objective | Reduce self-attention complexity | Enable long-document Transformer attention | Make exact attention faster and more memory efficient through IO awareness | Reduce trainable parameters/memory for adaptation | Partly | All address efficiency, but at different system levels |
| Core intervention | Low-dimensional projections of keys/values along sequence axis | Local windowed attention plus task-motivated global attention | Tiled exact attention avoiding full attention matrix materialization | Low-rank trainable update matrices with frozen base weights | No direct ranking | Mechanisms are not interchangeable from packet evidence |
| Attention exactness | Packet implies approximation/change through projection | Structured sparse attention pattern | Explicitly exact attention algorithm; also block-sparse extension reported | Not an attention algorithm in packet | No | FlashAttention differs because it preserves exact attention per packet |
| Scaling claim | Table 1 lists `O(n)` per-layer time for Linformer | Claims linear scaling with sequence length | Reduces IO/memory movement; exact attention, speed/memory evidence under hardware settings | Reduces adaptation parameters/memory | Only within claim type | Linear complexity, IO speed, and parameter efficiency are different metrics |
| Evaluation target | Validation perplexity and downstream classification | Autoregressive language modeling and downstream long-document tasks | BERT-large and GPT-2 training-time comparisons plus other tables/figures | RoBERTa, DeBERTa, GPT-2, GPT-3 adaptation | Mostly no | Different models, tasks, metrics, and protocols prevent global empirical ranking |
| Baseline relation | Compared to standard quadratic attention in complexity table | Compared around long-document modeling/tasks per packet | Training-time comparisons for BERT-large and GPT-2 | Adaptation baselines implied by tables, but packet does not list them | Insufficient for full fairness audit | Packet gives limited baseline details |
| Main limitation visible from packet | Assumption-dependent linear attention | Long-document-focused pattern and task choice | Hardware/model/sequence-setting dependence | Adaptation-focused, not general Transformer compute | Yes | These are scope boundaries, not proven failures |

## core_paper_identification

| Core role | Paper | Why it is core within this packet |
|---|---|---|
| Corpus organizer | Efficient Transformers survey | Provides the broad taxonomy framing transformer efficiency around quadratic attention cost and time/memory reduction |
| Representative algorithmic efficient attention method | Linformer | Directly targets self-attention complexity through low-rank sequence projection and reports linear complexity in Table 1 |
| Representative long-context sparse attention architecture | Longformer | Targets long-document processing with local and global attention and evaluates on long-document tasks |
| Representative systems/kernel efficiency method | FlashAttention | Does not change attention semantics for its exact variant; instead improves IO and memory behavior using tiling |
| Representative parameter-efficient adaptation method | LoRA | Shifts efficiency target from attention computation to downstream fine-tuning cost via frozen weights and low-rank updates |

## evidence_grounded_gap_list

| Gap visible within corpus | Grounding | Why it matters |
|---|---|---|
| No single shared benchmark across all methods is provided in the packet | Linformer, Longformer, FlashAttention, and LoRA use different evaluation targets and metrics in the supplied notes | Prevents a supported global ranking of “most efficient” method |
| Efficiency metrics are heterogeneous | Complexity for Linformer/Longformer, IO/training time/memory for FlashAttention, trainable parameters/adaptation memory for LoRA | Aggregating these into one score would be unsupported |
| Baseline and tuning details are incomplete in the packet | Packet names some tables/sections but does not supply full baseline configurations, seeds, variance, or tuning budgets | Limits experimental rigor assessment |
| Scope differs sharply by use case | Longformer focuses on long documents; LoRA focuses on downstream adaptation; FlashAttention focuses on exact attention implementation | Evidence supports use-case-specific conclusions, not universal replacement claims |
| Reproducibility details are only partially visible | Packet references appendices or experiment sections but does not provide full configs, raw outputs, seeds, or hardware details except that FlashAttention has stated model/hardware/sequence settings | Stronger reproducibility claims would require more source detail |
| Mechanism-level causal evidence is limited by packet granularity | The packet notes methods and reported results, but not full ablation outcomes except that some tables/figures exist | Claims about why a method works should stay close to stated mechanisms unless ablations are provided |

## unsupported_synthesis_warnings

| Unsupported or risky synthesis | Status |
|---|---|
| “Linformer is universally better than standard attention.” | Unsupported. Packet supports linear-complexity claims under Linformer’s assumptions and reported experiments, not universal superiority. |
| “Longformer is the best method for all long-context Transformer tasks.” | Unsupported. Packet supports long-document evaluations, not all long-context settings. |
| “FlashAttention and Linformer solve the same problem in the same way.” | Unsupported. FlashAttention is an exact IO-aware algorithm; Linformer changes attention computation through low-dimensional projections. |
| “LoRA makes Transformer attention computation linear or faster.” | Unsupported by packet. LoRA evidence concerns downstream adaptation with frozen weights and low-rank trainable updates. |
| “The corpus establishes a single frontier method for transformer efficiency.” | Unsupported. The papers address different efficiency targets and use different evidence types. |
| “Benchmark performance implies deployment robustness.” | Unsupported. The packet gives benchmark/experiment evidence but not deployment evidence. |
| “The survey proves the empirical superiority of its taxonomy categories.” | Unsupported. The survey organizes and compares approaches; the packet does not say it performs new controlled empirical comparisons across all categories. |

Overall synthesis: within this fixed corpus, transformer efficiency divides into at least four research lines: efficient attention approximations or projections, sparse/structured attention for long documents, exact attention made faster through IO-aware implementation, and parameter-efficient adaptation. The papers do not form a single apples-to-apples leaderboard. Their evidence is strongest when interpreted at the level each paper targets: sequence-length complexity for Linformer and Longformer, memory traffic and training-time behavior for FlashAttention, and adaptation parameter/memory reduction for LoRA.