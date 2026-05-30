## rl_protocol_audit

**Source inventory:** The packet contains two sources: D4RL, an offline RL benchmark suite paper, with evidence from the abstract, introduction, Section 3, Sections 4-5, p. 7 evaluation protocol, Appendix Tables 1-3, and discussion/limitations; and CQL, an offline RL method paper, with evidence from the abstract/introduction, Section 2, Sections 3.1-3.2, Tables 1-4, Appendix p. 29, and conclusion/limitations.

| Risk | Evidence-burden label | Source grounding | Why it matters | Severity |
|---|---|---|---|---|
| Offline evaluation may be overclaimed as online or deployment robustness if claims go beyond simulator rollout or benchmark scores. | LIMITED_CRITIQUE | D4RL p. 7 evaluation protocol; CQL Tables 1-2; additional notes distinguish normalized score, return, and value estimates. | D4RL and CQL support benchmark-level offline RL evaluation, not real-world deployment unless separately tested. | High |
| Dataset coverage is intentionally diverse but not exhaustive. | DIRECT_PACKET_EVIDENCE / LIMITED_CRITIQUE | D4RL Sections 4-5; dataset factors include narrow, biased, multitask, suboptimal, and non-representable behavior policies. | The benchmark probes several offline RL stressors, but the packet does not establish that these cover all deployment-relevant distribution shifts. | High |
| Behavior policy assumptions need explicit per-dataset documentation. | DIRECT_PACKET_EVIDENCE | D4RL Section 3 fixed dataset and behavior-policy framing; Sections 4-5 dataset design factors. | Offline RL performance depends heavily on behavior-policy support; non-representable or biased behavior policies change what conclusions are valid. | High |
| Train/eval separation is implied by static offline datasets plus simulator evaluation, but leakage controls are not fully specified in the packet. | LIMITED_CRITIQUE | D4RL Section 3; p. 7 evaluation protocol. | A protocol should state that no online interaction, tuning on test rollouts, or dataset contamination is allowed. | Medium |
| Normalized scores can obscure raw return differences and task-specific anchors. | DIRECT_PACKET_EVIDENCE / LIMITED_CRITIQUE | D4RL p. 7 normalized-score definition; Appendix Tables 1-3 include normalized scores and raw returns. | Aggregated normalized scores should not be treated as absolute performance across domains without reporting raw returns and anchors. | Medium |
| CQL reports four-seed D4RL results, but uncertainty format beyond seed count is not fully detailed in the packet. | DIRECT_PACKET_EVIDENCE / LIMITED_CRITIQUE | CQL Tables 1-2; Appendix p. 29 four-seed reporting. | Four seeds improve reliability, but confidence intervals, variance, or statistical testing should be specified for strong claims. | Medium |
| Estimated policy values and true returns must not be conflated. | DIRECT_PACKET_EVIDENCE | CQL Table 4; additional source notes. | Offline value estimates can support conservative-value analysis, but actual rollout returns are separate evidence. | High |
| Baseline fairness depends on comparable tuning and protocol details, which are only partially described in the packet. | LIMITED_CRITIQUE | CQL Tables 1-2 compare prior offline RL methods and behavioral cloning; Appendix p. 29 hyperparameters. | Strong claims require matched evaluation rules, tuning budget, and implementation detail. | Medium |

## dataset_and_environment_checklist

| Item | Packet-supported status | Evidence-burden label | Required protocol treatment |
|---|---|---|---|
| Dataset identity | D4RL defines benchmark domains and tasks; Appendix Tables 1-3 provide task identities. | DIRECT_PACKET_EVIDENCE | List every dataset/task by exact D4RL identity. |
| Dataset collection regime | D4RL frames offline RL as static, previously collected datasets. | DIRECT_PACKET_EVIDENCE | State that training uses fixed datasets only. |
| Behavior policy | D4RL highlights narrow, biased, multitask, suboptimal, and non-representable behavior policies. | DIRECT_PACKET_EVIDENCE | Record known or unknown behavior-policy properties per dataset. |
| Offline training | Both D4RL and CQL concern offline RL from fixed data. | DIRECT_PACKET_EVIDENCE | Forbid environment interaction during training unless explicitly labeled as a separate online experiment. |
| Evaluation environment | D4RL uses specified simulator-based evaluation. | DIRECT_PACKET_EVIDENCE | Name simulator/task versions and evaluation rules; packet does not give all version details. |
| Reward/return | D4RL reports raw returns and normalized scores. | DIRECT_PACKET_EVIDENCE | Report both raw environment return and normalized score. |
| Normalization anchors | D4RL defines normalized score using task- or domain-specific reference anchors. | DIRECT_PACKET_EVIDENCE | Publish anchor definitions with results. |
| Seeds/runs | D4RL Appendix Tables 1-3 include seed-reporting information; CQL D4RL results average over four seeds. | DIRECT_PACKET_EVIDENCE | Use at least the stated four-seed CQL standard for comparable D4RL claims; report dispersion. |
| Distribution shift | CQL explicitly addresses action distribution shift from unsupported learned-policy actions. | DIRECT_PACKET_EVIDENCE | Include diagnostics or discussion of action support and behavior-policy mismatch. |
| Deployment setting | Not established in packet. | UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW | Do not claim deployment robustness from these results alone. |

