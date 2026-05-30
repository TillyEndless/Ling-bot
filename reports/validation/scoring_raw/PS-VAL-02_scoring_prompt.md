You are scoring an internal fixed-source validation benchmark after generation is complete.

Use only the task specification, frozen validation gold annotation, scoring rubric, and generated outputs below. Do not use external facts. Do not reward style over correctness. Score each variant independently but compare across variants for calibration.

Return JSON matching the provided schema only. For each of the four variants, provide scores from 1-5 or null when a dimension is not applicable to this task. Include concise findings and scoring_notes. No markdown.

# Task ID
PS-VAL-02

# Task Specification
task_id: PS-VAL-02
split: validation
task_type: evidence_grounded_proposal_support
topic: mechanistic interpretability
research_question: "Can the provided mechanistic-interpretability claim be turned into a cautious, testable research proposal?"
input_prompt: |
  Using only the provided source packet, develop a small proposal to test the mechanistic-interpretability claim.
  Produce scoped research questions, evidence-grounded hypotheses, causal tests or interventions, controls, falsification criteria, alternative explanations, and a risk register.
  Do not treat correlational evidence as causal proof.
evaluation_mode: closed_source
source_material_required: true
provided_materials:
  - material_id: packet_ps_ho_mech_interp_claim
    type: claim_and_evidence_packet
    status: source_material_required
    description: "A frozen packet containing a mechanistic-interpretability claim, evidence summary, and source excerpts."
required_outputs:
  - scoped_research_questions
  - hypothesis_table
  - evidence_map
  - causal_test_plan
  - alternative_explanations
  - risk_register
critical_facts_to_capture:
  - "What the packet directly shows versus what it merely suggests."
  - "Whether evidence is correlational, interventional, causal, descriptive, or speculative."
  - "Controls and interventions needed to test the claim."
  - "Scope boundaries for model family, task, layer, feature, or behavior."
common_failure_modes:
  - "Converting activation observations into causal claims without intervention evidence."
  - "Ignoring alternative explanations."
  - "Proposing tests that cannot falsify the claim."
  - "Overstating scope beyond the provided model or task."
scoring_dimensions:
  - factual_accuracy
  - evidence_traceability
  - hypothesis_quality
  - experimental_rigor
  - inference_boundary_discipline
  - output_usefulness
  - efficiency
notes_on_domain_specificity: "Mechanistic interpretability is an optional extension topic; this task evaluates causal-evidence discipline."



# Frozen Gold Annotation
task_id: PS-VAL-02
source_packet_id: validation_PS-VAL-02_packet_v0_draft
drafted_by_agent: true
human_review_status: pending
eligible_for_scoring: false
must_capture:
- id: PS-VAL-02-M1
  finding: Separates descriptive/correlational mechanistic evidence from interventional or causal evidence.
  evidence_locations_to_verify:
  - IOI PDF p.1 Abstract and circuit/intervention sections; ROME PDF p.1 Abstract and causal tracing/model editing sections;
    local claim brief.
  scoring_weight: high
- id: PS-VAL-02-M2
  finding: Proposes tests with causal interventions, controls, falsification criteria, and alternative explanations.
  evidence_locations_to_verify:
  - IOI ablation/intervention figures/tables; ROME causal tracing and editing result sections.
  scoring_weight: high
- id: PS-VAL-02-M3
  finding: Limits claims to supplied model family, task, layer, feature, and behavior scope.
  evidence_locations_to_verify:
  - IOI and ROME limitations/discussion plus local claim brief scope.
  scoring_weight: medium
acceptable_equivalent_formulations:
- Equivalent wording is acceptable if it remains grounded in the supplied validation packet and preserves claim scope.
critical_errors:
- id: E1
  error: Uses external sources or remembered facts as evidence for a core claim in the closed-source task.
  penalty: major
- id: E2
  error: Presents a broad superiority, deployment, causality, or field-gap claim beyond packet evidence.
  penalty: major
- id: E3
  error: Invents missing metrics, seeds, versions, baselines, or numeric results.
  penalty: major
inference_boundary_requirements:
- Use only the packet as evidence.
- Separate direct source facts, within-packet synthesis, critique, and proposed hypotheses.
- Mark broader literature, deployment, causal, or superiority claims as requiring external review unless directly evidenced.
optional_high_value_findings:
- Identifies missing reproducibility details without treating absence from the packet as proof of source failure.
- Separates direct evidence from synthesis and proposed follow-up checks.
- Reports source/page/table grounding where the packet or canonical source supplies it.
ambiguities_requiring_human_review:
- Exact page, section, table, and figure locations must be verified against the acquired canonical sources.
- Some packet notes are compressed source summaries and should be checked against full PDFs before scoring approval.


