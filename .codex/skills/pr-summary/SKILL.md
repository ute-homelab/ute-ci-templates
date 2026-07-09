---
name: pr-summary
description: Prepare a concise Pull Request summary for UTE projects, including purpose, changed areas, validation, risks, docs impact, and rollback notes.
---
# UTE PR Summary

> Canonical portable skill (agent-neutral). Adapter copies: `adapters/claude/.claude/skills/pr-summary/SKILL.md`, `adapters/codex/skills/pr-summary/SKILL.md` — keep in sync with this file. See `docs/portable-skills.md`.

Canonical procedure: `core/standards/git/pull-requests.md`. Read it before
running this skill (there is no dedicated `core/sdlc/` file for this one —
it's Git/PR process, not a lifecycle stage).

## Goal

Prepare a PR description from the current diff and feature docs.

## Inputs

Current diff, feature folder (if one exists), test/validation results.

## Process

1. Read and apply `core/standards/git/pull-requests.md`.
2. When producing a GitHub-ready PR description, fill
   `core/templates/github/.github/pull_request_template.md` directly
   rather than inventing sections.
3. Summarize purpose, changes, verification actually run, docs impact,
   risks, and rollback notes from the real diff and feature docs.
4. Be specific — do not claim checks passed unless they actually ran.

## Required outputs

```md
## Purpose

## Changes

## Verification

## Docs impact

## Risks

## Rollback

## Notes for reviewer
```

## Safety constraints

Never fabricate test/verification results. Never include secrets found in
the diff.

## References

- `core/standards/git/pull-requests.md` — required sections and rationale
- `core/templates/github/.github/pull_request_template.md` — fillable GitHub version

## Required Final Output: Agent Run Report

Every run of this skill must end with:

### Agent Run Report

- Skill:
- Project type/archetype:
- Confidence: high / medium / low
- Inputs used:
- Applicable standards used:
- Missing inputs:
- Assumptions made:
- Project documentation gaps:
- UTE standards gaps:
- Recommended updates to `ute-agent-standards`:
- Items that belong to other UTE repositories:
- Follow-up questions, if any:
