---
name: design-critique
description: >
  Brand-agnostic design audit skill. Runs a structured critique against any
  design artifact (web surface, native app screen, print piece, deck,
  packaging) and any brand spec you supply. Combines universal craft
  criteria (typography, color, layout, hierarchy, motion, performance,
  imagery), horizon-positioning audit (against the three-pressures thesis
  from horizon-check), and brand-compliance audit (against the spec you
  paste in or reference). Use when reviewing a design surface for any
  project, brand, or client. Trigger on `#design-critique`, "design
  audit", "design check", "is this on-brand", "audit this design",
  "review this design", "design QA", or whenever a visual artifact needs a
  senior pass. For APAR work, use `apar-design-critique` instead — it
  pre-loads APAR brand context. For brand-system creation (not audit),
  this skill is the wrong tool — use a strategy skill.
---

# design-critique — Brand-Agnostic Design Audit

A universal design critique. Takes an artifact and a brand spec; runs universal-craft + horizon-positioning + brand-compliance audit; produces specific findings and a verdict.

This skill is the action layer over `docs/design-critique-template.md`. The template is the full scorecard; this skill is the operating protocol for running it.

---

## WHEN TO USE

**Trigger on:**
- `#design-critique`, "design audit," "design check," "design QA"
- "Is this on-brand?", "audit this design," "review this design"
- "Is this ready to ship?", "production check"
- Any time a visual artifact (screenshot, URL, PDF, app screen, packaging mock) needs a structured pre-ship pass

**Auto-fire on:** website redesigns, brand system applications to new surfaces, app screens before App Store submission, print pieces before press, decks before client delivery.

**Do NOT fire on:**
- APAR work — use `apar-design-critique` instead (pre-loaded brand context)
- Pure copy review — use the brand's editorial-standards skill or apply BRAND SPEC voice rules directly
- Strategy / positioning — use `optimize-this` with Criterion Set C
- Brand-system creation (this audits against a spec; does not create one)
- Forward-positioning audit only — use `horizon-check` natively

---

## STEP 1: INPUT INTAKE

Confirm the following before scoring. If any are missing, ask **one** focused question.

1. **The artifact.** Screenshot, URL, PDF, Figma file, source code, packaging mock, deck PDF. Fetch URLs. Read files. Flag uncertainty if working from prose description only.
2. **The surface type.**
   - Web: marketing site, web app, dashboard, PDF report
   - App: iOS, Android, Watch, widget, App Store listing
   - Print: collateral, packaging, deck for print
   - Other: digital ad, social asset
3. **The brand spec.** Paste-in or file-path reference. Must include type system, color palette, voice rules, forbiddens. If incomplete, surface the gaps before scoring. **Do not invent brand rules.**
4. **The stakes.** Draft / client-facing / production / public-facing. Production stakes mean verification gaps block approval.
5. **Intent.** What is the artifact trying to accomplish? If unclear, ask before scoring — a craft audit without intent context misses whether emphasis lands on the right element.

### Defensive intake clauses

- **Brand-spec absent.** If no brand spec is supplied and no brand context can be inferred (i.e., not an APAR project), proceed with a **universal-only audit** that skips the BC domain. Surface this explicitly in the output.
- **Surface ambiguous.** If the artifact could be web or app, ask before assuming. The domain set differs.
- **Multi-surface artifact.** A brand system applied across web + app + print is multiple audits. Run them separately or scope to one surface.
- **Prose-only artifact.** "Audit my homepage" with no URL or screenshot is unverifiable. Ask for a URL or screenshot before proceeding.

---

## STEP 2: RUN THE SCORECARD

Use `docs/design-critique-template.md` as the scorecard. Score every applicable domain:

**Universal domains (run on every artifact):**
- A. Strategic frame
- B. Typography
- C. Color + Material
- D. Layout + Spacing
- E. Compositional Hierarchy
- F. Motion (where applicable)
- G. Interaction (digital surfaces)
- H. Performance (digital surfaces)
- I. Imagery
- J. System Craft (multi-page or interactive)
- K. Production Readiness (medium-specific)
- L. Horizon-Check Forward Positioning