# Agent Review Authorization Layer
This authorizes internal scoring but is not itself a gold answer. Apply the global E/B rule: external facts or broad claims should be penalized only when used as evidence for a core scored claim; harmless background context clearly marked as non-evidence should not trigger a major penalty.

# Scoring Rubric
# Scoring Rubric

Score each dimension from 1 to 5. Keep dimensions separate; do not collapse them into one total score unless a later report explicitly defines a weighted decision rule.

## Scale

| Score | Meaning |
|---:|---|
| 5 | Excellent. Expert-useful, accurate, traceable, and complete for the task scope. |
| 4 | Strong. Minor omissions or calibration issues, but scientifically reliable. |
| 3 | Adequate. Useful with expert cleanup; some missing detail or weak organization. |
| 2 | Weak. Substantial omissions, unsupported reasoning, or poor task fit. |
| 1 | Unreliable. Misleading, unsupported, materially incorrect, or unsafe for research use. |

## Dimensions

### Factual Accuracy

Measures whether the output correctly states methods, assumptions, datasets, metrics, experimental findings, and limitations.

Strong outputs separate source claims from the agent's interpretation. Weak outputs misstate paper facts, confuse versions, invent details, or generalize beyond the source.

### Evidence Traceability

Measures whether substantive claims link to provided sources, source locations, evidence IDs, or retrieval results.

Strong outputs make it clear what each source supports and what it does not support. Weak outputs provide unsupported claims or citations that are only topically related.

### Citation Validity

Measures whether cited works exist, are identified correctly, and support the stated claim.

For closed-source tasks, citations must come from the source packet. For retrieval tasks, citations must follow fixed retrieval rules and include enough metadata to verify.

### Literature Coverage

Applies primarily to retrieval and literature-survey tasks. Measures whether the output includes canonical work, recent relevant work, and important contrasting lines of research.

Strong outputs document search strategy, coverage limits, and omissions. Weak outputs miss obvious core work or overfit to one source.

### Comparison Fairness

Measures whether methods are compared under compatible assumptions, datasets, metrics, compute, tuning effort, and evaluation protocols.

Strong outputs identify non-comparable settings and normalize conclusions. Weak outputs declare winners without accounting for task setup or baseline strength.

### Experimental Rigor

Measures handling of baselines, ablations, metrics, seeds, statistical uncertainty, compute, data splits, hyperparameter search, and reproduction risk.

Strong outputs distinguish confirmatory from exploratory evidence. Weak outputs ignore missing baselines, single-seed claims, metric mismatch, or leakage.

### Benchmark Validity

Measures whether benchmarks, datasets, tasks, metrics, and protocols are suitable for the claim being made.

Strong outputs identify contamination, leakage, saturation, protocol mismatch, metric gaming, and train/eval mismatch. Weak outputs treat a benchmark score as automatically meaningful.

### Inference-Boundary Discipline

Measures whether the output distinguishes source-supported conclusions, cross-paper synthesis, hypotheses, and speculation.

Strong outputs calibrate scope and uncertainty. Weak outputs launder speculation into conclusions or overstate causal/generalization claims.

### Hypothesis Quality

Applies primarily to proposal-support tasks. Measures whether hypotheses are grounded in evidence, falsifiable, scoped, feasible, and paired with disconfirming observations.

Strong outputs specify predictions, failure criteria, required evidence, and alternative explanations. Weak outputs generate attractive but untestable ideas.

### RL-Specific Correctness

Applies to RL tasks. Measures correctness about environment versions, wrappers, policies, reward functions, offline data, evaluation episodes, stochasticity, train/eval mismatch, and return distributions.

Strong outputs catch RL-specific failure modes. Weak outputs treat RL results like ordinary supervised-learning benchmarks.

### Output Usefulness

Measures whether the artifact supports a real research decision: reading, reviewing, planning, reproduction, proposal writing, or experimental design.

Strong outputs are structured, actionable, and concise enough to use. Weak outputs are polished but generic.

### Efficiency

Measures token cost, latency, tool calls, retrieval volume, and useful-information density.

High-quality but extremely inefficient outputs should be flagged. Efficient outputs must still satisfy reliability requirements.

## Hard-Fail Conditions

A task may receive an overall hard-fail flag if any of these occur:

- A hallucinated citation is presented as real.
- A critical claim is marked supported without direct evidence.
- A comparative conclusion is made without adequate baseline or setting normalization.
- An RL result is summarized from best seed/checkpoint only without disclosure.
- A causal interpretability claim is supported only by correlational evidence.
- A reproduction or experiment plan omits required data, environment, or evaluation protocol.
- Held-out gold annotation content appears in the output or prompt context.

