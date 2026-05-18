---
name: impeccable-swiftui
description: >
  Apple HIG and SwiftUI design enforcement for all native iOS/macOS UI work.
  Use this skill immediately and without hesitation whenever Claude is building SwiftUI
  views, components, screens, or apps. Also trigger on "#swiftui", "be HIG faithful",
  "model ecosystem citizen", "native feel", "think through from a HIG mindset", or any
  request to review/improve SwiftUI UI for usability, accessibility, or delight.
  This skill establishes the "enthusiastically faithful" operating contract: HIG
  compliance is a hard constraint, not a suggestion. Pairs with impeccable-design for
  web output — they do not conflict, they cover different platforms.
---

# Impeccable SwiftUI

Apple HIG and SwiftUI best-practice enforcement for every piece of native UI output.
You are a **model ecosystem citizen**: platform conventions are not constraints to work
around — they are the design language. Embrace them first, deviate only with clear
intent and clear reason.

This skill has two modes:

1. **Passive mode** (default on all SwiftUI output): HIG compliance, component
   selection, semantic color, and Dynamic Type are enforced automatically.
2. **Review mode** (triggered by keyword or explicit request): structured critique pass
   through four lenses — usability, accessibility, delight, HIG fidelity — with a
   list of concrete tunings.

---

## The native feel test

Before delivering any SwiftUI output, run this check internally:

If a user opened this in an iPhone running the latest iOS alongside Apple's own apps,
would it feel like it belongs? If anything looks custom where the system component
would have been right, or fights the platform instead of extending it — it fails.

This test is not optional. It gates every output.

---

## Hard constraints (non-negotiable)

These run before aesthetic choices. If output violates any of these, fix before delivery.

### Dynamic Type
- **Never hardcode font sizes.** Always use system text styles: `.title`, `.headline`,
  `.body`, `.callout`, `.subheadline`, `.footnote`, `.caption`, `.caption2`.
- Never use `.font(.system(size: 17))` when `.font(.body)` is the intent.
- Never use `.frame(height:)` on containers that hold text — it breaks Dynamic Type
  scaling. Use padding instead.
- When a custom font is required, wrap it: `.font(.custom("Name", size: 17, relativeTo: .body))`.

### Semantic colors
- **Never hardcode hex or RGB values for UI chrome.** Use semantic system colors:
  `.primary`, `.secondary`, `.tertiary`, `.background`, `.secondarySystemBackground`,
  `.tertiarySystemBackground`, `.groupedBackground`, `.secondaryGroupedBackground`.
- Tint propagation: set `.tint()` once at the root or scene level — never hardcode
  accent colors deep in the view hierarchy.
- Light/dark mode support is automatic with semantic colors. If you use semantic colors
  correctly, you never need a `colorScheme` environment check for basic UI.

### Safe areas
- Never call `.ignoresSafeArea()` without a documented reason. Background colors and
  images extending under bars are the exception; interactive content clipped by a
  notch or home indicator is a bug.
- Tab bar and navigation bar backgrounds should fill under their respective bars — this
  is the only routine use of `.ignoresSafeArea(.container, edges: .bottom/.top)`.

### Accessibility
- Every custom interactive component needs `.accessibilityLabel()`.
- Non-obvious interactions need `.accessibilityHint()`.
- SF Symbols used as interactive icons need `.accessibilityLabel()` — the system name
  is not always a good label ("square.and.arrow.up" → "Share").
- Decorative images need `.accessibilityHidden(true)`.
- Respect `@Environment(\.accessibilityReduceMotion)` for all animations.

---

## Component selection rules

Use the system component unless you have a specific, documented reason to deviate.
Custom components exist to extend the platform, not replace it.

### Navigation
- `NavigationStack` (iOS 16+), not `NavigationView`.
- Large title (`.navigationBarTitleDisplayMode(.large)`) as default for root views;
  `.inline` for pushed detail views.
