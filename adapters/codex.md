# Adapter — Codex

## Installing a generated agent

The artifact is identical to the Claude Code one — SKILL.md frontmatter (`name`, `description`)
is compatible across both harnesses. Only the install path differs:

1. Copy the built directory to:
   - user-scoped: `~/.codex/skills/<job-slug>/`
   - project-scoped: `<project>/.codex/skills/<job-slug>/`
2. If the project uses `AGENTS.md`, add a one-line pointer so discovery is explicit:
   `See .codex/skills/<job-slug>/SKILL.md for the <job> agent.`
3. Smoke test in a Codex session the same way: realistic phrasing, fires correctly, refuses
   writes above rung.

## Differences to respect

- No Claude-style hooks: rung enforcement is instruction-level plus the structural guard (the
  skill has no write access to its own files). Flag this in JOB.md as a known weaker guarantee.
- Scheduled/hosted execution: Codex has no CMA equivalent — jobs on a clock run via the user's
  own scheduler (cron, CI) invoking `codex exec` non-interactively.
- Verify against the current Codex skills docs when emitting — the format is young and moves:
  https://developers.openai.com/codex/skills