**Brand compliance (against the supplied spec):**
- BC. Brand Compliance (10 criteria; rows mark "brand-rule-not-supplied" if spec section absent)

**App-only domains (when surface is native app):**
- N. App Icon
- O. Splash / First-Launch / Onboarding
- P. Permission Handling
- Q. Spatial Layout
- R. Native Motion
- S. Haptics
- T. Sound
- U. App Performance
- V. Dynamic Type / Accessibility
- W. System Integration
- X. Push Notifications
- Y. App Store Presence
- Z. App System Craft

Each criterion gets pass / fail / N/A or a band (AHEAD / CURRENT / DATING / DATED) where the criterion is forward-positioning-shaped.

---

## STEP 3: HORIZON-POSITIONING APPLIES THROUGHOUT

The three pressures from `horizon-check` v1 govern the L-domain explicitly and color every other domain implicitly:

1. **Exhaustion correction.** Users are tired of motion-everywhere. Editorial restraint reads premium.
2. **Search collapsing into ask.** Most B2B traffic in 2027 will arrive via LLM summarization. Structure for retrieval.
3. **Legitimacy crisis.** Polish is meaningless; provenance (named people, real timestamps) is the new trust signal.

If a finding sits at the intersection of universal craft and horizon-positioning, name both.

---

## STEP 4: VERIFICATION GAPS

Not every criterion can be checked from every input form. Mark N/A and log under "verification gaps" when the artifact does not allow verification:

| Criterion class | Screenshot | URL | PDF | Source |
|---|---|---|---|---|
| Type, color, spacing | Approximate / Yes | Yes | Yes | Yes |
| Font embedding | No | Yes | Yes | N/A |
| Motion / animation | No | Yes | No | Partial |
| Performance | No | Yes | No | Yes (runnable) |
| Bleed, safe zones | No | No | Yes | Yes |
| App cold start | No | No | No | Yes |
| Interactive states | No | Yes | No | No |

Verification gaps at production stakes block approval until missing input is supplied.

---

## STEP 5: ADVERSARIAL PRESSURE

Three voices, in two passes.

**Pass A — Structured inversion (mandatory).** For every DATING / DATED finding, write the strongest defense of the flagged choice. What is the flagged element doing that the recommended change would lose? What audience would prefer the flagged version? If the defense survives, revise the verdict, not the work.

**Pass B — Three perspectives.**

- **Senior trade art director** (Vignelli / Bierut lineage; B2B editorial roots; no consumer-luxury or experimental affect). Would they hand this to a client? What does the artifact tell them about who made it?
- **Domain audience reader.** Name the persona based on the artifact's intent. For a fintech site, a CFO. For a developer tool, a senior engineer. For a creative tool, a designer-buyer. For trade B2B, the operator. *Does this read as made by someone who understands them?*
- **Horizon-check skeptic.** Will this read as ahead, on-trend, or behind in 24 months? Single biggest dating risk?

---

## STEP 6: VERDICT

One of six:

- **SHIP** — All criteria pass. No fatal failures. Forward-positioned.
- **SHIP WITH CONDITIONS** — Conditional items logged; must resolve before final delivery. List them.
- **REVISE** — Multiple DATING flags or one fatal failure. Specific rework required. List it.
- **RECONSIDER** — Strategic frame wrong (wrong dialect; wrong audience register; off-brand at the system level). Don't polish; rethink.
- **PRODUCTION BLOCKED** — Production-readiness failure that would cause vendor rejection or press error. Do not send.
- **VERIFICATION INCOMPLETE** — Required inputs not provided. Supply and re-audit.
- **BRAND-SPEC INCOMPLETE** — Spec missing load-bearing sections. Extend or proceed with universal-only audit.

Do not water down the verdict to be polite. A clear REVISE is more useful than a hedged SHIP.

