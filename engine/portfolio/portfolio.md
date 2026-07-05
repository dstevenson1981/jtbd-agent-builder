# Portfolio — dollarized plays on the constraint, sequenced, pruned visibly

Input: a completed `DIAGNOSIS.md`. Output: a menu the user picks from — not a list of ideas, a
ranked set of plays with numbers, experiments, and visible pruning.

## 0. Gather external evidence — mandatory, before any scoring

Internal data says where the system leaks; only external evidence says what actually moves
needles. A portfolio built from the model's general knowledge is an armchair strategy (critic
G10). Before scoring, produce and cite:

1. **Live product/site read** — what the business actually sells, at what prices, with what
   capture and offer architecture, TODAY (not from stale code or memory).
2. **Market demand check** — where demand in this space is growing/shrinking right now
   (web research; cite sources and dates).
3. **Benchmark teardown** — per the pack's `benchmarks.md`: who is winning at the constraint
   stage, and what their machine observably does.

Every recommended play must trace to at least one of: an internal measurement, or an external
evidence artifact. Plays supported by neither are labeled `speculative` and cannot be
recommended — only deferred pending evidence.

## 1. Sweep the full intervention library

Load the pack's `interventions.md` and score **every** entry. Never generate interventions ad
hoc — ad hoc generation is how things get silently missed. If during the sweep you notice a play
the library lacks, add it to the pack (that's a pack improvement, PR-able), then score it.

Score each intervention:

| Field | Meaning |
|---|---|
| `expected Δ` | movement in outcome units (dollars/hours/days), with arithmetic shown |
| `confidence` | high / medium / low, with the assumption that most moves the number |
| `time-to-value` | days until the metric plausibly moves |
| `agent-feasibility` | agent-able today / agent drafts + human executes / human-only |
| `starting rung` | L0–L4 per `engine/ladder/ladder.md`, driven by blast radius of a mistake |
| `on-constraint?` | does it act on the binding constraint, or a different stage? |
| `compounds with` | which other plays it feeds (content → outbound personalization → retargeting) |

## 2. Rank and prune — nothing disappears silently

- **Recommend**: on-constraint, agent-able, best Δ × confidence / time-to-value. Usually 2–4
  plays. More than 4 is a focus failure.
- **Defer with trigger**: good plays that are off-constraint. Every deferral states *which
  cleared constraint deploys it*: "LinkedIn outbound: high fit, deferred — it feeds a funnel
  that currently wastes 78% of what it catches. Deploys when follow-up conversion clears 40%."
- **Prune with reason**: infeasible or poor-fit plays, one line each. The user must be able to
  scan what was considered and overrule ("actually we have a Sales Nav seat").

## 3. Design the disconfirming experiment

Every recommended play ships with the test that would prove the causal claim wrong:

```markdown
## Experiment: <play>
- Claim: <this play moves metric M by Δ>
- Test: <smallest real-world trial — e.g. agent works 30 days of leads at L1 draft rung>
- Window: <days>
- Disconfirmed if: <threshold — e.g. contacted-lead close rate not above baseline>
- If disconfirmed: <kill / redesign / re-diagnose — the diagnosis may be wrong>
```

## 3b. Bridge to the target — the plan must reach the number

Levers multiply. Show the bridge arithmetic explicitly:

```
target: +75% in 90 days
bridge: C2 offer architecture (×1.20) × C3 mix shift to team deals (×1.25)
        × C1 flow recovery (×1.10) × C4 new-demand product push (×1.10) ≈ ×1.82  ✓ (slack: 7pp)
```

Rules:
- If the recommended plays don't bridge to the target, say so in the first paragraph — do not
  present a portfolio that silently under-delivers (critic G11).
- Each bridge factor carries its confidence and its evidence pointer.
- Anything with time-to-value longer than the window is excluded from the bridge (it can still
  be deferred-with-trigger for after).

## 4. Sequence for compounding

Prefer plays whose outputs feed each other. State the dependency order explicitly. A portfolio
of isolated agents is linear; a portfolio where the content agent's output becomes the outbound
agent's personalization corpus compounds.

## 5. Present the menu

One document, in this order: the diagnosis in three sentences with the dollarized constraint →
recommended plays with numbers and experiments → deferred plays with triggers → pruned plays
with reasons → the 0–3 questions whose answers would re-rank the board (only if such questions
genuinely exist). Then stop and let the user pick. Their reactions — including "we tried that,
it flopped" — get recorded in `agent-build/<outcome-slug>/EVIDENCE.md` with provenance `user`.

Run the critic before presenting.
