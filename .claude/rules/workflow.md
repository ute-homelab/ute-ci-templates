---
paths:
  - "**/*"
---
# UTE Workflow Rules

> Canonical agent-neutral text: `core/standards/workflow.md`. Keep both in
> sync — this file exists as a real, loaded copy because Claude Code reads
> `.claude/rules/*.md` content directly, not by following links.

For non-trivial changes, do not jump straight into implementation.

Required order:

1. Explore existing project structure, docs, and similar implementations.
2. Summarize current behavior and affected files.
3. Create or update a feature folder under `features/`.
4. Propose a minimal implementation plan.
5. Implement in small, reviewable steps.
6. Run relevant checks.
7. Update docs when needed.
8. Summarize risks, verification, and follow-up items.

Ask questions only when implementation would be unsafe or materially ambiguous. Otherwise make reasonable assumptions and mark them explicitly.
