# Inspect Source And Target

## Identity

- Node ID: 01-inspect-source-and-target
- Parent: 01-sync-codex-skill
- Status: done
- Stage: complete

## Objective

Inspect the repository skill materials and the currently installed Codex skill to determine the exact update scope.

## Deliverable

A clear mapping of source behavior to target Codex skill files that need changes.

## Acceptance Criteria

- The repository README and command files have been reviewed.
- The installed Codex skill files have been reviewed.
- The adaptation approach is concrete enough to implement in one pass.

## Dependencies

- None yet.

## Children

- None yet. Add child folders under `children/` when further decomposition is required.

## Notes

- Focus on workflow differences: Claude commands versus Codex skill instructions and metadata.

## Completion Evidence

- Reviewed `README.md` and the three command files in the source repository.
- Reviewed installed `SKILL.md`, `agents/openai.yaml`, templates, and tree rules in `~/.codex/skills/deep-planning/`.
- Confirmed the required update is an adaptation to Codex, not a direct copy of Claude command semantics.
