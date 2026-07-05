# Portfolio — dollarized plays on the constraint, sequenced, pruned visibly

Input: a completed `DIAGNOSIS.md`. Output: a menu the user picks from — not a list of ideas, a
ranked set of plays with numbers, experiments, and visible pruning.

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