## Scorecard Format

```yaml
run_id:
variant:
task_id:
reviewer:
scores:
  factual_accuracy:
  evidence_traceability:
  citation_validity:
  literature_coverage:
  comparison_fairness:
  experimental_rigor:
  benchmark_validity:
  inference_boundary_discipline:
  hypothesis_quality:
  rl_specific_correctness:
  output_usefulness:
  efficiency:
hard_fail:
  triggered: false
  reasons: []
findings:
  - severity: major|minor
    dimension:
    description:
    evidence:
summary:
```


# Generated Outputs
## OUTPUT: B0_base_agent

## scoped_research_questions

1. Can a small, localized internal circuit or representation be shown to be necessary for a target model behavior, rather than merely correlated with it?
2. Is the putative circuit sufficient, or partially sufficient, to recover the behavior when transplanted, restored, or selectively activated in otherwise degraded runs?
3. Are the circuit’s effects behavior-specific, or do interventions on it broadly damage model performance?
4. Does the localized mechanism generalize across prompt variants, counterfactual inputs, and held-out examples?
5. Can the mechanism be edited or perturbed in a predictable way, analogous to ROME-style factual association edits, without causing uncontrolled side effects?

## hypothesis_table

| ID | Hypothesis | Evidence grounding | Testable prediction | Falsification criterion |
|---|---|---|---|---|
| H1 | A localized circuit or representation contributes causally to the target behavior. | IOI paper reports circuit analysis with intervention/ablation-style evidence for indirect-object identification. | Targeted ablation of the proposed components reduces the target behavior more than matched control ablations. | Matched random or nearby-component ablations produce equal or larger effects. |
| H2 | Restoring the candidate circuit restores behavior under corrupted or counterfactual inputs. | ROME uses causal tracing to localize factual associations; IOI uses interventions to test circuit roles. | Activation patching or restoration of the proposed component recovers correct behavior relative to corrupted baselines. | Restoration has no specific recovery effect, or recovery is not stronger than unrelated-component restoration. |
| H3 | The circuit is behavior-specific rather than a generic performance bottleneck. | IOI limitations and intervention framing imply the need to distinguish mechanism-specific effects from broad model damage. | Ablating the circuit selectively impairs target cases while preserving unrelated tasks or matched non-target prompts. | Intervention causes broad degradation across unrelated prompts. |
| H4 | The localized representation can be predictably edited or redirected. | ROME reports localization and editing of factual associations using causal tracing and editing experiments. | A small edit changes the targeted association or behavior while leaving most neighboring behaviors unchanged. | Edits fail, affect unrelated behaviors heavily, or require broad distributed changes. |
| H5 | Correlational localization alone is insufficient. | Packet explicitly warns not to treat correlational evidence as causal proof. | Components identified by attribution must also pass intervention, restoration, and control tests. | Attribution-only components do not survive causal tests. |

## evidence_map

| Source | Relevant evidence from packet | Proposal use |
|---|---|---|
| IOI circuit paper | Analyzes a circuit for indirect-object identification in GPT-2 small. Includes circuit analysis, interventions, ablations, limitations. | Provides precedent for moving from circuit discovery to causal testing through targeted ablation and intervention. |
| ROME paper | Studies localization and editing of factual associations using causal tracing and model editing experiments. | Provides precedent for causal tracing, localization, and targeted edits as tests of internal factual representations. |
| Local claim brief | Asks for cautious testing of whether a localized internal circuit or representation is responsible for a behavior. | Defines the central claim but requires it to be treated as a hypothesis, not an established fact. |
| Packet scope note | Exact numeric values, full tables, appendix details, and implementation settings are not included. | Proposal should avoid numeric effect-size commitments and pre-register qualitative success/failure criteria. |

## causal_test_plan

1. Define the target behavior narrowly.
   Use a fixed family of prompts where the model reliably exhibits the behavior. Include held-out prompt templates and counterfactual variants.

2. Identify candidate components.
   Use attribution, activation inspection, or causal tracing-style localization to nominate layers, heads, MLPs, or representation sites. Treat this as hypothesis generation only.

3. Run necessity tests.
   Ablate or replace the candidate components during target prompts. Compare against:
   - random components of similar size,
   - nearby components,
   - components with similar activation magnitude,
   - non-target prompt conditions.

   Success requires target behavior degradation that is larger and more specific than controls.

