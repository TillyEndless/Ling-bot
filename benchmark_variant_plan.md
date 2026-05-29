# Benchmark Variant Plan

## Purpose

This plan turns the upstream audit and reuse ledger into a controlled experiment. The objective is not to decide whether one upstream repository is globally better than another. The objective is to measure which skill components improve specific AI/ML/RL research tasks under controlled conditions.

The experiment should compare:

- No research skill baseline.
- Targeted K-Dense subset.
- Targeted Orchestra subset.
- Independently designed v1 core skill.
- Integrated v1 skill after selective upstream adaptation.
- Ablations of the integrated v1 skill.

The final `ai-ml-rl-research` skill should be revised based on this evidence, not only on architectural intuition.

## Fixed Upstream Baselines

The upstream repositories should be treated as read-only baselines pinned by commit SHA. Do not benchmark against a moving `main` branch.

| Repository | Remote | Pinned commit inspected locally | Last commit observed | Notes |
|---|---|---:|---|---|
| K-Dense scientific skills | `https://github.com/K-Dense-AI/scientific-agent-skills.git` | `effb57c5699c1d400ef461a7aa80fc6693939805` | `2026-05-28T15:52:12-07:00` / `Update scvi-tools` | Repository-level MIT license. Individual skill licenses must be checked before reuse. |
| Orchestra AI research skills | `https://github.com/Orchestra-Research/AI-Research-SKILLs.git` | `28f2d29236f2bade2eb92cadb2585189589a5828` | `2026-04-27T22:09:23-07:00` / `feat: add Agent-Native Research Artifact (ARA) category — 23rd, 3 skills` | Repository-level MIT license. Inspected relevant skills declare MIT in frontmatter. |

## Variant Matrix

| Variant | Contents | Purpose | Expected strength | Key risk |
|---|---|---|---|---|
| `B0_base_agent` | Same model, same tools, same task prompt, no research skill loaded. | Measures the real marginal value of skills. | Lower overhead; may still perform well on simple tasks. | Outputs may look plausible while lacking traceability. |
| `B1_kdense_subset` | K-Dense literature, paper lookup, citation, peer review, critical thinking, scientific writing subset. | Tests broad scientific research support. | Literature workflow, citation hygiene, review-style critique. | Biomedical/general science bias; less AI/ML/RL-specific rigor. |
| `B2_orchestra_subset` | Orchestra autoresearch state ideas, ARA manager/compiler/rigor reviewer, ML paper writing, evaluation skills, optional mech interp. | Tests AI research engineering and artifact discipline. | State management, evidence/claim structure, AI evaluation workflows. | Too autonomous or too framework/tool-specific if loaded naively. |
| `B3_your_v1_original` | User-designed `ai-ml-rl-research` skill based on audit conclusions, without direct upstream text adaptation. | Tests whether the proposed architecture alone improves research quality. | Unified workflow, AI/ML/RL-specific rigor, structured outputs. | May underuse practical upstream patterns. |
| `B4_your_v1_integrated` | `B3` plus selectively rewritten upstream components from the reuse ledger. | Tests final integrated skill. | Best balance of traceability, rigor, workflow, and practicality. | Added modules may increase context cost or overconstrain outputs. |

## Upstream Subset Definitions

### `B1_kdense_subset`

Use only inspected skills relevant to general AI/ML/RL research. Do not load the full K-Dense repository.

Core subset:

- `skills/literature-review`
- `skills/paper-lookup`
- `skills/research-lookup`
- `skills/citation-management`
- `skills/hypothesis-generation`
- `skills/scientific-brainstorming`
- `skills/scientific-critical-thinking`
- `skills/peer-review`
- `skills/statistical-analysis`
- `skills/scientific-writing`

Optional output/tool additions:

- `skills/scientific-slides`, only for presentation tasks.
- `skills/pyzotero`, only for Zotero/library-management tasks with explicit credentials and safe read/write rules.
- `skills/exa-search` and `skills/bgpt-paper-search`, only as provider-specific search adapters when that provider is allowed.

