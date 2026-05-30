## scoped_research_questions

1. Do probing results on BERT-like contextual representations indicate stable linguistic structure across probe choices, or are they sensitive to probe capacity and analysis design?

2. When a probe recovers syntactic or edge-level linguistic information from representations, what evidence is needed to distinguish “information is recoverable” from “the model uses this information”?

3. Are layerwise patterns reported by probing analyses robust across probe families, baselines, and ablations, or do they depend on scalar mixing, cumulative scoring, or structural-probe design choices?

4. Can simpler baselines explain a substantial portion of reported probing performance, weakening claims that contextual representations encode rich linguistic structure?

## hypothesis_table

| Hypothesis | Grounding | What would support it | Falsification criteria | Claim boundary |
|---|---|---|---|---|
| H1: Some linguistic information is recoverable from BERT representations, but recoverability alone does not establish model use. | BERT Rediscovers uses edge probing and layer analysis; it explicitly warns that observing a pattern does not show how the model uses it. BERTology surveys probing and methodological cautions. | Probes recover linguistic labels above baseline, while causal or intervention evidence remains absent or weak. | If intervention evidence shows the model’s behavior changes predictably when the probed feature is manipulated, the claim may strengthen from recoverability toward use. | Representation recoverability, not mechanism. |
| H2: Layerwise probing conclusions are sensitive to analysis choices such as scalar mixing, cumulative scoring, probe task, and probe complexity. | BERT Rediscovers uses scalar mixing and cumulative scoring; Structural Probe discusses the tradeoff between probe complexity, probe task, and hypothesis. | Different probe configurations produce materially different layer rankings or conclusions. | If multiple probe types, scoring methods, and controls produce the same layerwise structure, sensitivity concern is reduced. | Stability of probing conclusions within the tested setup only. |
| H3: Structural probes can reveal syntactic geometry in contextual representations, but the strength of the conclusion depends on comparison to baselines and probe simplicity. | Structural Probe learns a linear transformation where squared distances or norms correspond to parse-tree distances or depths; it evaluates ELMo/BERT and includes baselines. | A simple structural probe outperforms baselines on parse-tree distance/depth recovery, with consistent patterns across figures/tables. | If comparable baselines match the structural probe, or if increased probe capacity drives results, the syntactic-geometry interpretation is weakened. | Evidence for recoverable structure under the probe’s hypothesis, not proof that the original model computes syntax that way. |
| H4: A rigorous probing study should treat dataset artifacts and probe capacity as alternative explanations, not afterthoughts. | Local seed idea identifies probe capacity, dataset artifacts, and analysis choices as concerns; Structural Probe and BERTology note probing limitations. | Control datasets, baseline probes, capacity sweeps, and task variants explain or fail to explain the observed signal. | If artifacts or high-capacity probes explain the effect, the stronger representation-structure claim fails. | Proposal hypothesis grounded in packet cautions. |

## evidence_map

| Packet fact | Source location | Evidence type | Use in proposal |
|---|---|---|---|
| BERT Rediscovers investigates linguistic information in BERT using edge-probing tasks and layer analysis. | BERT Rediscovers: abstract; Section 2; Figures 1-3 | Source fact | Motivates layerwise probing questions. |
| BERT Rediscovers uses scalar mixing and cumulative scoring. | BERT Rediscovers: Section 3 | Source fact | Motivates ablations over analysis choices. |
| BERT Rediscovers warns that probing observations do not necessarily show how the model uses information. | BERT Rediscovers: limitations paragraph | Source fact | Sets boundary between recoverability and mechanism. |
| BERTology surveys BERT representations, attention, probing, and methodological cautions. | BERTology primer: probing/representation sections; methodological cautions and discussion | Survey fact | Supports treating probing as informative but limited. |
| Structural Probe learns a linear transformation where squared distances or norms correspond to parse-tree distances or depths. | Structural Probe: abstract; Section 2 | Method fact | Supplies a concrete probe family for comparison. |
| Structural Probe evaluates contextual representations including ELMo and BERT and includes baselines. | Structural Probe: Table 1; Figures 1-5 | Empirical setup fact | Supports baseline-centered experiment design. |
| Structural Probe discusses the tradeoff between probe complexity, probe task, and hypothesis. | Structural Probe: limitations discussion around probing tasks | Methodological caution | Supports probe-capacity and task-design ablations. |
| Seed idea asks whether probing reveals stable structure or reflects probe capacity, dataset artifacts, and analysis choices. | Local seed idea brief | Proposal motivation | Defines the central research risk. |

## experiment_plan

1. Reproduce two probing styles within a controlled setup: edge-probing-style layer analysis from BERT Rediscovers and structural probing based on parse-tree distances/depths from Structural Probe.

2. Compare probe families under matched representations:
   - edge-probing classifier;
   - structural probe with linear transformation;
   - simpler baselines;
   - capacity-varied probes.

3. Required baselines:
   - baseline systems included or analogous to those used in Structural Probe;
   - simple non-contextual or weaker representation baselines where available in the packet’s experimental framing;
   - random or control representations if the study design permits;
   - majority or simple task baselines for probing labels.

4. Required ablations:
   - probe capacity sweep;
   - layer selection versus scalar mixing;
   - cumulative scoring versus individual-layer scoring;
   - structural probe objective variants: parse distance versus parse depth;
   - task/dataset controls to test artifact sensitivity;
   - representation comparison across contextual models only where setup is matched.

5. Metrics:
   - edge-probing task performance;
   - parse-tree distance/depth recovery metrics;
   - layerwise ranking stability;
   - baseline-normalized improvement;
   - sensitivity of conclusions under probe/task/scoring changes.

6. Falsification-oriented analyses:
   - If high-capacity probes erase differences between representations, avoid claims about stable encoded structure.
   - If dataset controls produce similar probe performance, treat artifact explanations as serious.
   - If layerwise conclusions change under scalar mixing or cumulative scoring choices, avoid strong claims about where information resides.
   - If structural probe gains disappear against strong baselines, weaken syntactic-geometry claims.
   - If no intervention is performed, do not claim the model uses the probed feature.

## risk_register

| Risk | Why it matters | Mitigation |
|---|---|---|
| Recoverability mistaken for mechanism | BERT Rediscovers explicitly warns that probing patterns do not show model use. | Label claims as recoverability unless intervention evidence is added. |
| Probe capacity drives results | Structural Probe discusses the tradeoff between probe complexity, probe task, and hypothesis. | Run capacity sweeps and compare against simple baselines. |
| Analysis choices create layerwise conclusions | BERT Rediscovers uses scalar mixing and cumulative scoring. | Compare individual-layer, scalar-mixed, and cumulative analyses. |
| Dataset artifacts explain probe success | The local seed idea names dataset artifacts as a central concern. | Add control tasks, artifact checks, and baseline comparisons. |
| Cross-paper comparison is unfair | The packet gives different methods and evidence types, not one unified benchmark. | Compare only inside matched experimental setups. |
| Baselines are too weak | Structural Probe includes baselines, but the packet does not specify all details. | Treat baseline strength as an audit item and avoid broad claims without strong controls. |
| Missing reproducibility details | The packet does not provide seeds, run counts, hardware, or full configs. | Report these as required details before making strong empirical claims. |
| Overclaiming stable linguistic structure | Probing evidence can show information is recoverable, not necessarily stable, causal, or used. | Require robustness across probes, tasks, baselines, and scoring choices before making stability claims. |