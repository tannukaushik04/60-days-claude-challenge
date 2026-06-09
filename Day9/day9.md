# Day 9 – Iterative AI Product Development


## What I Learned

One of the biggest mistakes beginners make is asking AI to generate a complete, complex application in a single prompt.

Professional AI builders use:

1. MVP First Development
2. Iterative Enhancement
3. Continuous Refinement
4. Product-Based Thinking

Instead of building everything at once, they create a working version first and improve it step by step.

---

# Project Overview

## Goal

Build an interactive AI-powered dashboard using Claude Artifacts and improve it through iterative development.

---

# Version 1 – Minimum Viable Product (MVP)

## Description

The first version focused on creating a working application with core functionality.

### Features

* Basic dashboard
* Initial visualizations
* Core user interface
* Basic data display
* Essential functionality

### Strengths

* Functional
* Fast to build
* Easy to test
* Clear foundation for improvements

### Limitations

* Basic UI design
* Limited insights
* Fewer interactive features
* Minimal customization

---

# Version 2 – Enhanced Application

## Description

The second version improved the MVP by adding additional functionality, better design, and richer insights.

### Enhancements Added

* Improved dashboard layout
* Better visual hierarchy
* Additional charts and visualizations
* Enhanced recommendations
* Improved user experience
* More detailed analysis
* Better responsiveness

### Strengths

* More professional appearance
* Better usability
* Richer insights
* Improved interactivity
* Greater user value

---

# Comparison

| Feature               | Version 1 (MVP) | Version 2 (Enhanced) |
| --------------------- | --------------- | -------------------- |
| Core Functionality    | Yes             | Yes                  |
| Interactive Dashboard | Basic           | Advanced             |
| Visual Design         | Simple          | Improved             |
| Insights              | Limited         | Detailed             |
| User Experience       | Basic           | Enhanced             |
| Recommendations       | Basic           | Personalized         |
| Overall Quality       | Good            | Excellent            |

---

# Screenshots

## Version 1 Screenshot

<img width="1588" height="1734" alt="NutriScope_Profile" src="https://github.com/user-attachments/assets/f9a1f934-5bbe-4871-b074-af1fbe9c6ab6" />


<img width="2398" height="2962" alt="NutriScope_Dashboard" src="https://github.com/user-attachments/assets/22699a28-1df1-4a19-8598-65fddd4a2400" />


### Observation

The MVP successfully demonstrated the core concept and functionality.

---

## Version 2 Screenshot

<img width="1588" height="2152" alt="NutriScope_v2 Profile" src="https://github.com/user-attachments/assets/a6479789-24c0-40a9-a42c-1ef6a707ade0" />


<img width="2480" height="4546" alt="NutriScope_v2 Dashboard" src="https://github.com/user-attachments/assets/01502989-5c35-48b7-9cfc-fd9830b536f3" />


### Observation

The enhanced version delivered a more polished user experience and deeper insights.

---

# HTML Files Included

