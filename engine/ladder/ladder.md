# Autonomy Ladder — graduated trust, earned with evidence

Replacing a job is an employment decision, not a deployment. Every capability of every agent
sits on a rung. Trust is earned per capability, never granted per agent.

## Rungs

| Rung | Name | The agent... | A human... |
|---|---|---|---|
| L0 | Shadow | produces output; nothing leaves | does the job; outputs compared |
| L1 | Draft | drafts the artifact | sends/executes it |
| L2 | Gated | executes | approves each write beforehand |
| L3 | Batched | executes | reviews a digest; can roll back |
| L4 | Autonomous | executes | audits the log |

Birth rungs: reads may start L2+; **external writes start L0 or L1, no exceptions.** Blast
radius decides: a mistaken CRM field update is L1-born; a mistaken customer email is L0-born.

## Promotion

A capability moves up one rung when ALL of:
1. N consecutive clean eval passes at the current rung (default N=10 runs or 2 weeks,
   whichever is longer; set per capability in ladder.json),
2. zero unresolved corrections at this rung,
3. synthetic evals replaced by real cases (required past L1),
4. explicit human sign-off, recorded with date in ladder.json.

Promotion is proposed by the agent in its performance review — never self-executed.

## Demotion — automatic, no sign-off needed

- A regression eval fails → down one rung immediately.
- A metric-contract window is missed → down one rung; next review must propose shutdown or
  redesign.
- A human reverts/corrects an executed write → down one rung for that capability + a new
  rejection eval from the correction.

Demotion is logged, visible, and not shameful — it is the system working.

## Performance review

On "how is my agent doing", on schedule, or after any demotion:
1. Run the eval suite; compare metric contract vs. instrumented actuals (never self-report).
2. Summarize: rung per capability, eval trend, metric trend, corrections since last review.
3. Propose: promotions (with evidence), demotions already taken, improvement proposals pending.
4. If the metric contract was HIT: recommend re-diagnosis — the constraint has moved, and the
   portfolio's deferred plays may now unlock.

## ladder.json

Template at `engine/agent-factory/templates/ladder.json`. It is the single source of truth for
current rungs; the generated skill checks it before every action and refuses writes above its
rung with "propose promotion instead."
