## corpus_coverage_table

| Paper | Efficiency target | Main method line | Evidence provided in packet | Scope supported |
|---|---|---|---|---|
| Efficient Transformers: A Survey | Transformer time and memory efficiency, especially attention quadratic scaling | Survey taxonomy of efficient Transformer approaches | Source notes say the survey frames efficiency around standard attention’s quadratic dependence on sequence length and organizes approaches for reducing time or memory; evidence locations include abstract, taxonomy sections, comparison tables, discussion/limitations | Supports a corpus-level taxonomy, not a new empirical claim |
| Linformer | Self-attention sequence-length complexity | Low-rank projection of keys and values along the sequence axis | Table 1 lists Linformer per-layer complexity as `O(n)` versus quadratic standard self-attention; method described in Section 3/Figure 2; experiments report validation perplexity and downstream classification in the paper’s settings | Supports linear-complexity claim under Linformer’s assumptions and reported experimental settings |
| Longformer | Long-document attention scalability | Sparse attention pattern: local windowed attention plus task-motivated global attention | Source notes say it claims linear scaling with sequence length; evaluates autoregressive language modeling and downstream long-document tasks; evidence locations include Figure 1, Table 1, Section 3, Tables 7-11, appendices | Supports long-document efficiency/performance claims for its attention pattern and reported tasks |
| FlashAttention | GPU memory traffic and attention runtime/memory | IO-aware exact attention using tiling, avoiding materialization of full attention matrix | Abstract identifies it as IO-aware exact attention; Section 3 describes reducing HBM reads/writes while computing exact attention; Tables/Figures report speed and memory under stated models, hardware, and sequence settings | Supports exact-attention efficiency under reported hardware/model/sequence settings |
| LoRA | Parameter and memory efficiency for adaptation/fine-tuning | Freeze pretrained weights and add trainable low-rank update matrices | Abstract/Sections 1 and 4 describe frozen weights plus low-rank trainable matrices; Tables 1-2 and GPT-3 discussion report trainable-parameter and memory reductions; evaluated on RoBERTa, DeBERTa, GPT-2, GPT-3 | Supports adaptation-efficiency claims, not general inference-time attention efficiency |

## literature_taxonomy

| Research line | Papers | Paper claims | Evidence type | Synthesis status |
|---|---|---|---|---|
| Survey and taxonomy of efficient Transformers | Efficient Transformers survey | Efficient Transformer methods can be organized around reducing time or memory costs, especially the quadratic attention bottleneck | Survey framing, taxonomy sections, comparison tables | Source-derived for the survey’s framing; cross-source synthesis when used to organize the corpus |
| Approximate or structured attention with lower sequence complexity | Linformer | Project keys and values to lower sequence dimension; self-attention becomes linear in sequence length under assumptions | Method section, Figure 2, Table 1 complexity, reported perplexity/classification experiments | Source-derived for Linformer; broader “approximate/structured attention” label is synthesis |
| Sparse attention for long contexts | Longformer | Local windowed attention plus global attention enables linear scaling for long documents | Architecture description, Figure 1, Table 1, LM and downstream long-document task results | Source-derived for Longformer; synthesis as a separate line from Linformer |
| Hardware-aware exact attention | FlashAttention | Exact attention can be made faster and more memory-efficient by IO-aware tiling and avoiding full attention matrix materialization | Abstract, Section 3 algorithm, theorem/complexity discussion, BERT-large/GPT-2 training-time tables | Source-derived for FlashAttention; distinct from approximate sparse methods because exactness is explicitly stated |
| Parameter-efficient adaptation | LoRA | Freeze pretrained weights and train low-rank update matrices, reducing trainable parameters and memory in adaptation | Abstract, Sections 1/4, Tables 1-2, GPT-3 discussion | Source-derived for LoRA; corpus-level inclusion as “transformer efficiency” is synthesis because it targets adaptation rather than attention computation |

## method_difference_matrix

