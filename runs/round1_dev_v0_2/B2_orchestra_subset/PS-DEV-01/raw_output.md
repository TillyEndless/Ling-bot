## scoped_research_questions

1. **RQ1: Stability of probed structure across layers and probe settings**  
   Can linguistic structure identified by probing BERT representations be treated as stable across layers, or does it depend materially on probe design, scoring method, and task formulation?

2. **RQ2: Probe capacity versus representation content**  
   When a probe recovers linguistic information from contextual representations, how much of the result is attributable to information already encoded in the representation versus the probe’s own capacity?

3. **RQ3: Dataset and analysis sensitivity**  
   Are apparent representational patterns robust to dataset splits, task variants, and aggregation choices, or do they shift under reasonable changes to the probing protocol?

4. **RQ4: Syntax-specific structural claims**  
   For structural probes, do linear transformations that recover parse-tree distances or depths indicate syntax-like geometry in the representation, or only recoverability under a chosen probe and parsing objective?

---

## hypothesis_table

| Hypothesis | Provenance | Evidence Grounding | Falsification Criteria | Required Evidence Burden |
|---|---|---|---|---|
| H1: Layerwise probing signals in BERT are reproducible under matched edge-probing protocols but not necessarily evidence of model use. | Proposed hypothesis, grounded in packet facts | BERT Rediscovers uses edge-probing and layer analysis; it warns that probing patterns do not show how the model uses information. | Repeated edge-probing runs show no consistent layerwise pattern, or patterns reverse under matched settings. | Direct baseline comparison under controlled probing setup, repeated runs, variance reporting. |
| H2: Some syntactic structure is linearly recoverable from contextual representations, but recovery strength depends on probe objective and complexity. | Proposed hypothesis, grounded in Structural Probe | Structural Probe learns a linear transformation mapping squared distances/norms to parse-tree distances/depths; it discusses probe complexity, task, and hypothesis tradeoffs. | Linear probes fail to recover parse distances/depths above baselines, or stronger results require substantially more complex probes. | Structural probe experiments with baselines, complexity controls, and task-specific metrics. |
| H3: Aggregate probing scores can mask task-specific instability. | Proposed synthesis/proposal | BERT Rediscovers uses scalar mixing/cumulative scoring and figures across probing tasks; evaluation reasoning cautions require preserving per-task results before aggregate claims. | Per-task results remain stable and aligned with aggregate trends across all tested tasks and seeds. | Per-task reporting, aggregation audit, repeated runs, uncertainty estimates. |
| H4: Probe results are sensitive to dataset artifacts and analysis choices unless controlled by negative controls and ablations. | Proposed hypothesis from seed idea | Seed idea explicitly raises probe capacity, dataset artifacts, and analysis choices; packet papers discuss methodological cautions and probing limitations. | Results remain stable across artifact controls, alternative splits, random-label controls, and probe-capacity ablations. | Controls for artifacts, split sensitivity, probe-capacity sweeps, negative controls. |
| H5: Evidence from probing supports recoverability claims more strongly than causal claims about how BERT uses linguistic information. | Cross-source synthesis | BERT Rediscovers warns observation does not show use; Structural Probe discusses probing limitations; BERTology surveys methodological cautions. | Interventional experiments show removing or perturbing probed structure causally affects downstream behavior in predicted ways. | Mechanism-isolating intervention or ablation evidence, not just probe accuracy. |

---

## evidence_map

| Packet Fact / Source-Derived Evidence | Source | Supports | Scope |
|---|---|---|---|
| BERT Rediscovers uses edge-probing tasks and layer analysis to investigate where linguistic information appears in BERT. | BERT Rediscovers, abstract; Section 2; Figures 1-3 | RQ1, H1 | Supports studying layerwise recoverability under edge-probing. |
| BERT Rediscovers uses scalar mixing and cumulative scoring. | BERT Rediscovers, Section 3 | RQ1, H3 | Supports auditing how aggregation and scoring affect conclusions. |
| BERT Rediscovers warns that observing a probing pattern does not necessarily show how the model uses that information. | BERT Rediscovers, limitations paragraph | H1, H5 | Limits claims to observed recoverability unless causal evidence is added. |
| BERTology primer surveys BERT representations, attention, probing, and methodological cautions. | BERTology primer, probing/representation sections and discussion | RQ1-RQ4, H5 | Provides survey-level support that probing requires methodological caution. |
| Structural Probe learns a linear transformation where squared distances or norms correspond to parse-tree distances or depths. | Structural Probe, abstract; Section 2 | RQ4, H2 | Supports testing syntax recoverability under a specific linear geometric hypothesis. |
| Structural Probe evaluates contextual representations including ELMo and BERT and includes baselines. | Structural Probe, Table 1; Figures 1-5 | H2, experiment baselines | Supports comparing contextual models against baselines under structural probing. |
| Structural Probe discusses limitations of probing and tradeoffs among probe complexity, probe task, and hypothesis. | Structural Probe limitations discussion | H2, H4, H5 | Supports capacity-control and scope-limitation requirements. |
| Seed idea asks whether probing reveals stable structure or reflects probe capacity, dataset artifacts, and analysis choices. | Local seed idea | RQ1-RQ3, H4 | Motivates the proposal; not itself evidence that such failures occur. |

---

## experiment_plan

### Experiment 1: Layerwise Edge-Probing Stability

**Goal:** Test whether BERT layerwise linguistic signals are stable under matched edge-probing protocols.

**Facts used:** BERT Rediscovers uses edge-probing tasks, layer analysis, scalar mixing, cumulative scoring, and reports layerwise patterns.

