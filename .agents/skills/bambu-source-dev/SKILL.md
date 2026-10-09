---
name: bambu-source-dev
description: Maintain bambu fork source, repository documentation and agent guidance with local ownership, evidence and runtime boundaries.
---

# Fork source maintenance

Read [AGENTS.md](../../../AGENTS.md), [SPEC.md](../../../SPEC.md) and
[README.md](../../../README.md). `internal/cmd/` owns CLI/output wiring;
`internal/printer/` owns status and HMS decoding; `internal/preflight/` owns
printer gates; `internal/job/` owns inspected 3MF payloads and AMS mapping.
Slicer, FTPS and camera implementations retain their separate owners.
`skills/bambu/` owns the consumer-facing printer workflow; preserve its explicit
file/plate approval rules. JSON fields and exit codes are public API.

For source changes, run `make ci`, the existing fmt/lint/vet/race-test/build gate.
Its fakes do not need a printer and cannot prove a completed physical print.
Documentation maintenance checks routes, metadata and consistency with SPEC
and implementation. Update CHANGELOG.md as required by the root guide.
Do not run live-test, discovery, credential setup, printer sends, settings,
install or release procedures for a documentation task. A dry-run payload is
simulated dispatch evidence; live firmware observations require their own
explicit scope and collection time.

## Repository delivery

Inspect the actual remotes, default branch and target GitHub repository before
publication. This task updates `jlapenna/bambu`; ownership of a fork does not
authorize an upstream merge. Use a dedicated feature worktree from the freshly
fetched configured base, preserving other branches and sessions. Read
[worktree-hygiene](https://github.com/jlapenna/repo-tools/blob/main/plugins/repo-tools/skills/worktree-hygiene/SKILL.md)
and [land-pr](https://github.com/jlapenna/repo-tools/blob/main/plugins/repo-tools/skills/land-pr/SKILL.md)
for normal checked delivery and cleanup; never bypass protection or hooks.

## Harness upkeep

Use the [shared harness-maintenance workflow](https://github.com/jlapenna/repo-tools/blob/main/plugins/repo-tools/skills/harness-maintenance/SKILL.md), adapted from
[Ryan Lopopolo's field guide](https://github.com/lopopolo/harness-engineering/tree/226c8d35fb6ea3ed55467753dba6dea2b5fd5778). Corroborate observed failures and
repair their earliest owner, keeping the root guide a route and conditional
procedures in references. Preserve current contracts separately from chronology.
A source check proves structure or consistency; comparable fresh use is required
to claim improved agent behavior. Keep fork decisions local and refer to shared
implementations rather than copying them across repositories.
