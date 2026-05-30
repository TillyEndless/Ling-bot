**scoped_research_questions**

1. Do probing results for BERT-like contextual representations remain stable when probe capacity, layer selection, and scoring choices are varied?
2. Can apparent syntactic or linguistic structure in representations be distinguished from structure introduced or amplified by the probe itself?
3. Are layer-wise probing patterns consistent across different probe families, such as edge-probing classifiers and structural probes?
4. Which experimental controls are necessary before claiming that a representation contains stable linguistic structure rather than task, dataset, or analysis artifacts?

Source inventory: the packet includes `BERT Rediscovers the Classical NLP Pipeline`, `A Primer in BERTology`, `A Structural Probe for Finding Syntax in Word Representations`, and a local seed idea brief. Evidence locations are limited to the packet’s controlled notes: BERT Rediscovers abstract, Sections 2-3, Figures 1-3, and limitations paragraph; BERTology survey sections on probing, representations, and methodological cautions; Structural Probe abstract, Section 2, Table 1, Figures 1-5, and limitations discussion.

**hypothesis_table**

| Hypothesis | Type | Evidence basis | Falsification criteria |
|---|---|---|---|
| H1: Some probing results will be stable across reasonable layer-selection and scoring choices, but their interpretation as model-used information will remain unsupported without intervention evidence. | SPECULATIVE_PROPOSAL | BERT Rediscovers uses layer analysis and scalar mixing/cumulative scoring; it warns that probing does not show model use. | If layer-wise conclusions change substantially under alternate scoring or layer aggregation, stability is not supported. If intervention tests show no behavioral dependence on probed information, use-claims are weakened. |
| H2: Higher-capacity probes will recover more linguistic structure than lower-capacity probes, but this may reduce interpretability of what was present in the original representation. | SPECULATIVE_PROPOSAL | Structural Probe discusses tradeoffs among probe complexity, probe task, and hypothesis. Local seed flags probe capacity as a concern. | If probe capacity has no effect on recovered structure across tasks and datasets, the capacity concern is weakened. If high-capacity probes perform similarly on control representations, linguistic interpretation is weakened. |
| H3: Structural-probe results and edge-probing layer trends will agree only partially, because they operationalize linguistic information differently. | SPECULATIVE_PROPOSAL | BERT Rediscovers uses edge-probing tasks; Structural Probe maps distances/norms to parse-tree distances/depths. | If both probe families produce the same layer rankings and conclusions across all tested settings, the partial-agreement hypothesis is weakened. |
| H4: Dataset and analysis artifacts can create apparent probing success unless controlled by baselines, control tasks, and sensitivity analyses. | SPECULATIVE_PROPOSAL | Local seed explicitly raises dataset artifacts and analysis choices; BERTology and Structural Probe include methodological cautions. | If artifact controls and randomized/control baselines do not affect conclusions, and results remain stable across datasets and analysis choices, the artifact-risk hypothesis is weakened. |

**evidence_map**

| Claim | Claim type | Evidence-burden label | Source location | Evidence directness | Supported scope | Missing detail |
|---|---|---|---|---|---|---|
| BERT Rediscovers studies where linguistic information appears in BERT representations using edge-probing and layer analysis. | source fact | DIRECT_PACKET_EVIDENCE | BERT Rediscovers: abstract; Section 2; Section 3; Figures 1-3 | Direct | This paper’s probing setup | Exact task list, metrics, and numeric results not supplied in packet |
| BERT Rediscovers warns that probing patterns do not necessarily show how the model uses the information. | limitation | DIRECT_PACKET_EVIDENCE | BERT Rediscovers: limitations paragraph | Direct | Interpretation of probing evidence | Exact wording and experimental implications not supplied |
| BERTology surveys BERT representations, attention, probing, and methodological cautions. | source fact | DIRECT_PACKET_EVIDENCE | BERTology: survey sections on probing and representations; methodological cautions | Direct | Surveyed BERTology literature as represented in packet | Specific cited studies and conclusions not supplied |
| Structural Probe learns a linear transformation where squared distances or norms correspond to parse-tree distances or depths. | method definition | DIRECT_PACKET_EVIDENCE | Structural Probe: abstract; Section 2 | Direct | Structural probe method | Exact loss, model details, and evaluation numbers not supplied |
| Structural Probe evaluates contextual representations including ELMo and BERT and includes baselines. | empirical setup | DIRECT_PACKET_EVIDENCE | Structural Probe: Table 1; Figures 1-5 | Direct | Structural Probe experiments | Exact baselines and scores not supplied |
| Probe complexity, probe task, and hypothesis choice affect interpretation. | limitation | DIRECT_PACKET_EVIDENCE | Structural Probe: limitations discussion | Direct | Probing interpretation | No full taxonomy of probe capacities supplied |
| The proposed study should not claim model mechanism from probing alone. | grounded critique | WITHIN_PACKET_SYNTHESIS | BERT Rediscovers limitations; BERTology methodological cautions; Structural Probe limitations | Comparative/indirect | Proposal framing | Intervention evidence is absent from packet |
| Stability across probes, layers, and analysis choices is an open testable target, not established fact. | proposal hypothesis | SPECULATIVE_PROPOSAL | Local seed idea plus probing cautions across packet | Indirect | Proposed research only | Requires new experiments |