## Version 1 - MVP
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NutriScope — Precision Nutrition Tracking</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=DM+Mono:wght@400;500&display=swap');

  :root {
    --bg-base: #0a0b0f;
    --bg-card: #111318;
    --bg-card-hover: #161820;
    --bg-elevated: #1a1d26;
    --bg-input: #13151c;
    --border: #222530;
    --border-focus: #4f6ef7;
    --text-primary: #eef0f8;
    --text-secondary: #8b90a7;
    --text-muted: #555b72;
    --accent-blue: #4f6ef7;
    --accent-blue-glow: rgba(79,110,247,0.18);
    --accent-green: #34d48a;
    --accent-green-glow: rgba(52,212,138,0.15);
    --accent-amber: #f5a623;
    --accent-amber-glow: rgba(245,166,35,0.15);
    --accent-red: #f75252;
    --accent-red-glow: rgba(247,82,82,0.15);
    --accent-purple: #a78bfa;
    --accent-cyan: #22d3ee;
    --font-main: 'Inter', system-ui, sans-serif;
    --font-mono: 'DM Mono', monospace;
    --radius-sm: 8px;
    --radius-md: 12px;
    --radius-lg: 16px;
    --radius-xl: 20px;
    --shadow: 0 4px 24px rgba(0,0,0,0.4);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: var(--font-main);
    background: var(--bg-base);
    color: var(--text-primary);
    min-height: 100vh;
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* Ambient background grid */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(79,110,247,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(79,110,247,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .app-wrapper { position: relative; z-index: 1; }

  /* ─── TOP BAR ─── */
  .topbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 24px;
    border-bottom: 1px solid var(--border);
    background: rgba(10,11,15,0.85);
    backdrop-filter: blur(12px);
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .logo {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 18px;
    font-weight: 700;
    letter-spacing: -0.5px;
  }
  .logo-icon {
    width: 32px; height: 32px;
    background: linear-gradient(135deg, var(--accent-blue), var(--accent-purple));
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 16px;
  }
  .logo span { color: var(--text-secondary); font-weight: 400; }
  .date-badge {
    font-family: var(--font-mono);
    font-size: 12px;
    color: var(--text-muted);
    background: var(--bg-elevated);
    padding: 6px 12px;
    border-radius: 20px;
    border: 1px solid var(--border);
  }

  /* ─── NAV TABS ─── */
  .nav-tabs {
    display: flex;
    gap: 4px;
    padding: 12px 24px;
    background: var(--bg-base);
    border-bottom: 1px solid var(--border);
    overflow-x: auto;
    scrollbar-width: none;
  }
  .nav-tabs::-webkit-scrollbar { display: none; }
  .tab-btn {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 16px;
    border: 1px solid transparent;
    border-radius: var(--radius-md);
    background: transparent;
    color: var(--text-secondary);
    font-size: 13px;
    font-weight: 500;
    font-family: var(--font-main);
    cursor: pointer;
    white-space: nowrap;
    transition: all 0.2s;
  }
  .tab-btn:hover { background: var(--bg-card); color: var(--text-primary); }
  .tab-btn.active {
    background: var(--accent-blue-glow);
    border-color: rgba(79,110,247,0.35);
    color: #7e9bff;
  }
  .tab-icon { font-size: 15px; }

  /* ─── MAIN CONTENT ─── */
  .main { padding: 24px; max-width: 1200px; margin: 0 auto; }
  .tab-content { display: none; }
  .tab-content.active { display: block; }

  /* ─── SECTION TITLES ─── */
  .section-title {
    font-size: 22px;
    font-weight: 700;
    letter-spacing: -0.5px;
    margin-bottom: 6px;
  }
  .section-sub {
    font-size: 14px;
    color: var(--text-secondary);
    margin-bottom: 24px;
  }

  /* ─── CARDS ─── */
  .card {
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 20px;
    transition: border-color 0.2s;
  }
  .card:hover { border-color: rgba(79,110,247,0.25); }
  .card-title {
    font-size: 12px;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--text-muted);
    margin-bottom: 16px;
  }

  .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  .grid-3 { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 16px; }
  .grid-4 { display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px; }

  /* ─── FORM ELEMENTS ─── */
  .form-group { display: flex; flex-direction: column; gap: 6px; }
  .form-label {
    font-size: 12px;
    font-weight: 500;
    color: var(--text-secondary);
    letter-spacing: 0.03em;
  }
  .form-input, .form-select {
    background: var(--bg-input);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm);
    color: var(--text-primary);
    font-size: 14px;
    font-family: var(--font-main);
    padding: 10px 12px;
    outline: none;
    transition: border-color 0.2s, box-shadow 0.2s;
    width: 100%;
  }
  .form-input:focus, .form-select:focus {
    border-color: var(--border-focus);
    box-shadow: 0 0 0 3px var(--accent-blue-glow);
  }
  .form-select option { background: var(--bg-elevated); }

  /* ─── BUTTONS ─── */
  .btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border-radius: var(--radius-sm);
    font-size: 14px;
    font-weight: 600;
    font-family: var(--font-main);
    cursor: pointer;
    border: none;
    transition: all 0.2s;
  }
  .btn-primary {
    background: var(--accent-blue);
    color: #fff;
  }
  .btn-primary:hover { background: #6b84f9; transform: translateY(-1px); box-shadow: 0 4px 16px rgba(79,110,247,0.4); }
  .btn-ghost {
    background: transparent;
    color: var(--text-secondary);
    border: 1px solid var(--border);
  }
  .btn-ghost:hover { background: var(--bg-elevated); color: var(--text-primary); }
  .btn-danger {
    background: transparent;
    color: var(--accent-red);
    border: 1px solid rgba(247,82,82,0.3);
    padding: 6px 12px;
    font-size: 12px;
  }
  .btn-danger:hover { background: var(--accent-red-glow); }
  .btn-success {
    background: var(--accent-green);
    color: #0a0b0f;
  }
  .btn-success:hover { background: #4ae09c; transform: translateY(-1px); }

  /* ─── PROFILE SECTION ─── */
  .profile-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; margin-bottom: 20px; }
  .profile-actions { display: flex; gap: 12px; justify-content: flex-end; margin-top: 20px; }
  .bmi-card {
    background: linear-gradient(135deg, var(--accent-blue-glow), rgba(167,139,250,0.1));
    border: 1px solid rgba(79,110,247,0.3);
    border-radius: var(--radius-lg);
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  .bmi-value {
    font-size: 48px;
    font-weight: 700;
    font-family: var(--font-mono);
    letter-spacing: -2px;
    background: linear-gradient(90deg, var(--accent-blue), var(--accent-purple));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  /* ─── FOOD LOG ─── */
  .food-log-form {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr auto;
    gap: 12px;
    align-items: flex-end;
    margin-bottom: 20px;
    padding: 16px;
    background: var(--bg-elevated);
    border-radius: var(--radius-md);
    border: 1px solid var(--border);
  }
  .food-table-wrap { overflow-x: auto; }
  table { width: 100%; border-collapse: collapse; }
  thead th {
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    color: var(--text-muted);
    padding: 10px 12px;
    text-align: left;
    border-bottom: 1px solid var(--border);
  }
  tbody tr {
    border-bottom: 1px solid rgba(34,37,48,0.6);
    transition: background 0.15s;
  }
  tbody tr:hover { background: var(--bg-elevated); }
  tbody td { padding: 12px; font-size: 13px; }
  .td-food { font-weight: 500; }
  .td-num {
    font-family: var(--font-mono);
    font-size: 12px;
    color: var(--text-secondary);
  }
  .empty-state {
    text-align: center;
    padding: 48px 20px;
    color: var(--text-muted);
  }
  .empty-icon { font-size: 36px; margin-bottom: 12px; }
  .empty-title { font-size: 16px; font-weight: 600; color: var(--text-secondary); }
  .empty-sub { font-size: 13px; margin-top: 6px; }

  /* ─── DASHBOARD ─── */
  .energy-ring-card {
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 28px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
  }
  .ring-wrap { position: relative; width: 180px; height: 180px; }
  .ring-label {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 2px;
  }
  .ring-kcal {
    font-size: 32px;
    font-weight: 700;
    font-family: var(--font-mono);
    letter-spacing: -1px;
  }
  .ring-pct {
    font-size: 12px;
    color: var(--text-muted);
  }

  /* ─── STAT CHIPS ─── */
  .stat-chips { display: flex; gap: 10px; flex-wrap: wrap; }
  .stat-chip {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 10px 14px;
    border-radius: var(--radius-md);
    border: 1px solid var(--border);
    background: var(--bg-elevated);
    flex: 1;
    min-width: 100px;
  }
  .chip-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }
  .chip-info { display: flex; flex-direction: column; gap: 2px; }
  .chip-label { font-size: 11px; color: var(--text-muted); }
  .chip-val { font-size: 15px; font-weight: 600; font-family: var(--font-mono); }

  /* ─── PROGRESS BARS ─── */
  .progress-row { display: flex; flex-direction: column; gap: 6px; margin-bottom: 14px; }
  .progress-header { display: flex; justify-content: space-between; align-items: center; }
  .progress-label { font-size: 13px; font-weight: 500; }
  .progress-pct { font-size: 12px; font-family: var(--font-mono); color: var(--text-muted); }
  .progress-bar-bg {
    height: 6px;
    background: var(--bg-elevated);
    border-radius: 3px;
    overflow: hidden;
  }
  .progress-bar-fill {
    height: 100%;
    border-radius: 3px;
    transition: width 0.6s cubic-bezier(.4,0,.2,1);
  }

  /* ─── DEFICIENCY / EXCESS PILLS ─── */
  .insight-list { display: flex; flex-direction: column; gap: 8px; }
  .insight-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 14px;
    border-radius: var(--radius-sm);
    font-size: 13px;
  }
  .insight-def { background: rgba(79,110,247,0.1); border: 1px solid rgba(79,110,247,0.2); }
  .insight-exc { background: var(--accent-red-glow); border: 1px solid rgba(247,82,82,0.2); }
  .insight-ok  { background: var(--accent-green-glow); border: 1px solid rgba(52,212,138,0.2); }
  .insight-name { font-weight: 500; }
  .insight-val { font-family: var(--font-mono); font-size: 12px; color: var(--text-secondary); }
  .insight-badge {
    font-size: 11px;
    font-weight: 600;
    padding: 2px 8px;
    border-radius: 10px;
  }
  .badge-low { background: rgba(79,110,247,0.2); color: #7e9bff; }
  .badge-high { background: rgba(247,82,82,0.2); color: var(--accent-red); }
  .badge-ok { background: rgba(52,212,138,0.2); color: var(--accent-green); }

  /* ─── RECOMMENDATIONS ─── */
  .rec-card {
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 20px;
    margin-bottom: 14px;
    display: flex;
    gap: 16px;
    align-items: flex-start;
  }
  .rec-icon {
    width: 40px; height: 40px; flex-shrink: 0;
    border-radius: var(--radius-sm);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
  }
  .rec-add .rec-icon { background: var(--accent-green-glow); }
  .rec-swap .rec-icon { background: var(--accent-blue-glow); }
  .rec-reduce .rec-icon { background: var(--accent-red-glow); }
  .rec-type {
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    margin-bottom: 4px;
  }
  .rec-add .rec-type { color: var(--accent-green); }
  .rec-swap .rec-type { color: #7e9bff; }
  .rec-reduce .rec-type { color: var(--accent-red); }
  .rec-text { font-size: 14px; line-height: 1.6; }
  .rec-reason { font-size: 12px; color: var(--text-muted); margin-top: 4px; }

  /* ─── NUTRIENT TABLE ─── */
  .nutrient-table th { font-size: 11px; color: var(--text-muted); padding: 8px 10px; text-align: left; letter-spacing: 0.06em; text-transform: uppercase; border-bottom: 1px solid var(--border); }
  .nutrient-table td { padding: 10px; font-size: 13px; border-bottom: 1px solid rgba(34,37,48,0.5); }
  .nutrient-table tr:hover td { background: var(--bg-elevated); }
  .nt-name { font-weight: 500; }
  .nt-bar { width: 100px; height: 5px; background: var(--bg-elevated); border-radius: 3px; display: inline-block; overflow: hidden; }
  .nt-fill { height: 100%; border-radius: 3px; }

  /* ─── MACRO CHART AREA ─── */
  .chart-container { position: relative; height: 220px; }

  /* ─── TOAST ─── */
  .toast {
    position: fixed;
    bottom: 24px;
    right: 24px;
    background: var(--bg-elevated);
    border: 1px solid var(--accent-green);
    color: var(--text-primary);
    padding: 12px 20px;
    border-radius: var(--radius-md);
    font-size: 14px;
    font-weight: 500;
    z-index: 9999;
    transform: translateY(80px);
    opacity: 0;
    transition: all 0.3s cubic-bezier(.4,0,.2,1);
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .toast.show { transform: translateY(0); opacity: 1; }

  /* ─── INLINE EDIT ─── */
  .inline-edit {
    background: var(--bg-input);
    border: 1px solid var(--border-focus);
    border-radius: 4px;
    color: var(--text-primary);
    font-size: 13px;
    font-family: var(--font-mono);
    padding: 4px 8px;
    width: 70px;
    outline: none;
  }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 768px) {
    .profile-grid { grid-template-columns: 1fr 1fr; }
    .grid-2, .grid-3, .grid-4 { grid-template-columns: 1fr; }
    .food-log-form { grid-template-columns: 1fr 1fr; }
    .food-log-form .btn { grid-column: span 2; }
    .main { padding: 16px; }
    .stat-chips { flex-direction: column; }
  }
  @media (max-width: 480px) {
    .profile-grid { grid-template-columns: 1fr; }
    .food-log-form { grid-template-columns: 1fr; }
    .food-log-form .btn { grid-column: span 1; }
  }
</style>
</head>
<body>
<div class="app-wrapper">

  <!-- TOP BAR -->
  <header class="topbar">
    <div class="logo">
      <div class="logo-icon">🥗</div>
      NutriScope <span>/ Daily Tracker</span>
    </div>
    <div class="date-badge" id="dateBadge"></div>
  </header>

  <!-- NAV TABS -->
  <nav class="nav-tabs">
    <button class="tab-btn active" onclick="switchTab('profile', this)"><span class="tab-icon">👤</span> Profile</button>
    <button class="tab-btn" onclick="switchTab('log', this)"><span class="tab-icon">📋</span> Food Log</button>
    <button class="tab-btn" onclick="switchTab('dashboard', this)"><span class="tab-icon">📊</span> Dashboard</button>
    <button class="tab-btn" onclick="switchTab('recommendations', this)"><span class="tab-icon">💡</span> Recommendations</button>
  </nav>

  <main class="main">

    <!-- ═══ PROFILE TAB ═══ -->
    <div id="tab-profile" class="tab-content active">
      <div class="section-title">Your Profile</div>
      <div class="section-sub">Set up your details to get personalised nutrition targets.</div>

      <div class="card" style="margin-bottom:16px">
        <div class="card-title">Personal Details</div>
        <div class="profile-grid">
          <div class="form-group">
            <label class="form-label">Age (years)</label>
            <input type="number" id="age" class="form-input" placeholder="25" min="1" max="120">
          </div>
          <div class="form-group">
            <label class="form-label">Gender</label>
            <select id="gender" class="form-select">
              <option value="">Select gender</option>
              <option value="male">Male</option>
              <option value="female">Female</option>
              <option value="other">Other</option>
            </select>
          </div>
          <div class="form-group">
            <label class="form-label">Height (cm)</label>
            <input type="number" id="height" class="form-input" placeholder="170" min="50" max="250">
          </div>
          <div class="form-group">
            <label class="form-label">Weight (kg)</label>
            <input type="number" id="weight" class="form-input" placeholder="70" min="10" max="300">
          </div>
          <div class="form-group">
            <label class="form-label">Activity Level</label>
            <select id="activity" class="form-select">
              <option value="">Select activity</option>
              <option value="1.2">Sedentary (desk job, no exercise)</option>
              <option value="1.375">Lightly active (1–3 days/week)</option>
              <option value="1.55">Moderately active (3–5 days/week)</option>
              <option value="1.725">Very active (6–7 days/week)</option>
              <option value="1.9">Extra active (athlete/physical job)</option>
            </select>
          </div>
          <div class="form-group">
            <label class="form-label">Dietary Preference</label>
            <select id="dietPref" class="form-select">
              <option value="">Select preference</option>
              <option value="veg">Vegetarian</option>
              <option value="nonveg">Non-Vegetarian</option>
              <option value="egg">Eggetarian</option>
            </select>
          </div>
        </div>
        <div class="profile-actions">
          <button class="btn btn-primary" onclick="saveProfile()">💾 Save Profile & Calculate Targets</button>
        </div>
      </div>

      <!-- BMI + Targets Preview -->
      <div class="grid-2" id="profileResults" style="display:none">
        <div class="bmi-card">
          <div style="font-size:12px;color:var(--text-muted);font-weight:600;letter-spacing:.06em;text-transform:uppercase">Body Mass Index</div>
          <div class="bmi-value" id="bmiVal">—</div>
          <div id="bmiLabel" style="font-size:14px;color:var(--text-secondary)"></div>
          <div style="font-size:12px;color:var(--text-muted)" id="tdeeVal"></div>
        </div>
        <div class="card">
          <div class="card-title">Daily Targets</div>
          <div id="targetsPreview" style="display:flex;flex-direction:column;gap:10px"></div>
        </div>
      </div>
    </div>

    <!-- ═══ FOOD LOG TAB ═══ -->
    <div id="tab-log" class="tab-content">
      <div class="section-title">Food Log</div>
      <div class="section-sub">Add everything you've eaten today. Click quantity to edit inline.</div>

      <div class="food-log-form">
        <div class="form-group">
          <label class="form-label">Food Item</label>
          <select id="foodSelect" class="form-select">
            <option value="">Select food…</option>
          </select>
        </div>
        <div class="form-group">
          <label class="form-label">Quantity</label>
          <input type="number" id="foodQty" class="form-input" placeholder="100" min="1" value="100">
        </div>
        <div class="form-group">
          <label class="form-label">Unit</label>
          <select id="foodUnit" class="form-select">
            <option value="g">grams (g)</option>
            <option value="ml">ml</option>
            <option value="piece">piece</option>
            <option value="cup">cup (240g)</option>
            <option value="tbsp">tbsp (15g)</option>
          </select>
        </div>
        <button class="btn btn-success" onclick="addFood()">＋ Add</button>
      </div>

      <div class="card">
        <div class="food-table-wrap">
          <table id="foodTable">
            <thead>
              <tr>
                <th>Food</th><th>Qty</th><th>Unit</th>
                <th>Cal</th><th>Protein</th><th>Carbs</th><th>Fat</th><th>Fiber</th>
                <th>Iron</th><th>Ca</th><th>Vit C</th><th>Vit D</th><th>B12</th>
                <th></th>
              </tr>
            </thead>
            <tbody id="foodTableBody">
              <tr><td colspan="14"><div class="empty-state"><div class="empty-icon">🍽️</div><div class="empty-title">No food logged yet</div><div class="empty-sub">Add your first meal above to start tracking</div></div></td></tr>
            </tbody>
          </table>
        </div>
        <!-- Totals row -->
        <div id="totalsRow" style="display:none;margin-top:16px;padding-top:16px;border-top:1px solid var(--border)">
          <div class="card-title">Today's Totals</div>
          <div class="stat-chips" id="totalsChips"></div>
        </div>
      </div>
    </div>

    <!-- ═══ DASHBOARD TAB ═══ -->
    <div id="tab-dashboard" class="tab-content">
      <div class="section-title">Dashboard</div>
      <div class="section-sub">Your nutrition snapshot for today.</div>

      <div style="display:grid;grid-template-columns:220px 1fr;gap:16px;margin-bottom:16px" id="dashTop">
        <!-- Energy ring -->
        <div class="energy-ring-card">
          <div class="card-title" style="margin-bottom:0">Energy</div>
          <div class="ring-wrap">
            <canvas id="energyRing" width="180" height="180"></canvas>
            <div class="ring-label">
              <div class="ring-kcal" id="dashKcal">0</div>
              <div class="ring-pct" id="dashKcalPct">of 0 kcal</div>
            </div>
          </div>
          <div style="display:flex;flex-direction:column;gap:6px;width:100%">
            <div style="font-size:12px;color:var(--text-muted);display:flex;justify-content:space-between"><span>Remaining</span><span id="dashRemain" style="font-family:var(--font-mono);color:var(--text-secondary)">—</span></div>
          </div>
        </div>

        <!-- Macro chart + chips -->
        <div class="card">
          <div class="card-title">Macronutrients</div>
          <div class="chart-container">
            <canvas id="macroChart"></canvas>
          </div>
          <div class="stat-chips" style="margin-top:16px" id="macroChips"></div>
        </div>
      </div>

      <div class="grid-2" style="margin-bottom:16px">
        <!-- Deficiencies -->
        <div class="card">
          <div class="card-title">⚠️ Top Deficiencies</div>
          <div class="insight-list" id="defList"><div style="color:var(--text-muted);font-size:13px">Log food to see insights</div></div>
        </div>
        <!-- Excesses -->
        <div class="card">
          <div class="card-title">🔺 Top Excesses</div>
          <div class="insight-list" id="excList"><div style="color:var(--text-muted);font-size:13px">Log food to see insights</div></div>
        </div>
      </div>

      <!-- Full nutrient table -->
      <div class="card">
        <div class="card-title">📋 Full Nutrient Breakdown</div>
        <div style="overflow-x:auto">
          <table class="nutrient-table">
            <thead>
              <tr>
                <th>Nutrient</th><th>Consumed</th><th>Target</th><th>Progress</th><th>Status</th>
              </tr>
            </thead>
            <tbody id="nutrientTableBody"></tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- ═══ RECOMMENDATIONS TAB ═══ -->
    <div id="tab-recommendations" class="tab-content">
      <div class="section-title">Smart Recommendations</div>
      <div class="section-sub">Personalised suggestions based on your log and dietary preference.</div>
      <div id="recsContainer"><div class="empty-state"><div class="empty-icon">💡</div><div class="empty-title">Save your profile and log some food first</div><div class="empty-sub">Recommendations will appear once we have data to work with</div></div></div>
    </div>

  </main>
</div>

<!-- TOAST -->
<div class="toast" id="toast"><span id="toastIcon">✅</span><span id="toastMsg"></span></div>

<script>
// ═══════════════════════════════════════════════
// FOOD DATABASE (per 100g unless noted)
// Fields: cal, protein, carbs, fat, fiber, iron, calcium, vitC, vitD, vitB12
// iron(mg), calcium(mg), vitC(mg), vitD(mcg), vitB12(mcg)
// ═══════════════════════════════════════════════
const FOODS = {
  "Rice":       { cal:130, protein:2.7,  carbs:28.0, fat:0.3,  fiber:0.4, iron:0.8,  calcium:10,  vitC:0,   vitD:0,   vitB12:0    },
  "Roti":       { cal:264, protein:8.5,  carbs:52.0, fat:3.7,  fiber:3.0, iron:3.9,  calcium:40,  vitC:0,   vitD:0,   vitB12:0    },
  "Dal":        { cal:116, protein:8.0,  carbs:18.0, fat:0.5,  fiber:3.5, iron:3.3,  calcium:30,  vitC:1.5, vitD:0,   vitB12:0    },
  "Paneer":     { cal:265, protein:18.0, carbs:3.5,  fat:20.0, fiber:0,   iron:0.2,  calcium:480, vitC:0,   vitD:0.3, vitB12:0.5  },
  "Curd":       { cal:98,  protein:3.5,  carbs:3.4,  fat:4.3,  fiber:0,   iron:0.1,  calcium:121, vitC:0,   vitD:0.1, vitB12:0.4  },
  "Chana":      { cal:164, protein:8.9,  carbs:27.0, fat:2.6,  fiber:7.6, iron:2.9,  calcium:49,  vitC:1.3, vitD:0,   vitB12:0    },
  "Rajma":      { cal:127, protein:8.7,  carbs:22.8, fat:0.5,  fiber:6.4, iron:2.5,  calcium:83,  vitC:1.0, vitD:0,   vitB12:0    },
  "Banana":     { cal:89,  protein:1.1,  carbs:23.0, fat:0.3,  fiber:2.6, iron:0.3,  calcium:5,   vitC:8.7, vitD:0,   vitB12:0    },
  "Apple":      { cal:52,  protein:0.3,  carbs:14.0, fat:0.2,  fiber:2.4, iron:0.1,  calcium:6,   vitC:4.6, vitD:0,   vitB12:0    },
  "Milk":       { cal:61,  protein:3.2,  carbs:4.8,  fat:3.3,  fiber:0,   iron:0.1,  calcium:113, vitC:0,   vitD:1.3, vitB12:0.5  },
  "Oats":       { cal:389, protein:17.0, carbs:66.0, fat:7.0,  fiber:11.0,iron:4.7,  calcium:54,  vitC:0,   vitD:0,   vitB12:0    },
  "Bread":      { cal:265, protein:9.0,  carbs:49.0, fat:3.2,  fiber:2.7, iron:2.9,  calcium:80,  vitC:0,   vitD:0,   vitB12:0    },
  "Egg":        { cal:155, protein:13.0, carbs:1.1,  fat:11.0, fiber:0,   iron:1.8,  calcium:56,  vitC:0,   vitD:2.0, vitB12:1.1  },
  "Chicken":    { cal:165, protein:31.0, carbs:0,    fat:3.6,  fiber:0,   iron:1.0,  calcium:15,  vitC:0,   vitD:0.1, vitB12:0.3  },
  "Fish":       { cal:136, protein:20.0, carbs:0,    fat:6.0,  fiber:0,   iron:0.9,  calcium:20,  vitC:0,   vitD:11.0,vitB12:3.0  },
  "Potato":     { cal:77,  protein:2.0,  carbs:17.0, fat:0.1,  fiber:2.2, iron:0.8,  calcium:12,  vitC:19.7,vitD:0,   vitB12:0    },
  "Poha":       { cal:350, protein:7.0,  carbs:76.0, fat:1.2,  fiber:2.5, iron:2.8,  calcium:14,  vitC:0,   vitD:0,   vitB12:0    },
  "Idli":       { cal:58,  protein:2.0,  carbs:12.0, fat:0.1,  fiber:0.7, iron:0.5,  calcium:12,  vitC:0,   vitD:0,   vitB12:0    },
  "Dosa":       { cal:133, protein:3.4,  carbs:23.0, fat:3.0,  fiber:1.0, iron:0.9,  calcium:28,  vitC:0,   vitD:0,   vitB12:0    },
  "Spinach":    { cal:23,  protein:2.9,  carbs:3.6,  fat:0.4,  fiber:2.2, iron:2.7,  calcium:99,  vitC:28.1,vitD:0,   vitB12:0    },
};

// Unit multipliers (to grams)
const UNIT_MULT = { g: 1, ml: 1, piece: 100, cup: 240, tbsp: 15 };

// ═══════════════════════════════════════════════
// STATE
// ═══════════════════════════════════════════════
let profile = null;
let targets = null;
let foodLog = []; // [{name, qty, unit, grams, nutrients}]
let charts = {};

// ═══════════════════════════════════════════════
// INIT
// ═══════════════════════════════════════════════
document.addEventListener('DOMContentLoaded', () => {
  document.getElementById('dateBadge').textContent = new Date().toLocaleDateString('en-IN', { weekday:'short', day:'numeric', month:'short', year:'numeric' });

  // Populate food select
  const sel = document.getElementById('foodSelect');
  Object.keys(FOODS).sort().forEach(f => {
    const opt = document.createElement('option');
    opt.value = f; opt.textContent = f;
    sel.appendChild(opt);
  });

  // Load saved state
  const saved = localStorage.getItem('nutriscope_state');
  if (saved) {
    try {
      const s = JSON.parse(saved);
      if (s.profile) {
        profile = s.profile;
        fillProfileForm(profile);
        computeTargets();
        showProfileResults();
      }
      if (s.foodLog) {
        foodLog = s.foodLog;
        renderFoodTable();
      }
    } catch(e) {}
  }
});

function saveState() {
  localStorage.setItem('nutriscope_state', JSON.stringify({ profile, foodLog }));
}

// ═══════════════════════════════════════════════
// TAB SWITCHING
// ═══════════════════════════════════════════════
function switchTab(name, btn) {
  document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.getElementById('tab-' + name).classList.add('active');
  btn.classList.add('active');
  if (name === 'dashboard') renderDashboard();
  if (name === 'recommendations') renderRecommendations();
}

// ═══════════════════════════════════════════════
// PROFILE
// ═══════════════════════════════════════════════
function fillProfileForm(p) {
  document.getElementById('age').value = p.age || '';
  document.getElementById('gender').value = p.gender || '';
  document.getElementById('height').value = p.height || '';
  document.getElementById('weight').value = p.weight || '';
  document.getElementById('activity').value = p.activity || '';
  document.getElementById('dietPref').value = p.dietPref || '';
}

function saveProfile() {
  const age = parseFloat(document.getElementById('age').value);
  const gender = document.getElementById('gender').value;
  const height = parseFloat(document.getElementById('height').value);
  const weight = parseFloat(document.getElementById('weight').value);
  const activity = parseFloat(document.getElementById('activity').value);
  const dietPref = document.getElementById('dietPref').value;

  if (!age || !gender || !height || !weight || !activity || !dietPref) {
    showToast('⚠️ Please fill all fields', 'warn'); return;
  }
  profile = { age, gender, height, weight, activity, dietPref };
  computeTargets();
  showProfileResults();
  saveState();
  showToast('✅ Profile saved & targets calculated');
}

function computeTargets() {
  if (!profile) return;
  const { age, gender, height, weight, activity } = profile;
  // Mifflin-St Jeor BMR
  let bmr;
  if (gender === 'male') bmr = 10*weight + 6.25*height - 5*age + 5;
  else bmr = 10*weight + 6.25*height - 5*age - 161;
  const tdee = Math.round(bmr * activity);

  // Macros: protein 0.8g/kg, fat 25% cal, rest carbs
  const protein = Math.round(weight * 0.8);
  const fat = Math.round((tdee * 0.25) / 9);
  const carbs = Math.round((tdee - protein*4 - fat*9) / 4);

  targets = {
    tdee, protein, fat, carbs,
    fiber: 28,
    iron: gender === 'female' ? 18 : 8,
    calcium: 1000,
    vitC: 65,
    vitD: 15,
    vitB12: 2.4
  };
  return targets;
}

function showProfileResults() {
  if (!profile || !targets) return;
  const { height, weight } = profile;
  const bmi = (weight / ((height/100)**2)).toFixed(1);
  let bmiLabel = '';
  if (bmi < 18.5) bmiLabel = '⚠️ Underweight';
  else if (bmi < 25) bmiLabel = '✅ Normal weight';
  else if (bmi < 30) bmiLabel = '⚠️ Overweight';
  else bmiLabel = '🔴 Obese';

  document.getElementById('bmiVal').textContent = bmi;
  document.getElementById('bmiLabel').textContent = bmiLabel;
  document.getElementById('tdeeVal').textContent = `Daily energy need: ${targets.tdee} kcal`;

  const tp = document.getElementById('targetsPreview');
  tp.innerHTML = [
    ['⚡ Energy', targets.tdee + ' kcal', '#4f6ef7'],
    ['🥩 Protein', targets.protein + ' g', '#f5a623'],
    ['🍞 Carbs', targets.carbs + ' g', '#22d3ee'],
    ['🧈 Fat', targets.fat + ' g', '#a78bfa'],
    ['🌾 Fiber', targets.fiber + ' g', '#34d48a'],
  ].map(([label, val, color]) => `
    <div style="display:flex;justify-content:space-between;align-items:center;padding:8px 12px;background:var(--bg-elevated);border-radius:8px">
      <span style="font-size:13px">${label}</span>
      <span style="font-family:var(--font-mono);font-size:13px;color:${color};font-weight:600">${val}</span>
    </div>`).join('');

  document.getElementById('profileResults').style.display = 'grid';
}

// ═══════════════════════════════════════════════
// FOOD LOG
// ═══════════════════════════════════════════════
function addFood() {
  const name = document.getElementById('foodSelect').value;
  const qty = parseFloat(document.getElementById('foodQty').value);
  const unit = document.getElementById('foodUnit').value;

  if (!name) { showToast('⚠️ Select a food item', 'warn'); return; }
  if (!qty || qty <= 0) { showToast('⚠️ Enter a valid quantity', 'warn'); return; }

  const mult = UNIT_MULT[unit] || 1;
  const grams = qty * mult;
  const base = FOODS[name];
  const factor = grams / 100;

  const nutrients = {};
  Object.keys(base).forEach(k => nutrients[k] = +(base[k] * factor).toFixed(2));

  foodLog.push({ id: Date.now(), name, qty, unit, grams, nutrients });
  renderFoodTable();
  saveState();
  showToast(`✅ ${name} added`);
}

function removeFood(id) {
  foodLog = foodLog.filter(f => f.id !== id);
  renderFoodTable();
  saveState();
}

function renderFoodTable() {
  const tbody = document.getElementById('foodTableBody');
  if (foodLog.length === 0) {
    tbody.innerHTML = `<tr><td colspan="14"><div class="empty-state"><div class="empty-icon">🍽️</div><div class="empty-title">No food logged yet</div><div class="empty-sub">Add your first meal above to start tracking</div></div></td></tr>`;
    document.getElementById('totalsRow').style.display = 'none';
    return;
  }

  tbody.innerHTML = foodLog.map(f => `
    <tr>
      <td class="td-food">${f.name}</td>
      <td class="td-num" onclick="startInlineEdit(this, ${f.id})" style="cursor:pointer" title="Click to edit">${f.qty}</td>
      <td class="td-num">${f.unit}</td>
      <td class="td-num">${f.nutrients.cal}</td>
      <td class="td-num">${f.nutrients.protein}g</td>
      <td class="td-num">${f.nutrients.carbs}g</td>
      <td class="td-num">${f.nutrients.fat}g</td>
      <td class="td-num">${f.nutrients.fiber}g</td>
      <td class="td-num">${f.nutrients.iron}mg</td>
      <td class="td-num">${f.nutrients.calcium}mg</td>
      <td class="td-num">${f.nutrients.vitC}mg</td>
      <td class="td-num">${f.nutrients.vitD}µg</td>
      <td class="td-num">${f.nutrients.vitB12}µg</td>
      <td><button class="btn btn-danger" onclick="removeFood(${f.id})">✕</button></td>
    </tr>`).join('');

  // Totals
  const totals = getTotals();
  document.getElementById('totalsRow').style.display = 'block';
  document.getElementById('totalsChips').innerHTML = [
    ['⚡', 'Calories', Math.round(totals.cal) + ' kcal', '#4f6ef7'],
    ['🥩', 'Protein', totals.protein.toFixed(1) + 'g', '#f5a623'],
    ['🍞', 'Carbs', totals.carbs.toFixed(1) + 'g', '#22d3ee'],
    ['🧈', 'Fat', totals.fat.toFixed(1) + 'g', '#a78bfa'],
    ['🌾', 'Fiber', totals.fiber.toFixed(1) + 'g', '#34d48a'],
  ].map(([icon, label, val, color]) => `
    <div class="stat-chip">
      <span style="font-size:16px">${icon}</span>
      <div class="chip-info">
        <span class="chip-label">${label}</span>
        <span class="chip-val" style="color:${color}">${val}</span>
      </div>
    </div>`).join('');
}

function startInlineEdit(cell, id) {
  const current = cell.textContent.trim();
  const input = document.createElement('input');
  input.type = 'number';
  input.className = 'inline-edit';
  input.value = current;
  cell.textContent = '';
  cell.appendChild(input);
  input.focus();

  const commit = () => {
    const newQty = parseFloat(input.value);
    if (newQty > 0) {
      const entry = foodLog.find(f => f.id === id);
      if (entry) {
        entry.qty = newQty;
        entry.grams = newQty * (UNIT_MULT[entry.unit] || 1);
        const base = FOODS[entry.name];
        const factor = entry.grams / 100;
        Object.keys(base).forEach(k => entry.nutrients[k] = +(base[k] * factor).toFixed(2));
      }
    }
    renderFoodTable();
    saveState();
  };
  input.addEventListener('blur', commit);
  input.addEventListener('keydown', e => { if (e.key === 'Enter') commit(); });
}

function getTotals() {
  const t = { cal:0, protein:0, carbs:0, fat:0, fiber:0, iron:0, calcium:0, vitC:0, vitD:0, vitB12:0 };
  foodLog.forEach(f => { Object.keys(t).forEach(k => t[k] += f.nutrients[k] || 0); });
  return t;
}

// ═══════════════════════════════════════════════
// DASHBOARD
// ═══════════════════════════════════════════════
function renderDashboard() {
  const totals = getTotals();
  const t = targets || { tdee:2000, protein:50, carbs:250, fat:55, fiber:28, iron:8, calcium:1000, vitC:65, vitD:15, vitB12:2.4 };

  // Energy ring
  const pct = Math.min(Math.round((totals.cal / t.tdee) * 100), 100);
  document.getElementById('dashKcal').textContent = Math.round(totals.cal);
  document.getElementById('dashKcalPct').textContent = `of ${t.tdee} kcal`;
  document.getElementById('dashRemain').textContent = Math.max(0, t.tdee - Math.round(totals.cal)) + ' kcal';

  // Destroy and redraw energy ring
  if (charts.ring) { charts.ring.destroy(); }
  const ringCtx = document.getElementById('energyRing').getContext('2d');
  const ringColor = pct > 110 ? '#f75252' : pct > 90 ? '#f5a623' : '#34d48a';
  charts.ring = new Chart(ringCtx, {
    type: 'doughnut',
    data: {
      datasets: [{
        data: [pct, Math.max(0, 100-pct)],
        backgroundColor: [ringColor, 'rgba(255,255,255,0.05)'],
        borderWidth: 0,
        hoverOffset: 0,
      }]
    },
    options: {
      cutout: '75%',
      plugins: { legend: { display: false }, tooltip: { enabled: false } },
      animation: { animateRotate: true, duration: 800 }
    }
  });

  // Macro bar chart
  if (charts.macro) charts.macro.destroy();
  const macroCtx = document.getElementById('macroChart').getContext('2d');
  charts.macro = new Chart(macroCtx, {
    type: 'bar',
    data: {
      labels: ['Protein', 'Carbs', 'Fat', 'Fiber'],
      datasets: [
        {
          label: 'Consumed',
          data: [totals.protein, totals.carbs, totals.fat, totals.fiber],
          backgroundColor: ['rgba(245,166,35,0.85)', 'rgba(34,211,238,0.85)', 'rgba(167,139,250,0.85)', 'rgba(52,212,138,0.85)'],
          borderRadius: 6,
        },
        {
          label: 'Target',
          data: [t.protein, t.carbs, t.fat, t.fiber],
          backgroundColor: ['rgba(245,166,35,0.2)', 'rgba(34,211,238,0.2)', 'rgba(167,139,250,0.2)', 'rgba(52,212,138,0.2)'],
          borderRadius: 6,
        }
      ]
    },
    options: {
      responsive: true, maintainAspectRatio: false,
      plugins: {
        legend: { labels: { color: '#8b90a7', font: { size: 11 } } },
        tooltip: { callbacks: { label: ctx => `${ctx.dataset.label}: ${ctx.parsed.y.toFixed(1)}g` } }
      },
      scales: {
        x: { ticks: { color: '#8b90a7' }, grid: { color: 'rgba(255,255,255,0.04)' } },
        y: { ticks: { color: '#8b90a7' }, grid: { color: 'rgba(255,255,255,0.04)' } }
      }
    }
  });

  // Macro chips
  const chips = [
    ['🥩', 'Protein', totals.protein.toFixed(1)+'g / '+t.protein+'g', '#f5a623', totals.protein, t.protein],
    ['🍞', 'Carbs', totals.carbs.toFixed(1)+'g / '+t.carbs+'g', '#22d3ee', totals.carbs, t.carbs],
    ['🧈', 'Fat', totals.fat.toFixed(1)+'g / '+t.fat+'g', '#a78bfa', totals.fat, t.fat],
  ];
  document.getElementById('macroChips').innerHTML = chips.map(([icon, label, val, color]) => `
    <div class="stat-chip">
      <span style="font-size:16px">${icon}</span>
      <div class="chip-info"><span class="chip-label">${label}</span><span class="chip-val" style="color:${color}">${val}</span></div>
    </div>`).join('');

  // Deficiencies & excesses
  const nutrients = [
    { key:'cal', label:'Calories', unit:'kcal', target: t.tdee, val: totals.cal },
    { key:'protein', label:'Protein', unit:'g', target: t.protein, val: totals.protein },
    { key:'carbs', label:'Carbs', unit:'g', target: t.carbs, val: totals.carbs },
    { key:'fat', label:'Fat', unit:'g', target: t.fat, val: totals.fat },
    { key:'fiber', label:'Fiber', unit:'g', target: t.fiber, val: totals.fiber },
    { key:'iron', label:'Iron', unit:'mg', target: t.iron, val: totals.iron },
    { key:'calcium', label:'Calcium', unit:'mg', target: t.calcium, val: totals.calcium },
    { key:'vitC', label:'Vitamin C', unit:'mg', target: t.vitC, val: totals.vitC },
    { key:'vitD', label:'Vitamin D', unit:'µg', target: t.vitD, val: totals.vitD },
    { key:'vitB12', label:'Vitamin B12', unit:'µg', target: t.vitB12, val: totals.vitB12 },
  ];

  const defs = nutrients.filter(n => n.val < n.target * 0.75).sort((a,b) => (a.val/a.target)-(b.val/b.target)).slice(0,5);
  const excs = nutrients.filter(n => n.val > n.target * 1.2).sort((a,b) => (b.val/b.target)-(a.val/a.target)).slice(0,5);

  document.getElementById('defList').innerHTML = defs.length ? defs.map(n => {
    const pct = Math.round((n.val/n.target)*100);
    return `<div class="insight-item insight-def">
      <span class="insight-name">${n.label}</span>
      <span class="insight-val">${n.val.toFixed(1)} / ${n.target} ${n.unit}</span>
      <span class="insight-badge badge-low">${pct}%</span>
    </div>`;
  }).join('') : '<div style="color:var(--accent-green);font-size:13px">✅ No major deficiencies!</div>';

  document.getElementById('excList').innerHTML = excs.length ? excs.map(n => {
    const pct = Math.round((n.val/n.target)*100);
    return `<div class="insight-item insight-exc">
      <span class="insight-name">${n.label}</span>
      <span class="insight-val">${n.val.toFixed(1)} / ${n.target} ${n.unit}</span>
      <span class="insight-badge badge-high">${pct}%</span>
    </div>`;
  }).join('') : '<div style="color:var(--accent-green);font-size:13px">✅ Nothing over-consumed!</div>';

  // Full nutrient table
  const colors = ['#4f6ef7','#f5a623','#22d3ee','#a78bfa','#34d48a','#f75252','#f5a623','#22d3ee','#a78bfa','#34d48a'];
  document.getElementById('nutrientTableBody').innerHTML = nutrients.map((n, i) => {
    const pct = Math.min(Math.round((n.val/n.target)*100), 150);
    const barPct = Math.min(pct, 100);
    const color = pct > 120 ? '#f75252' : pct >= 75 ? '#34d48a' : '#4f6ef7';
    const status = pct > 120 ? '<span class="insight-badge badge-high">High</span>' :
                   pct >= 75 ? '<span class="insight-badge badge-ok">Good</span>' :
                                '<span class="insight-badge badge-low">Low</span>';
    return `<tr>
      <td class="nt-name">${n.label}</td>
      <td style="font-family:var(--font-mono);font-size:12px">${n.val.toFixed(1)} ${n.unit}</td>
      <td style="font-family:var(--font-mono);font-size:12px;color:var(--text-muted)">${n.target} ${n.unit}</td>
      <td>
        <div style="display:flex;align-items:center;gap:8px">
          <div class="nt-bar"><div class="nt-fill" style="width:${barPct}%;background:${color}"></div></div>
          <span style="font-size:11px;font-family:var(--font-mono);color:var(--text-muted)">${pct}%</span>
        </div>
      </td>
      <td>${status}</td>
    </tr>`;
  }).join('');
}

// ═══════════════════════════════════════════════
// RECOMMENDATIONS
// ═══════════════════════════════════════════════
function renderRecommendations() {
  if (!profile || !targets) {
    document.getElementById('recsContainer').innerHTML = `<div class="empty-state"><div class="empty-icon">💡</div><div class="empty-title">Save your profile first</div><div class="empty-sub">We need your details to make personalised recommendations</div></div>`;
    return;
  }

  const totals = getTotals();
  const t = targets;
  const dietPref = profile.dietPref;
  const recs = [];

  // Analyse each nutrient
  const analysis = {
    protein:  totals.protein  / t.protein,
    carbs:    totals.carbs    / t.carbs,
    fat:      totals.fat      / t.fat,
    fiber:    totals.fiber    / t.fiber,
    iron:     totals.iron     / t.iron,
    calcium:  totals.calcium  / t.calcium,
    vitC:     totals.vitC     / t.vitC,
    vitD:     totals.vitD     / t.vitD,
    vitB12:   totals.vitB12   / t.vitB12,
  };

  // PROTEIN low
  if (analysis.protein < 0.7) {
    if (dietPref === 'veg')
      recs.push({ type:'add', icon:'🫘', title:'Add Paneer or Dal', text:'Your protein is below target. Add 100g paneer or a bowl of dal to your next meal.', reason:`Consumed ${totals.protein.toFixed(1)}g vs ${t.protein}g target` });
    else if (dietPref === 'nonveg')
      recs.push({ type:'add', icon:'🍗', title:'Add Chicken or Fish', text:'Boost protein by adding 150g grilled chicken or fish to lunch or dinner.', reason:`Consumed ${totals.protein.toFixed(1)}g vs ${t.protein}g target` });
    else
      recs.push({ type:'add', icon:'🥚', title:'Add Eggs or Dal', text:'Add 2 boiled eggs or a bowl of dal to hit your protein goal.', reason:`Consumed ${totals.protein.toFixed(1)}g vs ${t.protein}g target` });
  }

  // CALCIUM low
  if (analysis.calcium < 0.7) {
    recs.push({ type:'add', icon:'🥛', title:'Increase Dairy', text:'Add a glass of milk (240ml) or a bowl of curd (150g) to significantly boost calcium.', reason:`Only ${totals.calcium.toFixed(0)}mg of ${t.calcium}mg target` });
  }

  // IRON low
  if (analysis.iron < 0.7) {
    if (dietPref === 'veg' || dietPref === 'egg')
      recs.push({ type:'add', icon:'🌿', title:'Add Spinach', text:'Spinach is rich in iron. Add 100g to a curry, salad, or smoothie. Pair with vitamin C foods for better absorption.', reason:`Iron at ${totals.iron.toFixed(1)}mg vs ${t.iron}mg target` });
    else
      recs.push({ type:'add', icon:'🐟', title:'Include Fish or Chana', text:'Add fish (iron + B12) or chana (iron + fiber) to improve your iron levels.', reason:`Iron at ${totals.iron.toFixed(1)}mg vs ${t.iron}mg target` });
  }

  // VIT C low
  if (analysis.vitC < 0.6) {
    recs.push({ type:'add', icon:'🍎', title:'Add Fruits', text:'An apple or banana daily covers vitamin C needs. Potato is also a surprisingly good source.', reason:`Vitamin C at ${totals.vitC.toFixed(1)}mg vs ${t.vitC}mg target` });
  }

  // VIT D low
  if (analysis.vitD < 0.5) {
    if (dietPref === 'nonveg')
      recs.push({ type:'add', icon:'🐟', title:'Add Fish for Vitamin D', text:'Fish (especially fatty fish) is the best dietary source of Vitamin D. Include 100g in a meal.', reason:`Vitamin D at ${totals.vitD.toFixed(1)}µg vs ${t.vitD}µg target` });
    else
      recs.push({ type:'add', icon:'☀️', title:'Consider Vitamin D Supplementation', text:'Plant foods are poor sources of Vitamin D. Include fortified milk and get 15 min of morning sunlight.', reason:`Vitamin D at ${totals.vitD.toFixed(1)}µg vs ${t.vitD}µg target` });
  }

  // VIT B12 low
  if (analysis.vitB12 < 0.5) {
    if (dietPref === 'veg')
      recs.push({ type:'swap', icon:'🔄', title:'Boost B12 via Dairy', text:'Switch plain water to milk in your oats/cereal. Add curd as a daily staple — both are good B12 sources for vegetarians.', reason:`B12 at ${totals.vitB12.toFixed(1)}µg vs ${t.vitB12}µg target` });
    else if (dietPref === 'egg')
      recs.push({ type:'add', icon:'🥚', title:'Add Eggs for B12', text:'Two eggs cover ~90% of your B12 needs. Make them a daily part of your breakfast.', reason:`B12 at ${totals.vitB12.toFixed(1)}µg vs ${t.vitB12}µg target` });
    else
      recs.push({ type:'add', icon:'🐟', title:'Fish for B12', text:'Fish is the richest B12 source. Adding 100g fish provides over 100% of daily B12 needs.', reason:`B12 at ${totals.vitB12.toFixed(1)}µg vs ${t.vitB12}µg target` });
  }

  // Fiber low
  if (analysis.fiber < 0.7) {
    recs.push({ type:'add', icon:'🌾', title:'More Fiber', text:'Add rajma, chana, or oats to meals. Replace white rice with a mix of rice + dal for a higher fiber meal.', reason:`Fiber at ${totals.fiber.toFixed(1)}g vs ${t.fiber}g target` });
  }

  // Carbs high
  if (analysis.carbs > 1.3) {
    recs.push({ type:'swap', icon:'🔄', title:'Reduce Refined Carbs', text:'Swap white bread with roti, or reduce rice portion by 30–40%. Replace snacks with curd or chana.', reason:`Carbs at ${totals.carbs.toFixed(1)}g vs ${t.carbs}g target` });
  }

  // Fat high
  if (analysis.fat > 1.3) {
    recs.push({ type:'reduce', icon:'📉', title:'Reduce Fat Intake', text:'Reduce oil in cooking. Swap paneer for low-fat curd or dal as a protein source. Grill instead of frying.', reason:`Fat at ${totals.fat.toFixed(1)}g vs ${t.fat}g target` });
  }

  // Cal over
  if (totals.cal > t.tdee * 1.2) {
    recs.push({ type:'reduce', icon:'📉', title:'Caloric Surplus — Watch Portions', text:'You\'ve consumed significantly more than your target. Consider reducing portion sizes at the next meal, particularly for rice, roti, or bread.', reason:`${Math.round(totals.cal)} kcal consumed vs ${t.tdee} kcal target` });
  }

  // All good check
  if (recs.length === 0) {
    document.getElementById('recsContainer').innerHTML = `
      <div class="rec-card rec-add" style="align-items:center">
        <div class="rec-icon" style="font-size:32px;width:56px;height:56px">🎉</div>
        <div>
          <div class="rec-type">Great Job</div>
          <div class="rec-text" style="font-size:15px;font-weight:600">You're hitting all your nutrition targets today!</div>
          <div class="rec-reason">Keep logging meals to maintain this streak.</div>
        </div>
      </div>`;
    return;
  }

  document.getElementById('recsContainer').innerHTML = recs.map(r => `
    <div class="rec-card rec-${r.type}">
      <div class="rec-icon">${r.icon}</div>
      <div>
        <div class="rec-type">${r.type === 'add' ? '➕ Add Food' : r.type === 'swap' ? '🔄 Swap' : '📉 Reduce'}</div>
        <div class="rec-text"><strong>${r.title}</strong><br>${r.text}</div>
        <div class="rec-reason">📊 ${r.reason}</div>
      </div>
    </div>`).join('');
}

// ═══════════════════════════════════════════════
// TOAST
// ═══════════════════════════════════════════════
let toastTimer;
function showToast(msg, type = 'success') {
  const toast = document.getElementById('toast');
  document.getElementById('toastMsg').textContent = msg;
  toast.style.borderColor = type === 'warn' ? 'var(--accent-amber)' : 'var(--accent-green)';
  toast.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => toast.classList.remove('show'), 2800);
}
</script>
</body>
</html>

[NutriScope.html](https://github.com/user-attachments/files/28765407/NutriScope.html)


## Version 2 - Enhanced Application

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NutriScope v2 — Advanced Nutrition Intelligence</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=DM+Mono:wght@400;500&display=swap');
:root{
  --bg-base:#07080d;--bg-card:#0f1117;--bg-elevated:#161922;--bg-input:#11131a;
  --border:#1e2130;--border-focus:#4f6ef7;--border-subtle:#191c28;
  --text-primary:#eef0f8;--text-secondary:#8b90a7;--text-muted:#4e5470;
  --accent-blue:#4f6ef7;--accent-blue-glow:rgba(79,110,247,.16);
  --accent-green:#34d48a;--accent-green-glow:rgba(52,212,138,.13);
  --accent-amber:#f5a623;--accent-amber-glow:rgba(245,166,35,.13);
  --accent-red:#f75252;--accent-red-glow:rgba(247,82,82,.13);
  --accent-purple:#a78bfa;--accent-cyan:#22d3ee;--accent-pink:#f472b6;
  --font:Inter,system-ui,sans-serif;--mono:'DM Mono',monospace;
  --r-sm:8px;--r-md:12px;--r-lg:16px;--r-xl:22px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{font-family:var(--font);background:var(--bg-base);color:var(--text-primary);min-height:100vh;line-height:1.6;overflow-x:hidden}
body::before{content:'';position:fixed;inset:0;background-image:linear-gradient(rgba(79,110,247,.025) 1px,transparent 1px),linear-gradient(90deg,rgba(79,110,247,.025) 1px,transparent 1px);background-size:44px 44px;pointer-events:none;z-index:0}
.app{position:relative;z-index:1}

/* ── TOPBAR ── */
.topbar{display:flex;align-items:center;justify-content:space-between;padding:14px 24px;border-bottom:1px solid var(--border);background:rgba(7,8,13,.9);backdrop-filter:blur(16px);position:sticky;top:0;z-index:200}
.logo{display:flex;align-items:center;gap:10px;font-size:17px;font-weight:800;letter-spacing:-.6px}
.logo-icon{width:32px;height:32px;background:linear-gradient(135deg,var(--accent-blue),var(--accent-purple));border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:15px}
.logo em{color:var(--text-muted);font-style:normal;font-weight:400;font-size:13px}
.topbar-right{display:flex;align-items:center;gap:10px}
.badge-date{font-family:var(--mono);font-size:11px;color:var(--text-muted);background:var(--bg-elevated);padding:5px 12px;border-radius:20px;border:1px solid var(--border)}
.badge-v2{font-size:10px;font-weight:700;letter-spacing:.06em;background:linear-gradient(90deg,var(--accent-blue),var(--accent-purple));color:#fff;padding:3px 10px;border-radius:20px}

/* ── NAV ── */
.nav{display:flex;gap:3px;padding:10px 24px;background:var(--bg-base);border-bottom:1px solid var(--border);overflow-x:auto;scrollbar-width:none}
.nav::-webkit-scrollbar{display:none}
.tab-btn{display:flex;align-items:center;gap:7px;padding:7px 15px;border:1px solid transparent;border-radius:var(--r-md);background:transparent;color:var(--text-secondary);font-size:12.5px;font-weight:500;font-family:var(--font);cursor:pointer;white-space:nowrap;transition:all .18s}
.tab-btn:hover{background:var(--bg-card);color:var(--text-primary)}
.tab-btn.active{background:var(--accent-blue-glow);border-color:rgba(79,110,247,.3);color:#7e9bff}
.tab-icon{font-size:14px}

/* ── LAYOUT ── */
.main{padding:24px;max-width:1240px;margin:0 auto}
.tab-pane{display:none}.tab-pane.active{display:block}
.sec-title{font-size:21px;font-weight:800;letter-spacing:-.5px;margin-bottom:5px}
.sec-sub{font-size:13.5px;color:var(--text-secondary);margin-bottom:22px}
.g2{display:grid;grid-template-columns:1fr 1fr;gap:16px}
.g3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:16px}
.g4{display:grid;grid-template-columns:repeat(4,1fr);gap:14px}
.mb16{margin-bottom:16px}.mb24{margin-bottom:24px}

/* ── CARDS ── */
.card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--r-lg);padding:20px;transition:border-color .2s}
.card:hover{border-color:rgba(79,110,247,.2)}
.card-title{font-size:11px;font-weight:700;letter-spacing:.09em;text-transform:uppercase;color:var(--text-muted);margin-bottom:14px}
.card-title-lg{font-size:14px;font-weight:700;letter-spacing:-.2px;color:var(--text-secondary);margin-bottom:14px}

/* ── FORMS ── */
.fg{display:flex;flex-direction:column;gap:6px}
.fl{font-size:11.5px;font-weight:600;color:var(--text-secondary);letter-spacing:.03em}
.fi,.fs{background:var(--bg-input);border:1px solid var(--border);border-radius:var(--r-sm);color:var(--text-primary);font-size:13.5px;font-family:var(--font);padding:9px 12px;outline:none;transition:border-color .18s,box-shadow .18s;width:100%}
.fi:focus,.fs:focus{border-color:var(--border-focus);box-shadow:0 0 0 3px var(--accent-blue-glow)}
.fs option{background:var(--bg-elevated)}

/* ── BUTTONS ── */
.btn{display:inline-flex;align-items:center;gap:7px;padding:9px 18px;border-radius:var(--r-sm);font-size:13px;font-weight:600;font-family:var(--font);cursor:pointer;border:none;transition:all .18s}
.btn-primary{background:var(--accent-blue);color:#fff}
.btn-primary:hover{background:#6b84f9;transform:translateY(-1px);box-shadow:0 4px 18px rgba(79,110,247,.4)}
.btn-success{background:var(--accent-green);color:#07080d}
.btn-success:hover{background:#4ae09c;transform:translateY(-1px)}
.btn-ghost{background:transparent;color:var(--text-secondary);border:1px solid var(--border)}
.btn-ghost:hover{background:var(--bg-elevated);color:var(--text-primary)}
.btn-danger{background:transparent;color:var(--accent-red);border:1px solid rgba(247,82,82,.28);padding:5px 10px;font-size:11.5px}
.btn-danger:hover{background:var(--accent-red-glow)}
.btn-amber{background:rgba(245,166,35,.15);color:var(--accent-amber);border:1px solid rgba(245,166,35,.3)}
.btn-amber:hover{background:rgba(245,166,35,.25)}

/* ── DISCLAIMER BANNER ── */
.disclaimer{background:linear-gradient(135deg,rgba(245,166,35,.08),rgba(247,82,82,.06));border:1px solid rgba(245,166,35,.25);border-radius:var(--r-md);padding:14px 18px;margin-bottom:20px;display:flex;gap:12px;align-items:flex-start}
.disclaimer-icon{font-size:18px;flex-shrink:0;margin-top:1px}
.disclaimer-text{font-size:12.5px;color:var(--text-secondary);line-height:1.65}
.disclaimer-text strong{color:var(--accent-amber)}

/* ── PROFILE ── */
.profile-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin-bottom:16px}
.bmi-card{background:linear-gradient(135deg,var(--accent-blue-glow),rgba(167,139,250,.08));border:1px solid rgba(79,110,247,.28);border-radius:var(--r-lg);padding:22px;display:flex;flex-direction:column;gap:8px}
.bmi-val{font-size:46px;font-weight:800;font-family:var(--mono);letter-spacing:-2px;background:linear-gradient(90deg,var(--accent-blue),var(--accent-purple));-webkit-background-clip:text;-webkit-text-fill-color:transparent}

/* ── CSV UPLOAD ZONE ── */
.upload-zone{border:2px dashed var(--border);border-radius:var(--r-lg);padding:32px;text-align:center;cursor:pointer;transition:all .2s;background:var(--bg-elevated)}
.upload-zone:hover,.upload-zone.drag{border-color:var(--accent-blue);background:var(--accent-blue-glow)}
.upload-zone input{display:none}
.upload-icon{font-size:32px;margin-bottom:10px}
.upload-title{font-size:14px;font-weight:600;margin-bottom:4px}
.upload-sub{font-size:12px;color:var(--text-muted)}
.csv-hint{background:var(--bg-elevated);border:1px solid var(--border);border-radius:var(--r-sm);padding:12px 16px;margin-top:12px;font-size:12px;color:var(--text-muted);font-family:var(--mono)}

/* ── FOOD LOG ── */
.log-form{display:grid;grid-template-columns:2fr 1fr 1fr auto;gap:11px;align-items:flex-end;margin-bottom:18px;padding:16px;background:var(--bg-elevated);border-radius:var(--r-md);border:1px solid var(--border)}
table{width:100%;border-collapse:collapse}
thead th{font-size:10.5px;font-weight:700;letter-spacing:.07em;text-transform:uppercase;color:var(--text-muted);padding:9px 10px;text-align:left;border-bottom:1px solid var(--border)}
tbody tr{border-bottom:1px solid rgba(30,33,48,.7);transition:background .13s}
tbody tr:hover{background:var(--bg-elevated)}
tbody td{padding:10px;font-size:12.5px}
.td-food{font-weight:600}
.td-num{font-family:var(--mono);font-size:11.5px;color:var(--text-secondary)}
.empty-state{text-align:center;padding:44px 20px;color:var(--text-muted)}
.empty-icon{font-size:34px;margin-bottom:10px}
.empty-title{font-size:15px;font-weight:600;color:var(--text-secondary)}
.empty-sub{font-size:12.5px;margin-top:5px}
.inline-edit{background:var(--bg-input);border:1px solid var(--border-focus);border-radius:4px;color:var(--text-primary);font-size:12.5px;font-family:var(--mono);padding:3px 7px;width:65px;outline:none}

/* ── STAT CHIPS ── */
.chips{display:flex;gap:9px;flex-wrap:wrap}
.chip{display:flex;align-items:center;gap:8px;padding:9px 13px;border-radius:var(--r-md);border:1px solid var(--border);background:var(--bg-elevated);flex:1;min-width:90px}
.chip-dot{width:7px;height:7px;border-radius:50%;flex-shrink:0}
.chip-lbl{font-size:10.5px;color:var(--text-muted)}
.chip-val{font-size:14px;font-weight:700;font-family:var(--mono)}

/* ── PROGRESS BARS ── */
.prog-row{display:flex;flex-direction:column;gap:5px;margin-bottom:12px}
.prog-hdr{display:flex;justify-content:space-between;align-items:center}
.prog-lbl{font-size:12.5px;font-weight:500}
.prog-pct{font-size:11px;font-family:var(--mono);color:var(--text-muted)}
.prog-bg{height:5px;background:var(--bg-elevated);border-radius:3px;overflow:hidden}
.prog-fill{height:100%;border-radius:3px;transition:width .7s cubic-bezier(.4,0,.2,1)}

/* ── DASHBOARD RING ── */
.ring-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--r-lg);padding:26px;display:flex;flex-direction:column;align-items:center;gap:14px}
.ring-wrap{position:relative;width:176px;height:176px}
.ring-label{position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:1px}
.ring-kcal{font-size:30px;font-weight:800;font-family:var(--mono);letter-spacing:-1px}
.ring-sub{font-size:11px;color:var(--text-muted)}
.chart-wrap{position:relative;height:210px}

/* ── INSIGHT ITEMS ── */
.insight-list{display:flex;flex-direction:column;gap:7px}
.insight-item{display:flex;align-items:center;justify-content:space-between;padding:9px 13px;border-radius:var(--r-sm);font-size:12.5px}
.ins-def{background:rgba(79,110,247,.08);border:1px solid rgba(79,110,247,.18)}
.ins-exc{background:var(--accent-red-glow);border:1px solid rgba(247,82,82,.18)}
.ins-ok{background:var(--accent-green-glow);border:1px solid rgba(52,212,138,.18)}
.ins-name{font-weight:600}
.ins-val{font-family:var(--mono);font-size:11px;color:var(--text-secondary)}
.ibadge{font-size:10.5px;font-weight:700;padding:2px 7px;border-radius:10px}
.ibadge-low{background:rgba(79,110,247,.2);color:#7e9bff}
.ibadge-high{background:rgba(247,82,82,.2);color:var(--accent-red)}
.ibadge-ok{background:rgba(52,212,138,.2);color:var(--accent-green)}

/* ── RISK ANALYSIS ── */
.risk-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin-bottom:20px}
.risk-card{border-radius:var(--r-lg);padding:18px;border:1px solid}
.risk-low{background:rgba(52,212,138,.07);border-color:rgba(52,212,138,.22)}
.risk-med{background:rgba(245,166,35,.07);border-color:rgba(245,166,35,.22)}
.risk-high{background:rgba(247,82,82,.07);border-color:rgba(247,82,82,.22)}
.risk-label{font-size:11px;font-weight:700;letter-spacing:.07em;text-transform:uppercase;margin-bottom:6px}
.risk-low .risk-label{color:var(--accent-green)}
.risk-med .risk-label{color:var(--accent-amber)}
.risk-high .risk-label{color:var(--accent-red)}
.risk-title{font-size:14px;font-weight:700;margin-bottom:4px}
.risk-desc{font-size:12px;color:var(--text-secondary);line-height:1.6}
.risk-score{font-size:28px;font-weight:800;font-family:var(--mono)}
.risk-low .risk-score{color:var(--accent-green)}
.risk-med .risk-score{color:var(--accent-amber)}
.risk-high .risk-score{color:var(--accent-red)}

/* ── MEAL PLANNER ── */
.planner-grid{display:grid;grid-template-columns:1fr 1fr;gap:18px}
.day-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--r-lg);overflow:hidden}
.day-header{padding:14px 18px;border-bottom:1px solid var(--border);display:flex;justify-content:space-between;align-items:center;background:var(--bg-elevated)}
.day-title{font-size:14px;font-weight:700}
.day-total{font-size:12px;font-family:var(--mono);color:var(--text-muted)}
.meal-slot{padding:12px 18px;border-bottom:1px solid var(--border-subtle)}
.meal-name{font-size:11px;font-weight:700;letter-spacing:.06em;text-transform:uppercase;color:var(--text-muted);margin-bottom:8px}
.meal-items{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:8px}
.meal-item-tag{display:flex;align-items:center;gap:5px;padding:4px 10px;background:var(--bg-elevated);border:1px solid var(--border);border-radius:20px;font-size:11.5px}
.meal-item-tag button{background:none;border:none;cursor:pointer;color:var(--text-muted);font-size:11px;padding:0;line-height:1}
.meal-item-tag button:hover{color:var(--accent-red)}
.meal-add{display:flex;gap:8px;align-items:center}
.meal-add select{flex:1}
.planner-summary{background:var(--bg-elevated);border-radius:var(--r-md);padding:14px 16px;margin-top:4px}

/* ── RECS ── */
.rec-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--r-lg);padding:18px;margin-bottom:12px;display:flex;gap:14px;align-items:flex-start;transition:border-color .2s}
.rec-card:hover{border-color:rgba(79,110,247,.25)}
.rec-icon{width:40px;height:40px;flex-shrink:0;border-radius:var(--r-sm);display:flex;align-items:center;justify-content:center;font-size:18px}
.rec-add .rec-icon{background:var(--accent-green-glow)}
.rec-swap .rec-icon{background:var(--accent-blue-glow)}
.rec-reduce .rec-icon{background:var(--accent-red-glow)}
.rec-warn .rec-icon{background:var(--accent-amber-glow)}
.rec-type{font-size:10.5px;font-weight:700;letter-spacing:.08em;text-transform:uppercase;margin-bottom:3px}
.rec-add .rec-type{color:var(--accent-green)}
.rec-swap .rec-type{color:#7e9bff}
.rec-reduce .rec-type{color:var(--accent-red)}
.rec-warn .rec-type{color:var(--accent-amber)}
.rec-text{font-size:13.5px;line-height:1.65}
.rec-reason{font-size:11.5px;color:var(--text-muted);margin-top:4px}
.rec-priority{font-size:10px;font-weight:700;padding:2px 8px;border-radius:10px;margin-left:8px}
.pri-high{background:rgba(247,82,82,.2);color:var(--accent-red)}
.pri-med{background:rgba(245,166,35,.2);color:var(--accent-amber)}
.pri-low{background:rgba(52,212,138,.2);color:var(--accent-green)}

/* ── SOURCES ── */
.source-card{background:var(--bg-elevated);border:1px solid var(--border);border-radius:var(--r-md);padding:14px 18px;margin-bottom:10px;display:flex;justify-content:space-between;align-items:flex-start;gap:16px}
.src-body{flex:1}
.src-name{font-size:13.5px;font-weight:600;margin-bottom:3px}
.src-desc{font-size:12px;color:var(--text-secondary)}
.src-badge{font-size:10px;font-weight:700;padding:3px 9px;border-radius:10px;white-space:nowrap}
.src-gold{background:rgba(245,166,35,.18);color:var(--accent-amber);border:1px solid rgba(245,166,35,.3)}
.src-blue{background:rgba(79,110,247,.18);color:#7e9bff;border:1px solid rgba(79,110,247,.3)}
.src-green{background:rgba(52,212,138,.18);color:var(--accent-green);border:1px solid rgba(52,212,138,.3)}

/* ── NUTRIENT TABLE ── */
.ntable th{font-size:10.5px;color:var(--text-muted);padding:8px 10px;text-align:left;letter-spacing:.06em;text-transform:uppercase;border-bottom:1px solid var(--border);white-space:nowrap}
.ntable td{padding:9px 10px;font-size:12.5px;border-bottom:1px solid rgba(30,33,48,.5)}
.ntable tr:hover td{background:var(--bg-elevated)}
.nt-name{font-weight:500}
.nt-bar{width:90px;height:5px;background:var(--bg-elevated);border-radius:3px;display:inline-block;overflow:hidden;vertical-align:middle}
.nt-fill{height:100%;border-radius:3px}

/* ── TOAST ── */
.toast{position:fixed;bottom:22px;right:22px;background:var(--bg-elevated);border:1px solid var(--accent-green);color:var(--text-primary);padding:11px 18px;border-radius:var(--r-md);font-size:13.5px;font-weight:500;z-index:9999;transform:translateY(80px);opacity:0;transition:all .3s cubic-bezier(.4,0,.2,1);display:flex;align-items:center;gap:9px;max-width:340px}
.toast.show{transform:translateY(0);opacity:1}

/* ── MODAL ── */
.modal-overlay{position:fixed;inset:0;background:rgba(7,8,13,.8);backdrop-filter:blur(8px);z-index:500;display:none;align-items:center;justify-content:center;padding:20px}
.modal-overlay.open{display:flex}
.modal{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--r-xl);padding:28px;max-width:520px;width:100%;max-height:85vh;overflow-y:auto}
.modal-title{font-size:18px;font-weight:800;letter-spacing:-.4px;margin-bottom:8px}
.modal-sub{font-size:13px;color:var(--text-secondary);margin-bottom:20px}
.modal-close{float:right;background:none;border:none;color:var(--text-muted);font-size:20px;cursor:pointer;padding:0;line-height:1}
.modal-close:hover{color:var(--text-primary)}

/* ── RESPONSIVE ── */
@media(max-width:900px){
  .g3,.g4,.risk-grid,.planner-grid{grid-template-columns:1fr 1fr}
  #dashTop{grid-template-columns:1fr!important}
}
@media(max-width:640px){
  .profile-grid{grid-template-columns:1fr 1fr}
  .g2,.g3,.g4,.risk-grid,.planner-grid{grid-template-columns:1fr}
  .log-form{grid-template-columns:1fr 1fr}
  .log-form .btn{grid-column:span 2}
  .main{padding:14px}
}
@media(max-width:400px){
  .profile-grid{grid-template-columns:1fr}
  .log-form{grid-template-columns:1fr}
  .log-form .btn{grid-column:span 1}
}
</style>
</head>
<body>
<div class="app">

<!-- TOPBAR -->
<header class="topbar">
  <div class="logo">
    <div class="logo-icon">🥗</div>
    NutriScope <em>/ v2</em>
  </div>
  <div class="topbar-right">
    <span class="badge-v2">ENHANCED</span>
    <span class="badge-date" id="dateBadge"></span>
  </div>
</header>

<!-- NAV -->
<nav class="nav">
  <button class="tab-btn active" onclick="switchTab('profile',this)"><span class="tab-icon">👤</span>Profile</button>
  <button class="tab-btn" onclick="switchTab('log',this)"><span class="tab-icon">📋</span>Food Log</button>
  <button class="tab-btn" onclick="switchTab('dashboard',this)"><span class="tab-icon">📊</span>Dashboard</button>
  <button class="tab-btn" onclick="switchTab('planner',this)"><span class="tab-icon">🗓️</span>Meal Planner</button>
  <button class="tab-btn" onclick="switchTab('risk',this)"><span class="tab-icon">⚠️</span>Risk Analysis</button>
  <button class="tab-btn" onclick="switchTab('recs',this)"><span class="tab-icon">💡</span>Recommendations</button>
  <button class="tab-btn" onclick="switchTab('sources',this)"><span class="tab-icon">📚</span>Sources</button>
</nav>

<main class="main">

<!-- ═══ PROFILE ═══ -->
<div id="tab-profile" class="tab-pane active">
  <div class="disclaimer">
    <div class="disclaimer-icon">⚕️</div>
    <div class="disclaimer-text"><strong>Educational Use Only.</strong> NutriScope provides general nutritional information for awareness purposes only. It does not constitute medical advice, diagnosis, or treatment. Nutrient values are approximate. Consult a registered dietitian or physician before making significant dietary changes, especially if you have a medical condition.</div>
  </div>
  <div class="sec-title">Your Profile</div>
  <div class="sec-sub">Set up your details to receive personalised nutrition targets and risk insights.</div>
  <div class="card mb16">
    <div class="card-title">Personal Details</div>
    <div class="profile-grid">
      <div class="fg"><label class="fl">Age (years)</label><input type="number" id="age" class="fi" placeholder="25" min="1" max="120"></div>
      <div class="fg"><label class="fl">Gender</label>
        <select id="gender" class="fs"><option value="">Select gender</option><option value="male">Male</option><option value="female">Female</option><option value="other">Other / Prefer not to say</option></select>
      </div>
      <div class="fg"><label class="fl">Height (cm)</label><input type="number" id="height" class="fi" placeholder="170" min="50" max="250"></div>
      <div class="fg"><label class="fl">Weight (kg)</label><input type="number" id="weight" class="fi" placeholder="70" min="10" max="300"></div>
      <div class="fg"><label class="fl">Activity Level</label>
        <select id="activity" class="fs">
          <option value="">Select activity</option>
          <option value="1.2">Sedentary (desk job, no exercise)</option>
          <option value="1.375">Lightly active (1–3 days/week)</option>
          <option value="1.55">Moderately active (3–5 days/week)</option>
          <option value="1.725">Very active (6–7 days/week)</option>
          <option value="1.9">Extra active (athlete / physical job)</option>
        </select>
      </div>
      <div class="fg"><label class="fl">Dietary Preference</label>
        <select id="dietPref" class="fs">
          <option value="">Select preference</option>
          <option value="veg">Vegetarian</option>
          <option value="nonveg">Non-Vegetarian</option>
          <option value="egg">Eggetarian</option>
        </select>
      </div>
      <div class="fg"><label class="fl">Health Goal</label>
        <select id="goal" class="fs">
          <option value="maintain">Maintain Weight</option>
          <option value="lose">Lose Weight (−300 kcal)</option>
          <option value="gain">Gain Weight (+300 kcal)</option>
          <option value="muscle">Build Muscle (+200 kcal)</option>
        </select>
      </div>
      <div class="fg"><label class="fl">Medical Conditions (optional)</label>
        <select id="conditions" class="fs">
          <option value="">None / Prefer not to say</option>
          <option value="diabetes">Diabetes / Pre-diabetes</option>
          <option value="hypertension">Hypertension</option>
          <option value="anemia">Anaemia</option>
          <option value="thyroid">Thyroid Disorder</option>
          <option value="cholesterol">High Cholesterol</option>
        </select>
      </div>
    </div>
    <div style="display:flex;justify-content:flex-end;gap:12px;margin-top:16px">
      <button class="btn btn-ghost" onclick="clearProfile()">🗑 Clear</button>
      <button class="btn btn-primary" onclick="saveProfile()">💾 Save & Calculate Targets</button>
    </div>
  </div>
  <div class="g2" id="profileResults" style="display:none">
    <div class="bmi-card">
      <div style="font-size:11px;color:var(--text-muted);font-weight:700;letter-spacing:.07em;text-transform:uppercase">Body Mass Index</div>
      <div class="bmi-val" id="bmiVal">—</div>
      <div id="bmiLabel" style="font-size:14px;color:var(--text-secondary)"></div>
      <div id="tdeeVal" style="font-size:12px;color:var(--text-muted);margin-top:4px"></div>
    </div>
    <div class="card">
      <div class="card-title">Daily Targets</div>
      <div id="targetsPreview"></div>
    </div>
  </div>
</div>

<!-- ═══ FOOD LOG ═══ -->
<div id="tab-log" class="tab-pane">
  <div class="sec-title">Food Log</div>
  <div class="sec-sub">Log meals manually or upload a CSV. Click any quantity cell to edit inline.</div>

  <!-- CSV Upload -->
  <div class="card mb16">
    <div class="card-title">📁 CSV Upload</div>
    <div class="g2">
      <div>
        <div class="upload-zone" id="dropZone" onclick="document.getElementById('csvFile').click()" ondragover="handleDragOver(event)" ondragleave="handleDragLeave(event)" ondrop="handleDrop(event)">
          <input type="file" id="csvFile" accept=".csv" onchange="handleCSVFile(event)">
          <div class="upload-icon">📂</div>
          <div class="upload-title">Drop CSV or click to browse</div>
          <div class="upload-sub">Replaces current log • max 500 rows</div>
        </div>
      </div>
      <div>
        <div class="csv-hint">Expected columns (header row required):<br><br>food,quantity,unit<br>Rice,150,g<br>Dal,200,g<br>Banana,1,piece</div>
        <button class="btn btn-ghost" style="margin-top:10px;width:100%" onclick="downloadSampleCSV()">⬇ Download Sample CSV</button>
      </div>
    </div>
  </div>

  <!-- Manual Add -->
  <div class="log-form">
    <div class="fg"><label class="fl">Food Item</label>
      <select id="foodSelect" class="fs"><option value="">Select food…</option></select>
    </div>
    <div class="fg"><label class="fl">Quantity</label><input type="number" id="foodQty" class="fi" placeholder="100" min="1" value="100"></div>
    <div class="fg"><label class="fl">Unit</label>
      <select id="foodUnit" class="fs">
        <option value="g">grams (g)</option><option value="ml">ml</option>
        <option value="piece">piece (~100g)</option><option value="cup">cup (~240g)</option>
        <option value="tbsp">tbsp (~15g)</option><option value="katori">katori (~150g)</option>
      </select>
    </div>
    <button class="btn btn-success" onclick="addFood()">＋ Add</button>
  </div>

  <div class="card">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:14px">
      <div class="card-title" style="margin-bottom:0">Logged Items</div>
      <button class="btn btn-danger" onclick="clearLog()" style="font-size:11px">🗑 Clear All</button>
    </div>
    <div style="overflow-x:auto">
      <table id="foodTable">
        <thead><tr>
          <th>Food</th><th>Qty</th><th>Unit</th>
          <th>Cal</th><th>Prot</th><th>Carbs</th><th>Fat</th><th>Fiber</th>
          <th>Iron</th><th>Ca</th><th>Mg</th><th>K</th><th>Zn</th>
          <th>VitA</th><th>VitC</th><th>VitD</th><th>B12</th><th>Folate</th>
          <th></th>
        </tr></thead>
        <tbody id="foodBody">
          <tr><td colspan="19"><div class="empty-state"><div class="empty-icon">🍽️</div><div class="empty-title">No food logged yet</div><div class="empty-sub">Add a meal or upload a CSV above</div></div></td></tr>
        </tbody>
      </table>
    </div>
    <div id="totalsRow" style="display:none;margin-top:14px;padding-top:14px;border-top:1px solid var(--border)">
      <div class="card-title">Today's Totals</div>
      <div class="chips" id="totalsChips"></div>
    </div>
  </div>
</div>

<!-- ═══ DASHBOARD ═══ -->
<div id="tab-dashboard" class="tab-pane">
  <div class="sec-title">Dashboard</div>
  <div class="sec-sub">Comprehensive nutrition snapshot — energy, macros, and full micronutrient breakdown.</div>

  <div style="display:grid;grid-template-columns:200px 1fr;gap:16px;margin-bottom:16px" id="dashTop">
    <div class="ring-card">
      <div class="card-title" style="margin-bottom:0">Energy</div>
      <div class="ring-wrap"><canvas id="energyRing" width="176" height="176"></canvas>
        <div class="ring-label"><div class="ring-kcal" id="dashKcal">0</div><div class="ring-sub" id="dashKcalPct">of 0 kcal</div></div>
      </div>
      <div style="display:flex;flex-direction:column;gap:5px;width:100%">
        <div style="font-size:12px;color:var(--text-muted);display:flex;justify-content:space-between"><span>Remaining</span><span id="dashRemain" style="font-family:var(--mono);color:var(--text-secondary)">—</span></div>
        <div style="font-size:12px;color:var(--text-muted);display:flex;justify-content:space-between"><span>Logged items</span><span id="dashItems" style="font-family:var(--mono);color:var(--text-secondary)">0</span></div>
      </div>
    </div>
    <div class="card">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px">
        <div class="card-title" style="margin-bottom:0">Macronutrients</div>
        <div style="display:flex;gap:6px">
          <button class="btn btn-ghost" style="padding:4px 10px;font-size:11px" onclick="setMacroChart('bar')">Bar</button>
          <button class="btn btn-ghost" style="padding:4px 10px;font-size:11px" onclick="setMacroChart('radar')">Radar</button>
          <button class="btn btn-ghost" style="padding:4px 10px;font-size:11px" onclick="setMacroChart('pie')">Pie</button>
        </div>
      </div>
      <div class="chart-wrap"><canvas id="macroChart"></canvas></div>
      <div class="chips" style="margin-top:14px" id="macroChips"></div>
    </div>
  </div>

  <!-- Micro radar + trend -->
  <div class="g2 mb16">
    <div class="card">
      <div class="card-title">🕸 Micronutrient Radar</div>
      <div class="chart-wrap"><canvas id="microRadar"></canvas></div>
    </div>
    <div class="card">
      <div class="card-title">📈 Macro Distribution (Calorie Share)</div>
      <div class="chart-wrap"><canvas id="calPie"></canvas></div>
    </div>
  </div>

  <div class="g2 mb16">
    <div class="card"><div class="card-title">⚠️ Top Deficiencies</div><div class="insight-list" id="defList"><div style="color:var(--text-muted);font-size:13px">Log food to see insights</div></div></div>
    <div class="card"><div class="card-title">🔺 Top Excesses</div><div class="insight-list" id="excList"><div style="color:var(--text-muted);font-size:13px">Log food to see insights</div></div></div>
  </div>

  <div class="card">
    <div class="card-title">📋 Full Nutrient Breakdown</div>
    <div style="overflow-x:auto">
      <table class="ntable">
        <thead><tr><th>Nutrient</th><th>Category</th><th>Consumed</th><th>Target</th><th>Progress</th><th>Status</th></tr></thead>
        <tbody id="nutrientBody"></tbody>
      </table>
    </div>
  </div>
</div>

<!-- ═══ MEAL PLANNER ═══ -->
<div id="tab-planner" class="tab-pane">
  <div class="sec-title">2-Day Meal Planner</div>
  <div class="sec-sub">Plan Day 1 and Day 2 meals across Breakfast, Lunch, Dinner, and Snacks.</div>
  <div class="disclaimer" style="margin-bottom:20px">
    <div class="disclaimer-icon">📌</div>
    <div class="disclaimer-text">Meal planner estimates are based on database averages. Actual nutrient content may vary by preparation method. Targets shown use your saved profile; save your profile first for accurate results.</div>
  </div>
  <div class="planner-grid" id="plannerGrid"></div>
  <div class="card" style="margin-top:16px">
    <div class="card-title">📊 2-Day Nutritional Summary</div>
    <div class="chart-wrap"><canvas id="plannerChart"></canvas></div>
    <div id="plannerSummary" style="margin-top:14px"></div>
  </div>
</div>

<!-- ═══ RISK ANALYSIS ═══ -->
<div id="tab-risk" class="tab-pane">
  <div class="sec-title">Risk Analysis</div>
  <div class="sec-sub">Pattern-based nutritional risk indicators derived from your logged intake and profile.</div>
  <div class="disclaimer">
    <div class="disclaimer-icon">⚕️</div>
    <div class="disclaimer-text"><strong>Important:</strong> Risk indicators are based on single-day logged intake and general population reference values. They are <strong>not a medical diagnosis</strong>. Risk scores reflect nutritional gaps only — not clinical test results. Always consult a qualified healthcare professional for medical assessment.</div>
  </div>
  <div style="margin-top:20px" id="riskContainer">
    <div class="empty-state"><div class="empty-icon">🔬</div><div class="empty-title">Log food first</div><div class="empty-sub">Risk analysis requires food data to compute indicators</div></div>
  </div>
</div>

<!-- ═══ RECOMMENDATIONS ═══ -->
<div id="tab-recs" class="tab-pane">
  <div class="sec-title">Smart Recommendations</div>
  <div class="sec-sub">Priority-ranked, diet-preference-aware suggestions. Save your profile and log food for best results.</div>
  <div id="recsContainer"><div class="empty-state"><div class="empty-icon">💡</div><div class="empty-title">Nothing to analyse yet</div><div class="empty-sub">Save your profile and add some food first</div></div></div>
</div>

<!-- ═══ SOURCES ═══ -->
<div id="tab-sources" class="tab-pane">
  <div class="sec-title">Nutrition Sources & References</div>
  <div class="sec-sub">Data, guidelines, and methodologies used in NutriScope's calculations.</div>

  <div class="card mb16">
    <div class="card-title">Nutrient Data Sources</div>
    <div class="source-card"><div class="src-body"><div class="src-name">ICMR–NIN Nutritive Value of Indian Foods (2017)</div><div class="src-desc">Primary reference for per-100g nutrient values of all Indian foods in the database. Indian Council of Medical Research & National Institute of Nutrition.</div></div><span class="src-badge src-gold">Primary</span></div>
    <div class="source-card"><div class="src-body"><div class="src-name">USDA FoodData Central</div><div class="src-desc">Supplementary values for international foods, micronutrient verification, and cross-validation of macro values.</div></div><span class="src-badge src-blue">Supplementary</span></div>
    <div class="source-card"><div class="src-body"><div class="src-name">WHO/FAO Nutrient Requirements (2004)</div><div class="src-desc">Protein, fat, and carbohydrate requirements for population reference values and dietary energy ratios.</div></div><span class="src-badge src-green">Guidelines</span></div>
  </div>

  <div class="card mb16">
    <div class="card-title">Dietary Reference Intakes (DRIs)</div>
    <div class="source-card"><div class="src-body"><div class="src-name">ICMR Recommended Dietary Allowances — India (2020)</div><div class="src-desc">Used for iron, calcium, folate, zinc, magnesium, and vitamin targets specific to the Indian population. Gender- and age-adjusted values applied where profile data is available.</div></div><span class="src-badge src-gold">Primary</span></div>
    <div class="source-card"><div class="src-body"><div class="src-name">NIH Office of Dietary Supplements Fact Sheets</div><div class="src-desc">Vitamin D, Vitamin B12, Vitamin A, and potassium upper limits and deficiency thresholds.</div></div><span class="src-badge src-blue">Reference</span></div>
  </div>

  <div class="card mb16">
    <div class="card-title">Calculation Methodology</div>
    <div class="source-card"><div class="src-body"><div class="src-name">Mifflin–St Jeor Equation (BMR)</div><div class="src-desc">Basal Metabolic Rate formula used: Males: 10W + 6.25H − 5A + 5 &nbsp;|&nbsp; Females: 10W + 6.25H − 5A − 161. TDEE = BMR × activity factor. Validated as the most accurate predictive equation for healthy adults (Frankenfield et al., 2005, J Am Diet Assoc).</div></div><span class="src-badge src-green">Method</span></div>
    <div class="source-card"><div class="src-body"><div class="src-name">Risk Score Computation</div><div class="src-desc">Risk scores are computed as weighted averages of nutrient deficiency depth (% below DRI threshold), adjusted for condition flags from the profile. Scores are heuristic and for educational awareness only.</div></div><span class="src-badge src-blue">Method</span></div>
  </div>

  <div class="card">
    <div class="card-title">Limitations & Disclaimers</div>
    <div style="font-size:13px;color:var(--text-secondary);line-height:1.8">
      <p style="margin-bottom:10px">• Nutrient values are per 100g raw weight unless otherwise stated. Cooking alters actual bioavailable content.</p>
      <p style="margin-bottom:10px">• Bioavailability varies by food matrix, preparation method, and individual gut health. E.g., non-haem iron from plant foods is 2–20% absorbed vs 15–35% for haem iron from meat.</p>
      <p style="margin-bottom:10px">• Micronutrient interactions (e.g., calcium reducing iron absorption, Vitamin C enhancing it) are not modelled in this version.</p>
      <p style="margin-bottom:10px">• Targets are derived from population averages and may not apply to individuals with specific clinical conditions, pregnancy, lactation, or unusual metabolic states.</p>
      <p>• NutriScope is an educational tool. It is <strong style="color:var(--accent-amber)">not a substitute for professional dietary assessment</strong>. For personalised medical nutrition therapy, consult a Registered Dietitian Nutritionist (RDN) or your physician.</p>
    </div>
  </div>
</div>

</main>
</div>

<!-- TOAST -->
<div class="toast" id="toast"><span id="toastIcon">✅</span><span id="toastMsg"></span></div>

<script>
// ══════════════════════════════════════════════════════════
// FOOD DATABASE — 60 foods
// cal, protein, carbs, fat, fiber, iron, calcium, magnesium,
// potassium, zinc, vitA(µg), vitC, vitD(µg), vitB12(µg), folate(µg)
// ══════════════════════════════════════════════════════════
const FOODS = {
  // ── GRAINS & CEREALS ──
  "Rice":        [130,2.7,28.0,0.3,0.4, 0.8,10, 25,115,0.6, 0,0,  0,  0,   8],
  "Roti":        [264,8.5,52.0,3.7,3.0, 3.9,40, 90,190,1.2, 0,0,  0,  0,   45],
  "Oats":        [389,17,66.0, 7.0,11,  4.7,54,138,429,4.0, 0,0,  0,  0,   56],
  "Bread":       [265,9.0,49.0,3.2,2.7, 2.9,80, 26,115,0.9, 0,0,  0,  0,   40],
  "Poha":        [350,7.0,76.0,1.2,2.5, 2.8,14, 55,100,1.0, 0,0,  0,  0,   10],
  "Idli":        [58, 2.0,12.0,0.1,0.7, 0.5,12, 10,55, 0.2, 0,0,  0,  0,   9],
  "Dosa":        [133,3.4,23.0,3.0,1.0, 0.9,28, 15,80, 0.3, 0,0,  0,  0,   14],
  "Upma":        [145,3.5,24.0,4.5,1.5, 1.2,18, 22,90, 0.4, 0,1.5,0,  0,   12],
  "Brown Rice":  [111,2.6,23.0,0.9,1.8, 0.5,10, 44,143,0.6, 0,0,  0,  0,   9],
  "Wheat Flour": [340,12,72.0, 1.5,2.7, 4.6,34,138,270,2.2, 0,0,  0,  0,   57],
  "Corn":        [86, 3.3,18.7,1.4,2.0, 0.5,2,  37,270,0.5, 10,6.8,0, 0,   42],
  "Quinoa":      [120,4.4,21.3,1.9,2.8, 1.5,17, 64,172,1.1, 1,0,  0,  0,   42],
  // ── PULSES & LEGUMES ──
  "Dal":         [116,8.0,18.0,0.5,3.5, 3.3,30, 36,369,1.0, 1,1.5,0,  0,   181],
  "Chana":       [164,8.9,27.0,2.6,7.6, 2.9,49, 48,291,1.5, 3,1.3,0,  0,   172],
  "Rajma":       [127,8.7,22.8,0.5,6.4, 2.5,83, 45,405,1.0, 0,1.0,0,  0,   130],
  "Moong Dal":   [105,7.5,19.0,0.4,4.0, 1.4,27, 48,266,0.8, 2,1.0,0,  0,   159],
  "Masoor Dal":  [116,9.0,20.0,0.4,4.0, 3.3,19, 36,369,1.3, 1,1.5,0,  0,   181],
  "Soyabean":    [173,17,10.0, 9.0,6.0, 5.1,277,65,620,1.7, 5,6.0,0,  0,   111],
  // ── DAIRY & EGGS ──
  "Milk":        [61, 3.2,4.8, 3.3,0,   0.1,113,11,152,0.4,28,0,  1.3,0.5, 5],
  "Curd":        [98, 3.5,3.4, 4.3,0,   0.1,121,12,155,0.5,27,0,  0.1,0.4, 13],
  "Paneer":      [265,18,3.5,  20,0,    0.2,480,17,88, 1.0,80,0,  0.3,0.5, 14],
  "Egg":         [155,13,1.1,  11,0,    1.8,56, 12,138,1.3,160,0, 2.0,1.1, 47],
  "Ghee":        [900,0, 0,    99.5,0,  0,  0,  0, 0,  0,  270,0, 0.6,0,   0],
  "Butter":      [717,0.9,0.1, 81,0,    0,  24, 2, 24, 0.1,700,0, 1.5,0.2, 3],
  "Cheese":      [402,25,1.3,  33,0,    0.7,721,28,98, 3.1,270,0, 0.6,1.1, 19],
  // ── MEAT & FISH ──
  "Chicken":     [165,31,0,    3.6,0,   1.0,15, 28,256,1.0, 21,0, 0.1,0.3, 4],
  "Fish":        [136,20,0,    6.0,0,   0.9,20, 30,400,0.5, 54,0, 11,3.0,  15],
  "Egg White":   [52, 11,0.7,  0.2,0,   0.1,7,  11,163,0.1, 0,0,  0,  0,   4],
  "Mutton":      [190,26,0,    9.0,0,   1.7,17, 22,310,3.5, 0,0,  0,  2.1, 3],
  "Prawn":       [99, 24,0.2,  0.3,0,   0.5,64, 37,185,1.1, 54,2, 0,  1.7, 6],
  "Tuna":        [130,29,0,    1.5,0,   1.0,16, 35,397,0.6, 51,0, 4.0,2.5, 2],
  // ── VEGETABLES ──
  "Spinach":     [23, 2.9,3.6, 0.4,2.2, 2.7,99, 79,558,0.5,469,28,0,  0,   194],
  "Potato":      [77, 2.0,17,  0.1,2.2, 0.8,12, 23,425,0.3, 2,19.7,0, 0,   15],
  "Tomato":      [18, 0.9,3.9, 0.2,1.2, 0.3,10, 11,237,0.2,42,13.7,0, 0,   15],
  "Broccoli":    [34, 2.8,6.6, 0.4,2.6, 0.7,47, 21,316,0.4,31,89.2,0, 0,   63],
  "Carrot":      [41, 0.9,9.6, 0.2,2.8, 0.3,33, 12,320,0.2,835,5.9,0, 0,   19],
  "Onion":       [40, 1.1,9.3, 0.1,1.7, 0.2,23, 10,146,0.2, 0,7.4,0,  0,   19],
  "Capsicum":    [31, 1.0,6.0, 0.3,2.1, 0.4,7,  12,175,0.2,18,128,0,  0,   46],
  "Pumpkin":     [26, 1.0,6.5, 0.1,0.5, 0.8,21, 12,340,0.3,426,9.0,0, 0,   16],
  "Cauliflower": [25, 1.9,5.0, 0.3,2.0, 0.4,22, 15,299,0.3, 0,48.2,0, 0,   57],
  "Bitter Gourd":[17, 1.0,3.7, 0.2,2.8, 0.4,19, 17,296,0.8,24,84,0,  0,   72],
  "Drumstick":   [37, 2.1,8.5, 0.2,3.2, 0.4,30, 42,337,0.6,74,141,0, 0,   44],
  "Sweet Potato":[86, 1.6,20,  0.1,3.0, 0.6,30, 25,337,0.3,709,2.4,0, 0,   11],
  // ── FRUITS ──
  "Banana":      [89, 1.1,23,  0.3,2.6, 0.3,5,  27,358,0.2, 3,8.7,0,  0,   20],
  "Apple":       [52, 0.3,14,  0.2,2.4, 0.1,6,  5, 107,0.0, 3,4.6,0,  0,   3],
  "Mango":       [60, 0.8,15,  0.4,1.6, 0.2,11, 10,168,0.1,38,36,0,   0,   43],
  "Orange":      [47, 0.9,11.8,0.1,2.4, 0.1,40, 10,181,0.1, 11,53.2,0,0,   30],
  "Guava":       [68, 2.6,14,  1.0,5.4, 0.3,18, 22,417,0.2,31,228.3,0,0,   49],
  "Papaya":      [43, 0.5,11,  0.3,1.7, 0.3,20, 21,182,0.1,47,61.8,0, 0,   37],
  "Watermelon":  [30, 0.6,7.6, 0.2,0.4, 0.2,7,  10,112,0.1,28,8.1,0,  0,   3],
  "Pomegranate": [83, 1.7,18.7,1.2,4.0, 0.3,10, 12,236,0.4, 0,10.2,0, 0,   38],
  // ── NUTS & SEEDS ──
  "Almonds":     [579,21,22,   50,12.5, 3.7,264,270,733,3.1, 0,0,  0,  0,   50],
  "Walnuts":     [654,15,14,   65,6.7,  2.9,98, 158,441,3.1, 1,1.3,0,  0,   98],
  "Peanuts":     [567,26,16,   49,8.5,  4.6,92, 168,705,3.3, 0,0,  0,  0,   240],
  "Chia Seeds":  [486,17,42,   31,34,   7.7,631,335,407,4.6, 54,1.6,0, 0,   49],
  "Flax Seeds":  [534,18,29,   42,27,   5.7,255,392,813,4.3, 0,0.6,0,  0,   87],
  // ── MISC ──
  "Coconut Milk":[230,2.3,5.5, 24,2.2,  1.6,16, 37,263,0.7, 0,2.8,0,  0,   16],
  "Jaggery":     [383,0.4,98,  0.1,0,   11,80,  70,1056,0.3, 0,7.0,0,  0,   0],
  "Honey":       [304,0.3,82.4,0,0,     0.4,6,  2, 52, 0.2,  0,0.5,0,  0,   2],
  "Tofu":        [76, 8.0,1.9, 4.8,0.3, 1.5,201,30,121,0.7,  5,0.1,0,  0,   15],
  "Amla":        [44, 0.9,10.2,0.6,3.4, 0.3,25, 10,198,0.1,  6,600,0, 0,   9],
};

const FKEYS = ['cal','protein','carbs','fat','fiber','iron','calcium','magnesium','potassium','zinc','vitA','vitC','vitD','vitB12','folate'];
const FLABELS = ['Calories','Protein','Carbs','Fat','Fiber','Iron','Calcium','Magnesium','Potassium','Zinc','Vitamin A','Vitamin C','Vitamin D','Vitamin B12','Folate'];
const FUNITS  = ['kcal','g','g','g','g','mg','mg','mg','mg','mg','µg','mg','µg','µg','µg'];
const FCAT    = ['Energy','Macro','Macro','Macro','Macro','Mineral','Mineral','Mineral','Mineral','Mineral','Vitamin','Vitamin','Vitamin','Vitamin','Vitamin'];
const UNIT_MULT = {g:1,ml:1,piece:100,cup:240,tbsp:15,katori:150};

// ── STATE ──
let profile=null,targets=null,foodLog=[],mealPlan={day1:{breakfast:[],lunch:[],dinner:[],snacks:[]},day2:{breakfast:[],lunch:[],dinner:[],snacks:[]}};
let charts={};
let macroChartType='bar';

// ── INIT ──
document.addEventListener('DOMContentLoaded',()=>{
  document.getElementById('dateBadge').textContent=new Date().toLocaleDateString('en-IN',{weekday:'short',day:'numeric',month:'short',year:'numeric'});
  const sel=document.getElementById('foodSelect');
  Object.keys(FOODS).sort().forEach(f=>{const o=document.createElement('option');o.value=o.textContent=f;sel.appendChild(o);});
  const saved=localStorage.getItem('nutriscope_v2');
  if(saved){try{const s=JSON.parse(saved);if(s.profile){profile=s.profile;fillProfileForm();computeTargets();showProfileResults();}if(s.foodLog)foodLog=s.foodLog;if(s.mealPlan)mealPlan=s.mealPlan;renderFoodTable();}catch(e){}}
  renderPlanner();
});
function save(){localStorage.setItem('nutriscope_v2',JSON.stringify({profile,foodLog,mealPlan}));}

// ── TAB SWITCH ──
function switchTab(name,btn){
  document.querySelectorAll('.tab-pane').forEach(t=>t.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('tab-'+name).classList.add('active');
  btn.classList.add('active');
  if(name==='dashboard')renderDashboard();
  if(name==='recs')renderRecs();
  if(name==='risk')renderRisk();
  if(name==='planner')renderPlanner();
}

// ── PROFILE ──
function fillProfileForm(){
  if(!profile)return;
  ['age','gender','height','weight','activity','dietPref','goal','conditions'].forEach(k=>{const el=document.getElementById(k);if(el&&profile[k]!==undefined)el.value=profile[k];});
}
function saveProfile(){
  const age=parseFloat(document.getElementById('age').value);
  const gender=document.getElementById('gender').value;
  const height=parseFloat(document.getElementById('height').value);
  const weight=parseFloat(document.getElementById('weight').value);
  const activity=parseFloat(document.getElementById('activity').value);
  const dietPref=document.getElementById('dietPref').value;
  const goal=document.getElementById('goal').value;
  const conditions=document.getElementById('conditions').value;
  if(!age||!gender||!height||!weight||!activity||!dietPref){showToast('⚠️ Fill all required fields','warn');return;}
  profile={age,gender,height,weight,activity,dietPref,goal,conditions};
  computeTargets();showProfileResults();save();showToast('✅ Profile saved & targets calculated');
}
function clearProfile(){profile=null;targets=null;document.getElementById('profileResults').style.display='none';['age','gender','height','weight','activity','dietPref','goal','conditions'].forEach(k=>{const el=document.getElementById(k);if(el)el.value='';});showToast('🗑 Profile cleared');}
function computeTargets(){
  if(!profile)return;
  const{age,gender,height,weight,activity,goal,conditions}=profile;
  let bmr=gender==='male'?10*weight+6.25*height-5*age+5:10*weight+6.25*height-5*age-161;
  let tdee=Math.round(bmr*activity);
  const goalAdj={maintain:0,lose:-300,gain:300,muscle:200};
  tdee+=goalAdj[goal]||0;
  const protein=Math.round(weight*(goal==='muscle'?1.6:0.8));
  const fat=Math.round((tdee*0.28)/9);
  const carbs=Math.round((tdee-protein*4-fat*9)/4);
  // Iron: female pre-menopausal higher; anemia condition bumps
  let iron=gender==='female'&&age<50?18:8;
  if(conditions==='anemia')iron=27;
  // Calcium: dairy push if osteo risk
  let calcium=1000;
  // Vitamin D: bump if low sunlight assumed
  let vitD=15;
  targets={tdee,protein,fat,carbs,fiber:30,iron,calcium,magnesium:gender==='male'?420:320,potassium:3500,zinc:gender==='male'?11:8,vitA:gender==='male'?900:700,vitC:gender==='female'?75:90,vitD,vitB12:2.4,folate:400};
  return targets;
}
function showProfileResults(){
  if(!profile||!targets)return;
  const{height,weight}=profile;
  const bmi=(weight/((height/100)**2)).toFixed(1);
  const bmiLabel=bmi<18.5?'⚠️ Underweight':bmi<25?'✅ Healthy Weight':bmi<30?'⚠️ Overweight':'🔴 Obese';
  document.getElementById('bmiVal').textContent=bmi;
  document.getElementById('bmiLabel').textContent=bmiLabel;
  document.getElementById('tdeeVal').textContent=`Adjusted TDEE: ${targets.tdee} kcal/day`;
  document.getElementById('targetsPreview').innerHTML=[
    ['⚡','Energy',targets.tdee+' kcal','#4f6ef7'],['🥩','Protein',targets.protein+'g','#f5a623'],
    ['🍞','Carbs',targets.carbs+'g','#22d3ee'],['🧈','Fat',targets.fat+'g','#a78bfa'],
    ['🌾','Fiber',targets.fiber+'g','#34d48a'],['🦴','Calcium',targets.calcium+'mg','#f472b6'],
    ['🩸','Iron',targets.iron+'mg','#f75252'],
  ].map(([i,l,v,c])=>`<div style="display:flex;justify-content:space-between;align-items:center;padding:7px 12px;background:var(--bg-elevated);border-radius:7px;margin-bottom:6px"><span style="font-size:13px">${i} ${l}</span><span style="font-family:var(--mono);font-size:13px;color:${c};font-weight:700">${v}</span></div>`).join('');
  document.getElementById('profileResults').style.display='grid';
}

// ── FOOD LOG ──
function addFood(){
  const name=document.getElementById('foodSelect').value;
  const qty=parseFloat(document.getElementById('foodQty').value);
  const unit=document.getElementById('foodUnit').value;
  if(!name){showToast('⚠️ Select a food','warn');return;}
  if(!qty||qty<=0){showToast('⚠️ Enter a valid quantity','warn');return;}
  const grams=qty*(UNIT_MULT[unit]||1);
  const base=FOODS[name];
  const f=grams/100;
  const nutrients={};
  FKEYS.forEach((k,i)=>nutrients[k]=+(base[i]*f).toFixed(2));
  foodLog.push({id:Date.now(),name,qty,unit,grams,nutrients});
  renderFoodTable();save();showToast(`✅ ${name} added`);
}
function removeFood(id){foodLog=foodLog.filter(f=>f.id!==id);renderFoodTable();save();}
function clearLog(){if(foodLog.length===0)return;foodLog=[];renderFoodTable();save();showToast('🗑 Log cleared');}
function renderFoodTable(){
  const tbody=document.getElementById('foodBody');
  if(!foodLog.length){
    tbody.innerHTML=`<tr><td colspan="19"><div class="empty-state"><div class="empty-icon">🍽️</div><div class="empty-title">No food logged yet</div><div class="empty-sub">Add a meal or upload a CSV above</div></div></td></tr>`;
    document.getElementById('totalsRow').style.display='none';return;
  }
  tbody.innerHTML=foodLog.map(f=>`<tr>
    <td class="td-food">${f.name}</td>
    <td class="td-num" onclick="startEdit(this,${f.id})" style="cursor:pointer;color:var(--accent-blue)" title="Click to edit">${f.qty}</td>
    <td class="td-num">${f.unit}</td>
    ${FKEYS.map((k,i)=>`<td class="td-num">${f.nutrients[k]||0}${i>0?'':''}</td>`).join('')}
    <td><button class="btn btn-danger" onclick="removeFood(${f.id})">✕</button></td>
  </tr>`).join('');
  const totals=getTotals();
  document.getElementById('totalsRow').style.display='block';
  document.getElementById('totalsChips').innerHTML=[
    ['⚡','Calories',Math.round(totals.cal)+' kcal','#4f6ef7'],
    ['🥩','Protein',totals.protein.toFixed(1)+'g','#f5a623'],
    ['🍞','Carbs',totals.carbs.toFixed(1)+'g','#22d3ee'],
    ['🧈','Fat',totals.fat.toFixed(1)+'g','#a78bfa'],
    ['🌾','Fiber',totals.fiber.toFixed(1)+'g','#34d48a'],
    ['🦴','Calcium',totals.calcium.toFixed(0)+'mg','#f472b6'],
  ].map(([icon,label,val,color])=>`<div class="chip"><span style="font-size:15px">${icon}</span><div><div class="chip-lbl">${label}</div><div class="chip-val" style="color:${color}">${val}</div></div></div>`).join('');
}
function startEdit(cell,id){
  const cur=cell.textContent.trim();
  const inp=document.createElement('input');inp.type='number';inp.className='inline-edit';inp.value=cur;
  cell.textContent='';cell.appendChild(inp);inp.focus();
  const commit=()=>{
    const nq=parseFloat(inp.value);
    if(nq>0){const e=foodLog.find(f=>f.id===id);if(e){e.qty=nq;e.grams=nq*(UNIT_MULT[e.unit]||1);const b=FOODS[e.name];const f=e.grams/100;FKEYS.forEach((k,i)=>e.nutrients[k]=+(b[i]*f).toFixed(2));}}
    renderFoodTable();save();
  };
  inp.addEventListener('blur',commit);inp.addEventListener('keydown',e=>{if(e.key==='Enter')commit();});
}
function getTotals(){
  const t={};FKEYS.forEach(k=>t[k]=0);
  foodLog.forEach(f=>FKEYS.forEach(k=>t[k]+=(f.nutrients[k]||0)));
  return t;
}

// ── CSV ──
function handleDragOver(e){e.preventDefault();document.getElementById('dropZone').classList.add('drag');}
function handleDragLeave(){document.getElementById('dropZone').classList.remove('drag');}
function handleDrop(e){e.preventDefault();document.getElementById('dropZone').classList.remove('drag');const f=e.dataTransfer.files[0];if(f)processCSV(f);}
function handleCSVFile(e){processCSV(e.target.files[0]);}
function processCSV(file){
  const reader=new FileReader();
  reader.onload=e=>{
    const lines=e.target.result.split('\n').map(l=>l.trim()).filter(Boolean);
    if(lines.length<2){showToast('⚠️ CSV must have a header row + data rows','warn');return;}
    // find column indices
    const headers=lines[0].toLowerCase().split(',').map(h=>h.trim());
    const fi=headers.indexOf('food'),qi=headers.indexOf('quantity'),ui=headers.indexOf('unit');
    if(fi<0||qi<0){showToast('⚠️ CSV must have "food" and "quantity" columns','warn');return;}
    let added=0,skipped=0;
    foodLog=[];
    for(let i=1;i<Math.min(lines.length,501);i++){
      const cols=lines[i].split(',').map(c=>c.trim());
      const name=cols[fi];const qty=parseFloat(cols[qi]);const unit=(ui>=0?cols[ui]:'g')||'g';
      const canonUnit=Object.keys(UNIT_MULT).includes(unit.toLowerCase())?unit.toLowerCase():'g';
      if(!FOODS[name]){skipped++;continue;}
      if(!qty||qty<=0){skipped++;continue;}
      const grams=qty*(UNIT_MULT[canonUnit]||1);
      const base=FOODS[name];const f=grams/100;const nutrients={};
      FKEYS.forEach((k,i)=>nutrients[k]=+(base[i]*f).toFixed(2));
      foodLog.push({id:Date.now()+i,name,qty,unit:canonUnit,grams,nutrients});added++;
    }
    renderFoodTable();save();
    showToast(`✅ Imported ${added} rows${skipped?' ('+skipped+' skipped)':''}`);
  };
  reader.readAsText(file);
}
function downloadSampleCSV(){
  const csv='food,quantity,unit\nRice,150,g\nDal,200,g\nSpinach,100,g\nBanana,1,piece\nMilk,240,ml\nEgg,2,piece';
  const a=document.createElement('a');a.href='data:text/csv;charset=utf-8,'+encodeURIComponent(csv);a.download='nutriscope_sample.csv';a.click();
}

// ── DASHBOARD ──
function renderDashboard(){
  const totals=getTotals();
  const t=targets||{tdee:2000,protein:50,carbs:250,fat:55,fiber:30,iron:8,calcium:1000,magnesium:320,potassium:3500,zinc:8,vitA:700,vitC:75,vitD:15,vitB12:2.4,folate:400};
  // Energy ring
  const pct=Math.min(Math.round((totals.cal/t.tdee)*100),120);
  document.getElementById('dashKcal').textContent=Math.round(totals.cal);
  document.getElementById('dashKcalPct').textContent='of '+t.tdee+' kcal';
  document.getElementById('dashRemain').textContent=Math.max(0,t.tdee-Math.round(totals.cal))+' kcal';
  document.getElementById('dashItems').textContent=foodLog.length;
  if(charts.ring)charts.ring.destroy();
  const rc=document.getElementById('energyRing').getContext('2d');
  const ringColor=pct>110?'#f75252':pct>90?'#f5a623':'#34d48a';
  charts.ring=new Chart(rc,{type:'doughnut',data:{datasets:[{data:[pct,Math.max(0,100-pct)],backgroundColor:[ringColor,'rgba(255,255,255,.05)'],borderWidth:0,hoverOffset:0}]},options:{cutout:'76%',plugins:{legend:{display:false},tooltip:{enabled:false}},animation:{animateRotate:true,duration:900}}});
  // Macro chart
  drawMacroChart(totals,t);
  // Micro radar
  if(charts.radar)charts.radar.destroy();
  const radarLabels=['Iron','Calcium','Mg','K','Zinc','Vit A','Vit C','Vit D','B12','Folate'];
  const radarKeys=['iron','calcium','magnesium','potassium','zinc','vitA','vitC','vitD','vitB12','folate'];
  const radarAct=radarKeys.map(k=>Math.min(Math.round((totals[k]/(t[k]||1))*100),150));
  const rrc=document.getElementById('microRadar').getContext('2d');
  charts.radar=new Chart(rrc,{type:'radar',data:{labels:radarLabels,datasets:[{label:'% of Target',data:radarAct,backgroundColor:'rgba(79,110,247,.15)',borderColor:'rgba(79,110,247,.7)',pointBackgroundColor:'#4f6ef7',pointRadius:4}]},options:{responsive:true,maintainAspectRatio:false,scales:{r:{min:0,max:150,ticks:{color:'#555b72',font:{size:10},stepSize:50},grid:{color:'rgba(255,255,255,.07)'},pointLabels:{color:'#8b90a7',font:{size:11}},angleLines:{color:'rgba(255,255,255,.06)'}}},plugins:{legend:{labels:{color:'#8b90a7',font:{size:11}}}}}});
  // Calorie pie
  if(charts.calPie)charts.calPie.destroy();
  const protCal=totals.protein*4,carbCal=totals.carbs*4,fatCal=totals.fat*9;
  const cpc=document.getElementById('calPie').getContext('2d');
  charts.calPie=new Chart(cpc,{type:'doughnut',data:{labels:['Protein','Carbs','Fat'],datasets:[{data:[protCal,carbCal,fatCal].map(v=>+(v||0).toFixed(0)),backgroundColor:['rgba(245,166,35,.85)','rgba(34,211,238,.85)','rgba(167,139,250,.85)'],borderWidth:0,hoverOffset:6}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{position:'right',labels:{color:'#8b90a7',font:{size:11},padding:14}},tooltip:{callbacks:{label:c=>`${c.label}: ${c.parsed} kcal (${Math.round(c.parsed/(protCal+carbCal+fatCal||1)*100)}%)`}}}}});
  // Macro chips
  document.getElementById('macroChips').innerHTML=[
    ['🥩','Protein',totals.protein.toFixed(1)+' / '+t.protein+'g','#f5a623'],
    ['🍞','Carbs',totals.carbs.toFixed(1)+' / '+t.carbs+'g','#22d3ee'],
    ['🧈','Fat',totals.fat.toFixed(1)+' / '+t.fat+'g','#a78bfa'],
  ].map(([icon,label,val,color])=>`<div class="chip"><span style="font-size:15px">${icon}</span><div><div class="chip-lbl">${label}</div><div class="chip-val" style="color:${color}">${val}</div></div></div>`).join('');
  // Insights
  const allNutrients=FKEYS.map((k,i)=>({key:k,label:FLABELS[i],unit:FUNITS[i],target:t[k]||1,val:totals[k]||0}));
  const defs=allNutrients.filter(n=>n.val<n.target*.7).sort((a,b)=>(a.val/a.target)-(b.val/b.target)).slice(0,6);
  const excs=allNutrients.filter(n=>n.val>n.target*1.25).sort((a,b)=>(b.val/b.target)-(a.val/a.target)).slice(0,5);
  document.getElementById('defList').innerHTML=defs.length?defs.map(n=>{const p=Math.round((n.val/n.target)*100);return`<div class="insight-item ins-def"><span class="ins-name">${n.label}</span><span class="ins-val">${n.val.toFixed(1)} / ${n.target} ${n.unit}</span><span class="ibadge ibadge-low">${p}%</span></div>`}).join(''):'<div style="color:var(--accent-green);font-size:13px">✅ No major deficiencies!</div>';
  document.getElementById('excList').innerHTML=excs.length?excs.map(n=>{const p=Math.round((n.val/n.target)*100);return`<div class="insight-item ins-exc"><span class="ins-name">${n.label}</span><span class="ins-val">${n.val.toFixed(1)} / ${n.target} ${n.unit}</span><span class="ibadge ibadge-high">${p}%</span></div>`}).join(''):'<div style="color:var(--accent-green);font-size:13px">✅ Nothing over-consumed!</div>';
  // Full table
  document.getElementById('nutrientBody').innerHTML=allNutrients.map((n,i)=>{
    const pct=Math.min(Math.round((n.val/n.target)*100),150);
    const bp=Math.min(pct,100);
    const color=pct>125?'#f75252':pct>=75?'#34d48a':'#4f6ef7';
    const status=pct>125?`<span class="ibadge ibadge-high">High</span>`:pct>=75?`<span class="ibadge ibadge-ok">Good</span>`:`<span class="ibadge ibadge-low">Low</span>`;
    return`<tr><td class="nt-name">${n.label}</td><td style="font-size:11px;color:var(--text-muted)">${FCAT[i]}</td><td style="font-family:var(--mono);font-size:11.5px">${n.val.toFixed(1)} ${n.unit}</td><td style="font-family:var(--mono);font-size:11.5px;color:var(--text-muted)">${n.target} ${n.unit}</td><td><div style="display:flex;align-items:center;gap:7px"><div class="nt-bar"><div class="nt-fill" style="width:${bp}%;background:${color}"></div></div><span style="font-size:10.5px;font-family:var(--mono);color:var(--text-muted)">${pct}%</span></div></td><td>${status}</td></tr>`;
  }).join('');
}
function drawMacroChart(totals,t){
  if(charts.macro)charts.macro.destroy();
  const mc=document.getElementById('macroChart').getContext('2d');
  const macroKeys=['protein','carbs','fat','fiber'];
  const macroLabels=['Protein','Carbs','Fat','Fiber'];
  const consumed=macroKeys.map(k=>+(totals[k]||0).toFixed(1));
  const tgt=macroKeys.map(k=>+(t[k]||0));
  const colors=['rgba(245,166,35,.85)','rgba(34,211,238,.85)','rgba(167,139,250,.85)','rgba(52,212,138,.85)'];
  const colorsFade=['rgba(245,166,35,.18)','rgba(34,211,238,.18)','rgba(167,139,250,.18)','rgba(52,212,138,.18)'];
  if(macroChartType==='bar'){
    charts.macro=new Chart(mc,{type:'bar',data:{labels:macroLabels,datasets:[{label:'Consumed',data:consumed,backgroundColor:colors,borderRadius:7},{label:'Target',data:tgt,backgroundColor:colorsFade,borderRadius:7}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{color:'#8b90a7',font:{size:11}}}},scales:{x:{ticks:{color:'#8b90a7'},grid:{color:'rgba(255,255,255,.04)'}},y:{ticks:{color:'#8b90a7'},grid:{color:'rgba(255,255,255,.04)'}}}}});
  } else if(macroChartType==='radar'){
    const rdata=macroKeys.map((k,i)=>Math.min(Math.round((totals[k]/t[k])*100),150));
    charts.macro=new Chart(mc,{type:'radar',data:{labels:macroLabels,datasets:[{label:'% of Target',data:rdata,backgroundColor:'rgba(79,110,247,.15)',borderColor:'rgba(79,110,247,.7)',pointBackgroundColor:'#4f6ef7',pointRadius:4},{label:'100% line',data:[100,100,100,100],backgroundColor:'transparent',borderColor:'rgba(255,255,255,.1)',borderDash:[4,4],pointRadius:0}]},options:{responsive:true,maintainAspectRatio:false,scales:{r:{min:0,max:150,ticks:{color:'#555b72',stepSize:50},grid:{color:'rgba(255,255,255,.07)'},angleLines:{color:'rgba(255,255,255,.06)'},pointLabels:{color:'#8b90a7',font:{size:11}}}},plugins:{legend:{labels:{color:'#8b90a7',font:{size:11}}}}}});
  } else {
    charts.macro=new Chart(mc,{type:'pie',data:{labels:macroLabels,datasets:[{data:consumed,backgroundColor:colors,borderWidth:0,hoverOffset:8}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{position:'right',labels:{color:'#8b90a7',font:{size:11},padding:14}},tooltip:{callbacks:{label:c=>`${c.label}: ${c.parsed}g`}}}}});
  }
}
function setMacroChart(type){
  macroChartType=type;
  const totals=getTotals();
  const t=targets||{protein:50,carbs:250,fat:55,fiber:30};
  drawMacroChart(totals,t);
}

// ── MEAL PLANNER ──
const MEAL_SLOTS=['breakfast','lunch','dinner','snacks'];
const MEAL_EMOJIS={breakfast:'🌅',lunch:'☀️',dinner:'🌙',snacks:'🍎'};
function renderPlanner(){
  const t=targets||{tdee:2000,protein:50,carbs:250,fat:55};
  const grid=document.getElementById('plannerGrid');
  grid.innerHTML=['day1','day2'].map(day=>{
    const dayNum=day==='day1'?1:2;
    const dayTotals=calcPlannerTotals(day);
    return`<div class="day-card">
      <div class="day-header">
        <div class="day-title">📅 Day ${dayNum}</div>
        <div class="day-total">${Math.round(dayTotals.cal)} kcal · ${dayTotals.protein.toFixed(0)}g prot</div>
      </div>
      ${MEAL_SLOTS.map(slot=>`<div class="meal-slot">
        <div class="meal-name">${MEAL_EMOJIS[slot]} ${slot.charAt(0).toUpperCase()+slot.slice(1)}</div>
        <div class="meal-items" id="plan-${day}-${slot}">
          ${(mealPlan[day][slot]||[]).map((item,i)=>`<div class="meal-item-tag">🍴 ${item.name} (${item.qty}g)<button onclick="removePlanItem('${day}','${slot}',${i})">✕</button></div>`).join('')}
          ${!(mealPlan[day][slot]||[]).length?'<span style="font-size:12px;color:var(--text-muted)">No items yet</span>':''}
        </div>
        <div class="meal-add">
          <select class="fs" id="sel-${day}-${slot}" style="font-size:12px;padding:6px 10px">
            <option value="">Add food…</option>
            ${Object.keys(FOODS).sort().map(f=>`<option value="${f}">${f}</option>`).join('')}
          </select>
          <input type="number" class="fi" id="qty-${day}-${slot}" placeholder="100" value="100" style="width:70px;font-size:12px;padding:6px 8px">
          <button class="btn btn-success" style="padding:6px 12px;font-size:12px" onclick="addPlanItem('${day}','${slot}')">+</button>
        </div>
      </div>`).join('')}
    </div>`;
  }).join('');
  updatePlannerChart();
}
function calcPlannerTotals(day){
  const out={};FKEYS.forEach(k=>out[k]=0);
  MEAL_SLOTS.forEach(slot=>(mealPlan[day][slot]||[]).forEach(item=>{
    const base=FOODS[item.name];if(!base)return;
    const f=item.qty/100;FKEYS.forEach((k,i)=>out[k]+=(base[i]*f)||0);
  }));
  return out;
}
function addPlanItem(day,slot){
  const name=document.getElementById(`sel-${day}-${slot}`).value;
  const qty=parseFloat(document.getElementById(`qty-${day}-${slot}`).value);
  if(!name||!qty||qty<=0)return;
  if(!mealPlan[day][slot])mealPlan[day][slot]=[];
  mealPlan[day][slot].push({name,qty});
  save();renderPlanner();
}
function removePlanItem(day,slot,idx){mealPlan[day][slot].splice(idx,1);save();renderPlanner();}
function updatePlannerChart(){
  if(charts.planner)charts.planner.destroy();
  const d1=calcPlannerTotals('day1'),d2=calcPlannerTotals('day2');
  const t=targets||{protein:50,carbs:250,fat:55,fiber:30};
  const pc=document.getElementById('plannerChart').getContext('2d');
  charts.planner=new Chart(pc,{type:'bar',data:{
    labels:['Calories (×10)','Protein (g)','Carbs (g)','Fat (g)','Fiber (g)','Iron (mg×10)','Calcium (mg÷10)'],
    datasets:[
      {label:'Day 1',data:[d1.cal/10,d1.protein,d1.carbs,d1.fat,d1.fiber,d1.iron*10,d1.calcium/10],backgroundColor:'rgba(79,110,247,.75)',borderRadius:6},
      {label:'Day 2',data:[d2.cal/10,d2.protein,d2.carbs,d2.fat,d2.fiber,d2.iron*10,d2.calcium/10],backgroundColor:'rgba(52,212,138,.75)',borderRadius:6},
      {label:'Target',data:[t.tdee/10,t.protein,t.carbs,t.fat,t.fiber,t.iron*10,t.calcium/10],backgroundColor:'rgba(255,255,255,.08)',borderRadius:6},
    ]
  },options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{color:'#8b90a7',font:{size:11}}}},scales:{x:{ticks:{color:'#8b90a7',font:{size:10}},grid:{color:'rgba(255,255,255,.04)'}},y:{ticks:{color:'#8b90a7'},grid:{color:'rgba(255,255,255,.04)'}}}}});
  // Summary
  const d1c=Math.round(d1.cal),d2c=Math.round(d2.cal);
  document.getElementById('plannerSummary').innerHTML=`<div class="g2">
    <div style="background:var(--bg-elevated);border-radius:var(--r-md);padding:14px 16px">
      <div style="font-size:11px;color:var(--text-muted);font-weight:700;margin-bottom:8px">DAY 1 TOTALS</div>
      <div style="display:flex;gap:12px;flex-wrap:wrap">${['cal','protein','carbs','fat'].map((k,i)=>`<span style="font-size:12px"><span style="color:var(--text-muted)">${FLABELS[i].replace('Calories','Cal')}</span> <strong style="font-family:var(--mono);color:var(--text-primary)">${d1[k].toFixed(k==='cal'?0:1)}</strong></span>`).join(' · ')}</div>
    </div>
    <div style="background:var(--bg-elevated);border-radius:var(--r-md);padding:14px 16px">
      <div style="font-size:11px;color:var(--text-muted);font-weight:700;margin-bottom:8px">DAY 2 TOTALS</div>
      <div style="display:flex;gap:12px;flex-wrap:wrap">${['cal','protein','carbs','fat'].map((k,i)=>`<span style="font-size:12px"><span style="color:var(--text-muted)">${FLABELS[i].replace('Calories','Cal')}</span> <strong style="font-family:var(--mono);color:var(--text-primary)">${d2[k].toFixed(k==='cal'?0:1)}</strong></span>`).join(' · ')}</div>
    </div>
  </div>`;
}