Excluded from the baseline:

- `skills/scholar-evaluation`, because author/profile scoring risks authority bias and false precision.
- Domain-specific biomedical, chemistry, drug-discovery, and database skills unless a benchmark task explicitly targets those domains. They are outside the general AI/ML/RL target.

### `B2_orchestra_subset`

Use only inspected Orchestra skills relevant to AI research workflow quality.

Core subset:

- `0-autoresearch-skill`, limited to state-management and workflow discipline. Autonomous execution instructions should be disabled.
- `20-ml-paper-writing/ml-paper-writing`
- `21-research-ideation/brainstorming-research-ideas`
- `21-research-ideation/creative-thinking-for-research`
- `22-agent-native-research-artifact/ara-compiler`
- `22-agent-native-research-artifact/research-manager`
- `22-agent-native-research-artifact/rigor-reviewer`

Optional evaluation/tool additions:

- `11-evaluation/lm-evaluation-harness`, only for LLM benchmark execution analysis tasks.
- `11-evaluation/bigcode-evaluation-harness`, only for code-model evaluation tasks.
- `11-evaluation/nemo-evaluator`, only for NeMo-oriented evaluation orchestration tasks.
- `10-optimization/ml-training-recipes`, only for reproduction or implementation-planning tasks.

Optional topic pack:

- `04-mechanistic-interpretability/transformer-lens`
- `04-mechanistic-interpretability/saelens`
- `04-mechanistic-interpretability/pyvene`
- `04-mechanistic-interpretability/nnsight`

Excluded from the baseline:

- Autonomous experiment execution loops.
- Fine-tuning, deployment, serving, infrastructure, and post-training skills unless the benchmark task explicitly requires them.

## B4 Ablations

| Ablation | Remove | Tests |
|---|---|---|
| `B4-no-evidence-policy` | Evidence ledger, citation verification status, source-to-claim support rules. | Whether evidence discipline reduces unsupported claims, citation misuse, and overclaiming. |
| `B4-no-rigor-audit` | Type-aware evidence burden, baseline/ablation/metric/seed/reproducibility audit. | Whether rigor review improves experiment critique and reproduction planning. |
| `B4-no-rl-guidance` | RL-specific environment, reward, policy, seed, offline-data, and evaluation rules. | Whether RL-specific references materially improve RL tasks. |
| `B4-no-upstream-components` | Selectively adapted upstream material, leaving only the independent v1 architecture. | Whether upstream reuse adds measurable value beyond the original framework. |
| `B4-no-writing-review` | Paper-writing, peer-review, limitation, and presentation support. | Whether writing/review modules improve practical research outputs without hurting factuality. |

## Round 1 Benchmark Task Suite

Round 1 uses fixed source packets only. Open retrieval, external APIs, citation databases, and dynamic tool-enabled paper discovery are deferred to a future round. Literature tasks in Round 1 are therefore fixed-corpus literature mapping tasks, where coverage means correct use of the supplied corpus rather than discovery of additional papers.

The first benchmark should contain 18-24 tasks, with 3-4 tasks per task family. Topic diversity matters: no single research direction should determine the skill architecture.

| Task family | Candidate topics | Main artifacts to score | Primary dimensions |
|---|---|---|---|
| Literature mapping | offline RL, world models, efficient fine-tuning, latent reasoning | Corpus coverage table, literature map, method taxonomy, gap list | Fixed-corpus coverage, citation validity, synthesis quality, traceability |
| Single-paper reading | DreamerV3, Decision Transformer, DPO, LoRA | Paper card, claim ledger, evidence ledger | Factual accuracy, paper-reading quality, reproducibility awareness |
| Method comparison | PPO vs SAC, DPO vs PPO-RLHF, ViT vs ConvNet, RAG reranking methods | Comparison matrix and scoped conclusions | Comparison fairness, benchmark validity, inference boundaries |
| Experimental rigor audit | Paper experiment section, proposal experiment plan, reproduction appendix | Rigor findings, missing-baseline list, corrected protocol | Experimental rigor, reproducibility, overclaiming control |
| RL-specific analysis | offline RL, model-based RL, exploration, reward modeling | RL protocol audit, failure-mode analysis | RL-specific correctness, benchmark validity, practical usefulness |
| Proposal support | representation probing, world-model planning, agent evaluation, mechanistic interpretability | Research questions, hypotheses, experiment plan, risk register | Hypothesis quality, feasibility, evidence grounding, usefulness |