| Dimension | Linformer | Longformer | FlashAttention | LoRA | Comparable? | Caveat |
|---|---|---|---|---|---|---|
| Primary objective | Reduce self-attention complexity | Enable long-document Transformer attention | Reduce attention runtime/memory via GPU IO efficiency | Reduce trainable parameters/memory for adaptation | Partly | They target different bottlenecks |
| Mechanism | Project keys/values along sequence axis | Local windowed plus global sparse attention | Tiled exact attention, reduced HBM reads/writes, no full attention matrix materialization | Frozen base weights plus trainable low-rank updates | No direct method equivalence | Linformer/Longformer alter attention pattern; FlashAttention preserves exact attention; LoRA changes adaptation |
| Attention exactness | Not established as exact in packet | Sparse attention, not full standard attention | Explicitly exact attention | Not primarily an attention algorithm | Limited | Exactness comparison only supported for FlashAttention |
| Complexity claim | Table 1 lists `O(n)` per-layer versus quadratic standard attention | Claims linear scaling with sequence length | Uses IO-aware complexity and memory/runtime evidence | Reports parameter and memory reduction, not sequence-length attention complexity | Scoped | Metrics differ across papers |
| Evidence base | Complexity table plus validation perplexity and classification results | LM and downstream long-document tasks | BERT-large and GPT-2 training-time comparisons plus memory/speed evidence | RoBERTa, DeBERTa, GPT-2, GPT-3 adaptation experiments | Partly | Tasks, models, and metrics are not unified |
| Best-supported claim | Linear-complexity self-attention under assumptions | Linear-scaling long-document attention pattern with task results | Faster/more memory-efficient exact attention in reported settings | Parameter/memory-efficient downstream adaptation | No global winner supported | Packet does not provide a shared benchmark across all methods |

## core_paper_identification

| Role in corpus | Paper | Rationale | Provenance |
|---|---|---|---|
| Organizing survey | Efficient Transformers: A Survey | Provides the broad taxonomy and frames the standard attention bottleneck as quadratic in sequence length | Source-derived |
| Core efficient-attention approximation paper | Linformer | Directly targets self-attention complexity using low-rank sequence projection and reports linear complexity in Table 1 | Source-derived |
| Core sparse long-context architecture paper | Longformer | Represents sparse/local-global attention for long-document processing with LM and downstream evaluations | Source-derived |
| Core systems/algorithmic exact-attention paper | FlashAttention | Represents hardware-aware exact attention, improving speed/memory without approximating attention according to the packet | Source-derived |
| Core parameter-efficient adaptation paper | LoRA | Represents a distinct efficiency line: reducing trainable parameters and adaptation memory rather than changing attention computation | Source-derived plus taxonomy synthesis |

## evidence_grounded_gap_list

| Gap | Why it matters | Evidence basis | Status |
|---|---|---|---|
| No single shared benchmark across all five papers | Prevents ranking methods as generally “best” for transformer efficiency | Packet lists different tasks/settings: Linformer classification/perplexity, Longformer long-document tasks, FlashAttention BERT/GPT-2 training time, LoRA adaptation tasks | Source-derived synthesis |
| Attention-efficiency and adaptation-efficiency are not directly comparable | LoRA reduces trainable parameters/memory for fine-tuning, while Linformer/Longformer/FlashAttention target attention computation | LoRA source notes focus on frozen weights and low-rank updates; other papers focus on attention scaling/runtime | Source-derived synthesis |
| Hardware and implementation dependence is visible but not uniformly specified in packet | Runtime and memory claims depend on hardware, kernels, sequence length, and model setup | FlashAttention evidence is explicitly tied to stated model, hardware, and sequence settings; comparable details for other methods are not fully provided in packet | Agent-inferred from supplied evidence |
| Generalization beyond reported settings is not established | Efficiency/performance may vary by task, length regime, model size, and training setup | Packet only names each paper’s reported settings and evidence locations | Agent-inferred |
| Mechanism-level causal claims require ablations not described in packet | Claims that a specific component causes gains require isolating evidence | Packet mentions methods and results but does not enumerate ablations for every method | Agent-inferred; missing detail |
| Survey taxonomy is useful but not itself experimental evidence | A survey can organize evidence but does not independently validate every method | Survey described as taxonomy/comparison/discussion paper | Source-derived |

## unsupported_synthesis_warnings

| Warning | Unsupported conclusion | Why unsupported by packet |
|---|---|---|
| Do not claim one method is universally most efficient | “FlashAttention/Linformer/Longformer/LoRA is the best efficient Transformer method” | No shared benchmark, metric, task suite, hardware setup, or protocol across all methods is supplied |
| Do not equate all linear-scaling claims | “Linformer and Longformer provide the same kind of linear attention” | Linformer uses key/value projection; Longformer uses sparse local/global attention |
| Do not treat LoRA as an attention-efficiency method | “LoRA reduces quadratic attention cost” | Packet supports LoRA as parameter/memory-efficient adaptation with frozen weights and low-rank updates |
| Do not treat FlashAttention as approximate attention | “FlashAttention approximates attention to gain speed” | Packet explicitly states FlashAttention is exact attention |
| Do not generalize reported speedups or memory reductions outside settings | “The reported gains hold for all models, hardware, and sequence lengths” | Packet ties FlashAttention evidence to stated model, hardware, and sequence settings; other papers also report in their own settings |
| Do not infer reproducibility completeness | “All methods are fully reproducible from the packet” | The packet gives evidence locations and high-level notes, not full code, configs, seeds, environments, or hyperparameter details |