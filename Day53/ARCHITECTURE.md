# WhyIFeel — Architecture

Version 1.0 — Day 2 Design Deliverable
AB Talks 60-Day Claude AI Challenge — 10-Day Capstone

## Tech Stack Summary

| Layer | Choice | Rationale |
|---|---|---|
| Backend | Python + Flask | Matches existing skills; minimal boilerplate for a small app |
| Frontend | Jinja2 templates + vanilla JS | No build tooling risk; sufficient for 5 screens |
| Database | SQLite | Zero-config, file-based, free |
| Auth | Flask sessions + Werkzeug password hashing | Built-in, secure, no OAuth/email complexity |
| AI Model/API | None | Self-built statistical insight engine — no external LLM dependency |
| Charts | Chart.js (CDN) | No install step, handles line/bar charts with interactivity |
| Hosting | Render (free tier) | Deploys Flask from GitHub with no credit card required |
| Production server | Gunicorn | Standard WSGI server for Flask deployments |
| Version control | Git + GitHub | Already set up |

## Component Diagram

```mermaid
graph TB
    subgraph Client["Browser (Client)"]
        UI[HTML Pages via Jinja2<br/>+ Vanilla JS + Chart.js]
    end

    subgraph Server["Flask Application (Render)"]
        Routes[Flask Routes / Views]
        Auth[Auth Module<br/>session + password hashing]
        CheckinLogic[Check-in Logic]
        InsightEngine[Insight Engine<br/>pure Python, no external API]
        DemoGen[Demo Data Generator]
    end

    subgraph Data["Data Layer"]
        DB[(SQLite Database<br/>Users + CheckIns)]
    end

    UI -->|HTTP requests| Routes
    Routes --> Auth
    Routes --> CheckinLogic
    Routes --> InsightEngine
    Routes --> DemoGen
    Auth --> DB
    CheckinLogic --> DB
    InsightEngine -->|reads| DB
    DemoGen -->|writes| DB
    Routes -->|renders| UI
```

## Data Flow — Daily Check-in to Dashboard Insight

```mermaid
sequenceDiagram
    participant U as User (Browser)
    participant F as Flask Route
    participant DB as SQLite DB
    participant IE as Insight Engine

    U->>F: POST /checkin (form data)
    F->>F: Validate fields
    F->>DB: INSERT CheckIn (user_id, date, ...)
    DB-->>F: Success / Unique constraint error
    F-->>U: Redirect to /dashboard

    U->>F: GET /dashboard
    F->>DB: SELECT all CheckIns for user
    DB-->>F: Rows
    F->>IE: get_insights_for_user(rows)
    IE->>IE: Group by habit condition,<br/>compute avg, % diff, confidence tier
    IE-->>F: Ranked insight list
    F-->>U: Render dashboard.html (charts + insights)
```

## Request Lifecycle — Protected Route Example

```mermaid
flowchart LR
    A[Request comes in] --> B{Session has user_id?}
    B -- No --> C[Redirect to /login]
    B -- Yes --> D[Route handler runs]
    D --> E{DB query needed?}
    E -- Yes --> F[Query scoped by user_id]
    E -- No --> G[Render template]
    F --> G
    G --> H[Response sent to browser]
```

## AI Interaction

None. No external AI/LLM API is used anywhere in this system. The "insight engine" is a self-contained Python module using statistical comparison (group averages, percentage difference, confidence-by-sample-size). This was a deliberate Day 1 decision to avoid API cost, rate limits, and external dependency, and serves as a stronger engineering showcase for the challenge.

## External Services

Only GitHub (source control) and Render (hosting). No third-party APIs, payment processors, or email services are used in v1.0.

## Notes / Deviations From Day 1 Plan

None. This architecture is a direct, more detailed continuation of the Day 1 PRD and Implementation Blueprint. No redesign occurred.
