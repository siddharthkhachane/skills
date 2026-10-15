# Recreate my s-* skills

Instructions for Claude Code: for each section below, create the file at `~/.claude/skills/<name>/SKILL.md` with exactly the text in the code block (including the `---` frontmatter). Create the folders if needed. Do not change the wording. When done, list the files created and tell me to restart Claude Code.

Optional last step: save the "Style" section as `~/.claude/CLAUDE.md` (merge with any existing file, do not overwrite).

## s-api

File: `~/.claude/skills/s-api/SKILL.md`

````markdown
---
name: s-api
description: Catalog every API endpoint (method, route, handler, auth, params) and flag unauthenticated, unused, and inconsistent ones.
disable-model-invocation: true
---

Catalog every API endpoint exposed by this codebase. For each one list: HTTP method, full route path, the file and function that handles it, required authentication or authorization, request parameters or body shape, and a one sentence description of what it does. Group the endpoints by domain area, for example auth, users, billing. After the catalog, flag three things specifically: endpoints with no visible authentication check, endpoints that appear unused anywhere in the frontend or tests, and any inconsistent patterns across endpoints, such as some routes validating input and others not.
````

## s-arch

File: `~/.claude/skills/s-arch/SKILL.md`

````markdown
---
name: s-arch
description: Map the architecture - layers, responsibilities, communication, pattern, dependency diagram, violations. No code written.
disable-model-invocation: true
---

Map the architecture of this codebase without writing any code. Identify every major layer or module, for example API layer, service layer, data access layer, background jobs, frontend. For each layer, list the folders and files that belong to it and the responsibilities it owns. Describe how layers communicate: direct function calls, HTTP, message queue, or events. Name the architectural pattern in use, layered, hexagonal, MVC, microservices, or monolith, and justify your answer with specific file references, not general impressions. Draw the dependency direction between layers as a text diagram using arrows. Finally, list any places where the architecture is violated, such as a UI file importing directly from the database layer, and explain why that is a problem.
````

## s-bug

File: `~/.claude/skills/s-bug/SKILL.md`

````markdown
---
name: s-bug
description: Debug by tracing logical flow - hypothesis, confidence, suspect line, and where to log. No fix until cause is confirmed.
argument-hint: <bug and exact symptom / error message>
disable-model-invocation: true
---

I am debugging this issue: $ARGUMENTS

Before changing any code, trace the logical flow of the feature involved, from the entry point to where the bug manifests. Identify every place the relevant variable, state, or data is read, set, or transformed along that path. Based on that trace, give me your top hypothesis for the root cause, your confidence level, and the specific line or function you believe is responsible. Tell me exactly where you would add a temporary log statement to confirm the hypothesis before we touch any logic. Do not propose a fix until the cause is confirmed.
````

## s-explore

File: `~/.claude/skills/s-explore/SKILL.md`

````markdown
---
name: s-explore
description: First-pass tour of an unfamiliar repo - what it does, stack, folder map, files to read first, run/test commands.
disable-model-invocation: true
---

Act as a senior engineer doing a first pass on this repository. Read the README, package manifest, and entry point files first. Then produce: 1) a summary of what this application does and who it is for, 2) the tech stack with exact versions pulled from the manifest files, 3) an annotated folder tree covering only directories that matter, skip node_modules, build output, and vendor folders, with one line per folder explaining its role, 4) the five to eight files you would read first if you had one hour, ranked by importance, with a reason for each, 5) the exact commands to install dependencies, run the project locally, and run the test suite, taken directly from config files, not guessed. If something is unclear from the code, say so instead of assuming.
````

## s-feature

File: `~/.claude/skills/s-feature/SKILL.md`

````markdown
---
name: s-feature
description: Investigate and plan a new feature (files touched, patterns to copy, reuse, edge cases) - then wait for approval before coding.
argument-hint: <feature description>
disable-model-invocation: true
---

I want to add the following feature to this codebase: $ARGUMENTS

Do not write any code yet. First investigate: 1) which existing files and modules this feature will most likely touch, 2) whether a similar feature already exists that I should copy the pattern from, and exactly where it lives, 3) the naming conventions, error handling, and testing patterns used elsewhere so my code matches them, 4) existing utilities, hooks, or services I should reuse instead of writing from scratch, 5) edge cases this codebase seems to care about, based on how similar features validate input and handle errors. Then output a numbered implementation plan with file paths and a one line description of the change needed in each file. Stop and wait for my approval before writing any code.
````

## s-find

File: `~/.claude/skills/s-find/SKILL.md`

````markdown
---
name: s-find
description: Find where a specific behavior is implemented and show the full call chain with file paths and line numbers.
argument-hint: <behavior, e.g. discount code gets validated at checkout>
disable-model-invocation: true
---

I need to find exactly where this happens in this codebase: $ARGUMENTS

