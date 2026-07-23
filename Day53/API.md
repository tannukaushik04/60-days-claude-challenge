# WhyIFeel — API Design

Version 1.0 — Day 2 Design Deliverable

This is a server-rendered Flask application (not a JSON API), so "endpoints" below refer to Flask routes returning rendered HTML (with redirects and flash messages), not JSON payloads. No implementation happens today — this is the full specification implementation will follow on Days 3-7.

## Cross-Cutting Concerns (apply to all authenticated endpoints)

- **Authentication check:** every route marked "Auth: Required" is wrapped in a `login_required` decorator. Failing that check always redirects to `/login` — this app never returns a raw 401 JSON response, since it's server-rendered, not an API-only backend.
- **Data scoping:** every database query touching `checkins` must filter by `session['user_id']`. This is the single most important security rule in the whole app — a missing `WHERE user_id = ?` clause is the most likely source of a cross-user data leak.
- **CSRF:** only `POST` is accepted for any state-changing action. Full CSRF token protection is a reasonable v2 addition — noted but not blocking v1.0 given the small attack surface and free-tier deployment context.

---

## Auth Endpoints

### `GET /signup`
- **Purpose:** Show signup form
- **Auth:** None required
- **Response:** Renders `signup.html`

### `POST /signup`
- **Purpose:** Create a new user account
- **Request:** form-encoded — `username`, `password`
- **Validation:**
  - `username`: non-empty, 3-30 characters, alphanumeric/underscore only, not already taken
  - `password`: non-empty, minimum 6 characters
- **Response:** Redirect to `/login` on success, with flash message "Account created — please log in"
- **Error cases:**
  - `400` — re-render form with flash: "Username already taken"
  - `400` — re-render form with flash: "Username must be 3-30 characters"
  - `400` — re-render form with flash: "Password must be at least 6 characters"

### `GET /login`
- **Purpose:** Show login form
- **Auth:** None required (redirect to `/dashboard` if already logged in)
- **Response:** Renders `login.html`

### `POST /login`
- **Purpose:** Authenticate and start a session
- **Request:** form-encoded — `username`, `password`
- **Validation:** both fields present
- **Response:** Sets `session['user_id']`, redirects to `/dashboard`
- **Error cases:**
  - `401` — re-render form with flash: "Invalid username or password" (deliberately generic — never reveals which field was wrong)

### `POST /logout`
- **Purpose:** End the session
- **Auth:** Required
- **Response:** Clears session, redirects to `/login`

---

## Check-in Endpoints

### `GET /checkin`
- **Purpose:** Show today's check-in form
- **Auth:** Required
- **Response:**
  - If today's entry already exists for this user -> redirect to `/history` with flash "You've already checked in today"
  - Else -> render `checkin.html`

### `POST /checkin`
- **Purpose:** Submit today's check-in
- **Auth:** Required
- **Request:** form-encoded — `sleep_hours`, `workout_flag` (checkbox), `workout_intensity`, `water_intake`, `screen_time`, `energy`, `mood`, `stress`, `soreness`
- **Validation:**
  - All numeric fields within schema-defined ranges (see SCHEMA.md)
  - `workout_intensity` defaults to `'none'` if `workout_flag` is unchecked; otherwise must be one of `low`/`medium`/`high`
  - `energy`, `mood`, `stress`, `soreness` must be integers 1-5
- **Response:** Insert row with `entry_date = today`, `is_demo = 0`; redirect to `/dashboard`
- **Error cases:**
  - `409 Conflict` — UNIQUE(user_id, entry_date) violation (race-condition safeguard even though the GET route already checks) with flash "You've already logged today"
  - `400` — out-of-range values, with flash listing the invalid field(s)

### `GET /history`
- **Purpose:** List all past check-ins for the logged-in user
- **Auth:** Required
- **Response:** Renders `history.html` with all `checkins` rows for `user_id`, ordered by `entry_date DESC`

### `POST /checkin/delete/<id>`
- **Purpose:** Delete a specific check-in entry
- **Auth:** Required
- **Request:** `id` in URL path
- **Validation:** entry must exist AND belong to `session['user_id']`
- **Response:** Deletes row, redirects to `/history` with flash "Entry deleted"
- **Error cases:**
  - `403 Forbidden` — entry belongs to another user (response is a generic redirect + flash, never revealing whether the entry exists but belongs to someone else, to avoid leaking the existence of other users' data)
  - `404` — entry doesn't exist at all

---

## Dashboard & Insights Endpoints

### `GET /dashboard`
- **Purpose:** Show trend charts, correlation charts, and ranked insights
- **Auth:** Required
- **Request:** optional query parameter `?range=7|30|90|all` (default `30`)
- **Response:** Queries `checkins` filtered by `user_id` and date range, computes insights via the insight engine on-demand, renders `dashboard.html` with chart data (as JSON) and the insight list
- **Error cases:** If zero check-ins exist, render a designed empty state prompting the user to check in or generate demo data (not a true error condition)

### `POST /generate-demo-data`
- **Purpose:** Seed ~30 days of realistic synthetic check-ins for the current user
- **Auth:** Required
- **Request:** no body needed
- **Validation:** only inserts demo rows for dates that don't already have a real or demo entry for this user (never overwrites existing data)
- **Response:** Inserts rows with `is_demo = 1`, redirects to `/dashboard` with flash "Demo data generated"
- **Error cases:** If all candidate dates are already taken (unlikely edge case), redirect with flash "No new demo data needed — you already have entries for this range"

---

## Endpoint Summary Table

| Method | Path | Auth | Purpose |
|---|---|---|---|
| GET | /signup | No | Show signup form |
| POST | /signup | No | Create account |
| GET | /login | No | Show login form |
| POST | /login | No | Authenticate |
| POST | /logout | Yes | End session |
| GET | /checkin | Yes | Show check-in form |
| POST | /checkin | Yes | Submit check-in |
| GET | /history | Yes | List past entries |
| POST | /checkin/delete/<id> | Yes | Delete an entry |
| GET | /dashboard | Yes | View charts + insights |
| POST | /generate-demo-data | Yes | Seed demo data |