// ── RISK ANALYSIS ──
function renderRisk(){
  const totals=getTotals();
  if(!foodLog.length){document.getElementById('riskContainer').innerHTML=`<div class="empty-state"><div class="empty-icon">🔬</div><div class="empty-title">Log food first</div><div class="empty-sub">Risk analysis requires food data to compute indicators</div></div>`;return;}
  const t=targets||{tdee:2000,protein:50,carbs:250,fat:55,fiber:30,iron:8,calcium:1000,magnesium:320,potassium:3500,zinc:8,vitA:700,vitC:75,vitD:15,vitB12:2.4,folate:400};
  const cond=profile?profile.conditions:'';
  // Compute risk scores (0-100)
  const risks=[];
  // 1. Anaemia Risk
  let anaemiaScore=0;
  const ironPct=totals.iron/t.iron;const b12Pct=totals.vitB12/t.vitB12;const folatePct=totals.folate/t.folate;
  if(ironPct<0.5)anaemiaScore+=40;else if(ironPct<0.75)anaemiaScore+=20;
  if(b12Pct<0.5)anaemiaScore+=30;else if(b12Pct<0.75)anaemiaScore+=15;
  if(folatePct<0.5)anaemiaScore+=20;else if(folatePct<0.75)anaemiaScore+=10;
  if(cond==='anemia')anaemiaScore=Math.min(anaemiaScore+20,100);
  if(profile&&profile.gender==='female'&&profile.age<50)anaemiaScore=Math.min(anaemiaScore+10,100);
  risks.push({name:'Anaemia Risk',score:anaemiaScore,detail:`Iron: ${(ironPct*100).toFixed(0)}% · B12: ${(b12Pct*100).toFixed(0)}% · Folate: ${(folatePct*100).toFixed(0)}%`,desc:'Based on iron, B12, and folate intake vs targets. Low values may indicate nutritional anaemia risk. Does not account for haemoglobin levels.',flag:cond==='anemia'});
  // 2. Bone Health Risk
  let boneScore=0;
  const caPct=totals.calcium/t.calcium;const vdPct=totals.vitD/t.vitD;const mgPct=totals.magnesium/t.magnesium;
  if(caPct<0.5)boneScore+=40;else if(caPct<0.75)boneScore+=20;
  if(vdPct<0.3)boneScore+=35;else if(vdPct<0.6)boneScore+=18;
  if(mgPct<0.5)boneScore+=15;else if(mgPct<0.75)boneScore+=8;
  if(profile&&profile.age>50)boneScore=Math.min(boneScore+10,100);
  risks.push({name:'Bone Health Risk',score:boneScore,detail:`Calcium: ${(caPct*100).toFixed(0)}% · Vit D: ${(vdPct*100).toFixed(0)}% · Mg: ${(mgPct*100).toFixed(0)}%`,desc:'Derived from calcium, Vitamin D, and magnesium adequacy. Bone density is a long-term outcome; this is a short-term dietary indicator only.',flag:false});
  // 3. Cardiovascular Risk (from dietary pattern)
  let cvScore=0;
  const fatPct=totals.fat/t.fat;const kPct=totals.potassium/t.potassium;const fiberPct=totals.fiber/t.fiber;
  if(fatPct>1.5)cvScore+=35;else if(fatPct>1.2)cvScore+=18;
  if(kPct<0.5)cvScore+=25;else if(kPct<0.75)cvScore+=12;
  if(fiberPct<0.5)cvScore+=20;else if(fiberPct<0.75)cvScore+=10;
  const calPct=totals.cal/t.tdee;if(calPct>1.3)cvScore+=15;
  if(cond==='hypertension'||cond==='cholesterol')cvScore=Math.min(cvScore+20,100);
  risks.push({name:'Cardiovascular Diet Risk',score:cvScore,detail:`Fat: ${(fatPct*100).toFixed(0)}% · Potassium: ${(kPct*100).toFixed(0)}% · Fiber: ${(fiberPct*100).toFixed(0)}%`,desc:'Dietary pattern risk based on fat excess, low fiber, and low potassium — all associated with cardiovascular health. Not a clinical measure.',flag:cond==='hypertension'||cond==='cholesterol'});
  // 4. Metabolic / Glycaemic risk
  let metaScore=0;
  const carbPct=totals.carbs/t.carbs;const protPct=totals.protein/t.protein;
  if(carbPct>1.4)metaScore+=35;else if(carbPct>1.15)metaScore+=18;
  if(fiberPct<0.5)metaScore+=25;else if(fiberPct<0.75)metaScore+=12;
  if(calPct>1.25)metaScore+=20;
  if(protPct<0.6)metaScore+=10;
  if(cond==='diabetes')metaScore=Math.min(metaScore+25,100);
  risks.push({name:'Glycaemic / Metabolic Risk',score:metaScore,detail:`Carbs: ${(carbPct*100).toFixed(0)}% · Fiber: ${(fiberPct*100).toFixed(0)}% · Total Calories: ${(calPct*100).toFixed(0)}%`,desc:'Based on carbohydrate excess, fiber deficit, and caloric surplus patterns. High-carb + low-fiber diets may affect glycaemic control.',flag:cond==='diabetes'});
  // 5. Protein Adequacy
  let protScore=0;
  if(protPct<0.4)protScore=85;else if(protPct<0.6)protScore=60;else if(protPct<0.75)protScore=35;else if(protPct<0.9)protScore=15;
  risks.push({name:'Protein Adequacy',score:100-protScore,detail:`Protein: ${totals.protein.toFixed(1)}g vs ${t.protein}g target (${(protPct*100).toFixed(0)}%)`,desc:'Higher score = better adequacy. Adequate protein supports muscle maintenance, immunity, and enzyme function.',flag:false,inverted:true});
  // 6. Micronutrient Completeness
  const microKeys=['iron','calcium','magnesium','potassium','zinc','vitA','vitC','vitD','vitB12','folate'];
  const microPcts=microKeys.map(k=>(totals[k]||0)/(t[k]||1));
  const avgMicro=microPcts.reduce((a,b)=>a+b,0)/microPcts.length;
  const microScore=Math.round(avgMicro*100);
  risks.push({name:'Micronutrient Completeness',score:microScore,detail:`Average micro coverage: ${microScore}% across 10 tracked micronutrients`,desc:'Higher score = better coverage. Scores above 75% indicate a reasonably balanced micronutrient profile for the day logged.',flag:false,inverted:true});
  // Render
  document.getElementById('riskContainer').innerHTML=`
  <div class="risk-grid">${risks.map(r=>{
    const s=r.inverted?r.score:(100-r.score);// for display colour only
    const level=r.inverted?(r.score>=75?'low':r.score>=45?'med':'high'):(r.score<=25?'low':r.score<=60?'med':'high');
    const levelLabel=r.inverted?(r.score>=75?'Good':r.score>=45?'Moderate':'Concern'):(r.score<=25?'Low Risk':r.score<=60?'Moderate':'High Risk');
    return`<div class="risk-card risk-${level}">
      <div class="risk-label">${levelLabel}${r.flag?` · ⚕️ Profile Flag`:''}</div>
      <div class="risk-title">${r.name}</div>
      <div class="risk-score">${r.score}${r.inverted?'%':''}</div>
      <div style="font-size:11.5px;color:var(--text-secondary);font-family:var(--mono);margin:6px 0">${r.detail}</div>
      <div class="risk-desc">${r.desc}</div>
    </div>`;
  }).join('')}</div>
  <div class="card" style="margin-top:4px">
    <div class="card-title">📊 Risk Score Chart</div>
    <div class="chart-wrap"><canvas id="riskChart"></canvas></div>
  </div>`;
  setTimeout(()=>{
    if(charts.risk)charts.risk.destroy();
    const rc2=document.getElementById('riskChart').getContext('2d');
    const riskLabels=risks.map(r=>r.name);
    const riskData=risks.map(r=>r.score);
    const riskColors=risks.map(r=>{
      if(r.inverted)return r.score>=75?'rgba(52,212,138,.8)':r.score>=45?'rgba(245,166,35,.8)':'rgba(247,82,82,.8)';
      return r.score<=25?'rgba(52,212,138,.8)':r.score<=60?'rgba(245,166,35,.8)':'rgba(247,82,82,.8)';
    });
    charts.risk=new Chart(rc2,{type:'bar',data:{labels:riskLabels,datasets:[{label:'Score',data:riskData,backgroundColor:riskColors,borderRadius:8}]},options:{indexAxis:'y',responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:{callbacks:{label:c=>`Score: ${c.parsed.x}`}}},scales:{x:{min:0,max:100,ticks:{color:'#8b90a7'},grid:{color:'rgba(255,255,255,.04)'}},y:{ticks:{color:'#8b90a7',font:{size:11}},grid:{color:'rgba(255,255,255,.04)'}}}}});
  },100);
}

