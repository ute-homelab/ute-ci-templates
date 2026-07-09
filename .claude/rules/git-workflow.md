---
paths:
  - "**/*"
---
# UTE Git Workflow Rules

> Canonical agent-neutral text: `core/standards/git/`. Keep both in sync.

- Keep diffs small and reviewable.
- Do not force push.
- Do not rewrite history unless explicitly requested.
- Do not commit generated secrets, dumps, local config, temporary logs, or session notes.
- PR summaries must include: purpose, changed files, verification, risks, rollback notes if relevant.
