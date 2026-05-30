# Variant Runtime Instructions

You are running benchmark variant `B0_base_agent`. No research skill is loaded. Use only the task prompt and supplied source packet. Do not use external retrieval or dynamic tools. Do not use knowledge outside the supplied source packet as evidence.

# Task

- Task ID: `MC-VAL-02`
- Split: `validation`
- Task type: `method_comparison`
- Topic: visual representation learning
- Research question: How should ViT-style architectures and ConvNet-style architectures be compared given differences in data scale, inductive bias, compute, and evaluation?

## Input Prompt

Using only the provided source packet, compare ViT-style and ConvNet-style evidence claims.
Produce a comparison matrix covering assumptions, data scale, compute, augmentation/training recipe, benchmarks, metrics, and scope limits.
Do not use external retrieval.


## Required Outputs

- method_comparison_matrix
- assumption_and_inductive_bias_table
- data_compute_evaluation_caveats
- evidence_strength_summary
- scoped_conclusions

# Source Packet

# MC-VAL-02 Model Input Packet
## Sources
- Deep Residual Learning for Image Recognition (arXiv:1512.03385; 2015). Local file: `he_2015_deep_residual_learning.pdf`. Included evidence: Abstract; architecture; ImageNet/CIFAR experiments.
- An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (arXiv:2010.11929; 2020). Local file: `dosovitskiy_2020_vit.pdf`. Included evidence: Abstract; architecture; data scale; benchmark comparisons.
- A ConvNet for the 2020s (arXiv:2201.03545; 2022). Local file: `liu_2022_convnet_for_the_2020s.pdf`. Included evidence: Abstract; modernization/training recipe; ImageNet comparisons.

## Controlled Source Notes
- ResNet paper: introduces residual learning for deep convolutional networks and reports ImageNet/CIFAR object-recognition results.
- ViT paper: treats images as sequences of patches for Transformer-based image recognition and emphasizes data scale/pretraining conditions in evaluation.
- ConvNeXt paper: modernizes ConvNet design and training recipes for comparison with Transformer-era vision models.
- Evidence objects: abstracts, architecture/method sections, training/evaluation protocol sections, result tables, and ablations.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.

