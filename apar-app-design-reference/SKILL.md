---
name: apar-app-design-reference
description: >
  Loads the APAR App Design Reference into the current session. The
  reference is the partner doc to apar-premium-design-reference, covering
  what changes when the surface is a native app instead of a website.
  Includes the "should this be an app at all?" decision frame (defended
  yes for APAR Connect mobile; defended no for a Finish Line consumer
  app), platform posture (iOS-first native; Android parity), app-only
  layer specs (icon, splash, permissions, Dynamic Type, haptics, system
  integration, push, App Store, system craft), the APAR Connect mobile
  spec, and horizon bets for apps. Triggers on `#apar-app-ref`, "load the
  APAR app reference", "should we build an APAR app", "APAR Connect
  mobile spec", "iOS app for APAR". Reference content only; for audit
  use `apar-design-critique`.
---

# apar-app-design-reference — Load the APAR App Design Reference

A context-providing skill for app-related APAR design work. When invoked, surfaces the full content of `docs/apar-app-design-reference.md` into the current session.

---

## WHAT THIS SKILL DOES

When triggered, read `docs/apar-app-design-reference.md` and treat its contents as authoritative for app-related APAR design work. The reference contains:

1. **Strategic frame for apps.** The operator-premium thesis applied to small-screen surfaces with platform constraints. Three shifts when the surface is an app: platform as co-author, system surface area as primary, performance felt physically.
2. **"Should this be an app at all?"** A first-class question. Defended yes for APAR Connect mobile (dealer-operator audience, glanceable status, capture flows, push quality). Defended no for a Finish Line consumer app (consumable retention economics, cheaper alternative delivery channels). Other app candidates dispositioned.
3. **Platform posture.** Native iOS first, native Android parity within 6 months. Explicit rejection of cross-platform stacks at operator-premium tier with three defended reasons. Liquid Glass / iOS 26+ restrained adoption.
4. **Carry-vs-override matrix** against the web reference, so readers know which layers come over and which platform conventions take precedence.
5. **App-only layer specs.** Each banded AHEAD / CURRENT / DATING / DATED with concrete tokens:
   - App icon
   - Splash / first-launch / onboarding
   - Permission handling
   - Typography on-device (Dynamic Type discipline)
   - Color (system semantic roles + brand red)
   - Spatial layout (safe areas, Dynamic Island, lock screen)
   - Native motion
   - Haptics
   - Sound
   - Performance (cold start, sustained fps, app size, battery, data)
   - Imagery at thumbnail scale
   - System integration (widgets, App Intents, Live Activities, Watch, Spotlight)
   - Push notifications
   - App Store presence
   - Settings and account craft
6. **App-specific anti-patterns** (30 tells of mid-tier apps).
7. **App premium-leak inventory.**
8. **APAR Connect mobile spec.** Job-to-be-done, three-tab structure, four core questions, four core actions, opinionated gesture patterns, required system integration in priority order, v1 scope cuts.
9. **Finish Line app — the defended no.**
10. **Horizon bets for apps.** High confidence (App Intents as primary entry; Live Activities; on-device AI; Sign in with Apple default). Medium (Liquid Glass restrained adoption; calm-computing positioning). Low (Vision Pro; custom haptic signatures; in-app AI chat).
11. **First 90-minute app audit script.**
12. **Decision rules.**
13. **Forbiddens.**
14. **Iceberg reminders.**

---

## WHEN TO USE

**Trigger on:**
- `#apar-app-ref`
- "Load the APAR app reference"
- "Should we build an APAR app?"
- "APAR Connect mobile spec"
- "iOS app design for APAR"
- "What should an APAR widget look like?"
- "How should APAR Connect handle [push / Watch / App Intent / Live Activity]?"
- Finish Line app questions

**Auto-fire on:** APAR Connect mobile design starts, App Store listing design, widget design, Watch complication design, push notification design, App Intent definition, any APAR app-related design conversation.

**Do NOT fire on:**
- Web design — use `apar-premium-design-reference` instead
- iOS implementation specifics — use `impeccable-swiftui` (this is design reference; that is code reference)
- Audit of an existing app — use `apar-design-critique` (this is reference; that is audit)
- APAR Connect *web* design — that's in the web reference

---

## STEP 1: LOAD THE REFERENCE

Read `docs/apar-app-design-reference.md` in full. The document is structured for repeat use.

---

## STEP 2: PAIR WITH THE WEB REFERENCE

The app reference does not restate web content — it diffs against it. For full strategic context on any APAR work, both references should be loaded together.

`apar-premium-design-reference` should be loaded first; this skill second.

---

## STEP 3: HONOR PLATFORM-NATIVE SOURCE OF TRUTH

The app reference subordinates itself to:

1. `apar-brand-content/SKILL.md` (canonical brand spec)
2. `apar-editorial-standards/SKILL.md` (canonical voice rules)
3. `design-eye/SKILL.md` Domain 6 (canonical brand-compliance audit criteria)
4. `impeccable-swiftui/SKILL.md` (canonical iOS implementation guidance)
5. `horizon-check/SKILL.md` (canonical horizon thesis)
6. `docs/apar-premium-design-reference.md` (web reference)
7. `docs/apar-app-design-reference.md` (this reference)

If the app reference disagrees with anything above it, the reference is wrong.

---

## COMPOSITION

- **Pair with `apar-premium-design-reference`** for full strategic context on any APAR design work.
- **Pair with `apar-design-critique`** when auditing an APAR app surface.
- **Pair with `impeccable-swiftui`** when the conversation moves from design to SwiftUI implementation.
- **Pair with `horizon-check`** when running a forward-positioning audit on an APAR app artifact (the app reference's §10 horizon bets are calibrated against the same thesis).

---

## STEP 4: FINISH LINE APP — DEFAULT NO

If the conversation veers toward building a Finish Line consumer app, surface §9 of the reference (the defended no). The recommended position is **do not build a Finish Line app in the next 24 months**; deliver the value through cheaper channels (iMessage app for reorder, SMS-driven reorder, Live Activity for fulfillment, PWA install-to-home-screen). Revisit threshold: sustained 50k+ monthly active customers.

Do not silently agree to design a Finish Line app. Push back with the alternatives first.

---

## FINAL STANDARD

When this skill fires, the user's next app-related recommendation should reflect:

- Platform-native fluency (real API names; real durations; real native curves)
- The operator-premium dialect (not consumer-app aesthetic; not iOS-26 theater)
- The system surface area as primary (widgets, App Intents, Live Activities, Watch — not just the home-screen icon)
- The honest answer to "should this app exist?"

If the recommendation reads like generic premium-app advice, the reference was loaded but not applied.
