# UTE Agent Standards — Codex

This is the durable guidance entry point for Codex (or any similarly-driven
agent) working on a UTE project. Canonical, agent-neutral standards live in
`core/` — this file is the Codex-specific translation of them, the way
`adapters/claude/CLAUDE.md` is the Claude-specific translation. When in
doubt, `core/` wins; this file should never contradict it.

## Repository identity

You are working on a UTE project using the **UTE AI Agent Standards**
(`core/`, `adapters/claude/`, `adapters/codex/`). Claude is the first-class
adapter this standard set was originally built around; Codex is the second
first-class adapter. Both read the same `core/` content — they differ only
in how it's packaged and invoked.

## Required workflow

For any non-trivial change, follow this order — do not jump straight to
implementation:

1. **Discovery** (first pass on an unfamiliar project only) — see
   `core/sdlc/project-discovery.md`.
2. **Architecture review** for changes crossing module/service boundaries or
   touching infrastructure — see `core/sdlc/architecture-review.md`.
3. **Feature planning** — create/update `features/<name>/` per
   `core/sdlc/feature-planning.md` before writing code.
4. **Implementation** — implement the reviewed plan per
   `core/sdlc/implementation-pass.md`, in small reviewable steps.
5. **Change audit** — self-audit the diff per `core/sdlc/change-audit.md`.
6. **Test strategy** — per `core/sdlc/test-strategy.md`, scaled to risk.
7. **Docs sync** — per `core/sdlc/docs-sync.md`.
8. **Release readiness** — per `core/sdlc/release-readiness.md`, before
   merging/shipping.
9. **PR summary** — per `core/standards/git/pull-requests.md`.

Not every change needs every stage — a one-line docs fix skips straight to
implementation and docs sync. Scale to risk and size, per
`core/standards/workflow.md`.

Use `core/sdlc/rollback-plan.md`, `core/sdlc/production-readiness.md`, and
the DevOps review process (`core/archetypes/devops-infra/`) ad hoc, whenever
a change touches infrastructure, is risky enough to need an explicit
rollback plan, or the question is about a service's ongoing operational
posture.

Use `core/sdlc/standards-gap-audit.md` (`standards-gap-audit` skill)
whenever a skill's Agent Run Report shows non-trivial missing
inputs/assumptions/gaps, or a run's output is unclear — it classifies
whether the fix belongs in the project, a skill, a standard, an archetype,
or a different UTE repository. See `docs/evaluation-loop.md`.

## Use `core/` as the canonical source

Do not restate or reinvent standards already defined in `core/`. When a task
maps to a `core/sdlc/<stage>.md` file or a `core/standards/` file, read it
and follow it. `adapters/codex/skills/` gives you short, Codex-shaped
summaries with pointers back to the canonical text — read the canonical
file, don't guess from the summary alone for anything non-trivial.

## Do not bypass feature specs

Do not implement non-trivial changes without a reviewed feature folder
(`features/<name>/`, per `core/sdlc/feature-planning.md`). If one doesn't
exist yet, create it first and get it reviewed before implementing — this
is not optional for anything beyond a small, contained fix.

## Do not run destructive or deploy commands

Never run `terraform apply`, `terraform destroy`, `kubectl delete`,
`docker system prune`, `rm -rf`, force-pushes, or production
deploy/release/migration commands unless the user has explicitly asked for
that exact action and the rollback path is clear. See
`core/standards/security.md`. Codex has no built-in equivalent of Claude's
`permissions.deny`/hooks mechanism as of this writing — this file is the
only enforcement layer available to Codex, so treat it as load-bearing, not
advisory.

## Documentation sync rules

When a change alters behavior, architecture, environments, CI/CD,
deployment, secrets, rollback, observability, or operational flow, update
the relevant docs in the same change — see `core/standards/documentation.md`
and `core/sdlc/docs-sync.md`. Never leave a change's docs impact as a silent
gap.

## Testing expectations

Prefer project-native test/validation commands; never invent commands that
aren't defined in the project. Add tests for new behavior where test
infrastructure exists, and a regression test for bug fixes when practical.
If tests cannot be run in this environment, say exactly why and what should
be run manually. See `core/standards/testing.md` and
`core/sdlc/test-strategy.md`.

## Git / PR rules

Follow `core/standards/git/branching.md`, `core/standards/git/commits.md`,
and `core/standards/git/pull-requests.md`. Keep diffs small and reviewable.
Do not force-push or rewrite history unless explicitly requested. Validate
branch names and commit messages with `scripts/validate-branch-name.sh` /
`scripts/validate-commit-message.sh` when available.

## Vendor-skills policy

Do not import, embed, or reproduce third-party skill content into this
repository or a consuming project's Codex skills. `vendor-skills/` at the
repository root is the only place reviewed/attributed third-party skills may
eventually live, and as of this writing nothing has been imported there —
see `docs/vendor-skills-policy.md`. Never copy content from a marketplace,
catalog, or another team's shared-skills archive directly into
`adapters/codex/skills/`.

## Unknowns must be marked explicitly

If something about the project, its conventions, or the right course of
action cannot be determined from the repo or explicit user instruction,
state it as an open question rather than guessing or inventing an answer.
This applies to build/test/deploy commands, architectural assumptions, and
anything security- or deployment-sensitive.

## Skills

See `adapters/codex/skills/` for the full list (mirrors the Claude adapter's
the shared UTE skill set in spirit — see `adapters/codex/README.md` for what's
intentionally different).
