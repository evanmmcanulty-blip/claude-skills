---
name: apar-premium-design-reference
description: >
  Loads the APAR Premium Design Reference into the current session. The
  reference is the strategic point of view on what reads as professional-
  grade (operator premium) in digital today and 18-36 months out, grounded
  in APAR's brand system and dealer-operator audience. Covers web surfaces
  (marketing site, APAR Connect web, dealer PDFs, NASCAR collateral,
  Finish Line packaging). Triggers on `#apar-design-ref`, "load the APAR
  design reference", "what does premium mean for APAR", "what dialect is
  APAR", or any APAR design strategy question. Reference content only; for
  audit, use `apar-design-critique`. For app-specific design, also load
  `apar-app-design-reference`.
---

# apar-premium-design-reference — Load the APAR Premium Design Reference

A context-providing skill. When invoked, surfaces the full content of `docs/apar-premium-design-reference.md` into the current session so Claude can apply the strategic frame to design work without the user pasting the doc each time.

---

## WHAT THIS SKILL DOES

When triggered, read `docs/apar-premium-design-reference.md` and treat its contents as authoritative strategic context for the rest of the session. The reference contains:

1. **Strategic frame.** What "premium" means for APAR (operator premium, not luxury or editorial). The three horizon-check pressures applied to APAR specifically. The two-surface model (B2B operator + D2C Finish Line).
2. **Layer-by-layer specifications.** Typography, color, material, layout, motion, interaction, performance, imagery, voice, system craft. Each layer banded AHEAD / CURRENT / DATING / DATED with concrete tokens.
3. **Anti-patterns.** Tells of mid-tier recon and detailing brands.
4. **Premium-leak inventory.** Where craft falls apart in real APAR surfaces, in priority order.
5. **Surface specifications.** Marketing site, APAR Connect, print collateral, NASCAR-adjacent content.
6. **The Finish Line problem.** Defended recommendation for sub-brand architecture (Option B — operator-credentialed standalone) with display-face and accent-color options.
7. **Horizon bets.** High / medium / low confidence forward positioning calls.
8. **First 90-minute audit script.** Practical use.
9. **Decision rules.** APAR-specific defaults that override generic design intuition.
10. **Forbiddens.** Mirror of `apar-brand-content` and `apar-editorial-standards` for design context.
11. **Iceberg reminders.** Sticky notes.

---

## WHEN TO USE

**Trigger on:**
- `#apar-design-ref`
- "Load the APAR design reference"
- "What does premium mean for APAR?"
- "What dialect is APAR in?"
- "Should APAR look like [X]?"
- Any APAR design strategy question that benefits from the reference being loaded

**Auto-fire on:** APAR website redesigns, APAR Connect feature design, new APAR surfaces being conceived, Finish Line architecture discussions, dealer collateral design starts.

**Do NOT fire on:**
- Audit of an existing surface — use `apar-design-critique` instead (this skill is reference; that one is audit)
- Implementation specifics — use `impeccable-design` (HTML) or `impeccable-swiftui` (iOS)
- Brand-system updates — those go in `apar-brand-content`

---

## STEP 1: LOAD THE REFERENCE

Read `docs/apar-premium-design-reference.md` in full. The document is structured for repeat use; treat every section as live context.

If the document has been updated more recently than this skill's last revisit date (2026-11-19 per the doc's update protocol), surface the changes.

---

## STEP 2: APPLY THE REFERENCE TO THE USER'S TASK

The reference is the strategic frame. Use it to:

- Ground design recommendations in APAR's operator-premium dialect, not generic premium intuition
- Apply the layer-by-layer band specs to evaluate where existing or proposed work sits
- Identify anti-patterns and premium leaks in real artifacts
- Make horizon-correct bets (cut motion, lean into provenance, structure for LLM retrieval)
- Defend recommendations with reference-doc citations (§X.Y)

---

## STEP 3: HONOR THE SOURCE-ORDER PROTOCOL

The reference doc explicitly subordinates itself to:

1. `apar-brand-content/SKILL.md` (canonical brand spec)
2. `apar-editorial-standards/SKILL.md` (canonical voice rules)
3. `design-eye/SKILL.md` Domain 6 (canonical brand-compliance audit criteria)
4. `horizon-check/SKILL.md` (canonical horizon thesis)
5. `docs/apar-premium-design-reference.md` (this reference)

If the reference disagrees with anything above it, the reference is wrong. Surface the conflict and recommend updating the reference to match.

---

## COMPOSITION

- **Pair with `apar-app-design-reference`** when the design work spans web and app.
- **Pair with `apar-design-critique`** when the task is audit, not strategy.
- **Pair with `apar-brand-content`** when the task involves applying the design system to a specific HTML output.
- **Pair with `horizon-check`** when the task is a forward-positioning audit on an APAR artifact.

---

## FINAL STANDARD

When this skill fires, the user's next design recommendation should be unmistakably grounded in the APAR-specific dialect, not generic premium-design knowledge. If the recommendation could apply to any premium B2B brand, the reference was loaded but not applied.
