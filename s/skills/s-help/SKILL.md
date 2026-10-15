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
