## scoped_research_questions

**Facts From Packet**

The packet supports three methodological anchors:

1. BERT Rediscovers uses edge-probing tasks and layer analysis to study where linguistic information appears in BERT representations.
2. BERT Rediscovers warns that probing observations do not necessarily show how the model uses the information.
3. Structural Probe tests whether linear transformations of contextual representations can make squared distances or norms correspond to parse-tree distances or depths, while discussing probe complexity, task choice, and hypothesis design.

**Synthesis**

The seed idea can be scoped around whether probing evidence is stable across analysis choices or whether it is mainly produced by probe capacity, dataset artifacts, or probe design.

**Research Questions**

1. **RQ1: Stability Across Probe Families**  
   Do conclusions about syntactic or linguistic structure in BERT representations remain stable when comparing edge-probing-style classifiers with structural probes?

2. **RQ2: Layerwise Robustness**  
   Are layerwise claims about where linguistic information appears in BERT stable across scalar mixing, cumulative scoring, and structural-probe analyses?

3. **RQ3: Probe Capacity Sensitivity**  
   Do stronger probes produce apparent linguistic structure even when the representation should not plausibly contain the hypothesized structure?

4. **RQ4: Artifact Sensitivity**  
   Are probing results robust to controls intended to expose dataset artifacts, label shortcuts, or analysis choices?

5. **RQ5: Interpretability Boundary**  
   What evidence would justify the weaker claim “BERT representations encode recoverable linguistic structure,” versus the stronger claim “BERT uses that structure internally”?

---

## hypothesis_table

| ID | Type | Hypothesis | Packet Evidence | Falsification Criteria |
|---|---|---|---|---|
| H1 | Proposed hypothesis | If BERT contains stable recoverable syntactic structure, then both edge-probing and structural-probe methods should identify overlapping layer regions as strongest for syntax-related tasks. | BERT Rediscovers uses edge probing and layer analysis; Structural Probe tests syntax via transformed distances/depths. | Layer rankings differ substantially across probe families, with no consistent peak or ordering for syntax-related probes. |
| H2 | Proposed hypothesis | If probe results reflect probe capacity more than representation structure, then increasing probe complexity will improve scores even on controls that should not contain meaningful syntactic structure. | Structural Probe discusses the tradeoff between probe complexity, probe task, and hypothesis. | Low-capacity and high-capacity probes show similar behavior, and controls do not improve with added capacity. |
| H3 | Proposed hypothesis | If layerwise conclusions are analysis-dependent, then scalar mixing, cumulative scoring, and single-layer structural probes will produce different narratives about where linguistic information appears. | BERT Rediscovers uses scalar mixing and cumulative scoring; Structural Probe evaluates representations through transformed geometry. | All analysis methods identify similar layerwise patterns across tasks and controls. |
| H4 | Proposed hypothesis | If probing captures dataset artifacts, then shuffled-label, randomized-representation, or artifact-controlled baselines will achieve nontrivial performance. | Seed idea raises dataset artifacts; Structural Probe includes baselines; BERTology primer includes methodological cautions. | Artifact controls perform at chance or substantially below real-representation probes. |
| H5 | Proposed hypothesis | Probing evidence can support claims about recoverability of information, but not by itself claims about causal model use. | BERT Rediscovers explicitly warns that observed probing patterns do not show how the model uses that information. | A probe result alone is shown to predict or explain model behavior under intervention, not just recover information. |

---

## evidence_map

**Facts From Packet**

| Source | Relevant Fact | Proposal Use |
|---|---|---|
| BERT Rediscovers | Uses edge-probing tasks and layer analysis. | Supports RQ1 and RQ2; motivates edge-probing experiment family. |
| BERT Rediscovers | Uses scalar mixing and cumulative scoring. | Supports comparing layer aggregation choices. |
| BERT Rediscovers | Warns that probing/inspection has limitations and does not prove model use. | Supports RQ5 and limits the interpretation of all hypotheses. |
| BERTology primer | Surveys BERT representations, attention, probing, and methodological cautions. | Supports the need for careful controls and cautious claims. |
| Structural Probe | Learns a linear transformation where squared distances or norms correspond to parse-tree distances or depths. | Supports structural syntax experiment family. |
| Structural Probe | Evaluates contextual representations including ELMo and BERT and includes baselines. | Supports use of baseline representations and comparison models. |
| Structural Probe | Discusses limitations of probing tasks and the tradeoff between probe complexity, probe task, and hypothesis. | Supports probe-capacity ablations and falsification design. |
| Local seed idea | Questions whether probing reflects stable representational structure or probe capacity, artifacts, and analysis choices. | Directly motivates the proposal. |

**Synthesis**

The packet justifies a proposal that does not ask “Does BERT understand syntax?” but instead asks a narrower, testable question: “Which probing conclusions remain stable under changes in probe family, capacity, baseline, and layer-analysis method?”

**Proposed Hypotheses**

The central proposed claim is that a representation-probing result should be considered stronger only if it survives:

1. Multiple probe families.
2. Layer-analysis variants.
3. Probe-capacity controls.
4. Dataset-artifact controls.
5. Baselines against non-contextual, randomized, or weaker representations.

