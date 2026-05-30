## paper_card

| Field | Content |
|---|---|
| Paper | *Decision Transformer: Reinforcement Learning via Sequence Modeling* |
| Identifier/year | arXiv:2106.01345; 2021 |
| Topic | Offline reinforcement learning framed as sequence modeling |
| Core idea | The paper formulates offline RL as conditional sequence modeling over trajectories and returns. |
| Method family | Decision-Transformer-style sequence model for RL trajectories |
| Evidence available in packet | Abstract, method formulation, datasets/environments, baselines, experiments, reproducibility details, and limitations are said to be included. |
| Evidence unavailable in packet | Exact numeric values, full tables, appendix details, and implementation settings are not included. |
| Supported high-level takeaway | The paper demonstrates that an RL problem can be cast as return-conditioned trajectory sequence modeling and evaluated against offline RL baselines in reported datasets/environments. |
| Scope caution | The packet does not provide enough detail to verify exact performance margins, implementation fidelity, statistical uncertainty, or broad generalization beyond the included experiments. |

## claim_ledger

| Claim | Type | Evidence burden | Supplied evidence | Support status | Allowed scope |
|---|---|---|---|---|---|
| The paper formulates offline RL as conditional sequence modeling over trajectories and returns. | Method/formulation | Clear method description | Controlled source notes directly state this. | Supported, source-derived | Applies to the paper’s stated formulation. |
| Decision Transformer is a sequence-modeling approach to reinforcement learning. | Method characterization | Method formulation tying RL trajectories to sequence modeling | Source notes describe “Reinforcement Learning via Sequence Modeling” and conditional sequence modeling. | Supported, source-derived | Applies to this paper’s proposed method framing. |
| The paper evaluates the method on datasets/environments with baselines and metrics. | Evaluation existence | Description of experiments, baselines, metrics, datasets/environments | Packet says datasets/environments, baselines, experiments, and baseline/metric sections are included. | Supported, source-derived | Existence of evaluation only; not exact results. |
| The paper demonstrates empirical competitiveness or improvement over baselines. | Improvement claim | Direct baseline comparison under compatible setup, with metrics and results | Packet indicates baselines and experiments are included, but exact numeric values and full tables are absent. | Partially supported only at a coarse level | Can say the paper reports comparisons; cannot verify exact magnitude or robustness from packet. |
| The method generalizes broadly across RL tasks or settings. | Generalization claim | Heterogeneous tasks/datasets/settings plus transparent per-task results | Packet mentions datasets/environments but omits full tables and exact results. | Weakly supported / evidence-bound | Only within the unspecified included datasets/environments. |
| The method’s performance is causally due to the sequence-modeling formulation. | Causal/mechanism claim | Ablations or mechanism-isolating evidence | Packet does not mention ablations or mechanism tests. | Unsupported from packet | Cannot conclude causal mechanism. |
| The work is reproducible from the packet alone. | Reproducibility claim | Code/config/data/environment/seeds/hyperparameters sufficient for rerun | Packet says reproducibility details are included, but implementation settings and appendix details are not included. | Not supported from packet alone | Reproducibility cannot be fully assessed. |
| The paper acknowledges limitations. | Limitation claim | Limitations section or stated caveats | Source packet says limitations are included. | Supported, source-derived | Only existence of limitations; exact limitations are not detailed in packet. |

## evidence_ledger

| Evidence item | Provenance | Directness | Supports | Missing detail |
|---|---|---|---|---|
| Paper metadata: *Decision Transformer: Reinforcement Learning via Sequence Modeling*, arXiv:2106.01345, 2021 | source-derived | Direct | Identification and topic | None for basic citation metadata |
| Controlled note: “formulates offline reinforcement learning as conditional sequence modeling over trajectories and returns” | source-derived | Direct | Core method claim | Architecture details, tokenization, training objective specifics not included |
| Included evidence: abstract and method formulation | source-derived | Direct but summarized | Method characterization | Exact text and equations absent |
| Included evidence: datasets/environments | source-derived | Direct but summarized | Evaluation scope exists | Dataset names, task counts, train/test splits, environment versions absent |
| Included evidence: baselines and baseline/metric sections | source-derived | Direct but summarized | Comparisons were made | Baseline identities, tuning, metric definitions, aggregation absent |
| Included evidence: experiments | source-derived | Direct but summarized | Empirical evaluation exists | Exact scores, variance, full tables, negative results absent |
| Included evidence: reproducibility details | source-derived | Direct but summarized | Some reproducibility information exists | Code/configs/seeds/hardware/hyperparameters not specified in packet |
| Included evidence: limitations | source-derived | Direct but summarized | Limitations exist | Exact limitation statements absent |
| Packet note: exact numeric values, full tables, appendix details, and implementation settings are not included | source-derived | Direct | Evidence boundary | Prevents detailed quantitative audit |

