# Update Installed Skill

## Identity

- Node ID: 02-update-installed-skill
- Parent: 01-sync-codex-skill
- Status: done
- Stage: complete

## Objective

Edit the installed Codex skill files to reflect the adapted deep planning workflow from the repository.

## Deliverable

Updated `SKILL.md` and any stale supporting metadata under `~/.codex/skills/deep-planning/`.

## Acceptance Criteria

- The installed skill uses concise Codex-oriented instructions.
- Metadata remains consistent with the updated behavior.
- No Claude-specific command instructions remain unless explicitly translated for Codex.

## Dependencies

- 01-inspect-source-and-target

## Children

- None yet. Add child folders under `children/` when further decomposition is required.

## Notes

- Likely files: `SKILL.md` and `agents/openai.yaml`.

## Completion Evidence

- Updated `~/.codex/skills/deep-planning/SKILL.md` to include plan/resume/status-report behavior adapted from the source repository.
- Updated `~/.codex/skills/deep-planning/references/tree-rules.md` with cross-plan and status-reporting rules.
- Updated `~/.codex/skills/deep-planning/agents/openai.yaml` so the UI metadata matches the new scope.
