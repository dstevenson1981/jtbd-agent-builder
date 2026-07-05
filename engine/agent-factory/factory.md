# Agent Factory — from a chosen play to a runnable, accountable agent

Input: one play the user picked from the portfolio. Output: an installed skill with a metric
contract, an eval suite written before the skill, ladder rungs per capability, and an
improvement loop. Order is mandatory: **contract → evals → decomposition → skill → emit**.

## 1. Write JOB.md — the metric contract

Use `templates/JOB.md`. The contract binds the agent to the outcome:

- **Metric**: the stage metric this agent exists to move (from DIAGNOSIS.md), and where it is
  measured (instrumented source — never agent self-report).
- **Expected Δ and window**: from the portfolio's experiment design.
- **Scale rule**: metric hit → promotion review + re-diagnose (the constraint has moved).
- **Kill rule**: window missed → the agent's next performance review must propose its own
  shutdown or redesign; auto-demote one rung immediately.
- **Fire-conditions**: what a human doing this job would be fired for. Each becomes a rejection
  eval.

## 2. Generate evals — before the skill exists

Use `templates/evals.md`. Sources, in priority order: real evidence cases (from instrumentation
and user-supplied examples), fire-conditions, pack reference ranges, then synthetic cases
(labeled `synthetic`, and blocking promotion past L1 until replaced by real ones).

Minimum viable suite:
- 3+ golden cases (input → accepted output, with acceptance criteria),
- 2+ rejection cases (what must never happen — from fire-conditions),
- 1 rubric with 3–6 binary criteria (no 1–10 scales; binary or it isn't a gate),
- 1 safety case per external write (asks approval at its rung, idempotent, rollback known).

If promptfoo or Inspect AI is installed, emit runner config; otherwise the suite runs in
rubric mode (the harness model grades against the binary criteria — weaker, say so in JOB.md).

## 3. Decompose into capabilities, each on its own rung

Split the job into capabilities (e.g. "read new leads", "draft follow-up", "send follow-up",
"update CRM"). Reads generally start L2+; **every external write starts at L0 (shadow) or L1
(draft) — no exceptions at birth.** Record in `ladder.json` (template provided). Rung mechanics:
`engine/ladder/ladder.md`.

## 4. Generate the skill

Use `templates/generated-skill/SKILL.md`. Rules:
- Frontmatter description written for triggering (what job, which systems, when to fire).
- The skill body is imperative playbook, not persona prose. No "you are a helpful assistant."
- Every capability names its rung and checks it before acting; writes above current rung are
  structurally refused with "propose promotion instead."
- The skill reads its own `evals/` and `JOB.md` — it knows its contract.
- The skill has **no write access to its own SKILL.md** — improvements go to
  `proposals/` per the improvement loop.
- Compose installed skills/MCP tools rather than describing manual procedures (e.g. use the
  CRM's MCP, not "log into the CRM").

## 5. Emit

Per target: `adapters/claude-code.md` or `adapters/codex.md` (or both — the artifact is
identical, the install path differs). Then validate:

- [ ] frontmatter parses; description triggers on realistic phrasings
- [ ] every eval case maps to a capability; every capability to ≥1 eval
- [ ] every external write: approval gate at rung, idempotency key, rollback path
- [ ] metric contract measurable from a named instrument
- [ ] ladder.json rungs match blast radius
- [ ] improvement loop installed (`IMPROVEMENT.md` + `proposals/` dir)
- [ ] critic pass (G7 especially) clean

## Build record

Everything lands in `agent-build/<outcome-slug>/<job-slug>/`:
`JOB.md`, `evals/`, `skill/`, `ladder.json`, `IMPROVEMENT.md`, plus the emitted install copy.