4. Run restoration tests.
   Corrupt the input or internal activations so the behavior fails, then restore candidate activations from a clean run. Success requires selective recovery of the target behavior beyond unrelated restoration sites.

5. Run sufficiency or partial-sufficiency tests.
   Insert candidate activations into neutral or corrupted contexts and test whether they steer the model toward the target behavior. Interpret cautiously: partial recovery supports causal involvement, not full mechanistic completeness.

6. Run editing tests.
   If the claim concerns a factual or association-like representation, apply a small localized edit inspired by the ROME setup. Test whether the expected behavior changes while unrelated behaviors remain stable.

7. Generalization and robustness checks.
   Repeat across paraphrases, entity swaps, held-out examples, and adversarially similar prompts. A mechanism that only works on the discovery set should not be treated as established.

8. Predefined falsification.
   The claim is rejected or weakened if targeted interventions are not stronger than controls, if restoration fails, if effects are broad and nonspecific, or if the mechanism does not generalize beyond the original prompt set.

## alternative_explanations

- The localized component is correlated with the behavior but not causally responsible.
- The behavior depends on a distributed mechanism, and the apparent circuit is only one visible part.
- Ablation effects reflect generic model damage rather than behavior-specific causal structure.
- Activation patching may restore downstream states without identifying the true upstream computation.
- Prompt templates may accidentally favor the hypothesized mechanism.
- The candidate representation may encode a proxy feature rather than the intended semantic variable.
- Editing success may come from overwriting behavior heuristically rather than locating the original mechanism.
- Results from an IOI-like setting or factual-association setting may not transfer to the new target behavior.

## risk_register

| Risk | Impact | Mitigation |
|---|---|---|
| Overclaiming causality from attribution | False mechanistic conclusion | Require ablation, restoration, and matched controls before causal language. |
| Narrow prompt distribution | Mechanism appears stronger than it is | Use held-out templates, paraphrases, and counterfactual examples. |
| Nonspecific intervention damage | Misread generic degradation as causal evidence | Include unrelated-task and matched-component controls. |
| Distributed mechanism | Local intervention gives incomplete picture | Report localized contribution rather than full responsibility unless sufficiency tests pass. |
| Editing side effects | Local edit changes unrelated behaviors | Measure neighboring and unrelated behaviors before and after edits. |
| Missing implementation details in packet | Proposal may be underspecified numerically | Keep design qualitative and pre-register comparison logic rather than exact thresholds. |
| Confirmation bias in circuit selection | Candidate circuit reflects researcher expectations | Separate discovery and validation sets; test random and matched alternatives. |
| Failure to replicate across examples | Weak external validity | Treat non-generalization as evidence against the strong localized-mechanism claim. |
## OUTPUT: B1_kdense_subset

## scoped_research_questions

1. Can a localized internal component or representation be identified that is necessary for a target model behavior, rather than merely correlated with it?
2. Does intervening on the proposed component selectively change the target behavior while preserving nearby or unrelated behaviors?
3. Do localization methods agree across intervention styles, such as ablation/path-patching-style tests from the IOI circuit paper and causal tracing/editing-style tests from ROME?
4. Under what prompt distributions, model settings, and behavioral variants does the proposed localization fail?

## hypothesis_table

| Hypothesis | Evidence motivation | Prediction | Disconfirming observation | Required experiment | Feasibility caveat |
|---|---|---|---|---|---|
| H1: A small set of internal components is causally necessary for the target behavior. | IOI reports a circuit-level analysis of indirect-object identification with intervention/ablation-style evidence. Local claim asks whether a localized circuit or representation is responsible for behavior. | Ablating or corrupting the proposed components reduces target behavior performance more than matched control components. | Target behavior remains intact after intervention, or control components produce equal or larger effects. | Identify candidate components, perform targeted ablations/corruptions, compare against random and functionally matched controls. | Exact IOI implementation settings and numeric thresholds are not supplied in the packet. |
| H2: Restoring the candidate component rescues the behavior after upstream corruption. | ROME uses causal tracing to localize factual associations; IOI uses intervention-style analysis. | Corrupting the input/internal state impairs behavior, and patching the candidate activation from a clean run restores it selectively. | Patching does not restore behavior, or many unrelated sites restore behavior equally. | Clean/corrupted activation patching or causal tracing across layers, heads, and MLP states. | Packet does not include full tracing protocol details or result tables. |
| H3: Editing the localized representation changes the target behavior in a predictable direction. | ROME studies localization and editing of factual associations through causal tracing and model editing experiments. | A constrained edit at the localized site changes the target output while preserving unrelated outputs better than broad edits. | Edit has no effect, causes broad degradation, or changes outputs inconsistently with the proposed mechanism. | Apply a localized edit or replacement representation; evaluate target, neighboring, and unrelated prompts. | ROME’s scope concerns factual associations; transfer to another behavior must be treated as proposal speculation. |
| H4: The localized mechanism is behavior-specific rather than a general performance dependency. | IOI evidence includes circuit analysis and ablations; local claim asks for responsibility for a behavior. | Intervention effects are larger on target prompts than on matched non-target prompts. | Similar degradation appears across broad unrelated tasks, suggesting general damage rather than mechanism-specific causation. | Use target prompts, syntactic/semantic controls, and unrelated prompt controls. | The packet does not establish which behavior or dataset the local claim targets. |

