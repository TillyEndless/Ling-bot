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