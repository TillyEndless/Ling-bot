## rl_protocol_audit

| Area | Risk | Why it matters | Severity | Required fix |
|---|---|---:|---:|---|
| Dataset coverage | Protocol must explicitly cover dataset regimes: narrow, biased, multitask, suboptimal, and non-representable behavior policies. | D4RL emphasizes these as core offline RL failure modes. Claims based only on easy or narrow subsets would not support broad offline RL conclusions. | High | Stratify results by dataset type and state which regimes each claim covers. |
| Behavior policy assumptions | If the protocol assumes a known, stationary, or representable behavior policy, that is not generally supported. | D4RL includes datasets where behavior policies may be non-representable or difficult to characterize. CQL’s guarantees also depend on stated assumptions. | High | Report what is known about the dataset collection policy, what is assumed, and which methods require behavior-policy modeling. |
| Train/eval separation | Offline training must use only the fixed dataset; simulator interaction is only for final evaluation. | D4RL frames offline RL as training from static datasets, then evaluating learned policies in specified simulators. | Critical | Prohibit online data collection, environment rollouts for training, hyperparameter tuning via online returns, or adaptive evaluation leakage. |
| Environment details | The protocol must identify exact D4RL task/domain names and simulator evaluation conventions. | D4RL normalized scores are task/domain-specific and use reference anchors. Results are not interpretable without task identity and raw return context. | High | Report task names, domains, dataset variants, raw returns, normalized scores, and evaluation procedure. |
| Metrics | Normalized score alone is insufficient. | Source notes distinguish normalized benchmark score, actual environment return, and estimated policy value. CQL Table 4 separately analyzes estimated values and true returns. | Medium | Report raw return, normalized score, and, where relevant, offline value estimates separately. |
| Baselines | Claims require comparison to relevant offline RL baselines and behavioral cloning. | CQL compares against prior offline RL methods and behavioral cloning on D4RL. | High | Include BC and established offline RL baselines; avoid only comparing to online RL or weak baselines. |
| Seeds | Single-seed results are insufficient. | CQL reports D4RL results averaged over four seeds; D4RL appendices include seed-reporting information. | High | Use at least four seeds or justify deviations; report per-seed variability. |
| Uncertainty reporting | Means without uncertainty are weak evidence. | Offline RL results can vary across seeds and datasets. | Medium | Report mean plus standard deviation or confidence intervals across seeds. |
| Offline-to-online claims | Offline benchmark success does not by itself prove online deployment robustness. | D4RL and CQL evaluate fixed datasets with simulator-based evaluation. CQL addresses distributional shift but under assumptions. | Critical | Limit claims to offline training plus simulator evaluation unless additional online evidence is provided. |

## dataset_and_environment_checklist

- List every D4RL task, domain, and dataset variant used.
- Identify whether each dataset is narrow, biased, multitask, suboptimal, or involves a hard-to-represent behavior policy.
- State the fixed dataset size or composition when available from the source packet/protocol.
- Confirm no training-time environment interaction is used.
- Confirm no simulator rollouts are used for replay-buffer expansion, model selection, or early stopping.
- Specify simulator-based evaluation only after training.
- Report normalized scores using D4RL’s task/domain-specific reference anchors.
- Report raw environment returns alongside normalized scores.
- Separate true simulator returns from estimated policy values.
- State all behavior-policy assumptions explicitly.
- Mark claims unsupported if they depend on knowing or representing the behavior policy when the dataset does not provide that support.

## baseline_and_metric_review

The baseline set should include behavioral cloning and prior offline RL methods, because CQL’s D4RL evaluation compares against both. A protocol that only compares against BC is too weak for a new offline RL algorithm claim; a protocol that omits BC misses an important sanity check for whether policy improvement over dataset behavior is actually happening.

The metric set should include:

- D4RL normalized score.
- Raw simulator return.
- Mean over seeds.
- Seed variability, such as standard deviation or confidence intervals.
- Offline estimated policy value only as a separate diagnostic, not as a replacement for simulator return.

CQL’s conservative-value analysis separates estimated policy values from true returns. The revised protocol should preserve that distinction because offline value estimates can be misleading under action distribution shift.

## claim_scope_assessment

Supported claims, if the revised protocol is followed:

- The method improves offline RL performance on the specified D4RL tasks under fixed-dataset training.
- The method performs better than listed baselines on normalized D4RL scores and raw simulator returns, averaged over reported seeds.
- The method is more or less robust across specific dataset regimes, if results are stratified by D4RL dataset property.

Weak or unsupported claims under the provided protocol unless extra evidence is added:

- Broad superiority across offline RL as a whole.
- Robustness to arbitrary behavior policies.
- Safe deployment in online environments.
- Reliable off-policy evaluation without simulator evaluation.
- General mitigation of distributional shift beyond the tested datasets and stated assumptions.
- Online fine-tuning performance, unless online interaction experiments are separately run and clearly labeled.

## revised_protocol

1. Define scope  
   State that the study evaluates offline RL algorithms trained only on fixed D4RL datasets and evaluated using D4RL simulator-based returns and normalized-score conventions.

2. Select datasets deliberately  
   Include tasks spanning D4RL’s documented offline RL challenges: narrow data, biased data, multitask data, suboptimal data, and non-representable behavior-policy settings. Report results separately by domain and dataset type.

3. Lock train/eval separation  
   Train only on the static dataset. Do not use environment interaction, online rollouts, or simulator returns for training-data augmentation. If hyperparameters are tuned, describe the tuning source and prevent test-task leakage.

4. Document behavior-policy assumptions  
   For each dataset, state what is known and unknown about the behavior policy. Mark whether the evaluated algorithm assumes behavior-policy access, behavior-policy representability, coverage, or support overlap.

5. Evaluation procedure  
   Evaluate the final learned policy in the specified D4RL simulator setting. Report both raw environment return and D4RL normalized score. Keep estimated policy value separate from actual simulator return.

6. Baselines  
   Compare against behavioral cloning and established offline RL baselines used in the D4RL/CQL evaluation context. If CQL is the proposed method, compare to prior offline RL methods and BC; if another method is proposed, include CQL as a strong offline RL baseline.

7. Seeds and uncertainty  
   Run at least four random seeds, matching CQL’s D4RL reporting convention. Report mean and variability across seeds for every task and aggregate.

8. Reporting format  
   Provide per-task tables with task name, dataset variant, raw return, normalized score, seed count, uncertainty, and baseline comparisons. Add aggregate summaries only after per-task results.

9. Conservative-value diagnostics  
   If the method claims improved value estimation or reduced overestimation, include a diagnostic like CQL’s comparison of estimated policy values versus true returns. Do not use estimated values alone as final performance evidence.

10. Claim boundaries  
   Limit conclusions to fixed-dataset offline RL performance on the evaluated D4RL tasks. Any claim about online deployment, online fine-tuning, or general real-world safety must be labeled out of scope unless backed by additional experiments outside this protocol.