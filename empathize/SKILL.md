---
name: empathize
description: >
  Perspective-taking audit that simulates lived experience of a build to surface friction the builder is too close to see. Trigger on: "#EMPATHIZE", "empathize", "walk through this", "experience this", "audit the experience", "what's it like to use this", "find the friction", "stress test the journey", "walk it like a customer", or any signal the user wants a build pressure-tested through lived contact. Handles single-actor, concurrent multi-actor, sequential multi-actor, and divergent-jobs builds. Applies to websites, flows, dashboards, tools, emails, decks, packaging, and multi-person workflows. Distinct from design-eye (visual craft), fortify (security), horizon-check (trend), and rootcause (past failure). Do NOT run an experience audit without loading this skill first.

---

# #EMPATHIZE — Experience Audit Protocol

Walk through the build as if living inside it. Not as a critic scoring craft. As a real human meeting this thing for the first, second, and seventh time — on different devices, in different moods, with different stakes — and when applicable, as multiple humans whose contact affects each other.

Output: a prioritized friction log and fix list. Both grounded in specific moments of contact. No vibes essay.

---

## PHASE 1 — INPUT SHARPENING

Confirm three things before walking. If any are missing, ask one focused question. Never ask all three at once.

1. **The artifact.** What exactly is being audited? URL, file, screenshots, copy block, deck, physical product, retail flow, multi-step workflow. Fetch URLs. View files in context. Flag uncertainty when working from prose description only.
2. **The intended job(s).** What is this supposed to accomplish for the person on the other side? If multiple roles use the same artifact for different jobs, name each one.
3. **The known constraints.** Anything fixed (brand system, platform, deadline, audience) that should bound the audit.

Once clear, proceed to Phase 2 without asking for confirmation.

---

## PHASE 2 — TRACK AND SHAPE ROUTING

### 2A — Track

| Track | Applies to |
|---|---|
| Digital surface | Websites, landing pages, signup flows, dashboards, web apps, mobile apps |
| Communication artifact | Emails, presentations, decks, proposals, newsletters, sales collateral |
| Physical / retail | Packaging, in-store experience, vehicle delivery, showroom flow, event walk-up |
| Internal tool | Admin panels, internal dashboards, ops software, scripts and runbooks |

Tracks can blend. State the blend explicitly.

### 2B — Shape

| Shape | Definition | Examples |
|---|---|---|
| Single-actor | One human moves through it start to finish | Marketing email, personal dashboard, landing page |
| Concurrent multi-actor | Multiple humans touch it simultaneously, with shared real-time state | Trivia host + teams, presenter + audience, dispatch + driver |
| Sequential multi-actor | An object or task moves through multiple humans' hands in sequence | Order → approval → fulfillment, lease document, quote → invoice |

**Divergent-jobs overlay** — layer on any shape when the same artifact serves multiple roles with materially different goals.

| Overlay | Definition | Examples |
|---|---|---|
| Divergent jobs on a shared artifact | Same surface, multiple roles, different success criteria | Website serving public visitors + dealer staff + exec, dashboard read by ops + finance + legal |

### How shape changes the audit

- **Single-actor:** Phases 3, 4, 5, 6.
- **Concurrent multi-actor:** add Phase 4.5 — Interaction Surface.
- **Sequential multi-actor:** add Phase 4.6 — Handoff Audit.
- **Divergent-jobs overlay:** add Phase 4.7 — Job-by-Role Pass.

State track, shape, and overlay before walking.

---

## PHASE 3 — PERSONA SCOPING

Three to six personas. Always include at least one adversarial persona. Always include at least one internal/operational persona when the build will be sold, supported, or maintained. For multi-actor shapes, every named actor is mandatory.

### Persona library

**External-facing**
- First-time arriver — decides in seconds, no prior context.
- Returning user — annoyed when forced to relearn.
- Skeptical evaluator — looking for reasons to disqualify. Reads small print.
- Rushed mobile user — one thumb, in line, sun on screen, three minutes max.
- Comparison shopper — two other tabs open, live A/B against competitors.
- Accessibility-dependent user — screen reader, keyboard-only, low vision, motor or cognitive limitations.
- Low-bandwidth / older device user — slow loads, punished by JS-heavy pages.
- Returning to fix something — already frustrated on arrival.
- Wrong-arrival user — landed here by mistake or bad link.
- Decision delegator — researching for someone else, needs to capture and forward.

**Internal / operational**
- Frontline operator — uses, demos, or works inside this every day.
- Support / fix-it — picks up when something breaks.
- Sales user — walks a prospect through this live.
- Admin / maintainer — updates content six months from now.
- Executive reviewer — ninety seconds, judges the whole build.
- New hire onboarding — learns this from scratch in a week.

