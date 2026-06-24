# Routing Strategy

## Routing Is a Means, Not the Whole Product

OpenFugu should not only route requests across models. It should orchestrate a
model pool so applications can call it as one intelligent model endpoint.

Routing starts simple, then becomes measurable, then becomes trainable.

## Router Levels

### Level 0: Manual Policy

The user selects a policy such as:

- local-only
- cheapest-good-enough
- best-quality
- code-heavy
- privacy-first
- verify-before-return
- fallback-chain

The router follows explicit rules.

### Level 1: Rule-Based Router

The router uses request classification and worker tags:

- coding request -> coding-capable worker
- private content -> local or internal worker only
- long context -> long-context worker
- low budget -> cheap worker first
- reliability mode -> strong worker or fallback chain

This level is enough for the first gateway prototype.

### Level 2: Eval-Informed Router

The router uses trace and eval history:

- task type performance
- failure rate
- latency distribution
- cost profile
- verifier disagreement rate
- user correction rate

At this level, capability profiles become empirical instead of only hand-written.

### Level 3: Conductor

The conductor can create a multi-step plan:

1. classify task
2. choose solver
3. choose verifier if needed
4. trigger fallback when confidence or output quality is low
5. return final answer with trace

This is closer to the Fugu-style orchestration goal.

## Decision Object

Every routing decision should be structured.

```json
{
  "policy": "privacy_first",
  "eligible_workers": ["qwen3-local", "deepseek-internal"],
  "selected": "qwen3-local",
  "reason": "The active policy disallows external providers and the request matches the local coding profile.",
  "fallback": "deepseek-internal",
  "verification": "none",
  "estimated_cost_usd": 0.0,
  "trace": "full"
}
```

## Trace Requirements

Routing is only trustworthy if the user can inspect it. The trace should record:

- request class
- active policy
- candidate workers
- excluded workers and exclusion reason
- selected worker
- selection reason
- fallback events
- verifier calls
- token usage
- cost estimate
- latency
- final returned worker

## First Useful Router

The first router should be boring and inspectable:

- no hidden model magic
- explicit scoring function
- readable rules
- full trace output
- test fixtures for common request classes

This creates a baseline that future learned routers must beat.

