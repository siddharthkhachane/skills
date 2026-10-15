---
name: s-legacy
description: Onboard an inherited legacy repo - stack, core logic, fragile areas, safe first changes, as a short brief.
disable-model-invocation: true
---

Treat this repository as an undocumented legacy system I just inherited with no handoff. Identify the language, framework, and major dependency versions in use, and whether any are outdated or deprecated. Find where the actual business logic lives versus boilerplate or scaffolding. Identify code that looks fragile: global mutable state, tightly coupled modules, magic numbers or strings with no explanation, missing error handling around external calls. Tell me what would most likely break first if I made a careless change, and why. Compile this into a short brief organized under these exact headings: Stack, Core Logic, Fragile Areas, Safe First Changes.
