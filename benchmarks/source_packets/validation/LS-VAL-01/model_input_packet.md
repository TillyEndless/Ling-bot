# LS-VAL-01 Model Input Packet
## Sources
- Denoising Diffusion Implicit Models (arXiv:2010.02502; 2020). Local file: `song_2020_denoising_diffusion_implicit_models.pdf`. Included evidence: Abstract; sampling acceleration method; experiments; limitations.
- Progressive Distillation for Fast Sampling of Diffusion Models (arXiv:2202.00512; 2022). Local file: `salimans_2022_progressive_distillation.pdf`. Included evidence: Abstract; distillation method; sample-step tradeoffs; experiments.
- DPM-Solver: A Fast ODE Solver for Diffusion Probabilistic Model Sampling in Around 10 Steps (arXiv:2206.00927; 2022). Local file: `lu_2022_dpm_solver.pdf`. Included evidence: Abstract; solver design; experiments; step/quality tradeoffs.
- High-Resolution Image Synthesis with Latent Diffusion Models (arXiv:2112.10752; 2022). Local file: `rombach_2022_latent_diffusion_models.pdf`. Included evidence: Abstract; latent-space modeling; computational tradeoffs; experiments.
- Consistency Models (arXiv:2303.01469; 2023). Local file: `song_2023_consistency_models.pdf`. Included evidence: Abstract; one/few-step generation; distillation/training; experiments.

## Controlled Source Notes
- DDIM: introduces an implicit sampling formulation for diffusion models and reports faster sampling with fewer steps in its experimental settings.
- Progressive Distillation: compresses a diffusion sampler into fewer sampling steps through repeated distillation and reports sample-quality/speed tradeoffs.
- DPM-Solver: formulates diffusion sampling as solving an ODE and reports few-step sampling performance in selected settings.
- Latent Diffusion Models: performs diffusion in a learned latent space and reports high-resolution image synthesis with computational tradeoffs.
- Consistency Models: trains or distills models for one-step or few-step generation and reports generation-quality comparisons.
- Evidence objects: abstracts, method sections, experiment sections, result tables/figures, and stated limitations or discussion sections.

## Packet Scope
- This packet contains source metadata and neutral source notes prepared from the listed canonical files.
- Some exact numeric values, full tables, appendix details, and implementation settings are not included in this model input packet.
