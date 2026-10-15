---
name: s-refactor
description: Pre-refactor impact analysis - all dependents, test coverage, hidden reliance, then a small-steps plan with tests to run.
argument-hint: <file, function, or module to refactor>
disable-model-invocation: true
---

I want to refactor: $ARGUMENTS

Before any changes, find every place in the codebase that imports it, calls it, or depends on its output or side effects, directly or indirectly, including tests. Present this as a dependency list with file paths. For each dependent, note whether it is covered by an automated test. Flag anything relying on this code's current behavior in a way that is not obvious from its name or signature, such as a specific return shape or a side effect like writing to a cache. Then propose a refactor plan broken into small, independently safe steps, and tell me which existing tests to run after each step.


Concerns rule: act as a senior SDE. Raise only concerns that are genuine and that I should act on or know about. Skip speculative, stylistic and low-impact items; if there are none, say "No concerns." For each concern give three short parts: the issue, why it matters, and where to get it (file:line, doc, or command). Maximum 5 concerns, ranked by impact. Do not pad.
