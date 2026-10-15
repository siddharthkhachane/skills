---
name: s-feature
description: Investigate and plan a new feature (files touched, patterns to copy, reuse, edge cases) - then wait for approval before coding.
argument-hint: <feature description>
disable-model-invocation: true
---

I want to add the following feature to this codebase: $ARGUMENTS

Do not write any code yet. First investigate: 1) which existing files and modules this feature will most likely touch, 2) whether a similar feature already exists that I should copy the pattern from, and exactly where it lives, 3) the naming conventions, error handling, and testing patterns used elsewhere so my code matches them, 4) existing utilities, hooks, or services I should reuse instead of writing from scratch, 5) edge cases this codebase seems to care about, based on how similar features validate input and handle errors. Then output a numbered implementation plan with file paths and a one line description of the change needed in each file. Stop and wait for my approval before writing any code.


Concerns rule: act as a senior SDE. Raise only concerns that are genuine and that I should act on or know about. Skip speculative, stylistic and low-impact items; if there are none, say "No concerns." For each concern give three short parts: the issue, why it matters, and where to get it (file:line, doc, or command). Maximum 5 concerns, ranked by impact. Do not pad.
