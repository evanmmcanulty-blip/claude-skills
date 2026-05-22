---
name: karpathy-guidelines
description: >
  Behavioral guidelines to reduce common LLM coding mistakes — overcomplication, scope creep,
  unrelated refactors, hidden assumptions, weak success criteria. Use when writing, reviewing,
  or refactoring code. Trigger on "#karpathy", "karpathy mode", "code carefully", "be surgical",
  "minimum viable code", "no scope creep", or any signal the user wants disciplined coding
  behavior. Also fires implicitly on any non-trivial coding task. Pairs with prompt-boost
  (engineers the prompt that delivers the coding task) and fortify (audits the shipped code
  for security). Distinct from those skills: this one governs HOW Claude writes code in the
  middle of a task, not the prompt or the post-ship audit. Biases toward caution over speed —
  for trivial tasks, judgment overrides.
license: MIT
---

# Karpathy Guidelines

Behavioral guidelines to reduce common LLM coding mistakes, derived from [Andrej Karpathy's observations](https://x.com/karpathy/status/2015883857489522876) on LLM coding pitfalls.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

## 5. Write for the 10-Year Maintainer

**Write as though someone will maintain this app for 10 years while only touching it occasionally.**

- Keep modules organized so structure is obvious without running the code.
- Make behavior discoverable — names, seams, and boundaries should tell the story.
- Write tests that are meaningful, not just passing — a test that doesn't catch regressions is noise.
- Make seams easy to verify: a reader should be able to trace what enters, what changes, and what exits without reverse-engineering the whole module.

On security, explicitness is the discipline:
- Unsafe inputs must be marked at the boundary where they enter — not assumed handled somewhere downstream.
- Trust boundaries must be visible in the code structure, not just in the developer's head.
- Credentials must be isolated and named so they're impossible to miss in a review.
- Generated output escaping must be explicit at the output site — not delegated to "the framework probably does it."

The test: Could someone who hasn't touched this code in two years understand its security envelope from reading it cold? If not, it's not done.

If security seams are implicit rather than explicit, run `#FORTIFY` before shipping.

---

## Final Standard

The work passes when:

- Every changed line traces directly to the user's request — no speculative additions,
  no adjacent-improvement creep.
- Assumptions were stated explicitly before implementation, not embedded silently.
- The code is the minimum that solves the problem — a senior engineer reading it would
  not call it overcomplicated.
- Existing style was matched, not "improved" in passing.
- Success criteria for the change are stated in verifiable form (test passes, output
  matches, behavior reproduces) — not "make it work."

If the diff is twice as large as the user's request, fail. The diff size should be
proportional to the request, not to what Claude noticed adjacent to it.

If a confusion was hidden instead of surfaced, fail. The cost of asking is low; the
cost of guessing wrong is rework.

If new abstractions were introduced for code with one caller, fail. Three similar lines
beat a premature abstraction.