## baseline_and_metric_review

CQL’s baseline set includes prior offline RL methods and behavioral cloning on D4RL tasks, with normalized-score comparisons in Tables 1 and 2 across Gym, AntMaze, Adroit, and Kitchen. This is direct packet evidence for benchmark comparison within those reported settings.

The metric stack should keep three quantities separate:

| Quantity | Source grounding | Audit judgment |
|---|---|---|
| Normalized benchmark score | D4RL p. 7; CQL Tables 1-2 | Useful for benchmark comparison, but anchor-dependent. |
| Raw environment return | D4RL Appendix Tables 1-3; source notes | Needed to interpret actual task performance. |
| Estimated policy value | CQL Table 4 | Useful for conservative-value analysis, but not equivalent to rollout return. |

Baseline risks are mostly protocol-detail risks, not proven flaws. The packet says CQL compares against prior offline RL methods and behavioral cloning, and gives four-seed reporting and hyperparameter details in Appendix p. 29. It does not, from the controlled notes alone, fully establish matched tuning budgets, identical evaluation wrappers, or statistical tests. Label: `LIMITED_CRITIQUE`.

## claim_scope_assessment

| Proposed claim type | Supported? | Evidence-burden label | Boundary |
|---|---:|---|---|
| “The protocol evaluates offline RL on D4RL benchmark tasks.” | Yes | DIRECT_PACKET_EVIDENCE | Supported by D4RL’s fixed-dataset benchmark framing and simulator evaluation. |
| “CQL improves benchmark normalized scores over listed baselines in reported D4RL settings.” | Yes, within reported tables | DIRECT_PACKET_EVIDENCE | Limited to CQL Tables 1-2 tasks, baselines, and four-seed setup. |
| “CQL addresses action-distribution shift through conservative Q-learning.” | Yes | DIRECT_PACKET_EVIDENCE | Supported by CQL Sections 2-3.2 and Equations 3-4. |
| “Higher normalized D4RL score means universally better policy quality.” | No | LIMITED_CRITIQUE | Normalized scores are anchor-dependent and domain/task-specific. |
| “Offline value estimates prove actual online performance.” | No | DIRECT_PACKET_EVIDENCE / LIMITED_CRITIQUE | Packet explicitly separates value estimates from true returns. |
| “Benchmark performance establishes deployment robustness.” | No | UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW | Requires external deployment evidence not in packet. |
| “The datasets cover all important offline RL failure modes.” | No | UNSUPPORTED_OR_NEEDS_EXTERNAL_REVIEW | D4RL includes several dataset difficulties, but exhaustiveness is not established. |

## revised_protocol

1. **Dataset declaration**
   Use D4RL task identities exactly as defined in the benchmark. For each task, report domain, dataset variant, behavior-policy description if supplied, dataset difficulty category, and whether the behavior policy is narrow, biased, multitask, suboptimal, or non-representable.

2. **Training rule**
   Train only on the fixed offline dataset. No online rollouts, environment interaction, or test-environment feedback may be used for policy learning, model selection, or hyperparameter tuning unless reported as a separate non-offline condition.

3. **Environment and evaluation rule**
   Evaluate learned policies using the specified D4RL simulator-based protocol. Report environment/task version, episode horizon, termination handling, wrappers, number of evaluation episodes, and stochasticity settings where available. If these are not available from the packet, mark them as required missing protocol details.

4. **Metrics**
   Report normalized D4RL score, raw environment return, and, if used, estimated policy value as separate columns. Include the D4RL normalization anchors or definitions for each task/domain. Do not aggregate across heterogeneous domains without showing per-task results.

5. **Baselines**
   Include behavioral cloning and relevant prior offline RL methods, matching the CQL comparison structure where applicable. Document implementation source, tuning budget, selected hyperparameters, and whether each baseline receives the same data, evaluation episodes, and model-selection rules.

6. **Seeds and uncertainty**
   Use at least four seeds for comparability with the CQL D4RL reporting described in the packet. Report mean plus variability, such as standard deviation, standard error, or confidence interval. Keep raw per-seed results.

7. **Ablations and diagnostics**
   For CQL-style claims, include ablations or diagnostics that test the conservative Q-function mechanism: value estimates versus true returns, learned-policy action support, and sensitivity to the conservative regularization strength. Do not infer mechanism from final score alone.

8. **Claim limits**
   State claims as benchmark-specific: “Under the specified D4RL offline training and simulator evaluation protocol...” Avoid claims about real-world deployment, online fine-tuning performance, universal policy quality, or field-wide superiority unless additional evidence is supplied.

9. **Reproducibility package**
   Provide dataset identifiers, code/configs, hyperparameters, seeds, evaluation scripts, normalization code, raw returns, normalized scores, estimated values if used, and per-seed outputs. Missing items should be listed as limitations rather than silently assumed.