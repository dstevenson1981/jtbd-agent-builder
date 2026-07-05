# Revenue Growth — instrumentation playbook

Read before asking. Sources per stage, in the order to try them:

| Stage | Sources (try in order) |
|---|---|
| Attention | GA4/analytics MCP · Search Console · social/LinkedIn analytics · server logs · SEO tools already installed |
| Capture | form backend · ESP list growth (Mailchimp/ConvertKit) · CRM lead creation dates · site code (find the forms, count the paths) |
| Contact | CRM activity timestamps · sent-mail folders · ESP campaign logs — **compute lead-created → first-touch lag** |
| Qualify | CRM stage history · calendar booking tool · call recordings/transcripts |
| Close | Stripe/payment processor (ground truth for money) · invoicing · CRM closed-won |
| Value | payment processor line items · product/SKU mix |
| Repeat/referral | payment processor repeat customers · "how did you hear" fields · coupon attribution |

Techniques when nothing is connected via MCP:
- Site itself is an instrument: crawl it — count capture points, offers, proof elements,
  checkout friction. The repo is an instrument if the site is in one.
- Exports beat interviews: ask for a CSV export ("Stripe payments last 12mo") — one grant of
  access replaces twenty questions.
- Triangulate: list size ÷ months active ≈ capture rate; published cohort dates × seat price ×
  plausible fill ≈ revenue ceiling.

Compute and record (all with provenance):
1. the full stage table, last 90 days
2. lead-created → first-touch lag distribution (the Contact smoking gun)
3. revenue concentration by source (which channel actually pays today)
4. GAPs — every stage you cannot see is itself a finding and often the first play

Hard rule: money numbers come from the payment processor, not the CRM, not memory.
