# WhyIFeel — Setup Guide

Version 1.0 — Day 3 Deliverable

This guide lets anyone (including a future you, or a fresh AI conversation) get the project running locally from scratch.

## Prerequisites

- **Python 3.9+** (verified working on 3.13.7)
- **pip** (bundled with Python)
- **Git** (already configured from Day 1/2)
- **VS Code** with the **Python extension** (by Microsoft) installed

## First-Time Setup

**1. Clone the repository**
```
git clone https://github.com/tannukaushik04/WhyIFeel.git
cd WhyIFeel
```

**2. Create and activate a virtual environment**

Windows (PowerShell):
```
python -m venv venv
.\venv\Scripts\Activate.ps1
```
If PowerShell blocks the activation script with an execution policy error, run this once:
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

macOS/Linux (for reference — this project was built on Windows):
```
python3 -m venv venv
source venv/bin/activate
```

You'll know it worked when your terminal prompt starts with `(venv)`.

**3. Install dependencies**
```
pip install -r requirements.txt
```

**4. Initialize the database**
```
python database.py
```
This creates `instance/whyifeel.db` with the `users` and `checkins` tables (schema defined in `docs/SCHEMA.md`).

**5. Run the app**
```
python app.py
```

**6. Open the app in your browser**
```
http://127.0.0.1:5000/
```
You should see the "Hello, WhyIFeel" placeholder homepage with a nav bar.

## Stopping the Server

Press `Ctrl+C` in the terminal where Flask is running.

## Common Issues

- **`ModuleNotFoundError: No module named flask`** — your virtual environment isn't activated. Re-run the activation command from Step 2.
- **PowerShell execution policy error** — see the one-time fix in Step 2.
- **Port 5000 already in use** — another process is using it (or another Flask instance is still running from a previous session); stop it or change the port with `app.run(debug=True, port=5001)`.
- **404 for `/favicon.ico` in the terminal log** — this is normal; browsers automatically request a favicon, and we haven't added one. No action needed.

## Re-Running Setup on a New Machine

Steps 1-6 above are the complete process — no other manual configuration is required at this stage of the project (Day 3). Environment variables (specifically `SECRET_KEY` for production) are documented separately in `docs/ENVIRONMENT.md` and become relevant starting Day 4 (local) and Day 10 (deployment).
