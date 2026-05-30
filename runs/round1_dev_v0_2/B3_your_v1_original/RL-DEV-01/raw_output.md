## rl_protocol_audit

| Risk | Why it matters | Source-grounded evidence | Severity | Mitigation |
|---|---|---:|---|---|
| Dataset coverage may be too narrow for broad offline RL claims | Offline RL performance depends heavily on dataset support, behavior quality, and coverage. A protocol that treats all static datasets as interchangeable can overstate robustness. | D4RL emphasizes narrow data, biased data, multitask data, suboptimal data, and non-representable behavior policies as core offline RL difficulties; Sections 4-5 and limitations/discussion. | High | Report results separately by dataset property and domain, not only aggregate scores. |
| Behavior policy assumptions may be underspecified | Offline RL failure modes depend on whether the behavior policy is known, mixed, expert, suboptimal, human, scripted, or non-representable. | D4RL Section 3 frames fixed datasets and behavior-policy issues; D4RL notes non-representable behavior policies. CQL Section 2 focuses on action distribution shift. | High | For every dataset, document collection regime, behavior-policy type, and expected support mismatch. |
| Train/eval separation needs explicit enforcement | Offline training must use only the static dataset; simulator interaction should be reserved for evaluation. Otherwise the protocol no longer supports offline RL claims. | D4RL frames algorithms as training from static previously collected datasets; p. 1 Abstract, p. 2 Introduction, Section 3. | High | State that no online rollouts, environment queries, or adaptive data collection are used during training/tuning. |
| Simulator evaluation does not establish deployment robustness | D4RL benchmark performance is simulator-based and normalized; this supports benchmark claims, not real-world deployment claims. | D4RL p. 7 evaluation protocol and normalized-score definition; additional notes distinguish normalized score, raw return, and value estimates. | High | Limit claims to D4RL-style simulator benchmark performance unless real deployment evidence is added. |
| Normalized score can obscure raw-return behavior | Normalized scores use task/domain-specific anchors, so cross-domain aggregation can hide absolute return differences. | D4RL defines normalized-score conventions using task- or domain-specific reference anchors; p. 7 and Appendix Tables 1-3. | Medium | Report normalized score and raw environment return side by side. Avoid unsupported cross-domain ranking. |
| Policy value estimates may be confused with true returns | Offline value estimates are not the same as rollout returns. | CQL Table 4 reports estimated policy values and true returns separately; additional notes distinguish policy value estimates from actual environment return. | High | Use simulator rollout return as primary evaluation; present value estimates only as diagnostic analysis. |
| Seed and uncertainty reporting may be insufficient if only means are reported | Four seeds are reported for CQL, but uncertainty intervals or variance handling must be explicit for claims about reliability. | CQL Tables 1-2 average D4RL normalized scores over four seeds; Appendix p. 29 gives four-seed details. D4RL Appendix Tables 1-3 include seed-reporting information. | Medium | Report mean, standard deviation or confidence interval, number of seeds, and per-seed values. |
| Baseline fairness depends on tuning and protocol details | Offline RL baselines can differ in hyperparameters, tuning budgets, and implementation assumptions. | CQL compares against prior offline RL methods and behavioral cloning on D4RL; Appendix p. 29 provides D4RL hyperparameter details. | Medium | Specify baseline implementations, hyperparameters, tuning budget, model class, and evaluation frequency. |
| Aggregating Gym, AntMaze, Adroit, and Kitchen may overgeneralize | These domains test different capabilities and data regimes. | CQL Tables 1-2 report D4RL domains including Gym, AntMaze, Adroit, and Kitchen; D4RL Sections 4-5 define task design factors and instantiations. | Medium | Analyze by domain and dataset type before any overall summary. |

## dataset_and_environment_checklist

| Item | Required in protocol | Packet support | Current sufficiency risk |
|---|---|---|---|
| Dataset identity | Name each D4RL task/domain and dataset variant. | D4RL Appendix Tables 1-3 provide task identities; CQL Tables 1-2 use Gym, AntMaze, Adroit, Kitchen. | High if only “D4RL” is named globally. |
| Dataset collection regime | State whether data are narrow, biased, multitask, suboptimal, or from non-representable behavior policies. | D4RL Sections 4-5 and discussion emphasize these properties. | High if not reported per dataset. |
| Behavior policy | Identify known/unknown/mixed/expert/suboptimal/scripted/human where available from the packet. | D4RL Section 3 behavior-policy framing; notes mention non-representable behavior policies. | High if assumed to be representative or known. |
| Training mode | Confirm fixed dataset only. | D4RL defines offline RL as static previously collected datasets. | High if tuning uses simulator feedback. |
| Evaluation mode | Specify simulator-based rollout evaluation. | D4RL p. 7 evaluation protocol. | Medium if described only as “benchmark score.” |
| Environment details | Provide domain/task identities and environment versions if supplied. | Packet gives domains and task identities via D4RL Appendix Tables 1-3 but does not provide finer version details. | Medium; missing environment version details weaken reproducibility. |
| Reward/return | Report actual environment return. | D4RL Appendix Tables 1-3 include raw returns; additional notes distinguish raw return from normalized score. | Medium if omitted. |
| Normalized score | Define anchors and normalization convention. | D4RL p. 7 defines normalized-score conventions using task/domain-specific anchors. | Medium if normalized scores are treated as absolute performance. |
| Evaluation episodes | State number of rollout episodes if supplied. | Not specified in the packet. | Unknown; must be added or marked missing. |
| Stochasticity/wrappers/horizon/termination | Specify if available. | Not specified in the packet. | Unknown; reproducibility risk. |