## baseline_metric_summary

| Dimension | Packet-supported summary | Evidence boundary |
|---|---|---|
| Baselines | The paper includes baselines. | Baseline names, strength, tuning budget, and fairness controls are not provided. |
| Metrics | The paper includes baseline/metric sections. | Metric definitions, normalization, aggregation, and uncertainty reporting are not provided. |
| Datasets/environments | The paper includes datasets/environments. | Specific tasks, environment versions, dataset quality levels, and split protocols are not provided. |
| Experimental results | Experiments are included. | Exact scores, full tables, per-task results, confidence intervals, seeds, and variance are absent. |
| Improvement assessment | Comparisons appear to be part of the paper. | The packet is insufficient to verify magnitude, statistical reliability, or whether comparisons are fully compatible. |
| Generalization assessment | The method is evaluated in included environments. | The packet does not establish broad generalization beyond those environments. |

## reproducibility_notes

| Item | Status from packet |
|---|---|
| Code availability | Not specified. |
| Data availability | Datasets/environments are included as evidence, but exact dataset names and acquisition details are not in the packet. |
| Environment setup | Not specified. |
| Model architecture details | Method formulation is included, but exact implementation settings are absent. |
| Hyperparameters | Not included. |
| Training objective/configuration | Only the high-level conditional sequence modeling formulation is supported. |
| Compute budget | Not specified. |
| Seeds/runs | Not specified. |
| Variability/confidence intervals | Not specified. |
| Appendix details | Not included. |
| Reproducibility conclusion | The packet supports that the paper contains some reproducibility details, but it does not provide enough information to reproduce or fully audit the experiments. |

## limitations_and_open_questions

| Issue | Severity | Why it matters | Minimal information needed |
|---|---|---|---|
| Exact quantitative results are absent. | High | Prevents verification of performance margins and aggregate claims. | Full result tables with per-task scores. |
| Baseline identities and tuning details are absent. | High | Improvement claims require fair, compatible baseline comparisons. | Baseline list, hyperparameters, compute budgets, and tuning protocol. |
| Metric definitions and aggregation are absent. | High | Benchmark claims depend on whether metrics align with the claimed construct. | Metric formulas, normalization rules, aggregation method, and per-task results. |
| Seeds, variance, and uncertainty are not specified. | Medium | Without repeated runs or uncertainty, robustness of empirical claims is unclear. | Number of seeds/runs, variance, confidence intervals, or error bars. |
| Implementation settings are omitted. | Medium | Limits reproducibility and makes exact comparison difficult. | Architecture, optimizer, batch size, context length, training steps, hardware. |
| Ablation or mechanism evidence is not specified. | Medium | The packet does not support causal claims that sequence modeling itself explains performance. | Ablations isolating return conditioning, architecture, context length, and training objective. |
| Dataset/environment details are summarized only. | Medium | Limits assessment of generalization and possible dataset-specific effects. | Environment names, dataset construction, quality levels, splits, and evaluation protocol. |
| Limitations are said to exist but not quoted or summarized. | Low to medium | The paper’s own caveats cannot be evaluated from this packet. | Exact limitation section content. |

**Corrected scope:** From the supplied packet, the paper demonstrates a Decision-Transformer-style reframing of offline RL as return-conditioned trajectory sequence modeling and reports empirical evaluations against baselines. The packet does not support precise claims about performance magnitude, statistical robustness, causal mechanism, full reproducibility, or unrestricted generalization.