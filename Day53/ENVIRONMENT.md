# WhyIFeel — Environment Configuration

Version 1.0 — Day 3 Deliverable

## Tools & Versions Used

| Tool | Version (as configured) | Purpose |
|---|---|---|
| Python | 3.13.7 | Backend runtime |
| pip | 26.1.2 | Package manager |
| Flask | 3.1.3 | Web framework |
| Werkzeug | 3.1.8 | Password hashing (used starting Day 4), Flask's underlying WSGI toolkit |
| Jinja2 | 3.1.6 | HTML templating (bundled with Flask) |
| Git | (system-installed) | Version control |
| VS Code | (system-installed) | Editor, with the Python extension (Microsoft) and Pylance installed |

Exact locked versions are tracked in `requirements.txt` at the project root — always install from that file rather than installing packages ad hoc, to keep local, teammate, and deployed environments identical.

## Environment Variables

| Variable | Purpose | Local Development | Production (Day 10) |
|---|---|---|---|
| `SECRET_KEY` | Signs Flask session cookies so they can't be tampered with by the browser/user | Falls back to a hardcoded placeholder (`dev-only-placeholder-change-me`) defined directly in `app.py` if not set — acceptable for local-only development | Must be set to a long, random, unique value via the hosting platform's environment variable settings (Render dashboard) — never hardcoded or committed to source control |

No other environment variables are required for v1.0. There are no API keys, database connection strings, or third-party service credentials, because:
- The database is a local SQLite file (no connection string/credentials needed)
- No external AI/LLM API is used (self-built insight engine)
- No email service, payment processor, or OAuth provider is integrated

## How `SECRET_KEY` Is Read

In `app.py`:
```python
app.secret_key = os.environ.get("SECRET_KEY", "dev-only-placeholder-change-me")
```
This reads the `SECRET_KEY` environment variable if it's set on the machine/host; otherwise it falls back to the placeholder string. This pattern means the exact same code runs locally and in production — only the environment differs.

## Setting Environment Variables Locally (Optional, Not Required for Day 3)

Since the fallback placeholder is sufficient for local development, no action is needed today. If you ever want to set a real local `SECRET_KEY` for testing purposes, on Windows PowerShell:
```
$env:SECRET_KEY="your-random-string-here"
```
This only lasts for the current terminal session and is never committed to Git.

## Production Environment Variables (Day 10 Preview)

When deploying to Render on Day 10, we will set `SECRET_KEY` via Render's dashboard (Environment section of the Web Service settings) — not in code, not in `.env` files committed to the repo. This will be walked through step-by-step when we reach Day 10.

## Files Involved in Configuration

| File | Role |
|---|---|
| `app.py` | Reads `SECRET_KEY` from the environment |
| `requirements.txt` | Locks exact dependency versions |
| `.gitignore` | Excludes `venv/`, `instance/*.db`, `__pycache__/` from version control |
| `database.py` | Defines `DB_PATH`, always resolved relative to the project folder (works identically on any machine) |
