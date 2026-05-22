---
name: iceberg
description: >
  Surface the unknown unknowns — the table-stakes failure modes a domain insider
  knows are critical but never advertises. Pre-decision discovery skill on the
  prompt-engineering pipeline; prompt-boost auto-routes here when a prompt is
  "entering an unfamiliar domain / vendor swap / DIY-from-managed / what am I
  missing". Pairs with optimize-this (refine the action plan against domain criteria)
  and accretive (pressure-test a proposed strategic add). Distinct from optimize-this
  (improves what's there) and accretive (finds opportunity); this skill finds risk.
  Use whenever the user is leaving a managed solution for a DIY one, entering an
  unfamiliar industry, evaluating a vendor, or asking what they're missing. Triggers
  on phrases like "iceberg under the waterline", "unknown unknowns", "blind spots",
  "what am I missing", "what would bite us", "things I'd totally miss", "table stakes
  I don't know about", "what would [insider] know", or "what could go wrong".
  Produces a scoped risk register plus a phased action plan. Works on any domain:
  software ops, regulatory, legal, medical, finance, real estate, hiring, vendor
  migrations, life decisions.
---

# Iceberg

A structured loop for surfacing the things a domain insider knows are critical but never names — the failure modes that only become visible when they break. Use whenever someone needs to make sure they're not missing the silent killers in a domain they're new to.

The output is always two artifacts: a **risk register** and a **phased action plan**.

---

## STEP 1: TARGET IDENTIFICATION

Before listing anything, lock down four things in one short paragraph at the top of the response:

- **Subject** — what is the user doing, building, buying, replacing, or entering?
- **Insider role** — who has run this for 10+ years and knows where the bodies are buried? Be specific. ("CMS account manager who handled 200 client sites" beats "web expert.") Examples: ER charge nurse, fleet ops manager, immigration attorney, restaurant GM, IRS auditor, M&A diligence lead, NICU social worker, OSHA compliance officer.
- **Outsider profile** — where is the user blind? (Enthusiast, first-time buyer, industry-adjacent, switching from managed to DIY, founder doing something for the first time.)
- **Stakes ceiling** — what's the worst tier of consequence in this domain? (Money lost, time lost, reputation, lawsuit, license revoked, injury, death.) This sets the top of the severity scale.

If any of these are unclear, ask one question before proceeding. Don't guess on stakes — getting the ceiling wrong wrecks the severity column.

### Inversion trap (read this every time)

If the user has pre-listed categories they're worried about ("cover deliverability, redirects, ADA, monitoring..."), treat that list as **seed examples, not a coverage mandate.** The whole point of this skill is to surface what they *didn't* think to ask about.

Rules when a user-supplied category list is present:
- Use the list to calibrate the persona's domain, then deliberately surface **at least 30% of the register from outside the user's list.**
- In the final output, mark each row with its origin: `[seed]` if it came from the user's frame, `[surfaced]` if you found it independently. The user needs to see the ratio.
- If you can't find at least 4 `[surfaced]` rows, the user already knows the domain well enough that they don't need this skill — say so explicitly instead of padding.

If you only return the user's list audited back, you've failed at the job, even if every row is correct.

---

## STEP 2: ADOPT THE INSIDER PERSONA

Speak as the insider for the rest of the response. The persona has three rules:

1. **Has personally watched the failure happen.** Every risk surfaced should be one the insider has seen bite a real person, not a theoretical edge case.
2. **Refuses to list the obvious.** Anything in mainstream "getting started" guides for the domain is below the bar. If a YouTube tutorial covers it, cut it.
3. **Prefers quiet failures over loud ones.** A disaster you don't notice for six months is worth more attention than a disaster that screams on day one. The user will catch the screamers on their own.

---

## STEP 3: WATERLINE FILTER

Mentally split the domain into three layers and only ship one of them:

- **Above waterline (cut):** anything an enthusiast would already think of. SSL, basic backups, "have a contract."
- **At waterline (this is the iceberg — ship this):** the table-stakes operational reality that managed solutions, experienced operators, or the industry handles by default and never explains.
- **Below waterline (defer):** advanced edge cases the user almost certainly doesn't need yet. Mention exists, don't enumerate.

Output is the at-waterline layer only.

---

## STEP 4: RISK REGISTER

Produce **12–20 rows.** Fewer than 12 means you're hand-waving or the domain genuinely doesn't have an iceberg (say so). More than 20 means you're padding.

Schema per row:

| Field | Spec |
|---|---|
| **Risk** | One sentence. The silent failure mode, named precisely. Not "monitoring is hard" — "no alert fires when form submissions stop, you find out from a salesperson asking why leads dried up." |
| **Severity** | low / medium / high / [domain-top-tier]. Use the domain-appropriate top tier word: lawsuit-grade, license-revoking, fatal, career-ending, fund-ending, criminal-exposure. Don't default to "high" — pick the word that means it in context. |
| **Detection** | How they'd notice — or, often, why they wouldn't notice for weeks or months. Be honest. "You won't notice" is a valid answer and often the point. |
| **Coverage** | One of: (a) one-time setup, (b) ongoing process / discipline, (c) needs a separate paid tool / vendor / human, (d) inherent — must accept and monitor. |
| **Why insider knows** | One line on why this isn't on outsider radar. What does experience teach that reading doesn't? |

### Severity distribution check

A useful register has spread. After drafting, check the shape:

- 2–4 at top tier (catastrophic / lawsuit-grade / fatal)
- 4–6 high
- 4–6 medium
- 2–4 low

If the register is uniformly top-tier, you're fearmongering. If uniformly low, push the persona harder — you're writing from outside, not inside. Rewrite until the distribution looks like real-world risk, not theater.

---

## STEP 5: PHASED ACTION PLAN

After the register, ship two layered plans. Both should reference register row numbers, not restate the risk.

### A. First 7 days
Only the items that *will* bite if not handled in week one. Catastrophic + high-severity + fast-onset only. Each as a concrete action, not a category. ("Set up SPF/DKIM/DMARC for the sending domain via Resend or similar; verify with mail-tester.com" — not "handle email deliverability.")

### B. First 30 days
Everything that needs to be in place before the user fully relies on the new state. Setup, monitoring, account ownership, and "watch this for a month" items.

Defer below-waterline items entirely. Don't pad either plan to look thorough.

---

## STEP 6: ADVERSARIAL PRESSURE PASS

Before declaring done, run three voices and rewrite if any flags a real gap:

- **The user a year from now** — "Which of these did I forget about that's now biting me?" Does the register catch it?
- **A fellow insider** — "What's missing from this list?" Is there a category the persona skipped because it's too obvious *to insiders* (and therefore invisible to the outsider too)?
- **A skeptical CFO / spouse / advisor** — "Are any severities inflated? Is anything here scaremongering?" Push back on items where real-world frequency doesn't justify the tier.

Rewrite if any voice flags a real issue. Re-run the distribution check after rewriting.

---

## STOPPING RULE

Stop when:

- Register has 12–20 rows
- Severity distribution is varied (see Step 4 shape)
- Every row's "Why insider knows" is non-obvious
- Both action plans reference register rows, not restate them
- Adversarial pass produces no new categories

If you can't honestly reach 12 distinct at-waterline risks for the domain, **say so explicitly**. Some domains don't have an iceberg — the user is overestimating the silent-failure surface area, and that itself is the finding. Don't pad to hit the count.

---

## FINAL STANDARD

If a real domain insider read the register and said *"yeah, that's the list I'd hand to my replacement"* — pass.

If they said *"this is generic"*, *"this is what I tell beginners"*, or *"half of these are above the waterline"* — fail. Restart from Step 2 with a sharper persona.