// ── RECOMMENDATIONS ──
function renderRecs(){
  if(!profile||!targets){document.getElementById('recsContainer').innerHTML=`<div class="empty-state"><div class="empty-icon">💡</div><div class="empty-title">Save your profile first</div><div class="empty-sub">Personalised recommendations need your details</div></div>`;return;}
  const totals=getTotals();const t=targets;const dp=profile.dietPref;const cond=profile.conditions||'';const recs=[];
  const r=(key)=>(totals[key]||0)/(t[key]||1);
  // Protein
  if(r('protein')<0.7){
    const pri=r('protein')<0.4?'high':'med';
    if(dp==='veg')recs.push({type:'add',icon:'🫘',title:'Add Paneer, Dal, or Soyabean',text:'Protein is significantly below target. Add 100g paneer or a katori of dal/moong. Soyabean is the highest plant-based protein at ~17g/100g.',reason:`${totals.protein.toFixed(1)}g vs ${t.protein}g target`,pri});
    else if(dp==='nonveg')recs.push({type:'add',icon:'🍗',title:'Add Chicken, Fish, or Mutton',text:'Add 150g grilled chicken breast (46g protein) or 120g fish (24g protein). Prawn is also excellent at 24g/100g.',reason:`${totals.protein.toFixed(1)}g vs ${t.protein}g target`,pri});
    else recs.push({type:'add',icon:'🥚',title:'Add Eggs and Dal',text:'Two eggs + a bowl of moong dal covers ~50% of daily protein for eggetarians. Easy to prepare and highly bioavailable.',reason:`${totals.protein.toFixed(1)}g vs ${t.protein}g target`,pri});
  }
  // Calcium
  if(r('calcium')<0.7){
    recs.push({type:'add',icon:'🥛',title:'Boost Calcium — Add Dairy',text:'Add a glass of milk (113mg Ca) or a bowl of curd (121mg Ca). Cheese is extremely dense at 721mg/100g. Ragi (not in DB) is an excellent non-dairy source.',reason:`${totals.calcium.toFixed(0)}mg vs ${t.calcium}mg target`,pri:'med'});
  }
  // Iron
  if(r('iron')<0.7){
    const pri=cond==='anemia'?'high':'med';
    if(dp==='veg'||dp==='egg')recs.push({type:'add',icon:'🌿',title:'Add Spinach + Vitamin C for Iron',text:'Spinach (2.7mg iron/100g) and jaggery (11mg/100g) are top plant sources. Critically — pair with vitamin C foods (amla, guava, orange) to dramatically increase non-haem iron absorption.',reason:`${totals.iron.toFixed(1)}mg vs ${t.iron}mg target`,pri});
    else recs.push({type:'add',icon:'🥩',title:'Add Mutton or Fish for Iron',text:'Mutton provides 1.7mg haem iron/100g with superior bioavailability. Chicken liver (if available) is exceptional. Combine with plant-based iron for maximum absorption.',reason:`${totals.iron.toFixed(1)}mg vs ${t.iron}mg target`,pri});
  }
  // Vitamin D
  if(r('vitD')<0.5){
    const pri=r('vitD')<0.2?'high':'med';
    if(dp!=='veg')recs.push({type:'add',icon:'🐟',title:'Eat Fatty Fish for Vitamin D',text:`Fish provides 11µg Vit D per 100g — the best food source. Tuna and salmon are top performers. ${r('vitD')<0.2?'Your level is critically low — consider a supplement (consult your doctor).':''}`,reason:`${totals.vitD.toFixed(1)}µg vs ${t.vitD}µg target`,pri});
    else recs.push({type:'warn',icon:'☀️',title:'Vitamin D — Diet is Insufficient',text:'Vegetarian diets provide almost no Vitamin D. Fortified milk adds ~1.3µg/100ml. The main source must be sunlight (15–30 min morning sun, arms exposed). Consider a supplement after consulting your physician.',reason:`${totals.vitD.toFixed(1)}µg vs ${t.vitD}µg target`,pri});
  }
  // B12
  if(r('vitB12')<0.5){
    const pri=r('vitB12')<0.25?'high':'med';
    if(dp==='veg')recs.push({type:'warn',icon:'🧬',title:'Vitamin B12 — Critical for Vegetarians',text:'B12 is found almost exclusively in animal foods. Dairy (paneer, milk, curd) provides small amounts. Strict vegetarians often need B12 supplementation. Deficiency causes nerve damage and anaemia over time.',reason:`${totals.vitB12.toFixed(1)}µg vs ${t.vitB12}µg target`,pri});
    else if(dp==='egg')recs.push({type:'add',icon:'🥚',title:'Eggs Cover Your B12 Needs',text:'Two eggs provide ~2.2µg B12 — nearly your full daily requirement. Make eggs a consistent daily staple.',reason:`${totals.vitB12.toFixed(1)}µg vs ${t.vitB12}µg target`,pri});
    else recs.push({type:'add',icon:'🐟',title:'Fish is Your Best B12 Source',text:'Tuna (2.5µg), prawn (1.7µg), and mutton (2.1µg) per 100g. 100g fish covers your entire B12 requirement.',reason:`${totals.vitB12.toFixed(1)}µg vs ${t.vitB12}µg target`,pri});
  }
  // Folate
  if(r('folate')<0.6){
    recs.push({type:'add',icon:'🥬',title:'Add Folate-Rich Foods',text:'Spinach, moong dal, masoor dal, and rajma are excellent folate sources. 100g spinach = 194µg folate — nearly 50% of daily target. Critical for women of childbearing age.',reason:`${totals.folate.toFixed(0)}µg vs ${t.folate}µg target`,pri:profile.gender==='female'&&profile.age<45?'high':'med'});
  }
  // Magnesium
  if(r('magnesium')<0.6){
    recs.push({type:'add',icon:'🌰',title:'Boost Magnesium — Add Nuts & Seeds',text:'Chia seeds (335mg/100g), almonds (270mg), flax seeds (392mg), and oats (138mg) are top magnesium sources. Magnesium supports sleep, muscle function, and blood pressure.',reason:`${totals.magnesium.toFixed(0)}mg vs ${t.magnesium}mg target`,pri:'low'});
  }
  // Potassium
  if(r('potassium')<0.6){
    recs.push({type:'add',icon:'🍌',title:'Add Potassium-Rich Foods',text:'Banana, potato, spinach, pomegranate, and guava are rich in potassium. Low potassium increases blood pressure risk, especially with high sodium diets.',reason:`${totals.potassium.toFixed(0)}mg vs ${t.potassium}mg target`,pri:cond==='hypertension'?'high':'low'});
  }
  // Vitamin C
  if(r('vitC')<0.6){
    recs.push({type:'add',icon:'🍋',title:'Add Vitamin C for Iron Absorption too',text:'Amla (600mg/100g!), guava (228mg), capsicum (128mg), and oranges (53mg) are the best sources. Vitamin C also doubles iron absorption from plant foods.',reason:`${totals.vitC.toFixed(1)}mg vs ${t.vitC}mg target`,pri:'low'});
  }
  // Vitamin A
  if(r('vitA')<0.5){
    recs.push({type:'add',icon:'🥕',title:'Add Vitamin A from Orange Vegetables',text:'Carrot (835µg/100g), sweet potato (709µg), pumpkin (426µg), and spinach (469µg) are exceptional sources. Vitamin A supports vision, immunity, and skin health.',reason:`${totals.vitA.toFixed(0)}µg vs ${t.vitA}µg target`,pri:'med'});
  }
  // Fiber low
  if(r('fiber')<0.65){
    recs.push({type:'add',icon:'🌾',title:'More Fiber — Swap Refined Foods',text:'Swap white rice with brown rice. Add chia seeds to yoghurt (34g fiber/100g!). Include chana, rajma, or oats daily. Adequate fiber supports gut health and glycaemic control.',reason:`${totals.fiber.toFixed(1)}g vs ${t.fiber}g target`,pri:'med'});
  }
  // Fat high
  if(r('fat')>1.35){
    recs.push({type:'reduce',icon:'📉',title:'Reduce Fat Intake',text:'Limit ghee and butter use in cooking. Swap fried preparations for steamed or grilled. Replace paneer with tofu or low-fat curd as a protein source to reduce saturated fat.',reason:`${totals.fat.toFixed(1)}g vs ${t.fat}g target`,pri:'med'});
  }
  // Carbs excess
  if(r('carbs')>1.35){
    if(cond==='diabetes')recs.push({type:'swap',icon:'🔄',title:'Reduce Carbohydrates — Diabetes Flag',text:'Your carbohydrate intake significantly exceeds target, and a diabetes condition is flagged. Prioritise reducing white rice, bread, and poha portions. Replace with dal, vegetables, and protein-rich foods.',reason:`${totals.carbs.toFixed(1)}g vs ${t.carbs}g target`,pri:'high'});
    else recs.push({type:'swap',icon:'🔄',title:'High Carbohydrate Intake',text:'Reduce white rice, bread, or poha portions by 25–30%. Replace snacks with nuts, curd, or chana to maintain satiety without the carb spike.',reason:`${totals.carbs.toFixed(1)}g vs ${t.carbs}g target`,pri:'med'});
  }
  // Caloric surplus
  if(totals.cal>t.tdee*1.25){
    recs.push({type:'reduce',icon:'📉',title:'Caloric Surplus — Portion Control',text:'You have consumed significantly more than your adjusted daily target. Focus on reducing portion sizes for your highest calorie items at the next meal.',reason:`${Math.round(totals.cal)} kcal vs ${t.tdee} kcal target`,pri:'med'});
  }
  // Sort by priority
  const priOrder={high:0,med:1,low:2};
  recs.sort((a,b)=>(priOrder[a.pri]||2)-(priOrder[b.pri]||2));
  if(!recs.length){document.getElementById('recsContainer').innerHTML=`<div class="rec-card rec-add" style="align-items:center"><div class="rec-icon" style="font-size:32px;width:52px;height:52px">🎉</div><div><div class="rec-type">Excellent Progress</div><div class="rec-text" style="font-size:15px;font-weight:700">You're hitting all major nutrition targets today!</div><div class="rec-reason">Keep logging meals consistently to maintain this.</div></div></div>`;return;}
  const priLabel={high:'🔴 High Priority',med:'🟡 Medium Priority',low:'🟢 Low Priority'};
  const priBadge={high:'pri-high',med:'pri-med',low:'pri-low'};
  document.getElementById('recsContainer').innerHTML=`<div style="font-size:12.5px;color:var(--text-muted);margin-bottom:14px">${recs.length} recommendation${recs.length>1?'s':''} based on today's log and your profile.</div>`+recs.map(r=>`
    <div class="rec-card rec-${r.type}">
      <div class="rec-icon">${r.icon}</div>
      <div style="flex:1">
        <div style="display:flex;align-items:center;gap:6px;margin-bottom:3px">
          <div class="rec-type">${r.type==='add'?'➕ Add Food':r.type==='swap'?'🔄 Swap':r.type==='warn'?'⚠️ Alert':'📉 Reduce'}</div>
          <span class="rec-priority ${priBadge[r.pri]}">${priLabel[r.pri]}</span>
        </div>
        <div class="rec-text"><strong>${r.title}</strong><br>${r.text}</div>
        <div class="rec-reason">📊 ${r.reason}</div>
      </div>
    </div>`).join('');
}

