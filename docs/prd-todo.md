# Product Requirements Document (PRD) - Todo App: Due Dates, Priority, and Date Filters

## 1. Overview

We are upgrading the existing (very basic) Todo app so it is more practical for day-to-day use while staying lean and teachable. The MVP focuses on adding due dates, simple priority levels, and quick date-based filters, while keeping all storage local and making no backend changes.

---

## 2. MVP Scope

- Data model
  - Add `dueDate` to each task (optional), stored as ISO date string `YYYY-MM-DD`.
  - Add `priority` to each task with allowed values `P1 | P2 | P3`.
    - Default `priority` to `P3` for new tasks.
  - `title` remains required.
- Validation rules
  - If `dueDate` is not a valid ISO `YYYY-MM-DD`, it is ignored (treated as if absent).
- UI/UX
  - User can set/clear a task’s due date.
  - User can set a task’s priority (P1/P2/P3).
  - Provide filter tabs: **All**, **Today**, **Overdue**.
    - **All**: shows all tasks (including completed tasks).
    - **Today**: shows incomplete tasks with `dueDate` equal to the user’s current local date.
    - **Overdue**: shows incomplete tasks with `dueDate` before the user’s current local date.
- Persistence / architecture constraints
  - Keep storage local only.
  - No backend changes.
  - No external storage.

---

## 3. Post-MVP Scope

- Overdue tasks are visually highlighted (e.g., using a red emphasis).
- Sorting improvements
  - Sort tasks as: overdue first → priority (P1 → P3) → due date ascending → undated last.
- Visual priority treatment
  - Show priority as a visual badge (e.g., P1 red, P2 orange, P3 gray).

---

## 4. Out of Scope

- Notifications.
- Recurring tasks.
- Multi-user support.
- Keyboard navigation and other special accessibility features (beyond baseline).
- External storage (anything beyond local storage).
