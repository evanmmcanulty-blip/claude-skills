---
name: apar-design-critique
description: >
  APAR-specific design audit skill. Auto-loads APAR brand context
  (apar-brand-content, apar-editorial-standards, the APAR design system)
  and runs the design-critique scorecard against any APAR surface — web
  (allprorecon.com, APAR Connect, dealer PDFs, pricing sheets, Heritage,
  NASCAR content) or app (APAR Connect mobile, widgets, App Store
  listings, future Finish Line surfaces). Trigger on `#apar-design-critique`,
  "audit this APAR design", "is this APAR-compliant", "review this dealer
  PDF", "check this APAR Connect screen", or any visual artifact tagged
  for APAR review. For non-APAR projects, use `design-critique` directly
  with your own brand spec. For pure copy review, route to
  apar-editorial-standards.
---

# apar-design-critique — APAR-Specific Design Audit

A pre-loaded variant of `design-critique` for APAR work. Auto-loads APAR brand context so you don't have to paste the spec each time.

This skill is the action layer over `docs/apar-design-critique-template.md` (the paste-in template) and references `docs/apar-premium-design-reference.md` and `docs/apar-app-design-reference.md` as the strategic frame.

---

## WHEN TO USE

**Trigger on:**
- `#apar-design-critique`
- "audit this APAR design," "is this APAR-compliant," "design audit on this dealer PDF"
- "review this APAR Connect screen / mobile UI / widget"
- "is this on-brand for APAR"
- Any visual artifact tagged for APAR brand review

**Auto-fire on:** APAR website builds and redesigns, APAR Connect releases, dealer-facing PDFs before delivery, NASCAR sponsor materials, Finish Line packaging mocks, internal employee surfaces, leave-behinds and pricing sheets.

**Do NOT fire on:**
- Non-APAR projects — use `design-critique` with your own brand spec
- Pure APAR copy review — route to `apar-editorial-standards` (it covers fatal voice patterns)
- APAR strategy / positioning — use `optimize-this` Criterion Set C
- APAR brand-system updates themselves — those go in `apar-brand-content`

---

## PRE-LOADED CONTEXT

When this skill fires, the following are loaded automatically as the brand spec:

- **Type system:** Oswald (display, uppercase, tight tracking), Lato 300 (body, 1.7+ leading, 600px max measure), Archivo Narrow (metadata, section labels in `--red`, table headers, numeric data). Three families, each with a specific role. No substitutions.
- **Color palette:** Warm-tinted neutrals (`--paper #f9f7f4`, `--paper-2 #f2efe9`, `--ink #111010`, `--white #ffffff`), `--red #be2e2d` working accent (Performance Red `#CC3433` formal). Steel Grey, Aluminum Grey, Chrome Silver as supporting structure. Ratio: 60/25/15.
- **Voice rules:** From `apar-editorial-standards`. Fatal failures: negation-assertion, false-revelation framing, inspirational clichés, superlatives, AI-pattern words. Structural rules: no em dashes (cap 1), no filler transitions, no consecutive sentences with same opener.
- **Forbiddens:** From `apar-brand-content` and the reference docs §10 (web) / §13 (app). Visual, motion, copy, structural anti-patterns.
- **Audience:** Dealer principals, GMs, fixed ops directors, used car managers, service advisors. Peer-to-peer operator register.
- **Dialect:** Operator premium (per `docs/apar-premium-design-reference.md` §1.1). Not luxury-editorial; not consumer-aftermarket; not tech-startup.

If `apar-brand-content` updates, this skill auto-uses the latest. The brand spec is canonical at the source skill, not in this one.

---

## STEP 1: INPUT INTAKE

Confirm before scoring:

1. **The artifact.** Screenshot, URL, PDF, Figma, app screen, packaging mock.
2. **The APAR surface.** Marketing site / APAR Connect (web) / dealer PDF / pricing sheet / Heritage / NASCAR / Finish Line / internal / APAR Connect mobile / Watch / widget / push notification / App Store listing.
3. **Stakes.** Draft / client-facing / production / public.
4. **Intent.** What is the artifact trying to accomplish?

### Defensive intake clauses

- **Brand-system source check.** If the artifact looks like it's using outdated APAR brand values (old red, old typography, pre-warm-paper neutrals), surface this — the artifact may predate the current spec.
- **Sub-brand resolution.** If the artifact is Finish Line, ACV, or OOBE, note that sub-brand architecture for Finish Line is still open (per `apar-brand-content` factual tripwire). Score against the parent brand system unless a Finish Line-specific spec has been ratified.

---

## STEP 2: RUN THE SCORECARD

Use `docs/apar-design-critique-template.md` as the scorecard. Brand compliance (BC) is pre-parameterized to APAR.