**Concurrent-build personas**
- Live performer / on-stage operator — host, presenter, demo-er. UI friction = social cost. Dead air, having to apologize, losing the room.
- Audience-with-devices — attention split, synced to a pace they don't control, watching others watch them.

**Sequential-build personas**
- Upstream handoff sender — cares about whether what they sent is enough and whether they'll be blamed if the next person can't proceed.
- Downstream handoff receiver — cares about whether they have what they need, whether the input is trustworthy, who to escalate to.
- Approval gatekeeper — has to say yes or no with limited information. Rubber-stamping or actually deciding?

**Divergent-jobs personas**
- Shared-artifact role-holder — same artifact, different job. Name each role explicitly. Each gets its own walk.

**Adversarial / edge**
- Bad-actor / abuser — trying to misuse, exploit, or extract.
- Hostile-press / screenshot reader — sees one screenshot out of context.
- Cognitively overloaded user — exhausted, distracted, multi-tasking.
- Wrong-language / wrong-region user — assumed knowledge that doesn't apply.

State picks and exclusions before walking.

---

## PHASE 4 — JOURNEY WALKS

Walk every active stage for every persona. Lived experience in present tense from inside the persona's head. Brief. Specific.

### Journey stages by track

| Track | Stages |
|---|---|
| Digital surface | Pre-arrival → first contact → orientation → primary action → friction/recovery → completion → return/aftermath |
| Communication artifact | Inbox/context of receipt → first scan → decision to engage → reading → reaction/forward/file → recall later |
| Physical / retail | Approach → threshold → navigation → interaction/transaction → recovery from problem → exit → memory |
| Internal tool | Discovery → learning curve → daily use → edge case → breakage → maintenance → handoff |

### Per stage, per persona, capture six things

| Field | What to log |
|---|---|
| Sensory contact | What is concretely seen, read, tapped, heard |
| Cognitive load | What they're trying to figure out |
| Emotional state | Calm, confused, irritated, doubting, intrigued, relieved |
| Friction | Anything that slows, confuses, or distracts. Specific. |
| Trust signal read | What they pick up about whether this thing is legit |
| Next-step clarity | Do they know what to do next without thinking? |

**Coverage rule:** Every persona at first contact. Every persona at primary action. Adversarial walks at friction stage. All personas at completion. Skip other cells with one-line notes when nothing non-obvious surfaces.

---

## PHASE 4.5 — INTERACTION SURFACE AUDIT
*Fires only when shape is concurrent multi-actor.*

Concurrent builds fail at the seams between actors. Audit shared state and moments where experiences depend on each other.

### Per shared state element, log

| Field | Description |
|---|---|
| Shared state | What's the thing both actors are looking at or affecting? |
| Update mechanism | How does it change? Who triggers updates? |
| Desync risk | What happens when actors see different states? |
| Blocking moments | Where does one actor's inaction stall another's progress? |
| Recovery path | When desync happens, how do they get back in sync? Dignified or embarrassing? |

### Mandatory questions

- What does the host/operator see when one player hasn't acted yet — and how does that change their decision to advance?
- What happens when network drops for one actor mid-state-change?
- What does the room see during a recovery moment? Failed build or operator in control?
- Where can an actor act on stale information without realizing it?
- What's the dead-air cost when something glitches?

---

## PHASE 4.6 — HANDOFF AUDIT
*Fires only when shape is sequential multi-actor.*

Sequential builds fail at transitions. Audit each handoff explicitly.

### Per transition (Actor N → Actor N+1), log

| Field | Description |
|---|---|
| What's passed | The artifact, info, or task being handed off |
| What's lost | Information the upstream actor had that downstream doesn't |
| What's ambiguous | Fields, signals, or context readable multiple ways |
| What blocks downstream | Missing inputs, signoff, or context that prevents proceeding |
| Timing risk | What does downstream see during the wait? |
| Loop-back cost | Cost of going back upstream for clarification |

### Mandatory questions

- Does each handoff include enough for the next actor to proceed without asking?
- Where can the chain silently break?
- Who owns the artifact at any given moment? Visible to all actors?
- What happens when an actor needs to reject or send back? Dignified or punishing?
- For gatekeepers: do they have what they need to approve confidently, or are they rubber-stamping?

---

## PHASE 4.7 — JOB-BY-ROLE PASS
*Fires only when divergent-jobs overlay is active.*

Walking once per persona doesn't surface conflict between jobs. The conflict is between the jobs.

### Per role, log

| Field | Description |
|---|---|
| Role | Specific named role (not generic "user") |
| Job | What this role is trying to accomplish on this artifact |
| What they need | Information, action, signal, content — concrete |
| Does the artifact serve this job? | Pass/Fail. If fail, what's missing or in the way. |
| Conflict with other roles | Where does serving this role make another role's job harder? |

