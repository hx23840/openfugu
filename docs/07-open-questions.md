# Open Questions

## Product Questions

- Who is the first user: individual developer, AI power user, small team, or
  internal platform team?
- Which first workload best proves orchestration value?
- Is the strongest pain cost, privacy, quality, latency, reliability, or
  transparency?
- Should the first user experience be config-file-first, CLI-first, or
  lightweight local service first?
- Which traces should be visible by default, and which should require explicit
  opt-in because they may contain sensitive content?

## Technical Questions

- What is the minimal OpenAI-compatible surface for the first gateway?
- Should policies live in YAML, JSON, TOML, or code?
- What trace format is stable enough to keep across versions?
- How should OpenFugu represent provider-specific features without making the
  core interface provider-specific?
- How should local-only policy enforcement be tested?
- How should fallback avoid unexpected cost or privacy leaks?
- What is the smallest useful router scoring function?

## Eval Questions

- Which tasks are realistic enough for early proof?
- How should human preference be captured?
- Can verifier disagreement be used as a routing signal?
- What does "better than fixed worker" mean for each workload?
- How should traces be anonymized for shared eval data?

## Community Questions

- Should OpenFugu maintain official worker profiles?
- Should users share policy recipes?
- Should eval datasets live in the main repo or separate repos?
- What contribution format makes routing-policy proposals easy to review?

