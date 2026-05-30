## scoped_research_questions

**Packet facts**

| ID | Research question | Grounding |
|---|---|---|
| RQ1 | Do probing results for BERT-like representations remain stable across probe families, layers, and linguistic targets? | BERT Rediscovers uses edge-probing tasks, scalar mixing, cumulative scoring, and layer analysis to locate linguistic information in BERT representations. Evidence: abstract; Section 2; Section 3; Figures 1-3. |
| RQ2 | Can structural properties recovered by a structural probe be distinguished from effects of probe capacity or task design? | Structural Probe learns a linear transformation where squared distances or norms correspond to parse-tree distances or depths, and discusses the tradeoff between probe complexity, probe task, and hypothesis. Evidence: abstract; Section 2; Table 1; Figures 1-5; limitations discussion. |
| RQ3 | When probes detect linguistic information, does that imply the model uses that information? | BERT Rediscovers explicitly warns that observing a probing pattern does not show how the model uses the information. The BERTology primer surveys methodological cautions around probing and representations. |
| RQ4 | Which analysis choices most affect conclusions about representational structure: layer selection, scalar mixing, probe complexity, task formulation, or baselines? | Supported by BERT Rediscovers’ layer/scalar-mix analysis and Structural Probe’s discussion of probe complexity, baselines, and probing-task limitations. |

**Synthesis**

The proposal should not ask whether BERT “has syntax” globally. A better scoped question is whether specific probing conclusions are robust to controlled changes in probe type, layer aggregation, baselines, and task design.

---

## hypothesis_table

| Hypothesis | Evidence motivation | Prediction | Falsification criteria | Required experiment | Feasibility caveat |
|---|---|---|---|---|---|
| H1: Stable-structure hypothesis | BERT Rediscovers reports layer-wise linguistic probing behavior; Structural Probe reports recoverable parse-tree distance/depth structure from contextual representations. | A linguistic property detected by one probe should appear in similar layers or layer mixtures under another appropriately matched probe. | The apparent property shifts substantially across probe families, disappears under simpler controls, or depends on one scoring/aggregation choice. | Compare edge-probing and structural-probe-style analyses across BERT layers and scalar mixtures. | The packet does not provide exact implementation settings, datasets, or metrics needed for replication. |
| H2: Probe-capacity hypothesis | Structural Probe notes the tradeoff between probe complexity, probe task, and hypothesis; the seed idea asks whether results reflect probe capacity. | Higher-capacity probes will recover stronger apparent structure than constrained probes, especially on controls where true linguistic structure should be weak. | Constrained and higher-capacity probes give similar results, and controls do not show inflated recoverability. | Run probes with matched inputs but varying capacity; include non-linguistic or randomized controls. | Specific control datasets are not established by the packet. |
| H3: Analysis-choice sensitivity hypothesis | BERT Rediscovers uses scalar mixing/cumulative scoring and Figures 1-3 for layer analysis; the seed idea flags analysis choices. | Conclusions about “where” information appears will vary depending on whether single layers, scalar mixes, or cumulative scoring are used. | Layer-localization conclusions remain stable across these analysis choices. | Reproduce layer-wise probing with single-layer, scalar-mix, and cumulative-layer variants. | The packet only identifies the analysis methods, not their detailed numerical outcomes. |
| H4: Detection-versus-use hypothesis | BERT Rediscovers warns that probing observations do not prove model use; BERTology primer includes methodological cautions. | A representation may score well on a probe while causal intervention on that information has little or inconsistent effect on task behavior. | Probe-detected information consistently predicts behavioral sensitivity under controlled intervention. | Pair probing with intervention or ablation experiments on model behavior. | Intervention protocols are not specified in the packet and would require careful design. |

---

## evidence_map

| Claim | Source | Location supplied | Evidence type | Support status | Caveat |
|---|---|---|---|---|---|
| BERT representations can be analyzed by linguistic probing across layers. | BERT Rediscovers | Abstract; Section 2; Figures 1-3 | Empirical probing study | Direct | Exact results are not included in the packet. |
| Scalar mixing and cumulative scoring are relevant analysis choices for probing conclusions. | BERT Rediscovers | Section 3 | Methodological detail | Direct | Packet gives method names, not parameter details. |
| Probing results do not necessarily show how the model uses detected information. | BERT Rediscovers | Limitations paragraph | Methodological caution | Direct | This limits causal interpretation, not necessarily descriptive probing. |
| BERTology literature includes representations, attention, probing, and methodological cautions. | BERTology primer | Survey sections; discussion | Survey synthesis | Direct | Packet does not list individual surveyed findings. |
| Structural probes test whether parse-tree distances/depths are recoverable under a learned linear transformation. | Structural Probe | Abstract; Section 2 | Method/probe proposal | Direct | Recoverability is not identical to model use. |
| Probe design, complexity, task, and hypothesis must be aligned. | Structural Probe | Limitations discussion | Methodological caution | Direct | Does not by itself identify the best probe. |
| The seed idea concerns stability versus artifacts from capacity, datasets, and analysis choices. | Local seed idea | Brief | Research motivation | Direct | The packet does not establish which artifact dominates. |
| A robust proposal should compare probes, baselines, ablations, and layer choices. | Cross-source synthesis | From above sources | Synthesis | Indirect | The exact experimental design is proposed here, not source-stated. |