**experiment_plan**

1. **Experiment 1: Layer-stability audit**
   - Objective: test whether layer-wise linguistic conclusions are stable under alternate layer aggregation and scoring choices.
   - Data/model: contextual representations such as BERT, following the packet’s focus.
   - Probes: edge-probing-style classifiers inspired by BERT Rediscovers.
   - Metrics: probing task performance and rank/order stability across layers.
   - Baselines: non-contextual or randomized representations where feasible; simple majority or task-specific trivial baselines.
   - Ablations: single-layer probes, scalar mixing, cumulative scoring, alternative aggregation rules.
   - Evidence label: SPECULATIVE_PROPOSAL.

2. **Experiment 2: Probe-capacity sensitivity**
   - Objective: measure whether recovered linguistic structure changes as probe complexity increases.
   - Probes: low-capacity linear probes, structural probe-style linear transformations, and higher-capacity alternatives if allowed by the experimental design.
   - Baselines: random-label controls, random-representation controls, and simple lexical baselines.
   - Ablations: fixed representation with varying probe capacity; fixed probe with varying representation source.
   - Falsification: if conclusions are unchanged across capacity levels and controls, capacity sensitivity is less concerning.
   - Evidence label: SPECULATIVE_PROPOSAL grounded in DIRECT_PACKET_EVIDENCE from Structural Probe limitations.

3. **Experiment 3: Cross-probe agreement**
   - Objective: compare whether edge-probing and structural-probe approaches identify similar representational layers or structures.
   - Methods compared: edge-probing layer analysis from BERT Rediscovers versus structural probe distance/depth prediction from Structural Probe.
   - Metrics: layer ranking agreement, task performance, syntactic distance/depth correlation or accuracy where applicable.
   - Boundary: agreement would support recoverability of similar information, not causal use by the model.
   - Evidence label: WITHIN_PACKET_SYNTHESIS plus SPECULATIVE_PROPOSAL.

4. **Experiment 4: Artifact and control-task audit**
   - Objective: test whether probing success survives controls for dataset artifacts and analysis choices.
   - Controls: shuffled labels, randomized representations, dataset splits designed to reduce superficial cues, and alternative preprocessing choices.
   - Baselines: lexical memorization baseline, frequency-based baseline, random baseline.
   - Ablations: remove lexical identity features where possible; vary dataset split; vary probe training size.
   - Falsification: if control tasks obtain similar performance to real linguistic tasks, the representational-structure interpretation is weakened.
   - Evidence label: SPECULATIVE_PROPOSAL based on local seed and methodological cautions.

**risk_register**

| Risk | Evidence-burden label | Why it matters | Mitigation |
|---|---|---|---|
| Probing success may show recoverability, not model use. | DIRECT_PACKET_EVIDENCE / WITHIN_PACKET_SYNTHESIS | BERT Rediscovers explicitly warns against overinterpreting probing patterns. | Avoid causal language; add intervention tests only if claiming use. |
| Probe capacity may create or amplify apparent structure. | DIRECT_PACKET_EVIDENCE | Structural Probe notes tradeoffs among probe complexity, task, and hypothesis. | Compare multiple probe capacities and include random/control baselines. |
| Layer-wise conclusions may depend on scoring or aggregation choices. | LIMITED_CRITIQUE | BERT Rediscovers uses scalar mixing and cumulative scoring, so analysis choices are part of the evidence path. | Report sensitivity across aggregation methods. |
| Dataset artifacts may explain probing performance. | SPECULATIVE_PROPOSAL | The local seed flags dataset artifacts as a concern. | Use shuffled-label controls, lexical baselines, and alternate splits. |
| Cross-paper comparison may be unfair because tasks and metrics differ. | LIMITED_CRITIQUE | Edge probing and structural probing operationalize different targets. | Compare only within shared representations and explicitly mark incompatible metrics. |
| Claims of stable linguistic structure may exceed the packet evidence. | UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW | The packet supports probing cautions, not a completed empirical result for the new proposal. | Frame all new claims as hypotheses until experiments are run. |
| Reproducibility may be limited if exact datasets, seeds, metrics, and hyperparameters are unspecified. | LIMITED_CRITIQUE | The packet does not provide full experimental details. | Pre-register task definitions, splits, seeds, probe architectures, and reporting templates. |