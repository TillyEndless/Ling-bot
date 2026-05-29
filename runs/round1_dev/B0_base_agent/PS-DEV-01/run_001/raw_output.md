## scoped_research_questions

**Packet Facts**

- BERT Rediscovers uses edge-probing tasks and layer-wise analysis to study where linguistic information appears in BERT representations.
- It warns that probing observations do not necessarily show how a model uses the probed information.
- The Structural Probe learns a linear transformation where squared distances or norms correspond to parse-tree distances or depths.
- The Structural Probe evaluates contextual representations including BERT and includes baselines.
- The Structural Probe discusses limitations involving probe complexity, probe task choice, and hypothesis interpretation.
- The BERTology primer surveys probing, representations, attention, and methodological cautions.

**Synthesis**

The packet supports a proposal focused on whether probing findings are stable properties of representations or are sensitive to probe capacity, task design, dataset artifacts, and analysis choices. The proposal should avoid causal claims about model computation and instead test robustness of representational evidence.

**Research Questions**

1. Do probing results for BERT representations remain stable across probe families, probe capacities, and layer aggregation choices?
2. Are reported linguistic structures recoverable from representations under constrained probes, or do they depend strongly on probe expressiveness?
3. Do probing scores persist under controls that disrupt linguistic structure while preserving superficial dataset artifacts?
4. Are layer-wise conclusions consistent across edge-probing-style tasks and structural-probe-style syntax objectives?
5. Can baselines explain a substantial portion of probing performance, reducing the evidence that contextual representations encode the target structure?

---

## hypothesis_table

| ID | Proposed hypothesis | Packet-grounded motivation | Falsification criteria | Controls | Alternative explanations |
|---|---|---|---|---|---|
| H1 | Some linguistic probing results reflect stable representational structure rather than only probe capacity. | BERT Rediscovers reports layer-wise linguistic patterns; Structural Probe tests syntax via transformed distances/depths. | If performance varies mainly with probe capacity, random/control labels, or analysis choices, and constrained probes do not outperform baselines. | Random-label probes, non-contextual or trivial baselines, capacity-matched probes, fixed train/dev/test splits. | Dataset artifacts; memorization by high-capacity probes; annotation regularities; frequency or position cues. |
| H2 | Layer-wise conclusions are sensitive to aggregation and scoring choices. | BERT Rediscovers uses scalar mixing and cumulative scoring; packet notes Figures 1-3 and Section 3 as evidence locations. | If layer rankings remain unchanged across scalar mixing, single-layer probes, cumulative scoring, and alternative metrics. | Same task data, same probe capacity, same evaluation metric, repeated seeds. | Genuine distributed encoding across layers; task-specific layer specialization. |
| H3 | Structural syntax probes recover more than superficial token-position or sentence-length artifacts only when they beat strong structural baselines. | Structural Probe maps transformed distances/norms to parse-tree distances/depths and includes baselines. | If probe performance is matched by baselines using only position, sentence length, token identity, or random/context-free representations. | Position-only baseline, random representation baseline, linear baseline, right-branching/left-branching parse baselines if available in packet-compatible experiment design. | Parse datasets may contain predictable structure; syntax may correlate with surface order. |
| H4 | Probe complexity changes interpretation: higher-capacity probes improve scores but weaken evidence that the original representation explicitly encodes the target. | Structural Probe discusses tradeoffs between probe complexity, probe task, and hypothesis. | If low-capacity and high-capacity probes produce equivalent results and conclusions across tasks. | Linear probe, structural linear transform, MLP/high-capacity probe, parameter-count matched controls. | High-capacity probes may learn the task; low-capacity probes may underfit real encoded structure. |
| H5 | Probing correlations do not establish causal use of linguistic information by BERT. | BERT Rediscovers explicitly warns that probing/inspection does not prove model use. | Not directly falsifiable by probing alone; would require intervention-style evidence outside this proposal’s packet-supported scope. | Interpret all probing results as correlational; avoid claims about computation or decision mechanisms. | A model may encode information without using it; a model may use information not recoverable by the chosen probe. |

---

## evidence_map

| Claim type | Claim | Packet support |
|---|---|---|
| Fact | BERT Rediscovers studies linguistic information in BERT using edge-probing tasks and layer analysis. | Controlled notes: BERT Rediscovers, Section 2 probing tasks; Figures 1-3. |
| Fact | BERT Rediscovers cautions that probing observations do not show how the model uses information. | Controlled notes: limitations paragraph. |
| Fact | BERTology primer surveys BERT representations, attention, probing, and methodological cautions. | Controlled notes: BERTology primer description. |
| Fact | Structural Probe learns a linear transformation mapping representation geometry to parse-tree distances/depths. | Controlled notes: Structural Probe abstract and Section 2. |
| Fact | Structural Probe evaluates contextual representations including ELMo and BERT and includes baselines. | Controlled notes: Table 1; Figures 1-5. |
| Fact | Structural Probe discusses probe limitations and the tradeoff between probe complexity, task, and hypothesis. | Controlled notes: limitations discussion. |
| Synthesis | Probe results should be evaluated for robustness to probe capacity, task artifacts, and analysis choices. | Derived from the seed idea plus methodological cautions in all three packet sources. |
| Proposed hypothesis | Stable structure exists only if constrained probes outperform strong controls across choices. | Proposed by this answer; packet-supported but not established by packet facts. |
| Unknown/speculative | Specific numeric results, exact layer rankings, exact datasets, or exact metrics from the papers. | Not provided in packet; should not be asserted. |