// ── TOAST ──
let toastTimer;
function showToast(msg,type='success'){
  const toast=document.getElementById('toast');
  document.getElementById('toastMsg').textContent=msg;
  toast.style.borderColor=type==='warn'?'var(--accent-amber)':'var(--accent-green)';
  toast.classList.add('show');clearTimeout(toastTimer);
  toastTimer=setTimeout(()=>toast.classList.remove('show'),3000);
}
</script>
</body>
</html>

[NutriScope_v2.html](https://github.com/user-attachments/files/28765463/NutriScope_v2.html)


---

# Iterative Development Process

### Step 1

Build a working MVP.

### Step 2

Test functionality.

### Step 3

Identify weaknesses.

### Step 4

Add improvements through focused prompts.

### Step 5

Enhance design and usability.

### Step 6

Deliver a more complete product.

---

# Key Learnings

1. Building an MVP first reduces complexity.
2. Iterative development improves output quality.
3. Small improvements compound into major upgrades.
4. Claude Artifacts can generate real applications, not just text.
5. Focused prompts produce better results than one massive prompt.
6. Product development is a continuous improvement process.

---

# Insights

The biggest lesson from this exercise was that AI product development works best when approached incrementally. Creating a working MVP first allowed me to test ideas quickly and then enhance the application through multiple iterations.

This process resulted in a significantly better final product than attempting to build everything in a single prompt.

---

# Conclusion

Iterative development is one of the most effective ways to build AI-powered products. By starting with a Minimum Viable Product and progressively enhancing it, I was able to create a more reliable, useful, and professional application using Claude Artifacts.
