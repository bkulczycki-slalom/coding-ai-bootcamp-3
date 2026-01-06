# Cloud Architecture Overview

This monorepo contains a React frontend and an Express API. The API currently uses an in-memory SQLite database (via `better-sqlite3` with `:memory:`).

## System Context

```mermaid
flowchart LR
  U[User]
  B[Web Browser]
  FE[React Frontend\npackages/frontend]
  API[Express API\npackages/backend]
  DB[(In-memory SQLite DB\n":memory:")]

  U --> B
  B -->|HTTP| FE
  FE -->|REST: /api/tasks| API
  API -->|SQL| DB
```

## Sequence: Create a TODO

```mermaid
sequenceDiagram
  autonumber
  actor User
  participant Browser as Web Browser
  participant FE as React Frontend
  participant API as Express API
  participant DB as In-memory SQLite DB

  User->>Browser: Enter title (and optional fields)\nClick "Add Task"
  Browser->>FE: Submit form
  FE->>API: POST /api/tasks\n{ title, description, due_date }
  API->>DB: INSERT INTO tasks (...)
  DB-->>API: New task row (id)
  API-->>FE: 201 Created\nTask JSON
  FE-->>Browser: Re-render task list
```