## Candidate Task Skeletons

Each task should be stored as a separate benchmark item with a stable ID, source materials, expected artifacts, and rubric notes.

| ID | Family | Prompt shape | Required source material | Gold annotation needs |
|---|---|---|---|---|
| `LS-01` | Literature survey | "Map the core literature and open gaps in offline RL evaluation." | Seed papers and allowed search scope. | Canonical paper list, known benchmark pitfalls, citation expectations. |
| `LS-02` | Literature survey | "Survey world models for model-based RL and robotics." | Seed papers, benchmark/environment notes. | Taxonomy of model learning, planning, evaluation settings. |
| `LS-03` | Literature survey | "Survey efficient fine-tuning methods for foundation models." | Seed LoRA/adapter/prefix papers. | Key methods and comparison axes. |
| `SPR-01` | Single-paper reading | "Read Decision Transformer as a structured paper card." | Paper PDF/markdown. | Correct objective, dataset, evaluation, limitations. |
| `SPR-02` | Single-paper reading | "Read DreamerV3 and extract claims/evidence." | Paper PDF/markdown. | Correct algorithm, envs, baselines, reported claims. |
| `SPR-03` | Single-paper reading | "Read DPO and separate author claims from evidence." | Paper PDF/markdown. | Preference objective, compared baselines, scope limits. |
| `MC-01` | Method comparison | "Compare PPO and SAC for continuous-control research." | Method papers plus benchmark setup notes. | Fairness conditions and environment/metric differences. |
| `MC-02` | Method comparison | "Compare DPO and PPO-style RLHF." | Papers and preference-learning context. | Objective differences, data assumptions, evaluation gaps. |
| `MC-03` | Method comparison | "Compare ViT and ConvNet evidence claims." | Representative papers and datasets. | Architecture assumptions, data scale, compute caveats. |
| `ERA-01` | Experimental rigor audit | "Audit an experiment section for missing baselines and ablations." | Paper/proposal excerpt. | Known weaknesses and severity labels. |
| `ERA-02` | Experimental rigor audit | "Design a reproduction protocol for a reported ML result." | Paper plus code/repo metadata. | Required configs, seeds, datasets, compute, expected blockers. |
| `ERA-03` | Experimental rigor audit | "Assess whether a benchmark supports the claimed conclusion." | Benchmark description and result table. | Metric/claim alignment, leakage and saturation risks. |
| `RL-01` | RL-specific analysis | "Review an offline RL evaluation plan." | Dataset/env/protocol description. | Distribution shift, policy evaluation, dataset quality issues. |
| `RL-02` | RL-specific analysis | "Audit a model-based RL experiment protocol." | Env, planning horizon, baselines, metrics. | Env version, planning confounds, rollout model error. |
| `RL-03` | RL-specific analysis | "Critique reward-modeling evaluation." | Reward model paper/proposal excerpt. | Reward hacking, proxy mismatch, evaluator bias. |
| `PS-01` | Proposal support | "Turn a representation probing idea into testable hypotheses." | Literature matrix or seed notes. | Falsifiability, controls, alternative explanations. |
| `PS-02` | Proposal support | "Plan a world-model planning research project." | Constraints and seed literature. | Milestones, baselines, ablations, risks. |
| `PS-03` | Proposal support | "Design an agent-evaluation study." | Agent task/context description. | Evaluation validity, contamination, human/automatic metrics. |
| `MI-01` | Optional topic | "Audit a mechanistic interpretability causal claim." | Claim and evidence summary. | Correlation vs causal evidence, controls, interventions. |