### Mandatory questions

- Is there a role whose job the artifact actively obstructs while serving another role well?
- Is there a role whose needs are assumed but never verified?
- Where does the artifact try to serve too many jobs at once and end up serving none well?
- For each role: would you bet money this artifact gets their job done?

---

## PHASE 5 — FRICTION LOG

Aggregate everything into a single prioritized log. Every entry has six fields.

| Field | Description |
|---|---|
| ID | F01, F02… |
| Where | Specific moment, element, screen, object, or transition |
| Who feels it | Persona(s) or role(s) most affected |
| What happens | What the experience actually is right now |
| Why it matters | Stakes |
| Severity | Critical / High / Medium / Low |

### Severity definitions

- **Critical** — blocks primary action for any non-adversarial persona, breaks trust on first contact, fails accessibility floor, exposes brand to screenshot risk, blocks downstream actor with no escape, fails one role's job entirely
- **High** — significantly degrades experience for a primary persona, increases drop-off, forces support intervention, makes the build feel amateur, causes embarrassing dead air, causes a role to silently work around the artifact
- **Medium** — friction that erodes quality but doesn't break the journey
- **Low** — polish issue, minor inconsistency, edge-case nuisance

Group related entries under a parent issue if the log exceeds 25 entries.

---

## PHASE 6 — FIX PROPOSALS

For every Critical and High entry, propose a concrete fix.

| Field | Description |
|---|---|
| Friction ID | Tie to F01, F02… |
| What to change | The actual edit, redesign, copy swap, structural move, handoff field added, sync mechanism introduced |
| Where it goes | Exact location in the build or workflow |
| Lift | Low / Medium / High |

Do not invent fixes for friction that needs more thought. Name what would unlock the right fix instead.

---

## OUTPUT STRUCTURE

```
ARTIFACT: [what was audited]
JOB(S): [intended job(s) from Phase 1]
TRACK: [digital / communication / physical / internal — or blend]
SHAPE: [single / concurrent / sequential]
OVERLAY: [divergent-jobs, if active — otherwise omit]

PERSONAS WALKED
- [persona name]: [one-line reason]

PERSONAS EXCLUDED
- [persona name]: [one-line reason]

JOURNEY WALKS
[Per persona, per active stage. First-person present-tense.]

[IF CONCURRENT] INTERACTION SURFACE
[Per shared state element.]

[IF SEQUENTIAL] HANDOFF AUDIT
[Per transition.]

[IF DIVERGENT-JOBS] JOB-BY-ROLE PASS
[Per role.]

FRICTION LOG
F01 — [Where] — [Who] — [What] — [Why] — [Severity]

FIX PROPOSALS
F01 → [What to change] — [Where] — [Lift]

UNRESOLVED
[Friction needing more thought, with what would unlock the right fix]
```

---

## RULES

- Walk in present tense from inside the persona's head.
- Specificity over coverage. Five sharp friction entries beat twenty generic ones.
- Adversarial personas are mandatory.
- Internal personas are mandatory when the build will be sold, supported, or maintained.
- For multi-actor shapes, every named actor is a mandatory persona.
- Don't soften severity to be polite.
- If a fix isn't clear, say so. Don't invent.
- Humanizer rules apply. No AI rhythm, no triple cadence, no motivational framing.

## TONE

Direct. Observational. Treat the user as someone who can hear honest feedback about work they are close to. Walks should read like a trusted collaborator narrating their actual experience, not like a UX consultant performing thoroughness.

---

## FINAL STANDARD

The audit passes when:

- Every Critical and High friction entry traces to a specific moment, screen, or
  transition — not a category.
- For multi-actor shapes, the seam audit (Phase 4.5 / 4.6) surfaced friction the
  single-actor walk would have missed.
- For divergent-jobs overlay, the role-by-role pass (Phase 4.7) named at least one
  conflict between roles, not just per-role friction.
- The friction log is prioritized, not exhaustive. Five Critical entries beat
  twenty mixed-severity entries.
- Fix proposals are concrete edits, not directions. Anything still under-specified
  is in UNRESOLVED with what would unlock the right fix.
- A trusted collaborator reading the walks would recognize their own experience —
  not feel like they're reading a UX consultancy deliverable.

If the audit reads thorough but generic — "the CTA could be clearer", "consider a
loading state" — fail. Generic friction is a tell that the persona walk wasn't
lived. Re-walk from inside a sharper persona.

If the audit produces no Critical or High entries, say so plainly. Some builds are
genuinely friction-light at this stage; manufactured findings degrade trust in the
next audit.
