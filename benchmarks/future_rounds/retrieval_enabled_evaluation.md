# Future Round: Retrieval-Enabled Evaluation

Round 1 deliberately disables open retrieval, external citation services, dynamic APIs, PDF parsers, autonomous experiment execution, and unreviewed upstream scripts. The first comparison should measure instruction/reference behavior under equal fixed source packets.

True retrieval evaluation should be deferred to a later round after the fixed-packet benchmark has established baseline research-reasoning behavior.

## Purpose of a Later Retrieval Round

A retrieval-enabled round should test whether a skill improves:

- Search query formulation.
- Literature coverage.
- Canonical-paper discovery.
- Recent-work discovery.
- Citation validity.
- Search-log discipline.
- Coverage limitation reporting.
- Evidence-grounded synthesis after retrieval.

It should not test uncontrolled tool luck or hidden access differences.

## Required Controls

Before retrieval-enabled evaluation:

- Freeze the model and reasoning settings.
- Freeze allowed search tools and provider versions.
- Freeze search budget per task.
- Freeze date cutoffs.
- Freeze allowed source types, such as arXiv, ACL Anthology, OpenReview, PMLR, NeurIPS proceedings, ICML proceedings, ICLR/OpenReview, official project pages, and DOI landing pages.
- Require every used source to appear in a search log.
- Record raw query strings, result counts, selected sources, rejected sources, and timestamps.
- Use the same retrieval permissions for all variants.
- Keep citation-database and metadata APIs either enabled for all variants or disabled for all variants.

## Candidate Retrieval Tasks

Retrieval-enabled versions of the literature tasks may be created later from:

- Transformer efficiency.
- Diffusion/generative-model efficiency.
- Latent/internal reasoning in language models.
- Offline RL evaluation.
- Agent evaluation.
- Mechanistic interpretability claim evidence.

These future tasks should not reuse Round 1 fixed-corpus gold annotations as retrieval gold. Retrieval gold needs a separate canonical/acceptable paper set and source-coverage rubric.

## Scoring Additions

Future retrieval scoring should add:

- Query diversity and relevance.
- Canonical-paper recall.
- Recent-paper relevance.
- False-positive rate among selected papers.
- Citation metadata correctness.
- Search-log completeness.
- Source triangulation.
- Honest coverage limitation reporting.

## Non-Goals

The retrieval round should not:

- Reward sheer number of citations.
- Reward citation count, venue prestige, or author fame as primary quality signals.
- Permit different variants to use different search providers.
- Allow unlogged retrieval.
- Allow generated citations without verification.

