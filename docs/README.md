# OpenFugu Development Notes

This directory records the current OpenFugu development thinking. It is not a
finished product specification. It is the shared base for deciding what the
open-source main repository should build first.

## Reading Order

1. [Vision and Scope](./01-vision-and-scope.md)
2. [Core Concepts](./02-core-concepts.md)
3. [Architecture Draft](./03-architecture-draft.md)
4. [Routing Strategy](./04-routing-strategy.md)
5. [Evaluation Plan](./05-evaluation-plan.md)
6. [Roadmap](./06-roadmap.md)
7. [Open Questions](./07-open-questions.md)

## Guiding Sentence

OpenFugu is an open, transparent orchestration gateway that turns your own
model pool into one intelligent model endpoint.

## Design Boundary

The early repository should stay focused on:

- worker model registration
- capability description
- policy-controlled routing
- OpenAI-compatible request and response shape
- visible route trace
- evaluation data for improving routing quality

It should avoid drifting into a full chat application, a generic product
template, or a simple provider switcher.
