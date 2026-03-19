# Sync Codex Deep Planning Skill

## Identity

- Node ID: 01-sync-codex-skill
- Parent: root
- Status: done
- Stage: complete

## Objective

Read the source deep plan skill in this repository, map its behavior to the Codex skill model, and update the installed Codex skill accordingly.

## Deliverable

An updated `~/.codex/skills/deep-planning` skill that reflects the repository's workflow where it makes sense for Codex.

## Acceptance Criteria

- The source repository guidance has been reviewed.
- The installed Codex skill files are updated to reflect the adapted workflow.
- The installed skill reads coherently for Codex and passes a basic content sanity check.

## Dependencies

- Access to the source repository files.
- Access to the installed Codex skill folder.

## Children

- [in_progress] 01-inspect-source-and-target
- [in_progress] 02-update-installed-skill
- [in_progress] 03-verify-installed-skill

## Notes

- The source repository targets Claude Code commands, so the update must adapt concepts instead of copying them verbatim.

## Completion Evidence

- Inspection completed for repository README and command files plus the installed Codex skill files.
- Installed skill files were updated in `~/.codex/skills/deep-planning/`.
- Verification completed for SKILL frontmatter, `agents/openai.yaml`, and removal of Claude-specific command wording.
