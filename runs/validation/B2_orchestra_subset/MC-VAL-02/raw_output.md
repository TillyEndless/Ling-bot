## method_comparison_matrix

| Dimension | ViT-style evidence claims | ConvNet-style evidence claims | Comparable? | Evidence status | Scope caveat |
|---|---|---|---|---|---|
| Core objective | Image recognition using Transformer architecture over image patches. | Image recognition using convolutional residual or modernized ConvNet architectures. | Partly | source-derived | Same broad task family, but architectures differ in inductive bias and training assumptions. |
| Architecture | ViT treats images as sequences of patches. | ResNet uses deep residual convolutional networks; ConvNeXt updates ConvNet design toward Transformer-era practice. | Yes, architecturally | source-derived | Architectural comparison alone does not establish performance superiority. |
| Assumptions | ViT evidence emphasizes scale and pretraining conditions. | ConvNets encode stronger locality/spatial bias through convolutions; modern ConvNet evidence also depends on updated recipes. | Partly | source-derived + agent-inferred | The packet does not provide full implementation details or all ablations. |
| Data scale | ViT claims are explicitly tied to large-scale pretraining/evaluation conditions. | ResNet reports ImageNet/CIFAR object-recognition results; ConvNeXt reports ImageNet comparisons under modern training. | Only with controls | source-derived | Data scale must be matched or reported separately before making improvement claims. |
| Compute | Compute is a required comparison axis but exact budgets are missing from the packet. | Same: compute budget and tuning cost are not fully specified in the packet. | No, not from packet alone | missing detail | Compute-normalized claims are unsupported here. |
| Augmentation/training recipe | ViT evaluation depends on pretraining setup and Transformer-style training conditions. | ConvNeXt explicitly modernizes ConvNet design and training recipes; ResNet reflects earlier ConvNet-era training. | Partly | source-derived | Recipe differences can confound architecture claims. |
| Benchmarks | ViT includes benchmark comparisons for image recognition at scale. | ResNet includes ImageNet/CIFAR experiments; ConvNeXt includes ImageNet comparisons. | Partly | source-derived | Benchmark overlap exists, but protocols may differ across papers and eras. |
| Metrics | Image classification/object-recognition metrics are implied by ImageNet/CIFAR comparisons. | Same broad metric family. | Partly | source-derived | Exact metric definitions, aggregation, and uncertainty are not included. |
| Scope limits | Supports claims about ViT under stated scale/pretraining/evaluation conditions. | Supports claims about residual ConvNets and modernized ConvNets under their reported setups. | Scoped only | cross-source synthesis | Does not support unrestricted claims that one architecture family is generally better. |

## assumption_and_inductive_bias_table

| Category | ViT-style | ConvNet-style | Comparison implication |
|---|---|---|---|
| Input representation | Images are split into patches and processed as token sequences. | Images are processed with convolutional feature hierarchies. | ViT reduces built-in image locality assumptions relative to ConvNets. |
| Inductive bias | Weaker image-specific bias is implied by patch-token Transformer design. | Stronger locality and translation-related bias is implied by convolutional design. | Differences in data scale matter because inductive bias can substitute for data in some regimes. |
| Training dependence | Evidence emphasizes large-scale pretraining. | ResNet evidence comes from ImageNet/CIFAR; ConvNeXt evidence emphasizes modern recipes. | Comparisons must separate architecture from recipe and data scale. |
| Historical baseline | ViT compares Transformer vision models at scale. | ResNet is a strong earlier ConvNet baseline; ConvNeXt is a modernized ConvNet baseline. | ResNet alone may be an outdated ConvNet comparator for Transformer-era claims. |

## data_compute_evaluation_caveats

| Caveat | Why it matters | Support/provenance |
|---|---|---|
| Data scale mismatch | ViT evidence is explicitly tied to scale/pretraining; ConvNet results may use different data regimes. | source-derived |
| Training recipe mismatch | ConvNeXt shows that modern ConvNet recipes affect comparisons with vision Transformers. | source-derived |
| Compute budget missing | Without comparable compute and tuning budgets, efficiency or superiority claims are unsupported. | missing detail |
| Benchmark protocol drift | ResNet, ViT, and ConvNeXt are from different research periods with potentially different evaluation conventions. | agent-inferred |
| Metrics not fully specified | The packet omits exact numeric tables, aggregation rules, uncertainty, and implementation settings. | source-derived from packet scope |
| Architecture-vs-recipe confounding | A performance difference could come from model class, data, augmentation, optimization, or compute. | cross-source synthesis |

## evidence_strength_summary

| Claim | Type | Evidence burden | Supplied evidence | Support status | Allowed scope |
|---|---|---|---|---|---|
| ResNet supports deep convolutional image recognition through residual learning. | method claim | Architecture plus task results | Abstract, architecture, ImageNet/CIFAR experiments | Supported | ResNet-style ConvNets under reported object-recognition setups. |
| ViT supports image recognition by treating images as patch sequences. | method claim | Architecture plus benchmark results | Abstract, architecture, data scale, benchmark comparisons | Supported | ViT-style models under stated pretraining/evaluation conditions. |
| ViT is generally better than ConvNets. | improvement/generalization claim | Compatible direct comparisons across data, compute, metrics, protocols | Not provided in packet | Unsupported | Not allowed from this packet. |
| Modernized ConvNets can be compared more fairly with Transformer-era models than older ConvNet baselines alone. | benchmark-validity/comparison claim | Evidence that recipe/design modernization changes comparison setup | ConvNeXt modernization/training recipe and ImageNet comparisons | Partly supported | ImageNet-style comparisons discussed by ConvNeXt. |
| Architecture family alone explains performance differences. | causal claim | Ablations isolating architecture from data, compute, recipe, augmentation | Not fully included | Unsupported | Not allowed from this packet. |

## scoped_conclusions

ViT-style and ConvNet-style architectures should be compared under matched or explicitly stratified conditions: data scale, pretraining source, compute budget, augmentation, optimization recipe, benchmark protocol, and metrics must be reported before making improvement claims.

The supplied packet supports a narrower conclusion: ResNet establishes residual ConvNets as effective image-recognition models; ViT establishes patch-token Transformers as effective vision models especially in scale-aware settings; ConvNeXt shows that ConvNet baselines should be modernized before drawing Transformer-vs-ConvNet conclusions.

The packet does not support a general claim that ViTs or ConvNets are categorically superior. Stronger claims would need exact result tables, shared benchmarks, matched training recipes, compute-normalized comparisons, ablations isolating architecture from recipe, and uncertainty or repeated-run reporting.