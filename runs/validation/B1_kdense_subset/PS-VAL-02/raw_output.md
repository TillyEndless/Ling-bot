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