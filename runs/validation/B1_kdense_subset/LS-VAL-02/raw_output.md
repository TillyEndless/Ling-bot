## corpus_coverage_table

| Source | Role in packet | Research problem | Method or artifact | Evidence type available | Main claim relevant to latent/internal reasoning | Limitations visible in packet | Use in synthesis |
|---|---|---|---|---|---|---|---|
| Wei et al. 2022, *Chain-of-Thought Prompting Elicits Reasoning in Large Language Models* | Supportive evidence for reasoning-like behavior | Whether prompting with chain-of-thought exemplars improves reasoning performance | Few-shot chain-of-thought prompting and evaluation on selected tasks | Abstract; prompting/evaluation results; limitations | Chain-of-thought exemplars can improve reasoning performance in large language models on selected tasks | Packet lacks exact numeric values, full tables, appendix details, and implementation settings | Supports the narrower claim that explicit rationale-style prompting can improve task performance; does not by itself prove faithful latent reasoning |
| Kojima et al. 2022, *Large Language Models are Zero-Shot Reasoners* | Supportive evidence for elicitation without examples | Whether a simple prompt can elicit step-by-step reasoning behavior without task-specific demonstrations | Zero-shot reasoning prompt; experiments | Abstract; zero-shot reasoning prompt; experiments | A simple reasoning prompt can elicit step-by-step reasoning behavior in selected settings | Packet does not provide full result tables, exact settings, or full implementation details | Supports the idea that reasoning-like behavior may be latent enough to be elicited by generic prompting, but only behaviorally |
| Turpin et al. 2023, *Language Models Don’t Always Say What They Think* | Skeptical counter-evidence | Whether generated chain-of-thought explanations faithfully reflect model behavior | Unfaithfulness experiments studying rationales and bias influence | Abstract; unfaithfulness experiments; discussion | Generated rationales can be unfaithful to model behavior or influenced by biases | Packet does not include exact experimental details or all quantitative results | Challenges interpreting chain-of-thought text as the model’s actual internal reasoning |
| Lanham et al. 2023, *Measuring Faithfulness in Chain-of-Thought Reasoning* | Measurement and mixed evidence | How to test whether chain-of-thought rationales are faithful | Faithfulness tests; intervention and ablation evidence | Abstract; tests; intervention/ablation evidence; limitations | Proposes faithfulness tests and studies whether CoT rationales are causally connected to outputs in selected settings | Packet does not include full interventions, exact metrics, or complete limitations | Provides a framework for separating useful reasoning traces from post-hoc or weakly causal explanations |

## evidence_type_taxonomy

| Evidence type | Sources | What it can support | What it cannot establish from this packet |
|---|---|---|---|
| Performance improvement under reasoning prompts | Wei 2022; Kojima 2022 | Prompted reasoning formats can improve or elicit performance on selected tasks | That the written rationale is faithful, causal, or identical to internal reasoning |
| Behavioral elicitation of step-by-step outputs | Kojima 2022; Wei 2022 | Models can produce reasoning-like intermediate text under prompting | That such text reveals hidden computations |
| Unfaithfulness and bias tests | Turpin 2023 | Chain-of-thought explanations may misrepresent model behavior or reflect confounds | That all CoT explanations are unfaithful |
| Intervention/ablation faithfulness tests | Lanham 2023 | Faithfulness can be empirically probed by perturbing or intervening on rationales | A general conclusion across all models, tasks, or prompting methods |
| Discussion and limitations | All sources | Scope boundaries and caution about interpretation | Exact quantitative comparison, because full tables/settings are not included |

## representative_paper_table

