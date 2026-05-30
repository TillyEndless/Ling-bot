**Source inventory:** Packet contains three papers and one seed brief: `BERT Rediscovers the Classical NLP Pipeline` with edge probing, scalar mixing/cumulative scoring, Figures 1-3, and a stated caution that probing does not prove model use; `A Primer in BERTology` as a survey of BERT representations, attention, probing, and methodological cautions; `A Structural Probe for Finding Syntax in Word Representations` with a linear structural probe, Table 1, Figures 1-5, baselines, and limitations around probe complexity, task, and hypothesis; plus a local seed idea about whether probing reflects stable structure versus probe capacity, artifacts, and analysis choices.

## scoped_research_questions

1. When probing BERT representations, which findings remain stable across probe capacity, layer aggregation choices, and task formulations?
   - Type: proposed research question.
   - Evidence basis: `WITHIN_PACKET_SYNTHESIS` from BERT Rediscovers’ layer probing and scalar mixing setup, Structural Probe’s probe-complexity cautions, and the seed brief.

2. Can a low-capacity probe recover similar linguistic structure as a higher-capacity probe, or do reported signals depend materially on probe expressiveness?
   - Type: proposed research question.
   - Evidence basis: `SPECULATIVE_PROPOSAL` grounded in Structural Probe’s stated tradeoff between probe complexity, probe task, and hypothesis.

3. Do layer-wise probing peaks correspond to stable representational properties, or are they sensitive to dataset/task artifacts and analysis decisions?
   - Type: proposed research question.
   - Evidence basis: `SPECULATIVE_PROPOSAL` grounded in BERT Rediscovers’ layer analysis and the local seed idea.

4. What evidence would be needed before claiming that BERT uses probed information, rather than merely encoding information recoverable by an auxiliary classifier?
   - Type: boundary question.
   - Evidence basis: `DIRECT_PACKET_EVIDENCE` for the caution from BERT Rediscovers; `WITHIN_PACKET_SYNTHESIS` with primer methodological cautions.

## hypothesis_table

| Hypothesis | Status | Evidence-burden label | Observable support | Falsification criteria |
|---|---:|---|---|---|
| H1: Some linguistic information recovered by probes is stable across multiple low-capacity probe choices and layer analyses. | Proposed | `SPECULATIVE_PROPOSAL` | Similar layer-wise trends across edge probing, structural probe variants, and constrained probes. | Large changes in conclusions when probe capacity, layer mixing, or task formulation changes. |
| H2: Higher-capacity probes will recover more task signal but reduce confidence that the structure is intrinsic to the representation. | Proposed | `SPECULATIVE_PROPOSAL` | Probe performance increases with capacity while control tasks or randomized-label checks also improve. | Capacity increases improve linguistic probing without improving controls or artifact-sensitive diagnostics. |
| H3: Structural probe results are more interpretable when the probe hypothesis is explicitly tied to parse-tree distances/depths and compared against baselines. | Proposed but packet-grounded | `WITHIN_PACKET_SYNTHESIS` | Linear structural probes show parse-distance/depth correspondence, and baseline comparisons clarify what is attributable to contextual representations. | Comparable results from trivial/random baselines or failure to reproduce distance/depth correspondence. |
| H4: Layer-wise probing peaks should not be interpreted as evidence of causal model use without intervention or behavioral tests. | Boundary hypothesis | `DIRECT_PACKET_EVIDENCE` plus `LIMITED_CRITIQUE` | Probing shows recoverability, but no causal-use evidence is supplied in the packet. | Intervention experiments show that removing or manipulating the probed feature changes model behavior predictably. |
| H5: Dataset artifacts can create apparently strong probing results that do not reflect stable linguistic representation. | Proposed risk hypothesis | `SPECULATIVE_PROPOSAL` | Probe succeeds on artifact-prone splits but degrades under controlled or adversarial splits. | Results remain stable under artifact controls, balanced splits, and alternative datasets. |

## evidence_map

| Claim | Type | Evidence-burden label | Source location | Evidence directness | Supported scope | Missing detail |
|---|---|---|---|---|---|---|
| BERT Rediscovers uses edge-probing tasks and layer analysis to study where linguistic information appears in BERT. | Source fact | `DIRECT_PACKET_EVIDENCE` | BERT Rediscovers: abstract, Section 2, Section 3, Figures 1-3 | Direct | This paper’s probing setup | Exact task list, metrics, and numeric results not in packet |
| BERT Rediscovers warns that probing/inspection does not prove model use. | Limitation | `DIRECT_PACKET_EVIDENCE` | BERT Rediscovers: limitations paragraph | Direct | Interpretation of probing evidence | No intervention protocol supplied |
| BERTology primer surveys BERT representations, attention, probing, and methodological cautions. | Source fact | `DIRECT_PACKET_EVIDENCE` | Primer: probing/representation sections; discussion | Direct | Survey-level background | Specific surveyed claims not enumerated in packet |
| Structural Probe learns a linear transformation where squared distances or norms correspond to parse-tree distances/depths. | Method definition | `DIRECT_PACKET_EVIDENCE` | Structural Probe: abstract, Section 2 | Direct | Structural probing of contextual representations | Exact objective and evaluation numbers absent |
| Structural Probe evaluates ELMo/BERT and includes baselines. | Experimental fact | `DIRECT_PACKET_EVIDENCE` | Structural Probe: Table 1, Figures 1-5 | Direct | Reported evaluation setup | Baseline identities and scores not included in packet |
| Probe interpretation depends on probe complexity, probe task, and hypothesis. | Limitation | `DIRECT_PACKET_EVIDENCE` | Structural Probe: limitations discussion | Direct | Probing methodology | No full taxonomy of probe capacities supplied |
| The seed idea asks whether probing reveals stable structure or probe/dataset/analysis artifacts. | Seed claim | `DIRECT_PACKET_EVIDENCE` | Local seed idea brief | Direct | Proposal motivation | No prior experiment results supplied |
| A rigorous proposal should separate recoverability from causal model use. | Synthesis | `WITHIN_PACKET_SYNTHESIS` | BERT Rediscovers limitations + Structural Probe limitations + Primer cautions | Indirect | Research-design principle for this packet | Requires external literature for broader claims |

