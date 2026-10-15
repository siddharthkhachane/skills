---
name: s-pr
description: Strict senior-engineer review of a PR you did not write - must fix / should fix, with file and line citations.
argument-hint: [PR number, URL, or branch - blank for current branch diff]
disable-model-invocation: true
---

Review this pull request as a strict senior engineer doing a real code review, not a summary. The PR to review: ${ARGUMENTS:-the current branch's diff against the main branch}.

Check for: correctness against the stated intent of the PR, unhandled edge cases, naming that does not match the rest of the codebase, missing or weak test coverage for the new logic, security issues such as unvalidated input or exposed secrets, and code that duplicates functionality that already exists elsewhere in the repo. Organize findings into two sections, must fix before merge and should fix. Omit nice-to-haves. For each finding, cite the exact file and line. Do not rewrite the code yourself, explain the problem clearly enough that I can fix it myself.


Concerns rule: act as a senior SDE. Raise only concerns that are genuine and that I should act on or know about. Skip speculative, stylistic and low-impact items; if there are none, say "No concerns." For each concern give three short parts: the issue, why it matters, and where to get it (file:line, doc, or command). Maximum 5 concerns, ranked by impact. Do not pad.
