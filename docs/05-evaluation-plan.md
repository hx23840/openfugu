# Evaluation Plan

## Why Eval Matters

Without evaluation, OpenFugu is only a transparent gateway. Useful, but not yet
Fugu-like.

The first serious proof should show that orchestration beats a fixed worker on
at least one real workload under a clear constraint.

## Baselines

Each evaluation should compare:

- fixed cheap model
- fixed strong model
- fixed local model
- manual provider choice
- OpenFugu routed policy

The comparison must include cost, latency, reliability, and quality where
possible.

## Candidate Workloads

### Coding

- bug explanation
- small code edit
- test generation
- refactor suggestion
- repository-aware Q&A

### Chinese and Bilingual Work

- Chinese writing
- English-to-Chinese technical translation
- bilingual summarization
- mixed-language code and docs tasks

### Privacy-Constrained Tasks

- local-only summarization
- internal document Q&A
- private code explanation
- fallback blocked by policy

### Verification Tasks

- cheap draft + strong verifier
- local draft + external verifier when policy allows
- answer comparison across workers

## Metrics

Useful metrics include:

- task success rate
- human preference
- verifier agreement
- cost per successful answer
- latency per successful answer
- fallback frequency
- policy violation rate
- trace explainability

## First Eval Milestone

Create a small repeatable eval set with:

- 20 to 50 real prompts
- 3 to 5 workers
- 2 to 3 policies
- fixed-model baselines
- saved traces
- simple report output

The goal is not benchmark completeness. The goal is to prove that the routing
interface and trace data can support honest comparison.

## Data Flywheel

The long-term loop:

Route logs -> eval labels -> capability profiles -> better routing -> better
traces -> better eval data.

The project should design trace and eval formats early enough that this loop is
not an afterthought.

