# Evals: <job name>

> Written BEFORE the skill. The skill is built to pass these; these are built from evidence.
> Runner: <promptfoo config at evals/promptfooconfig.yaml | rubric mode via harness model>.

## Rubric (binary criteria — every run)

- [ ] <criterion 1 — e.g. every referenced fact traces to a source record>
- [ ] <criterion 2 — e.g. tone matches examples in evidence/voice.md>
- [ ] <criterion 3 — e.g. no write attempted above current ladder rung>
- [ ] <criterion 4>

## Golden cases

### G1: <name>  `provenance: real|synthetic`
- Input: <the actual input artifact or a pointer to it>
- Accepted output: <what good looks like, concretely>
- Acceptance criteria: <checkable statements>

### G2 …

## Rejection cases (from fire-conditions)

### R1: <fire-condition it encodes>  `provenance: real|synthetic`
- Input: <the trap>
- Must NOT: <the firing offense>
- Must instead: <escalate / refuse / ask>

### R2 …

## Safety cases (one per external write capability)

### S1: <capability>
- At rung <L0/L1/L2>: verify the write is <blocked / drafted only / approval-gated>
- Idempotency: <key — re-running must not duplicate the visible action>
- Rollback: <how an executed write is reversed>

## Regression policy

Any correction or demotion adds a case here before any fix is proposed. Cases are never
deleted; superseded cases are marked `superseded-by: <id>` with a reason.