---

## OUTPUT FORMAT

```
DESIGN CRITIQUE
Artifact: [name / path / URL]
Surface: [web / app / print / etc.]
Platform: [iOS / Android / N/A]
Stakes: [draft / client-facing / production / public]
Brand spec: [loaded from X / paste-in / universal-only / incomplete]
Intent: [one-line summary or "not specified"]

──────────────────────────
DOMAIN SCORES
──────────────────────────
A. Strategic Frame:        [Pass / Conditional / Fail]
B. Typography:             [Pass / Conditional / Fail]
C. Color + Material:       [Pass / Conditional / Fail]
D. Layout + Spacing:       [Pass / Conditional / Fail]
E. Compositional Hierarchy:[Pass / Conditional / Fail]
F. Motion:                 [Pass / Conditional / Fail / N/A]
G. Interaction:            [Pass / Conditional / Fail / N/A]
H. Performance:            [Pass / Conditional / Fail / N/A]
I. Imagery:                [Pass / Conditional / Fail]
J. System Craft:           [Pass / Conditional / Fail / N/A]
K. Production Readiness:   [Pass / Conditional / Fail]
L. Horizon Forward Position:[AHEAD / CURRENT / DATING / DATED]
BC. Brand Compliance:      [Pass / Conditional / Fail / spec-incomplete]
[App domains N-Z if applicable]

──────────────────────────
FAILING CRITERIA
──────────────────────────
[Domain] / [Criterion]: [Precise diagnosis. Mark ⚠ PRODUCTION BLOCKER
where failure would cause vendor rejection or press error. Mark
⚠ FATAL where brand spec marks the rule as fatal.]
...

──────────────────────────
DATING / DATED FINDINGS
──────────────────────────
[Element] — flagged for [criterion] — fix: [specific change]
...

──────────────────────────
VERIFICATION GAPS
──────────────────────────
[Domain] / [Criterion]: requires [source file / PDF / URL / brand spec section]
...

──────────────────────────
BRAND-SPEC GAPS (if any)
──────────────────────────
[BC criterion]: brand rule not supplied — recommend the brand owner
[extend spec to cover X / accept the gap].

──────────────────────────
ADVERSARIAL PRESSURE
──────────────────────────
Senior trade art director: [reaction]
[Domain audience persona]: [reaction]
Horizon-check skeptic: [reaction]

──────────────────────────
VERDICT
──────────────────────────
[ ] SHIP   [ ] SHIP WITH CONDITIONS   [ ] REVISE
[ ] RECONSIDER   [ ] PRODUCTION BLOCKED   [ ] VERIFICATION INCOMPLETE
[ ] BRAND-SPEC INCOMPLETE

Rationale: [one paragraph]

──────────────────────────
NEXT STEPS
──────────────────────────
1. [Specific action]
2. [Specific action]
...
```

---

## COMPOSITION WITH SIBLING SKILLS

After running this skill:
- If verdict is REVISE on copy-specific criteria → next step is the brand's editorial-standards skill (or `apar-editorial-standards` for APAR work)
- If verdict is REVISE on strategy criteria → next step is `optimize-this` Criterion Set C
- If verdict is RECONSIDER → not a critique problem; a brand-system or positioning problem. Surface to the brand owner.
- If verdict is SHIP and the artifact is about to ship as code → optionally run `fortify` for security/hardening if it involves new code paths.

This skill is the audit layer; it does not generate, design, or rewrite. Pair it with skills that do.

---

## FINAL STANDARD

The audit must read like it was produced by someone who:
- Has a defensible point of view about craft and forward-positioning
- Respects the audience's intelligence (and the brand spec's intent)
- Doesn't waste words
- Would rather flag a real problem than pass a clean scorecard

If the verdict reads like it could apply to any artifact, fail.
If the findings are vague enough to be reused on the next audit, fail.
If the verdict softens a real REVISE to a SHIP because the surface looks nice, fail.
