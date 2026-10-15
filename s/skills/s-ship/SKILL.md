---
name: s-ship
description: Pre-PR check of uncommitted changes - conventions, edge cases, test gaps, hidden impact, and a go / no-go call.
disable-model-invocation: true
---

Review my current uncommitted changes against the rest of this codebase before I open a PR. Check: does this change match the existing patterns and conventions in files near it, are there edge cases visible in the diff that are not handled, is there missing test coverage for the new or changed logic, does this change affect any other part of the codebase that is not obvious from the diff alone, and is there anything here you would want a second engineer to specifically double check. Give me a short go or no go recommendation at the end with your reasoning stated plainly.