## evidence_map

| Claim | Source | Location supplied | Evidence type | Support status | Caveat |
|---|---|---|---|---|---|
| Mechanistic interpretability can study localized circuits for specific model behaviors. | IOI circuit paper | Abstract; circuit analysis; interventions/ablations | Circuit analysis plus intervention evidence | Direct | Details and exact metrics are not included in the packet. |
| Ablation/intervention evidence is relevant but should not be treated as automatically complete causal proof. | IOI circuit paper; task instruction | Interventions/ablations; “Do not treat correlational evidence as causal proof” | Methodological caution | Direct | Packet gives neutral source notes, not full experimental controls. |
| Causal tracing can help localize internal states associated with factual behavior. | ROME paper | Abstract; causal tracing; scope | Causal tracing method | Direct | ROME is about factual associations, not necessarily every behavior. |
| Model editing can test whether a localized representation can influence behavior. | ROME paper | Editing intervention; scope | Intervention/editing experiment | Direct | Editing success would still require specificity and off-target evaluation. |
| The proposal should test whether a localized circuit or representation is responsible for behavior. | Local claim brief | local_seed_brief; 2026 | Seed claim | Direct | The packet does not provide the exact behavior, model, or metric. |
| A localized component is causally responsible for the target behavior. | Synthesis from all sources | Cross-source proposal | Proposed causal claim | Speculative | Must be tested; not established by the packet. |

## causal_test_plan

1. Define the behavior and evaluation set.
   Use a narrow target behavior with clean success metrics. Include matched negative controls that share surface features but do not require the proposed mechanism.

2. Localize candidate sites.
   Run causal tracing or clean/corrupted activation patching across layers, attention heads, and MLP states, following the general intervention logic supported by ROME and IOI source notes.

3. Test necessity.
   Ablate, corrupt, or replace only the candidate components. Compare target behavior degradation against random components, matched components with similar activation magnitude, and neighboring layers or heads.

4. Test sufficiency or rescue.
   Corrupt the model state or prompt so the behavior fails, then restore the candidate activation from a clean run. A causal interpretation requires selective rescue of the target behavior.

5. Test editability.
   Apply a localized edit at the candidate representation and measure whether target outputs change predictably. Evaluate unrelated prompts and nearby behaviors to detect off-target damage.

6. Stress-test scope.
   Repeat across prompt templates, lexical variants, distractors, and counterexamples. Report failures as boundary conditions rather than excluding them.

Falsification criteria:
A localized-mechanism claim is weakened or rejected if targeted interventions do not outperform controls, rescue fails, unrelated sites work equally well, effects do not generalize across target variants, or edits cause broad nonspecific degradation.

## alternative_explanations

- The candidate component is correlated with the behavior but not causally necessary.
- The intervention damages general computation, producing apparent behavioral effects without mechanism specificity.
- Multiple distributed components can compensate for the localized site.
- Prompt artifacts or dataset regularities create false localization.
- Causal tracing or patching identifies a bottleneck representation, not the full mechanism.
- Editing changes behavior through broad side effects rather than the intended localized association.
- The mechanism found for factual associations in ROME may not transfer to the target behavior.
- The IOI-style circuit evidence may apply only to narrow task distributions.

## risk_register

| Risk | Source basis | Likely effect | Mitigation |
|---|---|---|---|
| Overclaiming causality from correlation | Task instruction; evidence-handling rules | Proposal claims exceed evidence | Require intervention, rescue, and controls before causal language. |
| Poor construct validity | Local claim lacks exact behavior details | Tests may not measure the intended behavior | Define behavior, metrics, prompt families, and exclusion criteria before localization. |
| Nonspecific intervention damage | IOI intervention/ablation context | False evidence for necessity | Use matched controls and unrelated-task checks. |
| Weak external validity | IOI and ROME source scopes are narrow | Results may not generalize beyond selected model/task | State scope by model, behavior, and prompt distribution. |
| Incomplete reproducibility | Packet omits exact numeric values, tables, and settings | Hard to replicate or compare results | Pre-register model version, prompts, intervention code, random seeds, and thresholds. |
| Editing side effects | ROME editing intervention scope | Apparent success may hide broad degradation | Evaluate target, neighboring, and unrelated prompts after edits. |
| Localization ambiguity | Cross-source synthesis | Many sites may show similar causal effects | Require uniqueness tests against random, matched, and neighboring sites. |
## OUTPUT: B2_orchestra_subset