## experiment_plan

**Experiment 1: Probe-capacity sweep**

Goal: Test whether linguistic probing conclusions survive changes in probe complexity.

Design:
- Representations: BERT layers, and optionally ELMo if matching Structural Probe’s contextual-representation comparison.
- Tasks: edge-probing tasks from BERT Rediscovers and structural distance/depth tasks from Structural Probe, to the extent available.
- Probes: linear probe, structural probe, and controlled higher-capacity variants.
- Metrics: task performance, parse-distance/depth correspondence, and layer-wise peak location.
- Baselines: random representations, non-contextual or simpler representation baselines if available, majority/simple task baselines, and probe-only controls.
- Evidence label: `SPECULATIVE_PROPOSAL`.

Falsification:
- If conclusions change substantially with probe capacity, H1 is weakened.
- If high-capacity probes perform well on controls that should not contain linguistic structure, H2 gains support.

**Experiment 2: Layer-stability and scalar-mixing robustness**

Goal: Determine whether layer-wise linguistic patterns are stable or analysis-choice dependent.

Design:
- Compare single-layer probing, scalar mixing, and cumulative scoring inspired by BERT Rediscovers Section 3.
- Report whether the same linguistic phenomena peak in the same layers across analysis methods.
- Include uncertainty across random seeds or repeated probe initializations.

Baselines and ablations:
- Single-layer versus scalar-mixed representations.
- Frozen versus alternative random initialization controls, if available.
- Same probe across all layers to avoid confounding layer and probe differences.

Falsification:
- If layer rankings reverse under minor aggregation changes, claims about stable layer localization should be softened.

**Experiment 3: Dataset artifact and control-task audit**

Goal: Test whether probe success reflects dataset artifacts.

Design:
- Create controlled splits that reduce lexical or label-distribution shortcuts.
- Add randomized-label controls and structurally irrelevant control tasks.
- Compare performance degradation between true tasks and controls.

Baselines:
- Random-label probe.
- Frequency/lexical-feature baseline.
- Simple classifier using surface features only.

Falsification:
- If surface-feature baselines match contextual probes, the stable-representation interpretation is weakened.
- If contextual probes remain strong while controls fail, artifact concerns are reduced but not eliminated.

**Experiment 4: Recoverability versus use**

Goal: Avoid overclaiming causal use from probing.

Design:
- Treat probing as evidence of information recoverability.
- Add intervention-style tests only if feasible: manipulate or remove the probed feature and measure downstream behavioral change.
- Do not claim model use unless intervention changes model behavior in the predicted direction.

Baselines:
- No-intervention control.
- Random intervention control.
- Intervention on unrelated feature.

Falsification:
- If interventions on the probed feature do not affect downstream behavior, causal-use claims are unsupported even if probes decode the feature.

## risk_register

| Risk | Label | Why it matters | Mitigation |
|---|---|---|---|
| Probe performance is mistaken for evidence that the model uses the information. | `DIRECT_PACKET_EVIDENCE` / `LIMITED_CRITIQUE` | BERT Rediscovers explicitly warns that observed probing patterns do not prove use. | State claims as recoverability unless intervention evidence is added. |
| Higher-capacity probes learn the task rather than reveal representation structure. | `DIRECT_PACKET_EVIDENCE` / `SPECULATIVE_PROPOSAL` | Structural Probe notes the tradeoff between probe complexity, task, and hypothesis. | Use capacity sweeps, simple probes, and control tasks. |
| Layer-wise conclusions depend on scalar mixing or cumulative scoring choices. | `LIMITED_CRITIQUE` | BERT Rediscovers uses layer analysis and scalar mixing/cumulative scoring, making analysis choice part of the evidence path. | Compare multiple aggregation choices and report sensitivity. |
| Dataset artifacts inflate probing results. | `SPECULATIVE_PROPOSAL` | The seed idea explicitly raises dataset artifacts as a concern. | Use artifact-controlled splits, surface baselines, and randomized-label controls. |
| Baselines are too weak to support interpretation. | `LIMITED_CRITIQUE` | Structural Probe includes baselines, but the packet does not provide full details. | Require transparent baseline definitions and report probe-only/simple-feature baselines. |
| Reproducibility is under-specified from the packet. | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW` | Packet does not provide seeds, exact configs, code availability, or full metrics. | Record model versions, datasets, preprocessing, seeds, probe configs, and raw outputs. |
| Field-wide novelty is overclaimed. | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW` | Packet is small and closed; it cannot establish global gaps. | Frame contribution as a scoped empirical audit, not a claim of unexplored territory. |