# Product Requirements Document (PRD) - Todo App Upgrade

## 1. Overview

Upgrade the basic Todo app with due dates, priorities, and date-based filters so users can identify urgent work and organize tasks while keeping the experience simple and teachable. The MVP will remain local-only and will not require backend changes or external storage.

---

## 2. MVP Scope

- Add an optional `dueDate` field to each task.
  - Use the ISO `YYYY-MM-DD` format.
  - Ignore invalid due-date values and treat them as absent.
- Add a required `priority` field to each task.
  - Accept only `P1`, `P2`, or `P3`.
  - Default the priority to `P3` when none is provided.
  - Display priorities as color-coded badges: red for `P1`, orange for `P2`, and gray for `P3`.
- Provide three task-list filters:
  - **All**: show all tasks, including completed tasks.
  - **Today**: show only incomplete tasks due on the current date.
  - **Overdue**: show only incomplete tasks whose due date is before the current date.
- Continue requiring a task `title`.
- Keep task storage local to the application, with no backend changes or external storage.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks in red so they stand out.
- Sort tasks using the following precedence:
  - Overdue tasks first.
  - Priority from `P1` to `P3`.
  - Due date in ascending order.
  - Tasks without a due date last.

---

## 4. Out of Scope

- Notifications.
- Recurring tasks.
- Multi-user support.
- Keyboard navigation or additional accessibility features.
- Backend changes.
- External or remote storage.