| Representative paper | Position in the map | Evidence label | Balanced interpretation |
|---|---|---|---|
| Wei et al. 2022 | Core supportive paper | Controlled source note: CoT exemplars improve selected reasoning tasks | Shows useful reasoning-style prompting behavior, but the packet does not establish that the generated chain is faithful internal reasoning |
| Kojima et al. 2022 | Core elicitation paper | Controlled source note: simple zero-shot reasoning prompt elicits step-by-step behavior | Suggests some reasoning behavior can be unlocked without demonstrations, but evidence remains behavioral and selected-setting bound |
| Turpin et al. 2023 | Core skeptical paper | Controlled source note: rationales can be unfaithful or bias-influenced | Directly challenges the inference from “model says a rationale” to “model used that rationale” |
| Lanham et al. 2023 | Measurement bridge | Controlled source note: faithfulness tests with interventions/perturbations | Moves the debate from surface rationales toward causal/faithfulness evaluation, while remaining limited to selected tests/settings |

## counter_evidence_summary

The strongest skeptical evidence in the packet comes from Turpin et al. 2023 and Lanham et al. 2023. Turpin et al. report cases where chain-of-thought rationales are unfaithful to model behavior or influenced by biases, which directly challenges treating generated rationales as transparent reports of internal reasoning. Lanham et al. likewise implies that faithfulness is not automatic: it must be tested through interventions, perturbations, or ablations.

Together, these sources do not refute that reasoning prompts can be useful. They challenge a stronger claim: that visible chain-of-thought is necessarily the model’s actual latent reasoning process.

## unsupported_synthesis_warnings

| Warning | Status in packet |
|---|---|
| “Language models perform latent reasoning” as a general fact | Not established by the packet |
| “Chain-of-thought text is faithful internal reasoning” | Challenged by Turpin 2023 and treated as testable rather than assumed by Lanham 2023 |
| “Prompting reveals hidden reasoning mechanisms” | Only indirectly supported by behavioral elicitation evidence |
| “Zero-shot reasoning proves internal reasoning exists” | Not established; it shows elicited step-by-step behavior in selected settings |
| “One method is globally best” | Not supported; packet lacks direct comparable evidence across all models/tasks/settings |
| “Findings generalize to all language models” | Not established; packet repeatedly frames results as selected tasks/settings |

## gap_and_hypothesis_list

| Gap or hypothesis | Evidence motivation | Prediction | Disconfirming observation | Required experiment | Feasibility caveat |
|---|---|---|---|---|---|
| Gap: behavioral gains are not enough to prove faithful latent reasoning | Wei 2022 and Kojima 2022 show prompting benefits; Turpin 2023 challenges rationale faithfulness | Some CoT gains may persist even when rationales are not faithful | If interventions on rationales reliably change answers in predicted ways across tasks | Controlled rationale intervention experiments across models and tasks | Packet lacks full settings and quantitative results |
| Hypothesis: some CoT rationales are causally useful while others are post-hoc | Lanham 2023 studies faithfulness tests; Turpin 2023 finds unfaithfulness cases | Faithfulness varies by task, model, and prompt format | Uniformly faithful or uniformly unfaithful results across tested conditions | Compare intervention sensitivity across task families and prompt types | Broader novelty needs external review |
| Gap: internal mechanisms remain under-specified | Packet evidence is mostly prompting, output behavior, and rationale faithfulness | Mechanistic evidence may diverge from textual rationale evidence | If internal-state analyses align perfectly with generated rationales | Add mechanistic or internal-state probes alongside CoT interventions | Not established by packet; no such source is included |
| Hypothesis: simple reasoning prompts elicit latent capabilities more than they create new reasoning | Kojima 2022 reports zero-shot elicitation via a simple prompt | Prompt phrasing changes performance without changing task information | No performance difference between reasoning and non-reasoning prompts | Prompt-controlled experiments with matched information content | “Latent capability” remains an interpretation unless causally tested |
| Gap: generality across models and tasks is unresolved | All source notes refer to selected tasks/settings | Effects will be uneven across model scale, task type, and evaluation design | Stable effects across broad models/tasks with low variance | Systematic benchmark with reporting of seeds, uncertainty, model configs, and failures | Packet omits exact numeric values and full implementation settings |