Do not rely on filenames alone, search the actual code for relevant logic, string literals, and function names. Once found, show me the full call chain: which function is called first, what it calls next, and so on until the behavior is fully implemented. Include file paths and line numbers for every step. Explain any non obvious logic, such as why a particular condition or order of operations is used.
````

## s-flow

File: `~/.claude/skills/s-flow/SKILL.md`

````markdown
---
name: s-flow
description: Trace how a specific piece of data flows through the system - entry, transforms, storage, reads - and flag duplication.
argument-hint: <data, e.g. a user's email address>
disable-model-invocation: true
---

Trace how this data flows through this entire system: $ARGUMENTS

Start from every point it can be created or entered, signup form, API import, admin panel, and follow it through every transformation, validation, storage location, and place it gets read or displayed again. Present this as an ordered sequence of steps with file and function references at each step, not just a list of files that mention it. Flag any place the data is duplicated, cached, or stored in more than one location, since that is where inconsistency bugs usually live.
````

## s-help

File: `~/.claude/skills/s-help/SKILL.md`

````markdown
---
name: s-help
description: List every s-* skill with what it does and its argument hint. Always reads the skill files live, so new s-* skills appear automatically.
disable-model-invocation: true
---

List all my `s-*` skills. Do not rely on memory or a fixed list - discover them now:

1. Glob `~/.claude/skills/s-*/SKILL.md` (user-level) and `.claude/skills/s-*/SKILL.md` in the current project (project-level). Also check `~/.claude/commands/s-*.md` and `.claude/commands/s-*.md`.
2. Read only the YAML frontmatter of each file (`name`, `description`, `argument-hint`).
3. Print one table sorted by name: `/name <argument-hint>` | description | scope (user or project). Skip `s-help` itself only if the table would otherwise be empty; otherwise include it.
4. End with the total count and one line: "Add a new skill by creating `~/.claude/skills/s-<name>/SKILL.md` with `name`, `description` and optional `argument-hint` frontmatter - it will show up here automatically."

If $ARGUMENTS is given, only show skills whose name or description contains that text.
````

## s-known

File: `~/.claude/skills/s-known/SKILL.md`

````markdown
---
name: s-known
description: Sort a problem into known knowns, known unknowns, unknown knowns and unknown unknowns, plus a short codebase blind-spot pass and a sharper prompt. Deliberately terse.
argument-hint: <the problem or what you want to add>
disable-model-invocation: true
---

Problem: $ARGUMENTS

Do two things, in this order: a blind-spot pass, then the 2x2. Be brief. Extra text confuses me more.

## Step 1 - Blind-spot pass (silent; only its results are shown)

I may not know this codebase. Do not take my wording at face value: my terms, assumptions and scope may be wrong for this repo.
- If the problem concerns code in the current repo, look at it first: read `CLAUDE.md` and `NOTES.md` if present, then at most 5 more files or searches, chosen for relevance to the problem (entry points, the closest existing feature, related tests). Say which files you read in one line.
- If the problem is not about the current repo, skip the reading and say "no repo check".
- Find things relevant to the problem that I probably do not know: something already built that overlaps, a constraint or safety rule, a convention to follow, a past failure or note, or a term of mine that means something different here.
- Only report what you actually found in files, each with a `file:line` or file name. Never guess or fill with generic advice.

## Step 2 - Output

Output ONLY the format below. No intro, no recap of the problem, no closing summary, no extra headings.

Limits:
- At most 3 bullets per quadrant. Each bullet is one line, 12 words or fewer. Fewer is better; write "none found" rather than padding.
- Do not edit files, run tests, or run the app. Do not solve the problem. Give one next step only.

Quadrant rules:
- KNOWN KNOWNS: facts or constraints that are stated or checkable. Add "(unverified)" if not checked. Facts found in Step 1 go here with their file reference.
- KNOWN UNKNOWNS: questions that can be written down and answered by a lookup or a test. Write each as a question. Include the questions that Step 1 made visible.
- UNKNOWN KNOWNS: assumptions or tacit knowledge probably in play but never stated. Write each as "Assuming ...".
- UNKNOWN UNKNOWNS: these cannot be listed. Give up to 3 cheap probes (a spike, a review, an adversarial case, asking someone). Do not invent specific surprises.

Format (exactly):

| | You hold the answer | You don't |
|---|---|---|
| **Aware of it** | **Known knowns**<br>- ... | **Known unknowns**<br>- ...? |
| **Not aware of it** | **Unknown knowns**<br>- Assuming ... | **Unknown unknowns (probes)**<br>- ... |

**Blind spots found:** (max 3 bullets, 15 words or fewer each, each with a file reference; or "none found")
- ...

**Sharper prompt:** a rewritten version of my request, in a code block, 40 words or fewer, using the real file names, terms and constraints from the blind-spot pass. Do not run it.

**Next step:** one sentence - the single known unknown or assumption to resolve first, and how.
````

## s-legacy

File: `~/.claude/skills/s-legacy/SKILL.md`