## baseline_and_metric_review

| Area | Audit finding | Boundary |
|---|---|---|
| Baselines | CQL compares against prior offline RL methods and behavioral cloning on D4RL. Behavioral cloning is important because it tests whether offline RL improves over imitation of the dataset behavior. | The packet does not give the full baseline list, tuning budgets, or implementation details beyond CQL Appendix p. 29 hyperparameter and four-seed reporting notes. |
| Metrics | D4RL uses simulator-based evaluation and normalized-return conventions; Appendix Tables 1-3 include normalized scores and raw returns. | Normalized score, raw return, and estimated policy value must not be collapsed into one metric. |
| CQL-specific analysis | CQL Table 4 compares estimated policy values and true returns, supporting analysis of conservative value estimation. | This supports value-estimation analysis, not deployment performance by itself. |
| Seeds | CQL Tables 1-2 average over four seeds; Appendix p. 29 gives four-seed reporting details. | Four seeds help, but uncertainty reporting should include variance/CI or per-seed values. |
| Aggregation | Scores across Gym, AntMaze, Adroit, and Kitchen are not automatically comparable as one universal offline RL capability score. | Any aggregate must disclose task weighting and domain heterogeneity. |

## claim_scope_assessment

Supported claims, if the revised protocol is followed:

| Claim | Support level | Scope |
|---|---|---|
| The method can be evaluated as an offline RL algorithm on D4RL-style static datasets. | Supported | D4RL fixed-dataset offline RL framing; CQL D4RL evaluation. |
| The method’s benchmark performance can be compared to listed offline RL baselines and behavioral cloning on the same D4RL tasks. | Supported with protocol details | Requires same tasks, same evaluation protocol, clear baselines, and seed reporting. |
| Normalized D4RL scores summarize benchmark performance. | Supported with caution | Only under D4RL’s task/domain-specific normalization anchors. |
| Conservative value estimates can be analyzed against true returns for selected datasets. | Supported for CQL-style analysis | CQL Table 4 separates estimated policy values and true returns. |

Claims not sufficiently supported by the packet alone:

| Claim | Why not supported |
|---|---|
| The method is generally superior across offline RL. | D4RL/CQL results are benchmark- and protocol-specific. |
| The method is robust to real-world deployment shift. | Packet describes simulator-based benchmark evaluation, not deployment. |
| Normalized score proves absolute task mastery. | Normalized scores depend on task/domain-specific anchors. |
| Offline value estimates prove policy performance. | Packet explicitly distinguishes estimated policy values from true returns. |
| Results transfer across all dataset qualities. | D4RL highlights narrow, biased, multitask, suboptimal, and non-representable behavior-policy datasets as distinct challenges. |

## revised_protocol

1. **Dataset declaration**
   Report every D4RL task and dataset variant separately, using D4RL Appendix Tables 1-3 task identities where applicable. For each dataset, label the relevant data property: narrow, biased, multitask, suboptimal, or non-representable behavior policy when supported by D4RL.

2. **Offline training constraint**
   Train only on the fixed static dataset. Do not use simulator interaction, online rollouts, or adaptive data collection for training or model selection. If any environment access is used before final evaluation, report it and remove broad offline-only claims.

3. **Behavior-policy documentation**
   For each dataset, state what is known about the data-collection policy. If the behavior policy is unknown, mixed, suboptimal, or non-representable, mark that explicitly. Include an action-support or distribution-shift discussion, since CQL’s motivation is unsupported learned-policy actions and optimistic Q-values.

4. **Evaluation protocol**
   Evaluate learned policies using the specified D4RL simulator-based protocol. Report both raw environment return and D4RL normalized score. Define the normalization convention and reference anchors as D4RL does on p. 7.

5. **Metrics separation**
   Keep three quantities separate:
   normalized benchmark score,
   actual rollout return,
   estimated policy value.
   Use estimated policy values only for diagnostic value-analysis, following the distinction illustrated by CQL Table 4.

6. **Baselines**
   Include behavioral cloning and relevant prior offline RL methods under the same D4RL tasks and evaluation protocol. For each baseline, report implementation source, hyperparameters, tuning budget, model class where available, and whether the same training/evaluation split was used.

7. **Seeds and uncertainty**
   Run at least the four-seed reporting pattern described for CQL’s D4RL experiments, and report mean plus variance, standard deviation, confidence interval, or per-seed values. Do not present seed averages without uncertainty if making reliability claims.

8. **Domain-wise reporting**
   Report Gym, AntMaze, Adroit, Kitchen, and any other D4RL domains separately before any aggregate. If an aggregate is included, disclose weighting and warn that domains differ in task structure, data quality, and behavior-policy support.

9. **Ablations and diagnostics**
   Include ablations that test the claimed offline RL mechanism, especially sensitivity to conservative regularization or action-distribution support if evaluating a CQL-like claim. Where possible, compare estimated policy values against true rollout returns on selected datasets.

10. **Claim boundaries**
   Limit conclusions to offline RL benchmark performance on the specified D4RL datasets. Do not claim real-world deployment robustness, universal offline RL superiority, or cross-domain generalization unless additional evidence beyond this packet is supplied.