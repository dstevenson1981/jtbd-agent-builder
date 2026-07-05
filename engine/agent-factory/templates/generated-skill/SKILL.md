---
name: <job-slug>
description: >-
  <Written for triggering: what job this performs, for which outcome, touching which systems,
  and the phrasings a user would actually say. No marketing copy.>
---

# <Job name>

<One paragraph: the job, the metric contract in one line, and where the full contract lives.>

**Contract**: this skill exists to move <metric> by <Δ> within <window>. Contract, evidence and
current autonomy rungs: `JOB.md`, `evals/`, `ladder.json` (same directory). Check `ladder.json`
before every action; never write above the capability's current rung — refuse and propose
promotion instead.

## Workflow

1. <Imperative step — gather inputs from the declared systems>
2. <Imperative step — do the work, referencing evidence/voice/format standards>
3. Self-check against the rubric in `evals/` before producing anything.
4. For each external action: confirm rung in `ladder.json`; at L1 emit a draft, at L2 request
   approval, at L0 log to shadow output only.
5. Record every human correction verbatim in `proposals/inbox.md` — it becomes an eval.

## Escalation

Escalate to a human (do not guess) when: <ambiguity conditions from rejection cases>.

## Improvement

This skill does not edit itself. Misses and corrections follow `IMPROVEMENT.md`: failing eval
first, smallest diff to `proposals/`, human merges.
