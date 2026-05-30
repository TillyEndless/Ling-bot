## corpus_coverage_table

| Source | Role in corpus | Efficiency problem | Main method/artifact | Evidence type supplied | Stated/visible limitations | Use in synthesis |
|---|---|---|---|---|---|---|
| DDIM, 2020 | Central sampling-efficiency paper | Reduce diffusion sampling steps | Implicit/non-Markovian sampling formulation for faster generation with fewer steps | Controlled note: abstract, sampling acceleration method, experiments, limitations | Exact metrics, datasets, numeric tables, and implementation details are not included in the packet | Establishes fewer-step sampling as a core efficiency route |
| Progressive Distillation, 2022 | Central sampler-compression paper | Compress iterative diffusion sampling into fewer steps | Repeated distillation of a sampler into progressively shorter sampling chains | Controlled note: abstract, distillation method, sample-step tradeoffs, experiments | Precise sample-quality degradation patterns and training cost are not quantified in packet | Represents training-time cost used to reduce inference-time steps |
| DPM-Solver, 2022 | Central solver-design paper | Improve sampling speed without necessarily changing model training | Treat diffusion sampling as ODE solving; use a specialized fast solver for around 10-step sampling | Controlled note: abstract, solver design, experiments, step/quality tradeoffs | Packet lacks exact solver orders, equations, benchmark numbers, and failure cases | Represents numerical-integration efficiency |
| Latent Diffusion Models, 2022 | Central compute-reduction paper | Reduce cost of high-resolution image synthesis | Run diffusion in a learned latent space rather than pixel space | Controlled note: abstract, latent-space modeling, computational tradeoffs, experiments | Packet does not give exact compression ratios, reconstruction losses, or compute budgets | Represents representation-level efficiency |
| Consistency Models, 2023 | Central one/few-step generation paper | Enable very low-step generation | Train or distill models for one-step or few-step generation | Controlled note: abstract, one/few-step generation, distillation/training, experiments | Packet lacks exact comparison numbers and detailed training recipe | Extends distillation/training-based efficiency toward one-step generation |

## approach_taxonomy

| Approach family | Representative sources | Efficiency mechanism | What the packet supports | Main tradeoff introduced |
|---|---|---|---|---|
| Sampling trajectory reformulation | DDIM | Alters the sampling formulation so generation can use fewer denoising steps | DDIM reports faster sampling with fewer steps in its experimental settings | Speed depends on reduced-step sampling quality; exact degradation profile is not established by the packet |
| Sampler distillation | Progressive Distillation; Consistency Models | Uses training or distillation to make a model/sampler operate in fewer steps | Both sources report few-step or one/few-step generation with quality comparisons | Inference speed may require extra training/distillation cost and may introduce quality tradeoffs |
| Numerical solver acceleration | DPM-Solver | Uses an ODE formulation and specialized solver to reduce required sampling steps | Reports few-step sampling performance in selected settings | Solver performance is tied to selected settings; broad robustness is not established here |
| Representation-space efficiency | Latent Diffusion Models | Moves diffusion from pixel space to learned latent space | Reports high-resolution synthesis with computational tradeoffs | Efficiency may depend on latent representation quality and autoencoding costs |
| Training-for-fast-generation | Consistency Models | Directly trains or distills models for one-step/few-step generation | Reports one-step or few-step generation and comparisons | Quality, stability, and training complexity cannot be fully assessed from packet details |

## representative_paper_table

| Paper | Approach | Efficiency target | Evidence in packet | Tradeoff evidence | Claim support |
|---|---|---|---|---|---|
| DDIM, 2020 | Implicit sampling formulation | Faster sampling with fewer steps | Controlled source note says it introduces implicit sampling and reports faster sampling | Limitations included, but exact limits and numeric results absent | Direct for existence of method; partial for magnitude |
| Progressive Distillation, 2022 | Repeated distillation | Fewer sampling steps | Controlled source note says it compresses a sampler through repeated distillation | Packet explicitly notes sample-quality/speed tradeoffs | Direct for approach; partial for exact tradeoff curve |
| DPM-Solver, 2022 | Fast ODE solver | Around 10-step sampling | Controlled source note says it formulates sampling as ODE solving and reports few-step performance | Packet notes step/quality tradeoffs | Direct for approach; partial for generality |
| Latent Diffusion Models, 2022 | Latent-space diffusion | Lower-cost high-resolution synthesis | Controlled source note says diffusion is performed in learned latent space | Packet notes computational tradeoffs | Direct for approach; partial for exact compute savings |
| Consistency Models, 2023 | One/few-step consistency training or distillation | One-step or few-step generation | Controlled source note says it trains or distills models for one/few-step generation | Packet says quality comparisons are reported, but not the exact outcomes | Direct for approach; partial for comparative strength |