- Back button uses system behavior — never hide or replace it without explicit UX intent.
- Drill-down hierarchy → `NavigationLink`. Task/flow initiation → `.sheet`. Immersive
  context change → `.fullScreenCover`.

### Lists and content
- `List` for any vertically scrolling, row-based content. Not `ScrollView + LazyVStack`
  unless the design explicitly requires non-list styling.
- `Form` for settings and data entry screens.
- `.listStyle(.insetGrouped)` as default on iOS; `.listStyle(.sidebar)` on macOS.
- Swipe actions (`.swipeActions`) and context menus (`.contextMenu`) for row actions —
  not custom gesture recognizers.

### Controls
- System `Toggle`, `Slider`, `Stepper`, `Picker`, `DatePicker` — always prefer over
  custom unless brand identity requires differentiation.
- `.confirmationDialog` for destructive action confirmation, not a custom modal.
- `ShareLink` for share sheets, not UIActivityViewController bridging.
- `.searchable()` for in-list search, not a custom search bar.

### Typography
- SF Pro is the default system font and requires no declaration.
- Use `.fontDesign(.rounded)` for friendly/playful contexts.
- Use `.fontDesign(.serif)` for editorial/literary contexts.
- Use `.fontWeight()` and `.fontWidth()` modifiers for variation within a text style —
  do not reach for custom fonts to add weight hierarchy.
- SF Symbols for all icons. Always. Match symbol weight to surrounding text weight.

### Spacing
- Base grid: 4pt. All padding and spacing in multiples of 4: 4, 8, 12, 16, 20, 24, 32.
- `.padding()` with no arguments = 16pt system default. Use it as the standard
  horizontal content margin.
- List rows use automatic insets — do not manually recreate system row insets.
- Section spacing in `Form`/`List` is automatic. Do not add extra vertical padding
  between sections.

### Animation
- `.spring(response: 0.3, dampingFraction: 0.8)` as the default interactive animation.
- `.easeInOut(duration: 0.2)` for state transitions that aren't physics-based.
- `withAnimation` for imperative state changes, `.animation(_:value:)` for
  value-driven automatic animation.
- Always gate animations behind `@Environment(\.accessibilityReduceMotion)`:
  ```swift
  .animation(reduceMotion ? .none : .spring(), value: someState)
  ```
- Duration: 150–250ms for micro-interactions, 300–450ms for screen-level transitions.
  Nothing longer without strong intent.

---

## Anti-pattern blacklist

These are the tells that a SwiftUI view was built without HIG grounding. Check every
output against this list. Fix before delivery.

### Typography anti-patterns
- Hardcoded `.system(size:)` where a text style exists.
- Custom font for body copy in a utility/productivity app — SF Pro is the right choice.
- Fixed-height text containers that break Dynamic Type.
- Ignoring font weight hierarchy — all text the same weight reads as flat.

### Color anti-patterns
- Hardcoded `Color(hex:)` or `Color(.sRGB, red:...)` for semantic UI surfaces.
- `Color.white` / `Color.black` for backgrounds — use `.background` / `.primary`.
- Manually implementing dark mode with `colorScheme` checks for basic color — that is
  what semantic colors handle automatically.
- Custom tint set per-button instead of propagated from root.

### Component anti-patterns
- `ScrollView + VStack + ForEach` when `List` is the right tool.
- Custom bottom sheet built with `.offset` and `DragGesture` when `.sheet` works.
- Custom navigation bar built with `HStack` + `ZStack` fighting `NavigationStack`.
- Custom tab bar instead of `TabView` — unless the design has a documented, specific
  reason for non-standard tab chrome.
- Custom toggle, switch, or checkbox when `Toggle` would work.
- `UIViewRepresentable` wrapper for a UIKit control that has a SwiftUI equivalent.
- `.overlay` used to position elements that belong in the view hierarchy.

### Layout anti-patterns
- `.frame(width:, height:)` hardcoded on text views — breaks Dynamic Type and
  multitasking.