---

## experiment_plan

### Experiment 1: Layer-wise Edge-Probing Robustness

**Goal:** Test whether layer-wise linguistic probing conclusions are stable.

**Design**

- Use edge-probing-style tasks as in the packet description of BERT Rediscovers.
- Compare single-layer probes, scalar-mixed representations, and cumulative scoring.
- Keep probe architecture and training data fixed where possible.
- Run multiple random seeds.

**Baselines**

- Random-label baseline.
- Majority-class or simple task baseline.
- Non-contextual or random representation baseline, if available in the experimental setup.
- Capacity-matched probe on shuffled labels.

**Ablations**

- Remove scalar mixing.
- Use only individual layers.
- Vary probe capacity.
- Vary train/dev/test splits.
- Evaluate whether layer conclusions change under each setting.

**Falsification**

H1/H2 are weakened if layer-wise conclusions disappear or reverse under reasonable scoring, capacity, or seed changes.

---

### Experiment 2: Structural Probe Capacity Test

**Goal:** Test whether syntax recovery reflects representation geometry or probe expressiveness.

**Design**

- Implement a structural-probe-style objective where transformed squared distances/norms predict parse-tree distances/depths.
- Compare constrained linear structural probes against higher-capacity probes.
- Evaluate contextual BERT representations and simpler baselines.

**Baselines**

- Random representations.
- Token-position-only features.
- Sentence-length-only features.
- Simple branching parse baselines, where compatible with the data.
- Probe trained on shuffled parse labels.

**Ablations**

- Vary rank/dimensionality of the learned transformation.
- Compare distance objective vs depth objective.
- Freeze representations throughout.
- Compare lower, middle, and upper BERT layers.

**Falsification**

H3/H4 are weakened if position or random baselines match structural-probe performance, or if only high-capacity probes succeed.

---

### Experiment 3: Artifact and Label-Control Study

**Goal:** Test whether probing scores are explainable by dataset artifacts.

**Design**

- Preserve superficial properties such as token positions, sentence lengths, and label distributions while disrupting linguistic structure.
- Compare performance on original labels vs shuffled or control labels.

**Baselines**

- Label-frequency baseline.
- Position-only classifier.
- Random-label probe.
- Probe trained on permuted representation-token alignments.

**Ablations**

- Shuffle labels within sentence-length buckets.
- Shuffle token order while preserving sentence length.
- Control for token identity, if available.
- Compare results across probe capacities.

**Falsification**

Stable-structure hypotheses are weakened if probes retain high performance on artifact-preserving controls.

---

### Experiment 4: Cross-Probe Agreement

**Goal:** Test whether different probing approaches support the same representational conclusions.

**Design**

- Compare edge-probing-style task results with structural-probe-style syntax results across BERT layers.
- Ask whether the same layers appear informative under both approaches.

**Baselines**

- Same representation and task baselines from Experiments 1 and 2.
- Random seed and split controls.

**Ablations**

- Match probe parameter counts.
- Compare linear vs higher-capacity probes.
- Remove scalar mixing.
- Evaluate individual layers only.

**Falsification**

The claim of stable representational structure is weakened if different probe families imply incompatible layer-wise conclusions.

---

## risk_register

| Risk | Type | Why it matters | Mitigation |
|---|---|---|---|
| Treating probing as causal evidence | Interpretive | Packet explicitly warns that probing does not show model use. | State all conclusions as correlational; avoid claims about computation. |
| Probe capacity confound | Methodological | High-capacity probes may learn the task rather than reveal encoded structure. | Compare low/high-capacity probes and parameter-matched controls. |
| Dataset artifacts | Methodological | Position, length, frequency, or annotation artifacts may explain performance. | Use artifact-preserving controls and shuffled-label baselines. |
| Unstable layer conclusions | Analytical | Scalar mixing, cumulative scoring, or metric choices may change conclusions. | Report sensitivity across layer-selection and aggregation methods. |
| Weak baselines | Methodological | Without strong baselines, probe success is hard to interpret. | Include random, position-only, label, and simple structural baselines. |
| Overgeneralization from BERT | Scope | Packet concerns BERT and related contextual representations; broader claims are unsupported. | Scope conclusions to the tested model/representations. |
| Unsupported numeric claims | Evidence | Packet does not provide exact scores or layer rankings. | Mark such details unknown until measured; do not infer from outside knowledge. |
| Probe-task mismatch | Conceptual | A probe task may not align cleanly with the linguistic hypothesis. | Define each hypothesis before choosing probe objective and metric. |
| Reproducibility limits | Practical | Results may depend on random seeds, splits, or implementation details. | Use repeated seeds, fixed splits, and report variance. |