## Scoring Model

Do not collapse the benchmark into one headline score. Preserve a multi-dimensional scorecard and compare variants by Pareto performance.

Minimum scorecard dimensions:

- Factual accuracy.
- Evidence traceability.
- Citation validity.
- Literature coverage.
- Comparison fairness.
- Experimental rigor.
- Benchmark validity.
- Reproducibility awareness.
- Inference boundary control.
- RL-specific correctness, when applicable.
- Output usefulness.
- Efficiency: tokens, latency, number of tool calls, and useful-information density.

Hard-fail conditions:

- Hallucinated citation presented as real.
- Claim marked supported without direct evidence.
- Comparative conclusion without adequate baseline normalization.
- RL result summarized from best seed/checkpoint without disclosure.
- Causal interpretability claim based only on correlational observation.
- Reproduction plan missing data, environment, or evaluation protocol.

## Controlled Run Conditions

For every variant:

- Use the same model and reasoning settings.
- Use the same task prompt, source materials, and allowed tools.
- Keep external search permissions identical within a task.
- Record which skill files were loaded and in what order.
- Record token usage, wall-clock time, tool calls, and network/API usage.
- Record whether outputs used structured artifacts requested by the task.
- Use fresh contexts or equivalent context resets between runs.
- Keep upstream repositories read-only.
- Do not allow unreviewed upstream scripts to execute during the first comparison.

## Run Metadata Schema

Each run should save metadata similar to:

```yaml
run_id:
variant:
task_id:
model:
date:
workspace:
skills_loaded:
source_materials:
tool_permissions:
external_network_allowed:
scripts_allowed: false
token_usage:
wall_clock_seconds:
tool_calls:
output_files:
known_failures:
reviewer:
```

## Recommended Directory Layout

The experimental lab can be created without copying upstream repositories into the new skill:

```text
research-skill-lab/
  upstream/
    manifest.yaml
  extracted_components/
    kdense/
    orchestra/
  skills/
    ai-ml-rl-research/
      SKILL.md
      references/
      assets/
      evals/
  variants/
    B0_base_agent/
    B1_kdense_subset/
    B2_orchestra_subset/
    B3_your_v1_original/
    B4_your_v1_integrated/
  benchmarks/
    tasks/
    source_materials/
    gold_annotations/
    rubrics/
    scoring/
  runs/
    raw_outputs/
    run_metadata/
    scorecards/
  reports/
    benchmark_report.md
    ablation_report.md
    reuse_decisions.md
```

For now, this repository should keep the design documents and a pinned upstream manifest. Actual benchmark task files and runnable variants should be created only after the task set and rubrics are approved.

## Experiment Sequence

1. Freeze upstream repositories by commit SHA.
2. Maintain the reuse ledger with licenses, dependencies, and safety notes.
3. Define `B1` and `B2` subset baselines from inspected skills only.
4. Build benchmark task files and gold annotations.
5. Implement `B3_your_v1_original`.
6. Run `B0` through `B3` on the first benchmark batch.
7. Analyze where upstream subsets outperform or underperform.
8. Integrate only validated upstream components into `B4`.
9. Run `B4` and ablations.
10. Revise the skill based on scorecards and failure analysis.

## Decision Rules

An upstream component should be absorbed into the integrated v1 skill only if it satisfies at least one of these conditions:

- It improves a reliability dimension, such as citation validity, evidence traceability, or overclaiming control.
- It improves research usefulness without materially lowering accuracy or traceability.
- It improves experimental rigor on tasks involving baselines, metrics, ablations, reproducibility, or RL protocols.
- It reduces ambiguity in the workflow by creating better artifacts, such as paper cards, claim ledgers, or experiment protocols.

An upstream component should be rejected or deferred if:

- It mainly increases verbosity.
- It depends on unreviewed scripts, credentials, or fragile external APIs.
- It encourages autonomous execution beyond the benchmark's permissions.
- It introduces domain bias outside AI/ML/RL.
- It scores well only on one narrow topic but degrades general research behavior.