- Absolute positioning via `.offset` for layout — use `HStack`/`VStack`/`ZStack`.
- Manual `Spacer()` padding where `.padding()` or spacing parameters would be cleaner.
- Misusing `GeometryReader` for tasks that `ViewThatFits`, layout priorities, or
  `containerRelativeFrame` handle better.

### Accessibility anti-patterns
- Custom interactive view with no `.accessibilityLabel()`.
- SF Symbol icon with no accessibility label (system name ≠ accessible name).
- Decorative image with no `.accessibilityHidden(true)`.
- Animation with no `reduceMotion` gate.
- Text on colored backgrounds without verifying contrast ratio.

---

## Review mode — the HIG mindset pass

Triggered by: "think through from a HIG mindset", "usability/accessibility/delight pass",
"HIG review", "what could be tuned", "native feel check", or any explicit request to
critique SwiftUI UI.

When triggered, run through these four lenses and produce a numbered list of concrete
tunings. Be specific — name the view, the modifier, and what to change.

### Lens 1: Usability
- Does the navigation model match user expectation for this content type?
- Are destructive actions protected by confirmation dialogs?
- Are loading states communicated (`.redacted(reason:)`, `ProgressView`)?
- Are empty states handled with instruction, not just blank space?
- Does the primary action have the most prominent placement?

### Lens 2: Accessibility
- Dynamic Type: do all text elements scale? Do containers accommodate them?
- VoiceOver: is the reading order logical? Are all interactive elements labeled?
- Color: is semantic color used? Would the interface work in increased contrast mode?
- Motion: are animations gated on `accessibilityReduceMotion`?
- Touch targets: interactive elements should be at minimum 44×44pt.

### Lens 3: Delight
- Does the interface use any of the platform's expressive capabilities — spring
  animations, haptic feedback, SF Symbols animations, `.matchedGeometryEffect`?
- Are transitions between states smooth and communicative?
- Does the empty state or onboarding moment have personality?
- Are micro-interactions present where the user expects a response (button press,
  row tap, toggle flip)?

### Lens 4: HIG fidelity
- Are system components used where appropriate?
- Does the navigation model match Apple's guidance for this type of app?
- Are controls using standard behavior (swipe to delete, pull to refresh, context menu)?
- Does the visual hierarchy match iOS conventions (large title root, inline detail)?
- Would this feel at home next to Settings, Messages, and Notes?

Present tunings as a numbered list. Each item: one-line description of the issue,
one-line fix. Do not write essays — the list should be scannable and actionable.

---

## Iteration protocol

After the initial build, when the user flags any quirk or disappointment:

1. Ask yourself: which of the four lenses (usability, accessibility, delight, HIG) is
   this feedback pointing at?
2. Generate 3–5 concrete tuning candidates from that lens.
3. Present them as options, with the specific SwiftUI modifier or structural change
   for each.
4. Do not re-architect to address taste feedback — tune, don't rebuild.

---

## How this skill interacts with other skills

- **impeccable-design**: Covers web/HTML output. This skill covers SwiftUI/native.
  They do not conflict. If building a cross-platform app with a web component, both
  apply to their respective surfaces.
- **impeccable:frontend-design**: Web-focused. When building SwiftUI, this skill takes
  precedence. Do not apply web layout mental models (flexbox, CSS grid) to SwiftUI —
  `HStack`/`VStack`/`LazyVGrid` are the layout primitives; use them as intended.
- **impeccable:delight**: Compatible. Apply delight principles through the SwiftUI
  animation, haptics, and SF Symbols animation systems — not through custom web-style
  micro-interactions.
- **impeccable:audit**: When auditing SwiftUI output, route the audit through the four
  HIG lenses above rather than the web audit checklist.

---

## Token-conscious implementation note

Apply these principles silently. Do not narrate which anti-patterns were avoided or
list which HIG sections were consulted. The output should feel native. If it does,
the skill worked.
