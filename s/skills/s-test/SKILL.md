---
name: s-test
description: Diagnose a failing test - what it verifies, code path trace, implementation bug vs. outdated test, then minimal fix.
argument-hint: <test name/code and the exact error output>
disable-model-invocation: true
---

This test is failing: $ARGUMENTS

(If no test or output was given above, run the test suite to find the failing test and capture its exact output.)

Before proposing any fix, explain in plain language what this test is actually verifying and why it exists. Trace the exact code path the test exercises, step by step. Then tell me whether the root cause is a bug in the implementation code or a bug or outdated assumption in the test itself, and show me the specific evidence from the trace that supports your conclusion. Only after that, propose the minimal fix required.
