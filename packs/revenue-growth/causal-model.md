# Revenue Growth — causal model

`status: v1 — validated shape, refine reference ranges with real engagements`

## The flow

```
Revenue/mo = Attention × capture% × contact% × qualify% × close% × ACV × (1 + repeat & referral)
             ─────────   ────────────────────────────────────────   ────   ──────────────────
             top          mid-funnel (where most SMB revenue dies)   value   the ignored multiplier
```

Stages, observable boundaries, and where constraints hide:

| Stage | Boundary metric | Constraint smell |
|---|---|---|
| Attention | visits / impressions / profile views | low volume AND downstream stages healthy |
| Capture | visitor → identified lead % | traffic fine, list not growing (offer/form problem) |
| Contact | lead → actually-worked % | leads captured then never touched — **the most common SMB constraint and the most agent-able** |
| Qualify | worked → real-opportunity % | lots of touches, few conversations (targeting/message) |
| Close | opportunity → paid % | conversations happen, money doesn't (offer/pricing/proof/urgency) |
| Value | ACV / AOV | closing fine but small (packaging, upsell paths absent) |
| Repeat & referral | repeat rate, referral rate | one-and-done customers; near-zero here is free money |

## Motion adjustments

- **High-ticket B2B** (>$5k, sales-led): weight Contact/Qualify; cycle time is a hidden stage —
  measure days-in-stage, not just conversion.
- **Volume B2C / self-serve**: weight Capture/Close (page conversion, cart/checkout
  abandonment); Contact may not exist as a human stage.
- **Training/course businesses** (cohort-dated inventory): urgency is structural — empty-seat
  cost per cohort date is the dollarization unit; abandoned-registration recovery is a
  first-class stage.

## Reference ranges (for the leak check — B2B services/training defaults)

capture 1.5–4% · contact ≥90% within 24h (best-in-class: minutes) · qualify 30–50% ·
close 20–35% of qualified · repeat+referral ≥20% of revenue. A stage far below range beats any
volume play — flag it as candidate constraint before scoring anything.

## Constraint migration map

contact fixed → qualify or attention becomes binding · attention fixed → capture ·
close fixed → value/repeat. Write the predicted migration into NEXT.md at diagnosis time.
