# TODO App Architecture Overview

This monorepo contains a React frontend and an Express API. The API stores task data in an in-memory SQLite database, so task data is available only for the lifetime of the running API process.

## System Context

```mermaid
flowchart LR
    user[User]
    frontend[React Frontend\npackages/frontend]
    api[Express API\npackages/backend]
    store[(In-Memory SQLite Store)]

    user -->|Uses TODO app| frontend
    frontend -->|HTTPS/HTTP JSON\n/api/tasks| api
    api -->|Reads and writes tasks| store
```

## Create a TODO Sequence

```mermaid
sequenceDiagram
    actor User
    participant Form as React TaskForm
    participant App as React App
    participant API as Express API
    participant Store as In-Memory SQLite Store

    User->>Form: Enter title, description, and due date
    User->>Form: Submit task
    Form->>Form: Validate non-empty title
    Form->>App: onSave(task)
    App->>API: POST /api/tasks with JSON task data
    API->>API: Validate title
    API->>Store: INSERT task
    Store-->>API: Created task
    API-->>App: 201 Created with task JSON
    App->>App: Increment refresh key
    App->>Form: Clear form fields
```