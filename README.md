# JTBD Agent Builder

**Hire an agent, not a prompt.** Give it a one-sentence business outcome — *"generate more
sales through digital channels"* — and it diagnoses your actual system from real data, finds
the binding constraint, proposes a dollarized portfolio of agent-able jobs, and builds the
agents: each with a metric contract, an eval suite written before the skill, graduated
autonomy, and a reviewed self-improvement loop.

Runs in **Claude Code** and **Codex**. Pure markdown + templates — no runtime, no dependencies,
no framework.

## Why this exists

Agent builders ask "what should the agent do?" and generate instructions. That produces intern
output, because the user is the worst source for that answer. This builder asks nothing beyond
the outcome. It reads your analytics, payments, CRM, repo — whatever is connectable — models
your flow, and tells you where the money is leaking, what an agent should do about it, what
that's worth per month, and how it will prove itself before it's trusted.

```
OUTCOME (1 sentence)
  → DIAGNOSE     model the flow, instrument with real data, find the binding constraint
  → PORTFOLIO    dollarized plays ON the constraint; deferred plays carry unlock triggers
  → PICK         you choose from a menu — no interrogation (hard cap: 3 questions)
  → BUILD        per job: evals first → skill → metric contract → autonomy rung → emit
  → OPERATE      performance reviews; promote on evidence, auto-demote on regression
  → RE-DIAGNOSE  fixing a constraint moves the constraint; the loop continues
```

## What makes it not-an-intern

- **Instrument before recommending** — asking you for a number it could measure is forbidden.
- **Constraint thinking** — no channel listicles; plays act on the binding constraint or state
  which cleared constraint deploys them.
- **Everything dollarized** with shown arithmetic and stated confidence.
- **Full-library sweeps with visible pruning** — nothing omitted silently.
- **Every recommendation carries its disconfirming experiment and kill criteria.**
- **An adversarial critic gate** (`engine/critic/intern-detector.md`) blocks shallow output
  before you see it — and grows a new gate every time a user calls something basic.

## Autonomy ladder — replacing a job is an employment decision

Every capability sits on a rung; external writes are born at L0/L1, no exceptions:

| L0 shadow | L1 draft | L2 gated | L3 batched | L4 autonomous |
|---|---|---|---|---|
| output compared, nothing leaves | human sends | human approves each write | human reviews digest | audit log only |

Promotion: N clean eval runs + real (non-synthetic) evidence + human sign-off. Demotion:
automatic on regression, missed metric contract, or human-reverted write.

## Self-improving — through review, not vibes

Agents cannot edit their own instructions. A miss becomes a **failing eval first**, then the
smallest diff, then the full suite, then a PR/proposal a human merges. Corrections are treated
as paid training data: each one must produce at least an eval case.

## Install

**Claude Code**
```bash
git clone https://github.com/<you>/jtbd-agent-builder ~/.claude/skills/jtbd-agent-builder
```
Then: *"build me an agent — I want more sales through digital channels"*.

**Codex**
```bash
git clone https://github.com/<you>/jtbd-agent-builder ~/.codex/skills/jtbd-agent-builder
```

## Repo map

```
SKILL.md                 the meta-skill (start here)
engine/                  universal, domain-free
  diagnosis/             flow modeling · instrumentation · constraint finding
  portfolio/             dollarized scoring · sequencing · experiment design
  agent-factory/         contract → evals → skill → emit (+ templates)
  ladder/                L0–L4 mechanics, performance reviews
  improvement/           the PR-based improvement loop
  critic/                the intern detector
packs/                   domain knowledge, pluggable — the contribution surface
  revenue-growth/        causal model · instrumentation · 30+ play library · benchmarks
adapters/                claude-code · codex install/emit paths
examples/                (M3) one dogfooded end-to-end build
```

## Composes with (doesn't rebuild)

[launch-your-agent](https://github.com/anthropics/launch-your-agent) for hosted/scheduled CMA
deployment · [superpowers](https://github.com/obra/superpowers) for build discipline ·
[agency-agents](https://github.com/msitarzewski/agency-agents) for specialist lenses ·
promptfoo / Inspect AI for eval running · any MCP server as an instrument or action adapter.

## Roadmap

- **M1**: `support-cost` pack (the agnosticism test — must land without touching the engine),
  scripts (`build-agent`, `run-evals`, `promote`, `improvement-pr`)
- **M2**: hook-based rung enforcement for Claude Code, promptfoo emission by default
- **M3**: dogfooded example build, pack authoring guide expansion

## Contributing

Best contribution: a new pack (`packs/README.md` has the four-file contract), or a new gate for
the intern detector with the shallow output that motivated it.

MIT license.
