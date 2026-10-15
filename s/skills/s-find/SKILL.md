---
name: s-find
description: Find where a specific behavior is implemented and show the full call chain with file paths and line numbers.
argument-hint: <behavior, e.g. discount code gets validated at checkout>
disable-model-invocation: true
---

I need to find exactly where this happens in this codebase: $ARGUMENTS

Do not rely on filenames alone, search the actual code for relevant logic, string literals, and function names. Once found, show me the full call chain: which function is called first, what it calls next, and so on until the behavior is fully implemented. Include file paths and line numbers for every step. Explain any non obvious logic, such as why a particular condition or order of operations is used.
