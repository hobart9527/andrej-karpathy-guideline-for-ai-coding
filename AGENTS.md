# AGENTS.md

Behavioral guidelines to reduce common LLM coding mistakes.

Adapted for Codex from the Andrej Karpathy-inspired `CLAUDE.md` pattern.

Tradeoff: these guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

Don't assume. Don't hide confusion. Surface tradeoffs.

Before implementing:

- State assumptions explicitly.
- If uncertain, ask instead of guessing.
- If multiple interpretations exist, present them instead of picking silently.
- If a simpler approach exists, say so.
- If something is unclear enough to risk the wrong change, stop and name the confusion.

## 2. Simplicity First

Write the minimum code that solves the problem. Nothing speculative.

- No features beyond what was asked.
- No abstractions for single-use code.
- No flexibility or configurability that was not requested.
- No defensive handling for impossible scenarios unless the project already requires it.
- If 200 lines could clearly be 50, simplify before shipping.

Ask yourself: would a senior engineer say this is overcomplicated? If yes, simplify.

## 3. Surgical Changes

Touch only what you must. Clean up only issues introduced by your own change.

When editing existing code:

- Do not improve adjacent code, comments, or formatting unless the task requires it.
- Do not refactor unrelated code.
- Match existing style and local patterns unless asked otherwise.
- If you notice unrelated dead code or issues, mention them instead of changing them.

When your changes create orphans:

- Remove imports, variables, and functions made unused by your change.
- Do not remove unrelated pre-existing dead code unless asked.

The test: every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

Turn tasks into verifiable goals and loop until they are verified.

- Define success criteria before or during implementation.
- For bug fixes, prefer a reproduction or regression test when practical.
- For validation changes, prefer tests for invalid and valid inputs when practical.
- For refactors, preserve behavior and verify before and after.
- For multi-step work, use a short plan where each step has a verification check.

Example:

1. Reproduce or define the target behavior -> verify with a test or direct check.
2. Implement the smallest change -> verify with the relevant test, build, or command.
3. Clean up only change-caused fallout -> verify nothing regressed.

Strong success criteria let the model loop independently. Weak criteria like "make it work" invite mistakes.

## 5. Preserve Object Boundaries

Keep the information architecture clean even when simplifying for speed.

- You may simplify flows, UI, or implementation, but do not silently merge distinct domain objects just to close the loop faster.
- Before reusing an existing object for a new need, check whether the two concepts truly share ownership, lifecycle, and responsibilities.
- If the boundary between objects is still unclear, stop and name the ambiguity instead of encoding a convenient shortcut.
- Prefer temporary feature reduction over temporary object mixing.
- Treat object ownership errors as structural debt: they make every later feature harder, more coupled, and more expensive to change.

The heuristic: simplified behavior is usually recoverable later; collapsed object boundaries usually spread.
