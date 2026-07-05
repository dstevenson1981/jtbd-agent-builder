# Packs — domain knowledge, pluggable

The engine is domain-free; packs carry everything domain-specific. New outcome = new pack,
engine untouched. This is the community-contribution surface of the repo.

## Pack contract — four files

| File | Carries |
|---|---|
| `causal-model.md` | the flow template, stage boundaries, constraint smells, reference ranges, motion adjustments, migration map |
| `instrumentation.md` | where the numbers live per stage, techniques when nothing is connected, hard rules on provenance |
| `interventions.md` | the FULL play library with stage/feasibility/birth-rung per play, compounding edges |
| `benchmarks.md` | how to tear down who does this outcome well, and how teardowns become eval criteria |

## Authoring rules

- Write for the sweep: interventions must be enumerable and scoreable, not essays.
- Reference ranges need a stated segment ("B2B services/training defaults") — a range with no
  segment is a vibe.
- Bootstrapped packs (created mid-engagement by the diagnosis protocol) are labeled
  `status: bootstrapped` until validated against a real case.
- Gaps found during real engagements get added to the pack first, then scored — then PR'd
  upstream.

## Wanted

`support-cost` · `hiring-pipeline` · `retention` · `eng-velocity` · `content-ops` ·
`compliance-ops`