## scoped_research_questions

1. Can a localized internal circuit or representation be shown to be necessary for a narrowly defined model behavior under controlled prompts?
2. Does intervening on the proposed component change the target behavior more than matched interventions on control components?
3. Is the apparent localization specific to one behavior family, or does it reflect a broader prompt, dataset, or activation-distribution artifact?
4. Can evidence from causal tracing, ablation, and editing converge on the same internal mechanism without treating correlation as causal proof?

## hypothesis_table

| Hypothesis | Provenance | Evidence basis | Testable prediction | Falsification criteria | Support status |
|---|---|---|---|---|---|
| H1: A small set of localized components contributes causally to a narrowly specified behavior. | Agent-proposed, grounded in supplied sources | IOI source note reports circuit analysis with intervention/ablation-style evidence; ROME source note reports causal tracing and editing experiments. | Targeted activation/path/component interventions reduce or alter the behavior more than matched controls. | Matched controls produce equal or larger effects, or target effects vanish across prompt variants/seeds. | Plausible proposal, not established for the new claim. |
| H2: Localization evidence will be behavior-specific rather than globally explanatory. | Agent-inferred | Packet notes both papers have defined scopes and limitations. | Effects are strongest on the target behavior and weaker on unrelated behaviors. | Intervention causes broad nonspecific degradation or improves/harms many unrelated tasks similarly. | Cautiously supported as a design expectation. |
| H3: Editing or activation replacement can provide stronger evidence than passive probing alone. | Cross-source synthesis | IOI includes interventions/ablations; ROME includes causal tracing and editing. | Causal interventions predictably change behavior, while probes alone do not justify causal claims. | Probe accuracy fails to align with intervention effects, or edits do not produce targeted behavioral changes. | Supported as a methodological principle, not as an outcome. |

## evidence_map

| Evidence item | Provenance | What it supports | What it does not support |
|---|---|---|---|
| IOI paper analyzes an indirect-object-identification circuit in GPT-2 small. | Source-derived from packet notes | Mechanistic circuit analysis can be applied to a narrow language-model behavior. | Does not show that any arbitrary behavior has a localized circuit. |
| IOI reports intervention/ablation-style analyses. | Source-derived | Causal-style tests are relevant for moving beyond correlational attribution. | Exact strength, robustness, and implementation details are unavailable in the packet. |
| ROME uses causal tracing for factual associations. | Source-derived | Localization claims can be tested with causal tracing-style methods. | Does not prove the same localization pattern applies to non-factual behaviors. |
| ROME includes model-editing experiments. | Source-derived | Editing interventions can test whether changing localized representations changes outputs. | Does not guarantee edits are clean, isolated, or free of side effects. |
| Packet omits exact numeric values, full tables, appendices, and implementation settings. | Source-derived | Any proposal must remain scoped and avoid quantitative claims. | Prevents strong claims about effect size, reproducibility, or benchmark-level reliability. |

## causal_test_plan

1. Define the target behavior narrowly.
   Use a controlled prompt set where the behavior is clearly observable, plus matched counterfactual prompts that preserve surface form while changing the required answer.

2. Identify candidate components.
   Use causal tracing or activation-patching-style localization to find layers, heads, MLPs, or representations whose restoration changes the target output after corruption. Treat this as candidate generation, not proof.

3. Run targeted interventions.
   Ablate, patch, or edit the candidate component and measure whether the target behavior changes predictably. Compare against random components, same-layer noncandidate components, frequency-matched tokens, and unrelated prompt families.

4. Add positive and negative controls.
   Positive control: reproduce an effect on a source-like narrow behavior where intervention methods are expected to work.
   Negative control: intervene on components not implicated by tracing and verify that effects are smaller or nonspecific.

5. Test specificity.
   Measure whether the intervention affects only the target behavior or causes broad language-model degradation. Include unrelated factual, syntactic, and continuation-quality checks.

6. Test robustness.
   Repeat across prompt templates, entity/token substitutions, random seeds where applicable, and multiple corruption baselines. Report per-condition results before aggregates.

