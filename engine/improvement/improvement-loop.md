# Improvement Loop — self-improving through review, not vibes

Generated agents improve through a visible, gated cycle. The mechanism is structural: the agent
has no write access to its own SKILL.md, evals, or ladder.json — only to `proposals/`.

## The cycle

```
1. MISS OBSERVED     a correction, a failed eval, a missed metric, a new case
2. EVAL FIRST        write the failing eval that captures the miss (TDD for agents)
3. SMALLEST CHANGE   propose the minimal diff to skill/reference/template that passes it
4. FULL SUITE        run all evals — the fix must not regress anything
5. REVIEWED DIFF     open a PR (if the skill lives in git) or write proposals/<date>-<slug>.md
                     with the exact diff + the new eval + suite results
6. HUMAN MERGES      approval applies the change; ladder.json updated if rungs are affected
7. LOGGED            one line in IMPROVEMENT.md: date, trigger, change, eval added
```

## What each signal may change

| Signal | May change |
|---|---|
| Human correction of output | rejection eval, rubric criterion, skill instruction |
| Failed eval | skill instruction, tool choice, reference doc |
| Missed metric contract | redesign proposal or shutdown proposal (ladder.md) |
| New real-world case | golden/edge eval; replaces a synthetic case |
| System contract change | integration contract, adapter step, write policy |
| "That's basic/shallow" feedback on the BUILDER itself | new gate in engine/critic/intern-detector.md |

## Never allowed

- Silent edits to skill text, evals, rubric, or ladder.
- Tool/permission expansion inside an improvement diff (that is a promotion, use the ladder).
- Deleting or weakening an eval to make a change pass. Weakening requires its own proposal with
  the reason stated.
- Promotion bundled into a fix. One proposal, one concern.
- Memory/eval storage of secrets or unredacted customer data.

## Corrections are the fuel

Every human correction is treated as paid training data: it MUST produce at least an eval case,
and at most a proposal. A correction that produces nothing is a dropped signal — the review
step checks for this.