**Proposed design:**
- Run edge-probing tasks across BERT layers.
- Report per-task and aggregate results.
- Repeat across multiple random seeds.
- Compare scalar mixing versus single-layer probing.
- Preserve per-task curves before drawing aggregate conclusions.

**Baselines:**
- Non-contextual or lower-information representation baseline, if available in the packet-derived experimental framing.
- Random or untrained representation baseline.
- Majority or task-specific trivial baseline.

**Ablations:**
- Single-layer versus scalar-mixed representations.
- Per-task scoring versus cumulative aggregate scoring.
- Different random seeds.
- Reduced training data to test sample sensitivity.

**Falsification:**  
H1 is weakened if layerwise trends are unstable across seeds, tasks, or scoring variants.

---

### Experiment 2: Structural Probe Capacity Audit

**Goal:** Determine whether syntactic recoverability depends on probe complexity and objective.

**Facts used:** Structural Probe learns a linear transformation mapping representation geometry to parse-tree distances/depths and includes baselines.

**Proposed design:**
- Apply structural probes to BERT representations.
- Evaluate distance prediction and depth prediction separately.
- Compare against baselines.
- Vary probe rank or capacity where compatible with the structural probe setup.
- Report whether gains persist under constrained probe capacity.

**Baselines:**
- Random representation baseline.
- Linear control probe with comparable parameter budget but unrelated objective.
- Baselines from the Structural Probe setup.

**Ablations:**
- Distance objective only.
- Depth objective only.
- Full structural probe.
- Capacity-reduced probe.
- Layer-specific probes.

**Falsification:**  
H2 is weakened if syntactic recovery disappears under linear or capacity-controlled probes, or if baselines match performance.

---

### Experiment 3: Dataset Artifact and Split Sensitivity

**Goal:** Test whether probing results reflect stable representation structure or dataset-specific regularities.

**Facts used:** Seed idea raises dataset artifacts and analysis choices; packet sources warn that probing has limitations.

**Proposed design:**
- Re-run probing under alternative train/dev/test splits.
- Include label permutation or randomized-control conditions.
- Compare performance across original and controlled datasets.
- Track whether layerwise or structural conclusions remain stable.

**Baselines:**
- Random-label control.
- Random-representation control.
- Simple lexical or frequency-informed baseline if allowed by the dataset format.

**Ablations:**
- Original labels versus randomized labels.
- Original split versus alternative split.
- Full dataset versus artifact-controlled subset.
- Probe trained with restricted input features.

**Falsification:**  
H4 is weakened if no instability appears under reasonable artifact controls. It is strengthened if high probing performance persists in controls where linguistic structure should not be available.

---

### Experiment 4: Recoverability Versus Use

**Goal:** Separate “information can be decoded” from “the model uses the information.”

**Facts used:** BERT Rediscovers explicitly warns that probing patterns do not prove model use.

**Proposed design:**
- Treat probing results as recoverability evidence.
- Add intervention-style tests where representation dimensions or transformed subspaces associated with probe success are perturbed.
- Measure whether downstream task behavior changes in the predicted direction.

**Baselines:**
- Random subspace perturbation.
- Matched-magnitude perturbation unrelated to the probed structure.
- No-perturbation control.

**Ablations:**
- Perturb high-probe-signal layer.
- Perturb low-probe-signal layer.
- Perturb syntax-associated subspace versus random subspace.
- Compare task-specific effects.

**Falsification:**  
H5’s stronger causal extension is falsified if perturbing probed structure has no specific downstream effect beyond random perturbation.

---

## risk_register

| Risk | Provenance | Severity | Affected Claim | Consequence | Minimal Mitigation |
|---|---|---:|---|---|---|
| Probing shows recoverability, not model use. | Source-derived from BERT Rediscovers; cross-source synthesis with probing cautions | High | H1, H5 | Causal claims would be overstated. | State conclusions as recoverability unless intervention evidence is added. |
| Probe capacity may create apparent structure. | Source-derived from Structural Probe limitations; seed-derived | High | H2, H4 | Results may reflect the probe rather than representation geometry. | Include capacity sweeps, simple probes, and matched-capacity controls. |
| Aggregated scores may hide task-specific failures. | Agent-inferred from scalar/cumulative scoring and evaluation audit principles | Medium | H3 | Broad layerwise claims may be unsupported. | Report per-task results, variance, and aggregation method. |
| Dataset artifacts may inflate probing performance. | Seed-derived proposed risk | Medium | H4 | Probe success may not indicate linguistic representation. | Use randomized labels, alternative splits, and artifact-controlled subsets. |
| Baselines may be too weak. | Agent-proposed rigor risk | High | H1-H4 | Improvements may not be meaningful. | Include random, trivial, non-contextual, and matched-capacity baselines where applicable. |
| Lack of repeated runs and uncertainty estimates. | Agent-proposed rigor risk | Medium | H1-H4 | Stability claims cannot be assessed. | Run multiple seeds and report variance/confidence intervals. |
| Structural probe findings may not generalize beyond syntax-oriented objectives. | Source-derived from Structural Probe task framing; agent-inferred scope limit | Medium | H2, RQ4 | Claims about general representation structure would be too broad. | Limit claims to parse distance/depth recoverability unless other structures are tested. |
| Survey evidence supports caution but not a specific failure mode. | Source-derived from BERTology as survey source | Low | H4, H5 | The proposal may overstate known risks as established outcomes. | Mark artifact/capacity sensitivity as hypotheses, not packet facts. |