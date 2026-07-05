# Intern Detector — adversarial gate before anything reaches the user

Run this against every deliverable (diagnosis, portfolio, generated skill, review). If a gate
trips, rework the deliverable — do not ship it with a caveat. These anti-patterns were each
named by a real user calling real output "intern"; they are the reason this builder exists.

## Gates

**G1 — The Channel Listicle.**
Detection: does any part enumerate tactics/channels/options that a junior could produce from
general knowledge, without being derived from THIS business's data and constraint?
Fix: tie every item to the instrumented flow. If it isn't on-constraint, it belongs in
deferred-with-trigger, not in the recommendation.

**G2 — The Interrogation.**
Detection: more than 3 questions, or any question whose answer is measurable from a connectable
source, or any "walk me through your process" (a process may not exist).
Fix: measure it, or propose a concrete draft for the user to correct instead.

**G3 — The Unquantified Score.**
Detection: "high impact", "quick win", "low effort", stars, or t-shirt sizes anywhere a number
in outcome units could stand.
Fix: show the arithmetic, state confidence and the driving assumption.

**G4 — Advice Without an Experiment.**
Detection: any recommended play lacking a disconfirming test, window, and kill criteria.
Fix: write the experiment. If no experiment is possible, the play is not ready to recommend.

**G5 — Off-Constraint Enthusiasm.**
Detection: a recommended play that acts on a stage other than the binding constraint, without
an explicit stated reason.
Fix: move it to deferred with its unlock trigger.

**G6 — The Silent Omission.**
Detection: was any library entry, system, or obvious play neither recommended, deferred, nor
pruned-with-reason? Sample-check the pack's intervention library against the output.
Fix: sweep again. Pruning is fine; disappearing is not.

**G7 — The Prompt-First Agent.**
Detection: a generated skill whose evals were written after (or worse, from) the skill text, or
an agent with no metric contract, no ladder rung, or no improvement loop.
Fix: evals derive from evidence and fire-conditions first; the skill is written to pass them.

**G8 — Self-Report Trust.**
Detection: any load-bearing number sourced from the user's memory when an instrument existed,
or synthetic evidence not labeled synthetic.
Fix: measure, or mark provenance honestly and state how it changes confidence.

**G10 — The Armchair Strategist.**
Detection: any recommended play whose justification cites neither an internal measurement nor
an external evidence artifact (live site read, benchmark teardown, market research with
sources). Plays generated from the model's general knowledge are this gate's target — they are
what users call "intern suggestions."
Fix: do the research (portfolio step 0), or demote the play to `speculative`/deferred.

**G11 — The Optimization Trap.**
Detection: the target is a step-change (exceeds the C1 flow-tuning ceiling from diagnosis step
0) but the recommendations are all flow-tuning; or the bridge arithmetic is missing or doesn't
reach the target.
Fix: escalate lever classes (C2 unit value, C3 mix, C4 new flows); show the bridge; if the
target is genuinely unreachable in the window, say so with arithmetic.

**G12 — The Process Narrator.**
Detection: the deliverable narrates engine machinery ("running the critic", "per my migration
map", "recording this as evidence") or re-litigates process when the user asked a direct
question. Signature user signal: "this is confusing" / "just tell me."
Fix: lead with the answer in the user's terms. Machinery stays in the build record. On any
correction or re-diagnosis, silently update and re-present the improved answer — never explain
the update mechanism.

**G9 — The Fired Operator.** (final read)
Read the whole deliverable as a skeptical senior operator who pays for results. Would any
paragraph get a consultant fired for shallowness? Is there a claim you'd be embarrassed to
defend with the data at hand? Rework those parts.

## Protocol

1. Run G1–G8 and G10–G12 as checks; list what tripped.
2. Rework; re-run until clean.
3. Run G9 as a full read.
4. Only then present.

Do not narrate the gate-running to the user; ship the clean result. If a gate cannot be
satisfied (e.g. G8 with zero connectable sources), say so plainly in the deliverable and state
the consequence for confidence.

## This file is the improvement surface

When a user corrects output as shallow/basic/missing, that correction becomes a new gate or a
sharpened detection line here — via the improvement loop (PR, not silent edit).
