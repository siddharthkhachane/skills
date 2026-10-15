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
