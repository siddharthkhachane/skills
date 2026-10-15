---
name: s-bug
description: Debug by tracing logical flow - hypothesis, confidence, suspect line, and where to log. No fix until cause is confirmed.
argument-hint: <bug and exact symptom / error message>
disable-model-invocation: true
---

I am debugging this issue: $ARGUMENTS

Before changing any code, trace the logical flow of the feature involved, from the entry point to where the bug manifests. Identify every place the relevant variable, state, or data is read, set, or transformed along that path. Based on that trace, give me your top hypothesis for the root cause, your confidence level, and the specific line or function you believe is responsible. Tell me exactly where you would add a temporary log statement to confirm the hypothesis before we touch any logic. Do not propose a fix until the cause is confirmed.