## tradeoff_analysis

| Tradeoff | Sources involved | Evidence status | Analysis |
|---|---|---|---|
| Fewer sampling steps vs sample quality | DDIM; Progressive Distillation; DPM-Solver; Consistency Models | Directly indicated, but numeric details absent | The corpus consistently frames sampling efficiency as reducing step count. However, the packet only supports the existence of step/quality tradeoffs, not precise rankings among methods. |
| Extra training/distillation cost vs faster inference | Progressive Distillation; Consistency Models | Direct for distillation/training use; incomplete for cost | Distillation-based methods shift some burden from inference to training. The packet does not establish whether this is worthwhile under specific compute budgets. |
| Solver design vs model modification | DPM-Solver compared with DDIM/Distillation/Consistency Models | Cross-source synthesis | DPM-Solver appears to target sampling procedure efficiency, while distillation and consistency approaches alter or train models for fast generation. The packet does not directly compare them under identical settings. |
| Latent compression vs output fidelity/control | Latent Diffusion Models | Partial | Latent diffusion reduces computation by operating in compressed learned space, but the packet does not provide enough detail to quantify reconstruction or fidelity costs. |
| One-step/few-step generation vs robustness/general quality | Consistency Models; Progressive Distillation | Partial | The packet supports that one/few-step generation is studied and compared, but not whether it consistently matches many-step diffusion across tasks. |
| High-resolution feasibility vs added representation pipeline | Latent Diffusion Models | Partial | Latent diffusion introduces an autoencoding or latent representation stage. The packet supports computational tradeoffs but not full pipeline cost accounting. |

## unsupported_synthesis_warnings

| Potential claim | Status |
|---|---|
| “DPM-Solver is the best method overall.” | Not established by the packet; no directly comparable full benchmark evidence is supplied. |
| “Progressive distillation always preserves quality at very low step counts.” | Not established; the packet only says sample-quality/speed tradeoffs are reported. |
| “Latent diffusion is always cheaper end-to-end than pixel-space diffusion.” | Not established; full compute budgets and autoencoder costs are not supplied. |
| “Consistency Models solve diffusion sampling inefficiency without quality loss.” | Not established; packet mentions quality comparisons, not loss-free equivalence. |
| “DDIM, DPM-Solver, and distillation methods were evaluated under identical settings.” | Not established; controlled notes describe each paper separately. |
| “The corpus proves field-wide superiority of one-step generation.” | Unsupported; fixed corpus is small and exact comparative details are missing. |

## evidence_grounded_gap_list

| Gap visible within corpus | Evidence basis | Why it matters |
|---|---|---|
| Lack of directly comparable benchmark matrix across all five approaches | Packet gives separate source notes and says some exact numeric values/tables/settings are absent | Prevents reliable ranking of methods by quality, speed, or compute efficiency |
| Missing full training-cost accounting | Progressive Distillation and Consistency Models use training/distillation; packet lacks detailed compute budgets | Necessary to evaluate whether faster inference offsets additional training cost |
| Incomplete step-quality curves | DDIM, Progressive Distillation, DPM-Solver, and Consistency Models all concern fewer steps, but exact curves are not included | Needed to identify where quality degradation begins and which method is preferable at each step count |
| Limited evidence on robustness across datasets, resolutions, and model classes | Packet notes selected experiments but omits many implementation and appendix details | Limits external validity of conclusions about general efficiency |
| Unclear interaction between latent-space diffusion and fast samplers | Latent Diffusion Models addresses representation efficiency; other papers address sampling/training efficiency | The packet does not establish whether combining latent diffusion with DDIM, DPM-Solver, distillation, or consistency training changes tradeoffs |
| Missing reproducibility details | Packet says exact numeric values, tables, appendix details, and implementation settings are not included | Makes it impossible to assess statistical validity, seeds, variability, hardware, or implementation sensitivity |