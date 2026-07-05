# JOB: <job name>

> Built by jtbd-agent-builder on <date> from diagnosis `agent-build/<outcome-slug>/DIAGNOSIS.md`.

## Outcome served

<the one-sentence outcome this job exists to move>

## Metric contract

- **Metric**: <stage metric, e.g. "captured-lead → paid conversion">
- **Baseline**: <value, period, source>
- **Expected Δ**: <target movement> within <window, days>
- **Measured by**: <instrumented source — GA4 / Stripe / CRM report — never agent self-report>
- **Scale rule**: metric hit → promotion review + re-diagnose the outcome (constraint moved)
- **Kill rule**: window missed → auto-demote one rung; next review proposes shutdown or redesign

## Fire-conditions

What a human in this job would be fired for. Each maps to a rejection eval in `evals/`.

1. <e.g. contacting a lead who opted out>
2. <e.g. quoting a wrong price>
3. <e.g. letting a hot lead sit >24h without escalation>

## Capabilities and birth rungs

| Capability | Type | Birth rung | Blast radius of a mistake |
|---|---|---|---|
| <read leads> | read | L2 | none |
| <draft follow-up> | create | L1 | internal only |
| <send follow-up> | external write | L0 | customer-visible |

## Systems

| System | Role | Access today | Contract |
|---|---|---|---|
| <CRM> | source of truth for leads | <MCP / export / none> | <link or "deferred"> |

## Evidence basis

- Real cases: <count, source>
- Synthetic cases: <count — block promotion past L1 until replaced>
- User-provided corrections incorporated: <count>
