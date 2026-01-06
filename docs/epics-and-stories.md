<!--
Based on: docs/prd-todo.md
Format: docs/templates/epic-and-stories-template.md
-->

## MVP

- Epic: Task Data Model Updates
  - Story: Add due date to tasks
    - Acceptance Criteria:
      - Each task can have an optional `dueDate` value.
      - When present, `dueDate` is stored as an ISO date string in `YYYY-MM-DD` format.
      - Tasks without a due date are supported (no `dueDate` set).
  - Story: Add priority (P1/P2/P3) to tasks
    - Acceptance Criteria:
      - Each task has a `priority` value.
      - Allowed values are `P1`, `P2`, and `P3`.
  - Story: Default new tasks to priority P3
    - Acceptance Criteria:
      - When creating a new task, if the user does not choose a priority, the task is saved with priority `P3`.
  - Story: Ignore invalid due dates
    - Acceptance Criteria:
      - If a task’s `dueDate` is not a valid `YYYY-MM-DD` date, it is treated as if no due date is present.

- Epic: Task Create and Edit Experience
  - Story: Allow setting and clearing a task due date
    - Acceptance Criteria:
      - Users can set a due date on a task.
      - Users can clear a previously set due date.
      - Changes persist in local storage.
  - Story: Allow setting a task priority
    - Acceptance Criteria:
      - Users can set a task’s priority to `P1`, `P2`, or `P3`.
      - Changes persist in local storage.

- Epic: Date-Based Task Filters
  - Story: Add filter tabs for All, Today, and Overdue
    - Acceptance Criteria:
      - The UI includes filter tabs: **All**, **Today**, and **Overdue**.
      - **Today** shows tasks whose `dueDate` equals the user’s current local date.
      - **Overdue** shows tasks whose `dueDate` is before the user’s current local date.
  - Story: Show completed tasks in All filter
    - Acceptance Criteria:
      - In the **All** view, both completed and incomplete tasks are displayed.
  - Story: Hide completed tasks in Today filter
    - Acceptance Criteria:
      - In the **Today** view, completed tasks are not displayed.
  - Story: Hide completed tasks in Overdue filter
    - Acceptance Criteria:
      - In the **Overdue** view, completed tasks are not displayed.

- Epic: Local-Only Storage Constraint
  - Story: Keep task data stored locally only
    - Acceptance Criteria:
      - Task data is persisted locally (no external storage).
  - Story: Ensure no backend changes are required
    - Acceptance Criteria:
      - The feature works without any backend/API changes.

## Post-MVP

- Epic: Overdue Task Highlighting
  - Story: Visually highlight overdue tasks
    - Acceptance Criteria:
      - Overdue tasks are visually highlighted in the task list.
      - Overdue is determined by `dueDate` being before the user’s current local date.

- Epic: Task Sorting Enhancements
  - Story: Sort tasks with overdue items first
    - Acceptance Criteria:
      - When sorting is applied, overdue tasks appear before non-overdue tasks.
  - Story: Sort tasks by priority (P1 to P3)
    - Acceptance Criteria:
      - When sorting is applied, higher priority tasks come first in the order `P1`, then `P2`, then `P3`.
  - Story: Sort tasks by due date ascending
    - Acceptance Criteria:
      - When sorting is applied, tasks with due dates are ordered from earliest to latest.
  - Story: Place tasks without due dates last
    - Acceptance Criteria:
      - When sorting is applied, tasks without a due date appear after tasks with a due date.

- Epic: Priority Badges
  - Story: Display a priority badge on tasks
    - Acceptance Criteria:
      - Each task displays a badge indicating its priority (`P1`, `P2`, or `P3`).
  - Story: Use distinct badge colors for P1, P2, and P3
    - Acceptance Criteria:
      - Priority badges use distinct colors for each level.
      - Color mapping follows: `P1` red, `P2` orange, `P3` gray.
