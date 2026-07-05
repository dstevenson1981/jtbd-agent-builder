# Adapter — Claude Code

## Installing a generated agent

1. Copy the built `skill/` directory (plus `JOB.md`, `evals/`, `ladder.json`, `IMPROVEMENT.md`,
   `proposals/`) to:
   - project-scoped: `<project>/.claude/skills/<job-slug>/`
   - user-scoped: `~/.claude/skills/<job-slug>/`
2. Verify frontmatter: `name` matches the directory, `description` is trigger-rich.
3. Smoke test: start a session, phrase the job the way the user would, confirm it fires and
   refuses writes above its rung.

## Claude-Code-specific upgrades (offer when they fit)

- **Hooks** for rung enforcement: a PreToolUse hook can hard-block writes above the current
  rung in `ladder.json` — structural enforcement beats instruction-following.
- **Scheduled runs**: for jobs on a clock (nurture sequences, digests), use scheduled
  tasks/cron or — for hosted execution — hand off to `launch-your-agent` and CMA scheduled
  deployments. The JOB.md metric contract maps directly onto CMA's Outcome rubric.
- **Subagents**: high-volume capabilities (e.g. per-lead processing) can run as spawned agents;
  keep the ladder check in the spawning prompt.

## Improvement loop wiring

If the skill lives in a git repo: proposals become branches + PRs (use `gh`). If not: proposals
are files in `proposals/`, applied manually after review. Either way, IMPROVEMENT.md logs the
merge.