---

## experiment_plan

**Experiment 1: Layer-stability probing**

Goal: test whether a linguistic property appears consistently across BERT layers.

Protocol:
- Use edge-probing-style tasks from the BERT Rediscovers setup.
- Evaluate single layers, scalar mixing, and cumulative scoring.
- Report whether conclusions about layer localization change across these analysis choices.

Baselines:
- Majority or simple task baseline.
- Non-contextual or lower-information representation baseline, if available in the experimental setup.
- Randomized-label or control-task baseline to estimate probe memorization.

Ablations:
- Single layer vs scalar mix.
- Scalar mix vs cumulative scoring.
- Same probe across multiple linguistic targets.

Falsifies stability if the claimed property appears only under one aggregation or scoring choice.

**Experiment 2: Probe-capacity sweep**

Goal: test whether recovered structure reflects representation content or probe expressiveness.

Protocol:
- Run probes with increasing capacity on the same representation inputs.
- Include a constrained structural-probe-style setting and more flexible alternatives.
- Compare real linguistic labels against randomized or degraded controls.

Baselines:
- Linear or low-capacity probe.
- Random representation baseline.
- Dataset/control-label baseline.

Ablations:
- Probe rank or dimensionality.
- Amount of training data.
- Regularization strength.
- Structural target: parse distance vs parse depth.

Falsifies probe-capacity concern if high scores persist under constrained probes and controls remain low.

**Experiment 3: Structural probe versus edge-probing comparison**

Goal: test whether different probing formulations support the same representational claim.

Protocol:
- Apply a structural-probe-style analysis for parse-tree distance/depth.
- Apply an edge-probing-style analysis targeting related syntactic information.
- Compare whether both locate or recover similar syntactic structure from similar layers.

Baselines:
- Structural Probe baselines, as noted in the packet.
- Edge-probing task baselines.
- Randomized parse/tree control.

Ablations:
- BERT layer choice.
- Contextual representation type, if available from the Structural Probe setup.
- Structural objective: distance-only, depth-only, combined.

Falsifies cross-probe convergence if one probe strongly supports the claim and the other does not under matched conditions.

**Experiment 4: Detection versus use**

Goal: test the caution that probe success does not prove model use.

Protocol:
- Identify features that probes recover strongly.
- Perturb or mask information corresponding to those features.
- Measure whether downstream model behavior changes in the expected direction.

Baselines:
- Random perturbation.
- Perturbation of weakly probed features.
- No-perturbation control.

Ablations:
- Perturb high-scoring vs low-scoring layers.
- Perturb syntactic vs non-syntactic targets.
- Compare intervention effects against probe score strength.

Falsifies use claims if high probe recoverability does not correspond to behavioral sensitivity.

---

## risk_register

| Risk | Evidence basis | Severity | Effect on proposal | Mitigation |
|---|---|---:|---|---|
| Probe success may be overinterpreted as model use. | BERT Rediscovers limitations; BERTology methodological cautions. | High | Could make causal claims unsupported. | Separate “information is recoverable” from “model uses information”; include intervention experiments. |
| Probe capacity may create apparent structure. | Structural Probe limitations; local seed idea. | High | Could mistake probe-learned structure for representation structure. | Use capacity sweeps, constrained probes, and randomized controls. |
| Layer-localization claims may depend on aggregation method. | BERT Rediscovers scalar mixing/cumulative scoring. | Medium | Could produce unstable claims about where information resides. | Compare single-layer, scalar-mix, and cumulative analyses. |
| Dataset artifacts may inflate probing scores. | Local seed idea. | Medium | Could support spurious representational conclusions. | Add label randomization, control tasks, and dataset splits designed to expose artifacts. |
| Baselines may be too weak. | Structural Probe includes baselines and discusses probing limitations. | Medium | Could exaggerate probe performance. | Include simple, random, constrained, and task-specific baselines. |
| Packet lacks exact metrics, datasets, and numerical results. | Controlled notes only summarize sources. | High | Prevents precise power analysis or replication plan. | Mark implementation details as required follow-up within the closed corpus; avoid claiming expected effect sizes. |
| Fixed packet cannot establish field-wide novelty. | Runtime constraint and synthesis rules. | Medium | Proposal may overclaim novelty. | Frame novelty as “not established by the packet”; present this as a scoped test of the seed idea. |