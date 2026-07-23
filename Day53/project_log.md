# WhyIFeel — Project Log

## Day 1 — Product Discovery & Sprint Planning
- Interviewed to discover the project idea from scratch.
- Selected concept: WhyIFeel, a habit-feeling correlation tracker.
- Defined v1.0 scope: 4 habits, 4 feelings, self-built statistical insight engine (no external AI API), simple auth, seed/demo data for guaranteed strong demos.
- Deliverables generated: PRD, 9-Day Implementation Blueprint, Pitch Deck.

## Day 2 — System Design
- Created the GitHub repository (`tannukaushik04/WhyIFeel`), cloned locally, and set up the initial project folder structure (templates/, static/, instance/, docs/, tests/, placeholder app.py/database.py/requirements.txt).
- Finalized and documented the full tech stack: Flask, SQLite, Jinja2 + vanilla JS, Chart.js, Flask sessions + Werkzeug hashing, Render (free tier) hosting, Gunicorn.
- Designed the complete system architecture (component diagram, data flow, request lifecycle) — no external AI/LLM API used anywhere in the system.
- Designed the full database schema (users, checkins tables) and validated it against every PRD user story. Added one precision improvement not explicit in the Day 1 plan: an `is_demo` flag on `checkins` to distinguish generated demo data from real entries.
- Specified every v1.0 API endpoint (auth, check-in, history, dashboard, demo data) with request/response/validation/error details — no implementation yet.
- Designed the full user flow, screen flow, and low-fidelity wireframes for all 5 screens (signup, login, check-in, dashboard, history).
- Finalized the project folder structure and rationale.
- Updated the Day 3 section of the Implementation Blueprint to remove the now-redundant folder-structure step (already completed today) and to reference the finalized schema directly.
- Deliverables generated: ARCHITECTURE.md, SCHEMA.md, API.md, UI-WIREFRAMES.md, PROJECT-STRUCTURE.md; Implementation Blueprint updated.
- Confirmed Day 3 readiness: no scope creep, timeline on track, implementation can begin immediately tomorrow.
- Committed and pushed all Day 2 work to GitHub (commit `ab9e906`).

## Day 3 — Project Setup & Foundation
- Verified environment: Python 3.13.7, pip 26.1.2, VS Code with Python extension (Microsoft) + Pylance, workspace trust enabled.
- Created and activated a Python virtual environment (`venv/`).
- Installed Flask 3.1.3 and dependencies; locked versions in `requirements.txt`.
- Implemented `database.py`: `get_db()` and `init_db()`, creating `users` and `checkins` tables exactly per `docs/SCHEMA.md`, verified column-by-column.
- Implemented `app.py`: Flask app config with `SECRET_KEY` read from environment variable (with local dev fallback), placeholder `login_required` decorator stub (completed Day 4), and a working `/` homepage route.
- Created `templates/base.html` (shared layout + nav bar) and `templates/home.html` (placeholder homepage).
- Verified end-to-end: database initializes correctly, Flask server runs with no errors, browser shows "Hello, WhyIFeel" with working navigation.
- Confirmed branching strategy: single `main` branch for the whole project — appropriate for a solo, time-boxed build.
- Deliverables generated: SETUP.md, ENVIRONMENT.md, updated PROJECT-STRUCTURE.md, DAY3-SUMMARY.md. Implementation Blueprint's Day 3 checklist corrected (git init step was outdated since repo already existed from Day 2).
- Committed and pushed all Day 3 work to GitHub (commit `e6e2ee3`).
