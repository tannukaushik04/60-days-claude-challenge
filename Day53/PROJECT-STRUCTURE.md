# WhyIFeel — Project Structure

Version 1.1 — Updated Day 3 (originally created Day 2)

## Folder Structure (Current State, End of Day 3)

```
WhyIFeel/
|-- app.py                     # Flask entry point — DONE (Day 3): config, home route, login_required stub
|-- database.py                # DB connection + table creation — DONE (Day 3): matches docs/SCHEMA.md exactly
|-- insight_engine.py          # Pure-Python statistical analysis module — NOT YET CREATED (Day 6)
|-- demo_data_generator.py     # Synthetic data seeding logic — NOT YET CREATED (Day 7)
|-- requirements.txt           # Python dependencies — DONE (Day 3): flask, werkzeug, jinja2, etc.
|-- Procfile                   # Render/host start command — NOT YET CREATED (Day 10)
|-- .gitignore                 # Excludes venv/, instance/*.db, __pycache__ — DONE (Day 1)
|-- README.md                  # Project overview + live link — placeholder, finalized Day 10
|
|-- templates/                 # Jinja2 HTML templates
|   |-- base.html               # DONE (Day 3): shared layout + nav bar
|   |-- home.html                # DONE (Day 3): placeholder homepage
|   |-- signup.html              # NOT YET CREATED (Day 4)
|   |-- login.html               # NOT YET CREATED (Day 4)
|   |-- checkin.html             # NOT YET CREATED (Day 5)
|   |-- dashboard.html           # NOT YET CREATED (Day 7)
|   `-- history.html             # NOT YET CREATED (Day 5)
|
|-- static/
|   |-- css/
|   |   `-- style.css           # Created empty (Day 3), filled in Day 8
|   `-- js/
|       |-- checkin.js          # NOT YET CREATED (Day 5)
|       `-- dashboard.js        # NOT YET CREATED (Day 7)
|
|-- instance/
|   `-- whyifeel.db             # DONE (Day 3): generated locally, git-ignored
|
|-- tests/
|   `-- test_insight_engine.py  # NOT YET CREATED (Day 9)
|
|-- venv/                       # DONE (Day 3): local virtual environment, git-ignored
|
`-- docs/
    |-- architecture_decisions.md
    |-- ARCHITECTURE.md
    |-- SCHEMA.md
    |-- API.md
    |-- UI-WIREFRAMES.md
    |-- PROJECT-STRUCTURE.md    # this file
    |-- SETUP.md                 # NEW (Day 3)
    |-- ENVIRONMENT.md            # NEW (Day 3)
    |-- DAY3-SUMMARY.md           # NEW (Day 3)
    |-- project_log.md
    |-- manual_test_plan.md     # NOT YET CREATED (Day 9)
    |-- bugs.md                  # NOT YET CREATED (Day 9)
    `-- demo_script.md           # NOT YET CREATED (Day 10)
```

## What Changed Since Day 2

- `venv/` added — the local virtual environment (git-ignored, not committed)
- `app.py` and `database.py` are no longer empty placeholders — both are fully functional per today's implementation
- `templates/base.html` and `templates/home.html` created and verified working
- `static/css/style.css` created as an empty file (intentionally left blank until Day 8 styling)
- `instance/whyifeel.db` now exists locally (git-ignored — everyone who clones the repo generates their own copy via `python database.py`)
- No structural changes were needed beyond what Day 2 already planned — the folder layout defined in the original `PROJECT-STRUCTURE.md` required zero revisions, only population with real files

## Rationale (Unchanged from Day 2)

- Flat app-level files (`app.py`, `database.py`) rather than nested packages — appropriate for this project's size (~11 total routes across the whole v1.0 build).
- `templates/` and `static/` are Flask's expected default folder names — no custom configuration needed.
- `docs/` holds every planning and QA artifact in one place so any fresh AI conversation or future contributor has full context without digging through code.