**Universal domains:** A–L (same as `design-critique`)
**Brand compliance:** BC pre-loaded to APAR
**App domains:** N–Z when surface is iOS / Android / Watch / widget

The APAR template adds APAR-specific reference cross-references to:
- `docs/apar-premium-design-reference.md` §2 (web layer specs), §3 (web anti-patterns), §4 (web premium-leak inventory), §10 (web forbiddens)
- `docs/apar-app-design-reference.md` §5 (app layers), §6 (app anti-patterns), §7 (app premium-leak inventory), §13 (app forbiddens)
- `apar-editorial-standards/SKILL.md` for J-domain voice criteria
- `apar-brand-content/SKILL.md` Design System for all BC criteria

---

## STEP 3: APAR-SPECIFIC ADVERSARIAL PRESSURE

In addition to the universal three voices, name these personas for the audience read:

- **Marketing site / Heritage / NASCAR:** A dealer principal who has seen every recon vendor's pitch. They are reading on a phone between meetings. They have 30 seconds.
- **APAR Connect (web or mobile):** A fixed ops director walking the recon bay at 9 AM. They need to see aged units and exceptions in one tap. They will not tolerate vendor-software friction.
- **Dealer PDF / pricing sheet:** A used car manager who got it in their inbox. It is competing with 12 other vendor PDFs.
- **Internal employee surface:** A regional ops manager who hates corporate emails. They want the operational fact, not the inspiration.
- **NASCAR external:** A William Byron fan who cares about racing. They are not the primary audience but they are watching.
- **Finish Line consumer (when applicable):** A car owner who buys premium detailing chemicals. They respect the operator credibility on the back panel and will read it.

The horizon-check skeptic stays the same: will this read as ahead of trend in 24 months?

---

## STEP 4: VERDICT

Same six verdicts as `design-critique`. Add one APAR-specific failure mode:

**RECONSIDER triggers automatically if:**
- The artifact reads as consumer-aftermarket (auto-spa, sparkle, tier-card service grid)
- The artifact reads as luxury-editorial (apothecary aesthetic, jewel-tone palette, serif-display dominance) where operator-premium is required
- The artifact reads as tech-startup (gradient mesh, Inter at default, glass cards) where APAR's warm-paper system applies
- The brand voice violates `apar-editorial-standards` Section 1 fatal failures (negation-assertion, false-revelation, inspirational clichés)

These are dialect failures, not craft failures. Polish does not fix them.

---

## OUTPUT FORMAT

Same as `design-critique`. The Brand spec line in the header reads:

```
Brand spec: APAR (loaded from apar-brand-content + apar-editorial-standards + apar-premium-design-reference + apar-app-design-reference)
```

---

## COMPOSITION WITH SIBLING SKILLS

- **Voice failures (J-domain or BC voice criteria):** route to `apar-editorial-standards` for the corrected line and audit report.
- **Strategy / positioning failures:** route to `optimize-this` Criterion Set C.
- **Brand-system update needed:** route to the brand-content team to update `apar-brand-content`; do not silently expand brand rules in audit findings.
- **Code-bound failures (HTML / SwiftUI implementation):** route to `impeccable-design` (HTML) or `impeccable-swiftui` (iOS).
- **Production-readiness blockers:** route to the print vendor or release engineer with the specific block called out.

---

## APAR FACTUAL TRIPWIRE CHECK

Before declaring SHIP on any APAR artifact, verify these facts as a final pass (per `apar-editorial-standards` Section 4):

- Website URL: `allprorecon.com` (not allproautorecon.com, not allproreconditioning.com)
- Tagline: "The Recon Standard." (period included, no exceptions)
- Founding year: 1994
- Founder context: Brandon Berryman joined as an early technician, grew into co-owner, became CEO. He did not found the company.
- Two Treys: Trey Watson = Regional Operations Manager, South Region. Trey Bono = VP of Customer Success. Two people; do not conflate.
- NASCAR: William Byron / No. 24 / Hendrick Motorsports — full names on first reference. 2026 race weekends: COTA, Kansas, North Wilkesboro, Talladega.
- PPF / ceramic / tint: optional add-on services. Never positioned as standard workflow deliverables.
- ACV: subsidiary of APAR. Not a partner.
- OOBE: APAR's vehicle photography subsidiary (acquired March 2026). Not a partner.

A factual tripwire failure is a fatal failure regardless of craft. Block delivery.

---

## FINAL STANDARD

Same as `design-critique`. Add: if the audit reads like it could apply to any recon-services brand, you missed the APAR-specific dialect work. The audit must surface the parts that are *only* wrong because the surface is APAR's, not generic.
