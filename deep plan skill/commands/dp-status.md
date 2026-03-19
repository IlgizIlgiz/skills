# Deep Planning Agent — Status Report

Show the user a clear progress report for active plans.

## Arguments (optional)

$ARGUMENTS

If a plan ID is provided, show detailed status for that plan only.
If no arguments — show overview of ALL active plans.

## Instructions

### 1. Discover Active Plans

List all directories in `deep-planning-skill/*/` (ignore `HISTORY.md`).

### 2. If NO active plans:
- Say "No active plans."
- If `deep-planning-skill/history/` exists, show the most recent 3 report files from history as "Recently completed plans" (look at the latest date folders, then latest numbered files)
- Remind: `/deep-plan <description>` to create a new plan

### 3. If showing ALL plans (no argument):

For each active plan, read its `STATUS.md` and show a compact summary:

```
## Active Plans

### [plan-id] — [first 80 chars of original request]
Progress: ██████░░░░ 60% (3/5 tasks)
Current: 002/03-error-handling
Created: 2026-03-10

### [plan-id-2] — [first 80 chars of original request]
Progress: ██░░░░░░░░ 20% (1/5 tasks)
Current: 001/02-add-validation
Created: 2026-03-10
```

Then remind: `/dp-next <plan-id>` to continue a specific plan, `/dp-status <plan-id>` for details.

### 4. If showing ONE plan (plan ID provided):

Read its `STATUS.md`, count total tasks/subtasks/steps, count completed items, and show detailed view:

```
## Deep Plan: [plan-id]

### Overall: ██████░░░░ 60% (3/5 tasks)

### Task 001: auth-refactor ✅ COMPLETE
  └─ 01-extract-middleware ✅
  └─ 02-add-validation ✅
  └─ 03-tests ✅

### Task 002: api-endpoints ▶️ IN PROGRESS (2/4 subtasks)
  └─ 01-create-routes ✅
  └─ 02-add-validation ✅
  └─ 03-error-handling ← CURRENT
  └─ 04-tests ⏳

### Task 003: frontend-forms ⏳ NOT STARTED (0/3 subtasks)
  └─ 01-form-components
  └─ 02-validation-logic
  └─ 03-api-integration
```

Show last 5 entries from Execution Log.

Remind: `/dp-next <plan-id>` to continue execution.
