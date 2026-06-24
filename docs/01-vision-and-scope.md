# Vision and Scope

## Vision

OpenFugu should make a heterogeneous model pool behave like one intelligent
model endpoint.

The user owns the pool. The pool may include local models, hosted open-source
models, proprietary frontier models, internal services, and any
OpenAI-compatible endpoint.

OpenFugu sits between the application and those workers. It decides, under a
visible policy, which worker or set of workers should handle each request.

## Why This Exists

Current multi-model usage is fragmented:

- Users manually choose a model per task.
- Applications hard-code one provider or model.
- Provider routers are often opaque.
- Cost, privacy, latency, quality, and reliability tradeoffs are difficult to
  inspect.
- Fallback and verification logic is repeated across applications.

OpenFugu should turn these decisions into a reusable orchestration layer.

## Product Thesis

Model pool + orchestration strategy = a new model interface.

The important unit is not a single model name. The important unit is an
OpenAI-compatible endpoint backed by a transparent model pool, policy layer,
router, trace, and eval loop.

## First-Phase Scope

The first implementation should prove a narrow but complete path:

1. Register several worker models.
2. Describe their capabilities and constraints.
3. Accept an OpenAI-compatible chat completion request.
4. Apply a policy.
5. Route the request to one or more workers.
6. Return an OpenAI-compatible response.
7. Record a route trace explaining the decision.
8. Compare routed output against fixed-model baselines.

## Non-Goals

OpenFugu should not start as:

- a chat UI
- a local model downloader
- a generic agent framework
- a black-box router API
- a simple provider switch

Those features may be adjacent later, but they are not the core.

## Success Criterion

The first serious proof is:

OpenFugu orchestration beats a fixed worker on at least one real workload under
a clear policy constraint.

Examples:

- similar quality at lower cost
- better privacy under local-first policy
- better reliability through fallback
- better answer quality through verifier routing
- better latency through task-aware routing