---

## experiment_plan

**Experiment 1: Probe-Family Agreement**

Goal: Test whether edge-probing and structural-probe methods produce compatible claims.

Design:

- Apply edge-probing-style tasks to BERT layer representations.
- Apply structural probing to the same or comparable BERT layers.
- Compare which layers appear strongest for syntax-related information.

Required outputs:

- Layerwise performance curves.
- Rank correlation between probe-family layer rankings.
- Agreement/disagreement analysis.

Baselines:

- Non-contextual or simpler representation baseline, following the Structural Probe packet note that baselines are included.
- Randomized representation baseline.
- Majority or trivial label baseline for classification-style probes.

Falsifies H1 if:

- Edge probing and structural probing identify substantially different layer regions with no stable overlap.

---

**Experiment 2: Layer Aggregation Sensitivity**

Goal: Test whether conclusions depend on analysis choice.

Design:

- Compare single-layer probing, scalar mixing, and cumulative scoring.
- Use the same probe task family where possible.
- Evaluate whether conclusions about “where information appears” change under each method.

Baselines:

- Same baselines as Experiment 1.
- Random layer ordering or shuffled-layer control if appropriate.

Ablations:

- Remove scalar mixing.
- Compare cumulative versus non-cumulative scoring.
- Compare early, middle, and late layer groups.

Falsifies H3 if:

- All layer-analysis methods produce consistent layerwise conclusions.

Supports H3 if:

- Different analysis choices yield materially different narratives.

---

**Experiment 3: Probe Capacity Control**

Goal: Test whether better probing scores reflect representation structure or probe power.

Design:

- Run probes with multiple complexity levels.
- Include low-capacity linear probes and higher-capacity alternatives.
- Compare gains on real representations versus controls.

Baselines:

- Randomized representations.
- Shuffled labels.
- Simple lexical or surface-feature controls, where available from the probe task setup.

Ablations:

- Vary probe dimensionality.
- Vary regularization strength.
- Compare structural probe rank or transformation capacity.

Falsifies H2 if:

- Higher-capacity probes improve only on real BERT representations and not on controls.

Supports H2 if:

- Higher-capacity probes improve substantially even under controls.

---

**Experiment 4: Artifact and Label-Control Evaluation**

Goal: Test whether probing results depend on dataset shortcuts.

Design:

- Evaluate probes on original labels.
- Re-run with shuffled labels.
- Re-run with controlled or perturbed inputs where task-specific artifacts are reduced.
- Compare performance gaps.

Baselines:

- Majority class baseline.
- Surface-feature baseline.
- Randomized-label baseline.

Falsifies H4 if:

- Artifact controls collapse to chance while real probes remain strong.

Supports H4 if:

- Artifact controls retain nontrivial performance.

---

**Experiment 5: Interpretation Boundary Test**

Goal: Separate recoverability claims from model-use claims.

Design:

- Treat probing results as evidence of recoverable information only.
- Do not infer causal model use unless paired with intervention-style evidence.
- Report claims in two tiers:
  - Tier 1: information is recoverable from representations.
  - Tier 2: information is used by the model.

Required criterion:

- A normal probe can support Tier 1.
- Tier 2 requires additional causal or behavioral evidence not supplied by standard probing alone.

Falsifies H5 only if:

- Probe evidence alone is sufficient to demonstrate internal use, contradicting the warning in BERT Rediscovers.

---

## risk_register

| Risk | Type | Why It Matters | Mitigation |
|---|---|---|---|
| Overclaiming from probes | Interpretive risk | BERT Rediscovers warns that observed patterns do not prove model use. | Separate recoverability claims from causal-use claims. |
| Probe capacity confound | Methodological risk | Structural Probe notes the tradeoff between probe complexity, task, and hypothesis. | Include capacity sweeps, regularization, and low-capacity baselines. |
| Dataset artifacts | Validity risk | The seed idea explicitly raises artifacts as an alternative explanation. | Use shuffled labels, surface-feature baselines, and artifact controls. |
| Analysis-choice dependence | Reproducibility risk | BERT Rediscovers uses scalar mixing and cumulative scoring, which may affect conclusions. | Compare single-layer, scalar-mix, and cumulative methods. |
| Baseline weakness | Evaluation risk | Structural Probe includes baselines, implying baseline choice is central. | Include random, trivial, simpler-representation, and surface-feature baselines. |
| Ambiguous hypothesis | Design risk | Probing can answer many different questions depending on task and probe. | Pre-register hypotheses as recoverability, stability, or causal-use claims. |
| Cross-probe incompatibility | Measurement risk | Edge probing and structural probing operationalize linguistic structure differently. | Analyze agreement qualitatively and quantitatively rather than assuming equivalence. |
| False negative from overly weak probes | Methodological risk | Low-capacity probes may miss real but nonlinearly encoded information. | Interpret low-capacity failures cautiously and compare across capacity levels. |
| False positive from powerful probes | Methodological risk | High-capacity probes may learn the task rather than reveal representation structure. | Require controls where high-capacity probes should fail. |
| Unstable layer conclusions | Scientific risk | Layerwise findings may change with scoring method. | Report layer conclusions only when robust across analysis choices. |