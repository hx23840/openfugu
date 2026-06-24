# Core Concepts

## Model Pool

The model pool is the set of workers OpenFugu can call. A pool can include:

- local models
- self-hosted inference servers
- company-internal models
- hosted open-source models
- proprietary model APIs
- OpenAI-compatible third-party endpoints

The pool belongs to the user or team. OpenFugu should make the pool explicit
instead of hiding it inside a vendor.

## Worker

A worker is one callable model endpoint. It may be a single model, a wrapper
around a provider API, or a local inference service.

Example:

```yaml
workers:
  - id: qwen3-coder-local
    provider: llama.cpp
    endpoint: http://localhost:8101/v1
    tags: [coding, local, private, cheap]
    context_window: 32768
    privacy: local
    cost: low
    latency: low

  - id: frontier-verifier
    provider: external
    endpoint: https://api.example.com/v1
    tags: [reasoning, verifier, expensive]
    privacy: external
    cost: high
    latency: medium
```

## Capability Profile

A capability profile describes when a worker is useful. It should include
objective data where possible and human labels where needed.

Possible fields:

- task tags
- language strengths
- coding strengths
- context window
- tool calling support
- structured output support
- cost class
- latency profile
- privacy level
- reliability history
- eval scores

## Policy

A policy constrains what the router is allowed to do.

Example:

```yaml
policies:
  default:
    mode: balanced
    allow_external: true
    max_cost_usd: 0.20
    trace: full

  private:
    allow_external: false
    require_local: true
    trace: full

  verify_before_return:
    first_pass: cheap
    verifier: strong
    trace: full
```

## Router

A router selects a worker for a request. The first router can be rule-based.
Later routers can use eval data, learned capability profiles, or a conductor
model.

A router must emit a decision object, not just a model name.

```json
{
  "selected": "qwen3-coder-local",
  "reason": "The request is a coding task and the active policy prefers local workers when capability is sufficient.",
  "fallback": "frontier-verifier",
  "estimated_cost_usd": 0.03,
  "trace_level": "full"
}
```

## Conductor

A conductor is a higher-level router that can plan multi-step execution:

- classify the task
- select a solver
- call a verifier
- trigger fallback
- combine worker outputs
- decide whether to return or retry

The conductor is where OpenFugu becomes more than provider selection.

## Trace

A trace explains what happened during orchestration.

Trace fields should answer:

- What policy was active?
- Which workers were eligible?
- Which worker was selected?
- Why was it selected?
- Did fallback happen?
- Did verification happen?
- What was the token, cost, and latency profile?
- Which output was returned?

## Eval

Eval data measures whether routing improves outcomes. Without eval, routing is
only a product story. With eval, OpenFugu can learn which workers are good for
which tasks under which constraints.

