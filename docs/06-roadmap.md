# Roadmap

This roadmap is intentionally conservative. OpenFugu should prove the
orchestration interface before expanding into a large product surface.

## Phase 0: Public Design Repository

Status: current phase.

Goals:

- publish Apache-2.0 repository
- document core product thesis
- define early architecture
- define routing and trace concepts
- collect open questions and use cases

## Phase 1: Minimal Gateway

Goals:

- OpenAI-compatible chat completions endpoint
- static worker registry
- policy resolver
- rule-based router
- worker client for OpenAI-compatible endpoints
- full route trace for each request

Success:

- existing OpenAI-compatible clients can call OpenFugu
- users can configure at least two workers
- users can see why a worker was selected

## Phase 2: Trace and Eval

Goals:

- trace persistence
- eval fixture format
- fixed-worker baseline runner
- routed-policy runner
- simple report generation

Success:

- one workload shows routed policy improvement over a fixed worker under a
  declared constraint

## Phase 3: Conductor

Goals:

- multi-step routing plan
- verifier role
- fallback chain
- output comparison
- policy-aware plan limits

Success:

- OpenFugu can solve at least one workflow through worker collaboration, not
  only single-worker selection

## Phase 4: Learned Routing

Goals:

- eval-informed capability profiles
- routing features from trace data
- trainable or tunable router
- transparent comparison against rule-based router

Success:

- learned routing improves measurable outcomes without reducing trace
  interpretability

## Deferred Work

- dashboard-heavy UX
- full chat client
- broad provider adapter matrix
