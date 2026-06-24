# OpenFugu

OpenFugu is an open-source, transparent multi-model orchestration gateway.

OpenFugu turns a user-owned model pool into one OpenAI-compatible intelligent
model endpoint. The goal is not to build another chat UI, model downloader, or
provider switcher. The goal is to make model selection, fallback, verification,
and multi-step collaboration visible, configurable, and measurable.

## Current Status

This repository is at the development-idea and architecture-design stage.
The first public content is documentation: product direction, core concepts,
architecture draft, routing strategy, evaluation plan, and roadmap.

Production gateway code will be added after the design boundaries are clear.

## Core Idea

Many users already use multiple models:

- local models through llama.cpp, Ollama, LM Studio, or vLLM
- hosted open-source models
- frontier proprietary models
- internal company models
- OpenAI-compatible third-party endpoints

Today, the choice of model is usually manual, hidden inside one vendor, or
reduced to a simple provider switch. OpenFugu treats the model pool as a
runtime system. A router or conductor decides which worker should handle each
request, why it was selected, whether a verifier is needed, and how fallback
should happen under the user's policy.

## What OpenFugu Is

- An OpenAI-compatible gateway over a user-controlled model pool.
- A transparent worker capability registry.
- A policy layer for privacy, cost, latency, quality, and provider constraints.
- A router or conductor that can select, verify, and fall back across workers.
- A trace and evaluation system for understanding routing quality.
- A future data flywheel for improving model orchestration.

## What OpenFugu Is Not

- Not a chatbot.
- Not a local-model-only product.
- Not an OpenRouter clone.
- Not a model downloader.
- Not a black-box Fugu API clone.
- Not merely a provider switcher.

## Documentation

Start here:

1. [Development Notes](./docs/README.md)
2. [Vision and Scope](./docs/01-vision-and-scope.md)
3. [Core Concepts](./docs/02-core-concepts.md)
4. [Architecture Draft](./docs/03-architecture-draft.md)
5. [Routing Strategy](./docs/04-routing-strategy.md)
6. [Evaluation Plan](./docs/05-evaluation-plan.md)
7. [Roadmap](./docs/06-roadmap.md)
8. [Open Questions](./docs/07-open-questions.md)

## License

OpenFugu is licensed under the [Apache License 2.0](./LICENSE).