7. Evaluate falsification.
   The localized-circuit claim should be rejected or weakened if effects are not larger than controls, do not replicate across prompt variants, or are explained by broad distribution shift rather than targeted mechanism change.

## alternative_explanations

| Alternative explanation | Why it matters | How to test |
|---|---|---|
| Prompt artifact | The component may track a template feature rather than the behavior. | Use diverse templates and counterfactual prompt pairs. |
| Token-frequency or lexical cue | Localization may reflect common token statistics. | Match entities/tokens by frequency and lexical properties. |
| General performance degradation | Ablation may harm the model broadly rather than target the mechanism. | Include unrelated behavior and fluency controls. |
| Distributed mechanism | No single localized circuit may be responsible. | Test multi-component interventions and compare with single-component effects. |
| Method artifact | Causal tracing or patching may create off-distribution activations. | Use multiple intervention types and check consistency. |
| Editing side effects | Model editing may alter nearby associations or unrelated outputs. | Measure locality, specificity, and unrelated task behavior after edits. |

## risk_register

| Risk | Severity | Claim affected | Consequence | Minimal mitigation |
|---|---:|---|---|---|
| Correlational localization is overstated as causal. | High | Localized representation is responsible for behavior. | Proposal would overclaim mechanism evidence. | Require intervention effects and matched controls. |
| Controls are too weak or unmatched. | High | Candidate component is special. | Apparent effect may reflect layer position, activation scale, or prompt sensitivity. | Use same-layer, random, and behavior-negative controls. |
| Prompt set is too narrow. | High | Mechanism generalizes beyond examples. | Findings may only hold for a template artifact. | Use template and entity variation; report scoped conclusions. |
| Missing implementation details from packet. | Medium | Reproducibility of proposed tests. | Exact setup cannot be specified from sources alone. | Mark implementation choices as proposal details to be preregistered. |
| Intervention creates off-distribution states. | Medium | Causal interpretation of patching/editing. | Behavioral changes may be artifacts of unnatural activations. | Compare ablation, patching, and editing; monitor unrelated degradation. |
| Aggregate metrics hide failures. | Medium | Intervention works reliably. | Strong average effects may mask per-template failures. | Preserve per-task and per-condition results before aggregation. |
| Editing effects are not local. | Medium | Representation encodes specific association or behavior. | Changes may spread to unrelated outputs. | Include locality checks and unrelated behavior probes. |
## OUTPUT: B3_final_for_validation

**scoped_research_questions**

1. Can a candidate localized circuit or representation be identified for the target behavior under a tightly specified prompt/task distribution?
2. Does intervention on that candidate component causally change the target behavior, beyond correlational activation or attribution evidence?
3. Are effects behavior-specific, or do interventions broadly degrade model performance?
4. Does the localization remain stable across paraphrases, distractors, and near-control tasks?
5. Can editing or activation-level interventions produce predictable behavioral changes without claiming a general mechanism beyond the tested setup?

**hypothesis_table**

| Hypothesis | Evidence-burden label | Grounding | Support criterion | Falsification criterion |
|---|---:|---|---|---|
| H1: A localized candidate component can be associated with the target behavior. | `SPECULATIVE_PROPOSAL` | Local claim brief asks whether a localized circuit/representation is responsible; IOI and ROME provide examples of localization-oriented analyses. | Candidate component shows task-specific activation/attribution patterns on target examples. | No component or small set of components shows repeatable task-specific signal. |
| H2: The candidate component is causally involved in the behavior. | `SPECULATIVE_PROPOSAL` | IOI reports intervention/ablation-style mechanistic evidence; ROME uses causal tracing and editing interventions. | Patch, ablate, or edit the component changes target behavior more than matched controls. | Intervention has no reliable target-behavior effect, or matched random/control interventions have equal effect. |
| H3: The component is behavior-specific rather than a general performance bottleneck. | `SPECULATIVE_PROPOSAL` | Packet notes limitations and scope; causal proof requires specificity checks. | Intervention affects target task more than unrelated or minimally different control tasks. | Intervention broadly harms language modeling or unrelated tasks at similar magnitude. |
| H4: Localization generalizes within the scoped task family. | `SPECULATIVE_PROPOSAL` | Packet supports cautious testing, not broad claims. | Effects replicate across held-out templates, paraphrases, and distractor conditions. | Effects disappear under modest prompt variation. |

**evidence_map**

