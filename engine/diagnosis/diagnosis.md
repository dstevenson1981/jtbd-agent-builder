# Diagnosis — size the ambition, model the flow, instrument it, find the constraint

The outcome is not a menu of tactics. It is a system with one binding constraint. Your job here
is to find it with real numbers, so the portfolio step puts force where the physics says, not
where enthusiasm says.

## 0. Size the ambition — magnitude + deadline select the lever class

"Grow revenue" and "grow revenue 75% in 90 days" are different problems with different valid
answers. Before modeling anything, establish the target Δ and window:

- If the user stated them, record them.
- If not, do NOT ask another question — propose a default ("I'll plan for a meaningful move:
  +20% within a quarter") and let them correct it. Corrections are free; questions are not.

Then classify the gap against the **lever classes** (domain-free; packs map them to concrete
plays):

| Class | What it changes | Typical ceiling |
|---|---|---|
| C1 Tune the flow | stage conversions toward reference ranges | low double digits % |
| C2 Change unit value | price/packaging/offer architecture, cost per unit | 10–30% |
| C3 Change the mix | shift toward higher-value segments/deals/jobs | large, step-change |
| C4 Add flows | new products, channels, or sources built on existing assets | large, slower |
| C5 Structural | partnerships, capacity, business-model changes | largest, slowest |

**Eligibility rule**: estimate the ceiling of C1 alone (sum of realistic stage improvements).
If the target exceeds it, C2/C3 levers are MANDATORY in the portfolio and the diagnosis must
say so explicitly — recommending only flow-tuning against a step-change target is critic
violation G11. If the target exceeds what any lever stack can plausibly bridge in the window,
say that plainly, with arithmetic, and offer the largest honest plan.

## 1. Model the flow

Every business outcome is a flow through stages:

```
Outcome value = volume × stage-conversion(s) × unit value × frequency
```

Examples of the shape (packs carry the full templates):

| Outcome | Flow |
|---|---|
| Revenue | attention → interest → pipeline → close → repeat/referral |
| Support cost | tickets in → triage → resolution → satisfaction → deflection |
| Hiring | sourcing → screen → interview → offer → accept → ramp |
| Retention | activation → habit → expansion → renewal |
| Eng velocity | idea → PR → review → deploy → incident |

Load the matching pack's `causal-model.md` and adapt the template to THIS business (their
motion, price points, sales cycle, team size). If no pack exists:

**Bootstrap protocol** — derive the flow from first principles: (a) who has the money/value,
(b) how does it move toward the outcome, (c) what are the observable stage boundaries,
(d) what is the unit value at the end. Write the result as a draft `packs/<outcome>/` so the
next engagement starts warmer. Label it `status: bootstrapped — validate against a real case`.

## 2. Instrument — read before you ask

Inventory what is connectable or readable **right now**: MCP servers, CLIs (`gh`, `psql`,
`sqlite3`), analytics, payment processors, CRMs, email platforms, exports, spreadsheets, the
website itself, the repo. The pack's `instrumentation.md` lists the usual sources per stage.

Fill the stage table with real numbers:

```markdown
| Stage | Metric | Value | Period | Source | Provenance |
|---|---|---|---|---|---|
| Attention | site visits | 4,200/mo | last 90d | GA4 | measured |
| Interest | leads captured | 80/mo (1.9%) | last 90d | form + ESP | measured |
| Pipeline | qualified convos | unknown | — | none found | GAP |
| Close | purchases | 18/mo (22% of leads) | last 90d | Stripe | measured |
| Value | ACV | $1,190 | last 90d | Stripe | measured |
| Repeat | repeat rate | ~0 | 12mo | Stripe | measured |
```

Rules:
- **Provenance on every number**: `measured` / `estimated` (state basis) / `assumed` (state why)
  / `GAP`.
- A `GAP` is a finding, not a blocker — "you cannot see your own pipeline stage" is often the
  first intervention.
- Asking the user for a number you could measure is forbidden. Asking them to grant access to a
  source is allowed and encouraged.
- If truly nothing is connectable, run the diagnosis on estimates, label every number `assumed`,
  and make "instrument the funnel" the mandatory first play in the portfolio.

## 3. Find the binding constraint

For each stage, compute the marginal value of improvement:

```
Δ outcome if this stage improves by a realistic step (e.g. +50% relative), holding others fixed
```

The binding constraint is the stage with the highest Δ **that is actually addressable**. Sanity
checks before you commit to it:

- **Leak check**: a stage converting far below the pack's reference range beats a volume play.
  Feeding more traffic into a funnel that wastes 78% of captured interest burns money.
- **Ceiling check**: is the stage near its natural ceiling (close rate already 40%+)? Then it is
  not the constraint no matter how important it feels.
- **Sequencing check**: fixing this stage — does it expose the next constraint immediately?
  Note what the constraint will migrate to. This becomes `NEXT.md`.

## 4. Dollarize

State the constraint's cost in outcome units:

> "Your constraint is mid-funnel follow-up. 80 leads/mo × 78% never contacted × 22% baseline
> close × $1,190 = **~$16.4k/mo left on the table** (confidence: medium — close rate on
> contacted leads assumed equal to overall)."

Show the arithmetic. State confidence and which assumption moves the number most.

## 5. Output

Write `agent-build/<outcome-slug>/DIAGNOSIS.md`: the flow model, the instrumented stage table
with provenance, the constraint with dollarized cost and arithmetic, the migration prediction,
and any GAPs found. Then run the critic (`engine/critic/intern-detector.md`) before showing the
user anything.