````markdown
---
name: s-legacy
description: Onboard an inherited legacy repo - stack, core logic, fragile areas, safe first changes, as a short brief.
disable-model-invocation: true
---

Treat this repository as an undocumented legacy system I just inherited with no handoff. Identify the language, framework, and major dependency versions in use, and whether any are outdated or deprecated. Find where the actual business logic lives versus boilerplate or scaffolding. Identify code that looks fragile: global mutable state, tightly coupled modules, magic numbers or strings with no explanation, missing error handling around external calls. Tell me what would most likely break first if I made a careless change, and why. Compile this into a short brief organized under these exact headings: Stack, Core Logic, Fragile Areas, Safe First Changes.
````

## s-pr

File: `~/.claude/skills/s-pr/SKILL.md`

````markdown
---
name: s-pr
description: Strict senior-engineer review of a PR you did not write - must fix / should fix / nice to have, with file and line citations.
argument-hint: [PR number, URL, or branch - blank for current branch diff]
disable-model-invocation: true
---

Review this pull request as a strict senior engineer doing a real code review, not a summary. The PR to review: ${ARGUMENTS:-the current branch's diff against the main branch}.

Check for: correctness against the stated intent of the PR, unhandled edge cases, naming that does not match the rest of the codebase, missing or weak test coverage for the new logic, security issues such as unvalidated input or exposed secrets, and code that duplicates functionality that already exists elsewhere in the repo. Organize findings into three sections, must fix before merge, should fix, and nice to have. For each finding, cite the exact file and line. Do not rewrite the code yourself, explain the problem clearly enough that I can fix it myself.
````

## s-refactor

File: `~/.claude/skills/s-refactor/SKILL.md`

````markdown
---
name: s-refactor
description: Pre-refactor impact analysis - all dependents, test coverage, hidden reliance, then a small-steps plan with tests to run.
argument-hint: <file, function, or module to refactor>
disable-model-invocation: true
---

I want to refactor: $ARGUMENTS

Before any changes, find every place in the codebase that imports it, calls it, or depends on its output or side effects, directly or indirectly, including tests. Present this as a dependency list with file paths. For each dependent, note whether it is covered by an automated test. Flag anything relying on this code's current behavior in a way that is not obvious from its name or signature, such as a specific return shape or a side effect like writing to a cache. Then propose a refactor plan broken into small, independently safe steps, and tell me which existing tests to run after each step.
````

## s-ship

File: `~/.claude/skills/s-ship/SKILL.md`

````markdown
---
name: s-ship
description: Pre-PR check of uncommitted changes - conventions, edge cases, test gaps, hidden impact, and a go / no-go call.
disable-model-invocation: true
---

Review my current uncommitted changes against the rest of this codebase before I open a PR. Check: does this change match the existing patterns and conventions in files near it, are there edge cases visible in the diff that are not handled, is there missing test coverage for the new or changed logic, does this change affect any other part of the codebase that is not obvious from the diff alone, and is there anything here you would want a second engineer to specifically double check. Give me a short go or no go recommendation at the end with your reasoning stated plainly.
````

## s-test

File: `~/.claude/skills/s-test/SKILL.md`

````markdown
---
name: s-test
description: Diagnose a failing test - what it verifies, code path trace, implementation bug vs. outdated test, then minimal fix.
argument-hint: <test name/code and the exact error output>
disable-model-invocation: true
---

This test is failing: $ARGUMENTS

(If no test or output was given above, run the test suite to find the failing test and capture its exact output.)

Before proposing any fix, explain in plain language what this test is actually verifying and why it exists. Trace the exact code path the test exercises, step by step. Then tell me whether the root cause is a bug in the implementation code or a bug or outdated assumption in the test itself, and show me the specific evidence from the trace that supports your conclusion. Only after that, propose the minimal fix required.
````

## s-trace

File: `~/.claude/skills/s-trace/SKILL.md`

````markdown
---
name: s-trace
description: Trace the full backend execution path of an endpoint or action - middleware, handlers, services, DB calls, branches, async paths.
argument-hint: <endpoint or action, e.g. POST /api/orders>
disable-model-invocation: true
---

Trace the complete backend execution path for: $ARGUMENTS

Start at the route definition and follow the code exactly as it executes: middleware in order, the controller or handler function, every service or helper function it calls, all database queries or external API calls, and the final response returned to the client. For each step, give the file path and function name. Note every conditional branch, if/else, try/catch, or feature flag that changes the execution path, and explain the condition under which each branch is taken. If async or background processing is involved, queues, workers, webhooks, trace that separately and note where the two paths reconnect, if they ever do.
````

## Style (optional)

````markdown
# Response style

- Reply in the most concise form possible.
- Skip pleasantries, preambles, and recaps of my question.
- No phrases like "I'd be happy to", "great question", "let me explain".
- Drop articles and filler words wherever the meaning stays clear.
- Prefer short declarative sentences.
- If a tool is needed, run it first and show only the result. Do not narrate steps.
````
