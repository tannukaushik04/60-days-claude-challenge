# WhyIFeel — Project Structure

Version 1.0 — Day 2 Design Deliverable

## Folder Structure

```
WhyIFeel/
|-- app.py                     # Flask entry point: routes, login_required decorator
|-- database.py                # DB connection helper + table creation (init_db)
|-- insight_engine.py          # Pure-Python statistical analysis module (no Flask dependency)
|-- demo_data_generator.py     # Synthetic data seeding logic
|-- requirements.txt           # Python dependencies (Flask, gunicorn, werkzeug, etc.)
|-- Procfile                   # Render/host start command (added Day 10)
|-- .gitignore                 # Excludes venv/, instance/*.db, __pycache__
|-- README.md                  # Project overview + live link (finalized Day 10)
|
|-- templates/                 # Jinja2 HTML templates
|   |-- base.html               # Shared layout + nav bar
|   |-- signup.html
|   |-- login.html
|   |-- checkin.html
|   |-- dashboard.html
|   `-- history.html
|
|-- static/
|   |-- css/
|   |   `-- style.css           # All visual styling (Day 8)
|   `-- js/
|       |-- checkin.js          # Slider labels + conditional workout intensity field
|       `-- dashboard.js        # Chart.js rendering + date filter logic
|
|-- instance/
|   `-- whyifeel.db             # SQLite database file (git-ignored, generated locally)
|
|-- tests/
|   `-- test_insight_engine.py  # Automated unit tests for the insight engine (Day 9)
|
`-- docs/
    |-- architecture_decisions.md
    |-- ARCHITECTURE.md
    |-- SCHEMA.md
    |-- API.md
    |-- UI-WIREFRAMES.md
    |-- PROJECT-STRUCTURE.md
    |-- manual_test_plan.md     # Day 9
    |-- bugs.md                 # Day 9
    |-- demo_script.md          # Day 10
    `-- project_log.md          # Ongoing daily log
```

## Rationale

- **Flat app-level files** (`app.py`, `database.py`, `insight_engine.py`) rather than nested packages/blueprints — appropriate for a project this size. Nesting would add navigation overhead with no real benefit for roughly 11 routes.
- **`insight_engine.py` and `demo_data_generator.py` live outside `app.py`** deliberately, so the core differentiator (the insight logic) can be tested independently of Flask (see the Day 6 plan and `tests/test_insight_engine.py`).
- **`templates/` and `static/` are Flask's expected default folder names** — no custom configuration needed, one less thing to get wrong.
- **`docs/` holds every planning and QA artifact** in one place, so anyone — including a fresh AI conversation on any future day — can find full context without digging through code.
- **`instance/` is Flask's conventional folder** for environment-specific files (like the local DB) that shouldn't be committed to version control.

## Where Future Code Will Live

| Day | What Gets Added | Where |
|---|---|---|
| Day 3 | Flask app skeleton, DB init | `app.py`, `database.py` |
| Day 4 | Auth routes + templates | `app.py`, `templates/signup.html`, `templates/login.html` |
| Day 5 | Check-in + history routes | `app.py`, `templates/checkin.html`, `templates/history.html`, `static/js/checkin.js` |
| Day 6 | Insight engine | `insight_engine.py`, manual test script |
| Day 7 | Dashboard + demo data | `app.py`, `templates/dashboard.html`, `static/js/dashboard.js`, `demo_data_generator.py` |
| Day 8 | Styling | `static/css/style.css` |
| Day 9 | Testing | `tests/test_insight_engine.py`, `docs/manual_test_plan.md`, `docs/bugs.md` |
| Day 10 | Deployment | `Procfile`, updated `requirements.txt`, `README.md`, `docs/demo_script.md` |