| Claim | Claim type | Evidence-burden label | Source location | Evidence directness | Supported scope | Missing detail |
|---|---|---|---|---|---|---|
| IOI paper analyzes a circuit for indirect-object identification in GPT-2 small. | method/evidence precedent | `DIRECT_PACKET_EVIDENCE` | Source list and controlled source notes | Direct | IOI task in GPT-2 small | Exact circuit components, metrics, tables, implementation settings |
| IOI includes intervention/ablation-style analyses. | method precedent | `DIRECT_PACKET_EVIDENCE` | Controlled source notes | Direct | Mechanistic evidence style, not this proposed claim | Full intervention protocols and quantitative results |
| ROME studies localization and editing of factual associations using causal tracing and editing. | method precedent | `DIRECT_PACKET_EVIDENCE` | Source list and controlled source notes | Direct | Factual-association localization/editing precedent | Exact causal tracing setup and editing metrics |
| The local claim asks whether a localized internal circuit or representation is responsible for a behavior. | proposal target | `DIRECT_PACKET_EVIDENCE` | Local claim brief note | Direct | Seed proposal only | Target model, behavior, dataset, metrics |
| Correlational localization alone does not establish causality. | inference boundary | `METHOD_BACKGROUND` / `LIMITED_CRITIQUE` | Inference boundary rule in supplied instructions; task prompt | Direct as rule, critique as application | Applies to proposal design | None within packet |

**causal_test_plan**

1. **Define the behavior and scope.**  
   Specify model, prompt distribution, target output metric, and control tasks. Because the packet omits exact target behavior and model details, this must be treated as a proposal requirement, not an established fact. Label: `SPECULATIVE_PROPOSAL`.

2. **Localize candidate components.**  
   Use activation analysis, attribution, causal tracing-style scans, or circuit discovery to nominate layers, heads, MLPs, or representations. This stage generates candidates only; it does not prove mechanism. Label: `SPECULATIVE_PROPOSAL`.

3. **Run activation patching or causal tracing.**  
   Compare clean, corrupted, and restored runs. A candidate is stronger if restoring its activation restores the target behavior while matched irrelevant components do not. Label: `SPECULATIVE_PROPOSAL`, grounded by ROME causal tracing precedent.

4. **Ablate or replace candidate components.**  
   Test whether removing, mean-ablating, resampling, or noise-perturbing the component selectively reduces the target behavior. Include random matched components, same-layer controls, and prompt-position controls. Label: `SPECULATIVE_PROPOSAL`, grounded by IOI intervention/ablation precedent.

5. **Edit or steer the representation.**  
   If the claim involves stored associations or internal representations, perform a small editing-style intervention and test whether behavior changes in the predicted direction. Use locality checks to ensure the edit does not broadly alter unrelated outputs. Label: `SPECULATIVE_PROPOSAL`, grounded by ROME editing precedent.

6. **Replicate across variants.**  
   Test held-out prompts, paraphrases, distractors, and near-control behaviors. Report failures instead of treating one successful prompt family as general mechanism evidence.

**alternative_explanations**

- The candidate component may correlate with the behavior but not causally drive it.
- Intervention effects may reflect distribution shift or activation damage rather than removal of a specific mechanism.
- The behavior may be implemented redundantly across multiple components, so single-component tests may underestimate causal structure.
- The proposed circuit may be task-template-specific rather than behavior-general.
- Editing effects may alter surface associations without identifying the full mechanism.
- Control failures could arise from poorly matched controls rather than true specificity.

**risk_register**

| Risk | Evidence-burden label | Why it matters | Mitigation |
|---|---:|---|---|
| Overclaiming causality from activation correlations | `LIMITED_CRITIQUE` | The task explicitly warns not to treat correlation as causal proof. | Require interventions, controls, and falsification criteria. |
| Narrow prompt distribution | `LIMITED_CRITIQUE` | Packet scope lacks full datasets or task diversity. | Use held-out templates, paraphrases, distractors, and near-control tasks. |
| Poorly matched controls | `LIMITED_CRITIQUE` | Apparent specificity may be an artifact of component choice. | Match controls by layer, component type, activation norm, and position where possible. |
| General degradation mistaken for mechanistic effect | `LIMITED_CRITIQUE` | Ablations can damage model computation broadly. | Measure unrelated task performance and fluency/locality metrics. |
| Missing reproducibility details | `DIRECT_PACKET_EVIDENCE` / `LIMITED_CRITIQUE` | Packet says exact numbers, tables, appendix details, and implementation settings are not included. | Pre-register prompts, metrics, seeds/runs, model version, code, and raw outputs. |
| Field-wide novelty overclaim | `UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW` | Packet does not support claims about what the broader literature has or has not shown. | Limit claims to this experiment and cite external review only if later performed. |
