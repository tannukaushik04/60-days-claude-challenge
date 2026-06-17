# Day 17 – Vehicle Cost Analysis Dashboard

## Objective
Learn how AI can analyze CSV datasets, calculate business metrics, and generate a complete HTML dashboard for vehicle cost analysis.

---

# Vehicle Details Used

| Parameter | Value |
|------------|--------|
| Vehicle | Tata Punch |
| Fuel Type | Petrol |
| Usage | City Driving |
| Average KM/Month | 790 KM |
| Vehicle Age | 4 Years |

---

# Dashboard Overview

The generated HTML dashboard analyzed vehicle operating costs and provided:

- Cost per kilometer analysis
- Monthly and yearly fuel expenses
- Maintenance cost breakdown
- Environmental impact analysis
- Fuel comparison metrics
- KPI summary cards
- SVG-based visualizations
- Cost trend insights

---

# Generated HTML File

File Included:

[fuel_dashboard.html](https://github.com/user-attachments/files/29062309/fuel_dashboard.html)<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fuel Intelligence Dashboard · Tata Punch</title>
<style>
  :root {
    --bg: #0a0f1e;
    --bg2: #0d1428;
    --glass: rgba(255,255,255,0.04);
    --glass-border: rgba(255,255,255,0.08);
    --glass-hover: rgba(255,255,255,0.07);
    --amber: #f59e0b;
    --amber-light: #fbbf24;
    --amber-glow: rgba(245,158,11,0.3);
    --blue: #3b82f6;
    --blue-light: #60a5fa;
    --blue-glow: rgba(59,130,246,0.35);
    --grey: #9ca3af;
    --green: #22c55e;
    --purple: #a855f7;
    --text: #e2e8f0;
    --text-muted: #94a3b8;
    --text-dim: #64748b;
    --red: #ef4444;
  }
  * { margin:0; padding:0; box-sizing:border-box; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: -apple-system, 'Segoe UI', sans-serif;
    min-height: 100vh;
    padding: 0;
  }

  /* ── HEADER ── */
  .header {
    background: linear-gradient(135deg, #0d1428 0%, #111827 50%, #0a0f1e 100%);
    border-bottom: 1px solid var(--glass-border);
    padding: 20px 24px 16px;
    position: sticky; top:0; z-index:100;
  }
  .header-inner { max-width:1280px; margin:0 auto; display:flex; align-items:center; gap:16px; flex-wrap:wrap; }
  .car-icon {
    width:48px; height:48px; background:var(--blue-glow);
    border:1px solid var(--blue); border-radius:12px;
    display:flex; align-items:center; justify-content:center; font-size:22px; flex-shrink:0;
    box-shadow: 0 0 20px var(--blue-glow);
  }
  .header-text { flex:1; min-width:220px; }
  .header-title { font-size:clamp(15px,3vw,20px); font-weight:700; color:var(--text); letter-spacing:.3px; }
  .header-title span { color:var(--blue-light); }
  .header-sub { font-size:12px; color:var(--text-muted); margin-top:3px; letter-spacing:.5px; }
  .header-badge {
    background: linear-gradient(135deg, var(--amber-glow), rgba(59,130,246,0.15));
    border:1px solid var(--amber);
    color: var(--amber-light); font-size:11px; font-weight:600;
    padding:4px 12px; border-radius:20px; letter-spacing:.6px;
    box-shadow: 0 0 12px var(--amber-glow);
  }

  /* ── LAYOUT ── */
  .main { max-width:1280px; margin:0 auto; padding:20px 16px 40px; }

  /* ── GLASS CARD ── */
  .card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius:16px;
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    padding:20px;
    transition: border-color .2s, background .2s;
  }
  .card:hover { background: var(--glass-hover); border-color: rgba(255,255,255,0.13); }
  .card-title {
    font-size:11px; font-weight:600; color:var(--text-muted);
    letter-spacing:1.2px; text-transform:uppercase; margin-bottom:10px;
    display:flex; align-items:center; gap:6px;
  }
  .card-title::before { content:''; width:3px; height:12px; border-radius:2px; background:var(--blue); display:block; }

  /* ── KPI GRID ── */
  .kpi-grid { display:grid; grid-template-columns: repeat(auto-fit, minmax(180px,1fr)); gap:12px; margin-bottom:20px; }
  .kpi-card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius:14px;
    padding:16px 18px;
    position:relative; overflow:hidden;
    transition: transform .2s, box-shadow .2s;
  }
  .kpi-card:hover { transform:translateY(-2px); }
  .kpi-card.highlight {
    border-color: var(--blue);
    box-shadow: 0 0 20px var(--blue-glow), inset 0 0 40px rgba(59,130,246,0.05);
  }
  .kpi-card.highlight-amber {
    border-color: var(--amber);
    box-shadow: 0 0 20px var(--amber-glow), inset 0 0 40px rgba(245,158,11,0.05);
  }
  .kpi-label { font-size:10px; color:var(--text-muted); font-weight:500; letter-spacing:.8px; text-transform:uppercase; margin-bottom:6px; }
  .kpi-value { font-size:clamp(22px,4vw,30px); font-weight:700; line-height:1; }
  .kpi-value .unit { font-size:13px; font-weight:400; color:var(--text-muted); margin-left:2px; }
  .kpi-sub { font-size:11px; color:var(--text-dim); margin-top:5px; }
  .kpi-accent { position:absolute; top:0; right:0; width:60px; height:60px; border-radius:50%; opacity:.08; }

  /* ── CHART ROW ── */
  .chart-row { display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-bottom:20px; }
  @media(max-width:680px){ .chart-row { grid-template-columns:1fr; } }

  /* ── TOOLTIP ── */
  .tooltip {
    position:fixed; background:#1e293b; border:1px solid var(--glass-border);
    border-radius:8px; padding:8px 12px; font-size:12px; color:var(--text);
    pointer-events:none; z-index:999; display:none; box-shadow:0 8px 24px rgba(0,0,0,.5);
  }
  .tooltip.visible { display:block; }

  /* ── GAUGE ── */
  .gauge-wrap { display:flex; flex-direction:column; align-items:center; }
  .gauge-score { font-size:36px; font-weight:800; color:var(--amber); margin-top:8px; }
  .gauge-label { font-size:12px; color:var(--text-muted); }
  .gauge-verdict {
    margin-top:12px; font-size:13px; color:var(--text); line-height:1.5;
    text-align:center; padding:10px 14px;
    background:rgba(245,158,11,0.07); border:1px solid rgba(245,158,11,0.2);
    border-radius:8px;
  }

  /* ── PARADOX ── */
  .paradox-row { display:grid; grid-template-columns:repeat(3,1fr); gap:12px; }
  @media(max-width:500px){ .paradox-row { grid-template-columns:1fr; } }
  .paradox-item { text-align:center; }
  .paradox-val { font-size:22px; font-weight:700; margin-bottom:4px; }
  .paradox-label { font-size:11px; color:var(--text-muted); }
  .paradox-desc { font-size:10px; color:var(--text-dim); margin-top:2px; }

  /* ── FUEL CARDS ── */
  .fuel-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(220px,1fr)); gap:14px; margin-top:20px; }
  .fuel-card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius:14px; padding:18px;
    transition: transform .2s, box-shadow .2s;
  }
  .fuel-card:hover { transform:translateY(-3px); }
  .fuel-card.petrol-glow {
    border-color: var(--blue);
    box-shadow: 0 0 24px var(--blue-glow), 0 0 60px rgba(59,130,246,0.1);
  }
  .fuel-name { font-size:14px; font-weight:700; margin-bottom:12px; display:flex; align-items:center; gap:8px; }
  .fuel-dot { width:10px; height:10px; border-radius:50%; flex-shrink:0; }
  .fuel-stats { display:grid; grid-template-columns:1fr 1fr; gap:6px; margin-bottom:12px; }
  .fuel-stat { background:rgba(255,255,255,0.03); border-radius:6px; padding:7px 9px; }
  .fuel-stat-label { font-size:9px; color:var(--text-dim); letter-spacing:.5px; }
  .fuel-stat-val { font-size:13px; font-weight:600; margin-top:1px; }
  .fuel-pros, .fuel-cons { font-size:11px; line-height:1.6; margin-bottom:4px; }
  .fuel-best { font-size:10px; color:var(--text-muted); margin-top:8px; border-top:1px solid var(--glass-border); padding-top:7px; }

  /* ── AGE LINE ── */
  .age-section { margin-bottom:20px; }

  /* ── SCORE BAR BREAKDOWN ── */
  .score-breakdown { display:grid; grid-template-columns:1fr 1fr; gap:8px; margin-top:12px; }
  .score-bar-row { }
  .score-bar-label { font-size:10px; color:var(--text-muted); margin-bottom:3px; display:flex; justify-content:space-between; }
  .score-bar-bg { height:5px; background:rgba(255,255,255,0.06); border-radius:3px; }
  .score-bar-fill { height:5px; border-radius:3px; transition: width 1.2s ease; }

  /* ── BOTTOM ROW ── */
  .bottom-row { display:grid; grid-template-columns:1fr 2fr; gap:16px; margin-bottom:20px; }
  @media(max-width:700px){ .bottom-row { grid-template-columns:1fr; } }

  /* scrollbar */
  ::-webkit-scrollbar { width:6px; }
  ::-webkit-scrollbar-track { background:var(--bg); }
  ::-webkit-scrollbar-thumb { background:rgba(255,255,255,0.1); border-radius:3px; }

  svg text { font-family: -apple-system,'Segoe UI',sans-serif; }
</style>
</head>
<body>

<!-- HEADER -->
<header class="header">
  <div class="header-inner">
    <div class="car-icon">🚗</div>
    <div class="header-text">
      <div class="header-title">Tata Punch · <span>Petrol (E20)</span> · Age: 4y · 790 km/mo</div>
      <div class="header-sub">E85 FUEL INTELLIGENCE DASHBOARD · DATA FROM 52 RECORDS</div>
    </div>
    <div class="header-badge">LIVE ANALYSIS</div>
  </div>
</header>

<div class="main">

  <!-- KPI CARDS -->
  <div class="kpi-grid">
    <div class="kpi-card highlight">
      <div class="kpi-label">Your Cost / km</div>
      <div class="kpi-value" style="color:var(--blue-light)">₹6.15<span class="unit">/km</span></div>
      <div class="kpi-sub">Petrol (E20) · City usage</div>
      <div class="kpi-accent" style="background:var(--blue); top:-10px; right:-10px;"></div>
    </div>
    <div class="kpi-card">
      <div class="kpi-label">E85 Cost / km</div>
      <div class="kpi-value" style="color:var(--amber)">₹6.37<span class="unit">/km</span></div>
      <div class="kpi-sub">Flex-Fuel alternative</div>
    </div>
    <div class="kpi-card">
      <div class="kpi-label">E85 Premium vs Petrol</div>
      <div class="kpi-value" style="color:var(--red)">+3.6<span class="unit">%</span></div>
      <div class="kpi-sub">Running cost penalty</div>
    </div>
    <div class="kpi-card highlight-amber">
      <div class="kpi-label">E85 Break-even Price</div>
      <div class="kpi-value" style="color:var(--amber)">₹79.11<span class="unit">/L</span></div>
      <div class="kpi-sub">E85 must be ≤ ₹79.11 to win</div>
    </div>
    <div class="kpi-card">
      <div class="kpi-label">Your Monthly Cost</div>
      <div class="kpi-value" style="color:var(--text)">₹4,862</div>
      <div class="kpi-sub">790 km/mo · Petrol (E20)</div>
    </div>
  </div>

  <!-- BAR + DONUT -->
  <div class="chart-row">
    <div class="card">
      <div class="card-title">Cost / km by Fuel Type</div>
      <svg id="barChart" viewBox="0 0 420 240" width="100%" xmlns="http://www.w3.org/2000/svg"></svg>
    </div>
    <div class="card">
      <div class="card-title">CO₂ / km by Fuel Type</div>
      <svg id="donutChart" viewBox="0 0 340 240" width="100%" xmlns="http://www.w3.org/2000/svg"></svg>
    </div>
  </div>

  <!-- LINE CHART -->
  <div class="card age-section" style="margin-bottom:20px;">
    <div class="card-title">Cost / km vs Vehicle Age (0–12y)</div>
    <svg id="lineChart" viewBox="0 0 900 280" width="100%" xmlns="http://www.w3.org/2000/svg"></svg>
  </div>

  <!-- GAUGE + PARADOX -->
  <div class="bottom-row">
    <div class="card" style="display:flex;flex-direction:column;align-items:center;justify-content:center;">
      <div class="card-title" style="width:100%;justify-content:center;">E85 Score / 10</div>
      <div class="gauge-wrap">
        <svg id="gaugeChart" viewBox="0 0 200 130" width="200" xmlns="http://www.w3.org/2000/svg"></svg>
        <div class="gauge-score" id="gaugeScore">0.0</div>
        <div class="gauge-label">out of 10</div>
        <div class="score-breakdown">
          <div class="score-bar-row">
            <div class="score-bar-label"><span>Cost (4pt)</span><span>0.0</span></div>
            <div class="score-bar-bg"><div class="score-bar-fill" id="sb-cost" style="width:0%;background:var(--amber)"></div></div>
          </div>
          <div class="score-bar-row">
            <div class="score-bar-label"><span>CO₂ (3pt)</span><span>3.0</span></div>
            <div class="score-bar-bg"><div class="score-bar-fill" id="sb-co2" style="width:0%;background:var(--green)"></div></div>
          </div>
          <div class="score-bar-row">
            <div class="score-bar-label"><span>Refuel (2pt)</span><span>1.5</span></div>
            <div class="score-bar-bg"><div class="score-bar-fill" id="sb-refuel" style="width:0%;background:var(--blue)"></div></div>
          </div>
          <div class="score-bar-row">
            <div class="score-bar-label"><span>Maint (1pt)</span><span>0.75</span></div>
            <div class="score-bar-bg"><div class="score-bar-fill" id="sb-maint" style="width:0%;background:var(--purple)"></div></div>
          </div>
        </div>
        <div class="gauge-verdict">E85 excels at cutting CO₂ (−59% vs Petrol) but its higher running cost and lower mileage make it a green choice only if E85 pump price drops below ₹79/L.</div>
      </div>
    </div>

    <div class="card">
      <div class="card-title">E85 Paradox — Pump vs Reality</div>
      <div class="paradox-row">
        <div class="paradox-item">
          <div class="paradox-val" style="color:var(--green)">−18.0%</div>
          <div class="paradox-label">Pump Saving</div>
          <div class="paradox-desc">E85 cheaper at pump<br>vs Petrol (E20)</div>
        </div>
        <div class="paradox-item">
          <div class="paradox-val" style="color:var(--red)">+3.6%</div>
          <div class="paradox-label">Running Penalty</div>
          <div class="paradox-desc">Lower mileage makes<br>E85 costlier per km</div>
        </div>
        <div class="paradox-item">
          <div class="paradox-val" style="color:var(--amber)">₹79.11</div>
          <div class="paradox-label">Break-even / L</div>
          <div class="paradox-desc">E85 must stay below<br>this price to save money</div>
        </div>
      </div>
      <svg id="paradoxBar" viewBox="0 0 520 100" width="100%" xmlns="http://www.w3.org/2000/svg" style="margin-top:16px;"></svg>
    </div>
  </div>

  <!-- FUEL CARDS -->
  <div class="card-title" style="margin-bottom:12px;">
    <span style="width:3px;height:12px;background:var(--blue);display:inline-block;border-radius:2px;margin-right:6px;"></span>
    FUEL COMPARISON CARDS
  </div>
  <div class="fuel-grid" id="fuelCards"></div>

</div>

<!-- TOOLTIP -->
<div class="tooltip" id="tooltip"></div>

<script>
// ── DATA ──────────────────────────────────────────────────────────────────────
const FUELS = [
  { name:'Electric (EV)', short:'EV', color:'#a855f7', cost:1.75, co2:0.0912, maint:0.2331, refuel:45.0,
    pros:['Lowest cost/km at ₹1.75 ✅','Near-zero tailpipe CO₂ ✅'],
    cons:['45-min charging time ❌','Limited fast-charging infra ❌'],
    best:'🚗 Daily city commuters with home charging' },
  { name:'CNG', short:'CNG', color:'#22c55e', cost:3.32, co2:0.1253, maint:0.6616, refuel:8.0,
    pros:['Low running cost ₹3.32/km ✅','Cleaner than petrol/diesel ✅'],
    cons:['Boot space loss from CNG kit ❌','Limited CNG pumps in India ❌'],
    best:'🚗 High-mileage city & highway use' },
  { name:'Diesel', short:'Diesel', color:'#9ca3af', cost:4.67, co2:0.1787, maint:1.0046, refuel:5.0,
    pros:['Better long-range torque ✅','Efficient on highways ✅'],
    cons:['Highest maintenance cost ❌','Highest CO₂ per km ❌'],
    best:'🚗 Long highway trips & fleet vehicles' },
  { name:'E85 (Flex-Fuel)', short:'E85', color:'#f59e0b', cost:6.37, co2:0.0698, maint:0.4597, refuel:5.0,
    pros:['Lowest CO₂ among liquid fuels ✅','Supports sugarcane ethanol economy ✅'],
    cons:['3.6% running cost penalty vs Petrol ❌','Mileage drop (12.9 vs 16.3 km/L) ❌'],
    best:'🚗 Eco-conscious drivers in E85-available cities' },
  { name:'Petrol (E20)', short:'Petrol', color:'#3b82f6', cost:6.15, co2:0.1706, maint:0.4661, refuel:5.0,
    pros:['Widespread fuel availability ✅','Smoother refinement/performance ✅'],
    cons:['High cost/km vs CNG/EV ❌','Significant CO₂ emissions ❌'],
    best:'🚗 General city use — YOUR VEHICLE' },
];

const colors = { 'Electric (EV)':'#a855f7', 'CNG':'#22c55e', 'Diesel':'#9ca3af', 'E85 (Flex-Fuel)':'#f59e0b', 'Petrol (E20)':'#3b82f6' };

// ── AGE LINE DATA ─────────────────────────────────────────────────────────────
const ageRaw = [
  {f:'CNG',y:2,v:3.08},{f:'CNG',y:3,v:3.24},{f:'CNG',y:4,v:3.24},{f:'CNG',y:5,v:3.24},{f:'CNG',y:6,v:3.49},{f:'CNG',y:7,v:3.50},{f:'CNG',y:8,v:3.49},
  {f:'Diesel',y:3,v:4.35},{f:'Diesel',y:4,v:4.35},{f:'Diesel',y:6,v:4.69},{f:'Diesel',y:9,v:4.69},{f:'Diesel',y:11,v:5.29},{f:'Diesel',y:12,v:5.29},
  {f:'E85 (Flex-Fuel)',y:1,v:6.31},{f:'E85 (Flex-Fuel)',y:2,v:6.31},{f:'E85 (Flex-Fuel)',y:3,v:6.67},
  {f:'Electric (EV)',y:1,v:1.71},{f:'Electric (EV)',y:2,v:1.71},{f:'Electric (EV)',y:3,v:1.82},{f:'Electric (EV)',y:4,v:1.82},
  {f:'Petrol (E20)',y:3,v:5.85},{f:'Petrol (E20)',y:4,v:5.85},{f:'Petrol (E20)',y:5,v:5.85},{f:'Petrol (E20)',y:6,v:6.33},{f:'Petrol (E20)',y:7,v:6.33},{f:'Petrol (E20)',y:8,v:6.33},
];

const tooltip = document.getElementById('tooltip');
function showTip(e, html) {
  tooltip.innerHTML = html;
  tooltip.classList.add('visible');
  moveTip(e);
}
function moveTip(e) {
  const x = e.clientX + 14, y = e.clientY - 40;
  tooltip.style.left = Math.min(x, window.innerWidth-160)+'px';
  tooltip.style.top = Math.max(y, 8)+'px';
}
function hideTip() { tooltip.classList.remove('visible'); }

// ── BAR CHART ─────────────────────────────────────────────────────────────────
function drawBar() {
  const svg = document.getElementById('barChart');
  const W=420, H=240, pad={l:44,r:16,t:16,b:56};
  const cw=W-pad.l-pad.r, ch=H-pad.t-pad.b;
  const data = FUELS.map(f=>({name:f.short, full:f.name, val:f.cost, color:f.color}));
  const maxV=7.5, barW=cw/data.length*0.55, gap=cw/data.length;

  let out = `<rect width="${W}" height="${H}" fill="none"/>`;
  // grid
  [0,2,4,6].forEach(v=>{
    const y=pad.t+ch*(1-v/maxV);
    out+=`<line x1="${pad.l}" y1="${y}" x2="${W-pad.r}" y2="${y}" stroke="rgba(255,255,255,0.06)" stroke-width="1"/>`;
    out+=`<text x="${pad.l-6}" y="${y+4}" text-anchor="end" font-size="9" fill="#64748b">₹${v}</text>`;
  });
  // bars
  data.forEach((d,i)=>{
    const x=pad.l+i*gap+(gap-barW)/2;
    const bh=ch*(d.val/maxV);
    const y=pad.t+ch-bh;
    const isPetrol=d.full==='Petrol (E20)';
    out+=`<rect x="${x}" y="${y}" width="${barW}" height="${bh}" rx="4" fill="${d.color}" opacity="${isPetrol?1:0.7}"
      class="bar-rect" data-name="${d.full}" data-val="${d.val}"
      style="cursor:pointer;filter:${isPetrol?'drop-shadow(0 0 6px '+d.color+')':'none'}"/>`;
    if(isPetrol) out+=`<rect x="${x}" y="${y-3}" width="${barW}" height="3" rx="1" fill="${d.color}"/>`;
    out+=`<text x="${x+barW/2}" y="${pad.t+ch+14}" text-anchor="middle" font-size="9.5" fill="${isPetrol?'#60a5fa':'#94a3b8'}" font-weight="${isPetrol?700:400}">${d.name}</text>`;
    out+=`<text x="${x+barW/2}" y="${y-6}" text-anchor="middle" font-size="9" fill="${d.color}" font-weight="600">₹${d.val}</text>`;
  });
  svg.innerHTML = out;

  svg.querySelectorAll('.bar-rect').forEach(el=>{
    el.addEventListener('mouseenter',e=>showTip(e,`<b>${el.dataset.name}</b><br>Cost/km: <span style="color:#f59e0b">₹${parseFloat(el.dataset.val).toFixed(2)}</span>`));
    el.addEventListener('mousemove',moveTip);
    el.addEventListener('mouseleave',hideTip);
  });
}

// ── DONUT CHART ───────────────────────────────────────────────────────────────
function drawDonut() {
  const svg = document.getElementById('donutChart');
  const data = FUELS.map(f=>({name:f.name, short:f.short, val:f.co2, color:f.color}));
  const total=data.reduce((s,d)=>s+d.val,0);
  const cx=120, cy=110, r=78, ir=50;
  let angle=-Math.PI/2;
  let out=`<rect width="340" height="240" fill="none"/>`;

  data.forEach(d=>{
    const sweep=2*Math.PI*(d.val/total);
    const x1=cx+r*Math.cos(angle), y1=cy+r*Math.sin(angle);
    const x2=cx+r*Math.cos(angle+sweep), y2=cy+r*Math.sin(angle+sweep);
    const xi1=cx+ir*Math.cos(angle), yi1=cy+ir*Math.sin(angle);
    const xi2=cx+ir*Math.cos(angle+sweep), yi2=cy+ir*Math.sin(angle+sweep);
    const lg=sweep>Math.PI?1:0;
    const path=`M${xi1},${yi1} L${x1},${y1} A${r},${r} 0 ${lg} 1 ${x2},${y2} L${xi2},${yi2} A${ir},${ir} 0 ${lg} 0 ${xi1},${yi1}`;
    out+=`<path d="${path}" fill="${d.color}" opacity="0.85" class="donut-seg" data-name="${d.name}" data-val="${d.val.toFixed(4)}" style="cursor:pointer;transition:opacity .2s"/>`;
    // mid-angle label
    const ma=angle+sweep/2;
    if(sweep>0.35){
      const lx=cx+(r+18)*Math.cos(ma), ly=cy+(r+18)*Math.sin(ma);
      out+=`<text x="${lx}" y="${ly}" text-anchor="middle" font-size="9" fill="${d.color}" font-weight="600">${d.short}</text>`;
    }
    angle+=sweep;
  });
  // center
  out+=`<text x="${cx}" y="${cy-6}" text-anchor="middle" font-size="10" fill="#64748b">CO₂/km</text>`;
  out+=`<text x="${cx}" y="${cy+10}" text-anchor="middle" font-size="13" fill="#e2e8f0" font-weight="700">kg/km</text>`;

  // legend
  const lx=210;
  data.forEach((d,i)=>{
    const ly=30+i*38;
    out+=`<rect x="${lx}" y="${ly}" width="9" height="9" rx="2" fill="${d.color}"/>`;
    out+=`<text x="${lx+14}" y="${ly+9}" font-size="10" fill="#94a3b8">${d.short}</text>`;
    out+=`<text x="${lx+14}" y="${ly+21}" font-size="11" fill="${d.color}" font-weight="600">${d.val.toFixed(4)}</text>`;
  });

  svg.innerHTML=out;
  svg.querySelectorAll('.donut-seg').forEach(el=>{
    el.addEventListener('mouseenter',e=>{el.style.opacity=1;showTip(e,`<b>${el.dataset.name}</b><br>CO₂/km: <span style="color:#f59e0b">${parseFloat(el.dataset.val).toFixed(4)} kg/km</span>`);});
    el.addEventListener('mousemove',moveTip);
    el.addEventListener('mouseleave',()=>{el.style.opacity=0.85;hideTip();});
  });
}

// ── LINE CHART ────────────────────────────────────────────────────────────────
function drawLine() {
  const svg = document.getElementById('lineChart');
  const W=900, H=280, pad={l:46,r=20,t:20,b:48};
  const cw=W-pad.l-pad.r, ch=H-pad.t-pad.b;
  const maxAge=12, maxV=8.0;
  const CAR_AGE=4;

  const fuelGroups = {};
  ageRaw.forEach(d=>{ if(!fuelGroups[d.f]) fuelGroups[d.f]=[]; fuelGroups[d.f].push(d); });
  Object.values(fuelGroups).forEach(arr=>arr.sort((a,b)=>a.y-b.y));

  let out=`<rect width="${W}" height="${H}" fill="none"/>`;
  // grid
  [0,2,4,6,8].forEach(v=>{
    const y=pad.t+ch*(1-v/maxV);
    out+=`<line x1="${pad.l}" y1="${y}" x2="${W-pad.r}" y2="${y}" stroke="rgba(255,255,255,0.05)" stroke-width="1"/>`;
    out+=`<text x="${pad.l-6}" y="${y+4}" text-anchor="end" font-size="9" fill="#64748b">₹${v}</text>`;
  });
  [0,2,4,6,8,10,12].forEach(a=>{
    const x=pad.l+cw*(a/maxAge);
    out+=`<line x1="${x}" y1="${pad.t}" x2="${x}" y2="${pad.t+ch}" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>`;
    out+=`<text x="${x}" y="${pad.t+ch+14}" text-anchor="middle" font-size="9" fill="#64748b">${a}y</text>`;
  });

  // car age vertical line
  const ax=pad.l+cw*(CAR_AGE/maxAge);
  out+=`<line x1="${ax}" y1="${pad.t}" x2="${ax}" y2="${pad.t+ch}" stroke="#3b82f6" stroke-width="1.5" stroke-dasharray="4,3" opacity="0.7"/>`;
  out+=`<rect x="${ax-18}" y="${pad.t-18}" width="36" height="16" rx="4" fill="#3b82f6" opacity="0.15"/>`;
  out+=`<text x="${ax}" y="${pad.t-6}" text-anchor="middle" font-size="9" fill="#60a5fa" font-weight="600">4y ◀ YOU</text>`;

  // lines
  Object.entries(fuelGroups).forEach(([fname, pts])=>{
    const col=colors[fname]||'#fff';
    const isPetrol=fname==='Petrol (E20)';
    const pts2=pts.map(p=>({
      x:pad.l+cw*(p.y/maxAge),
      y:pad.t+ch*(1-p.v/maxV),
      v:p.v, yr:p.y
    }));
    // fill area
    const fpath=`M${pts2[0].x},${pad.t+ch} `+pts2.map(p=>`L${p.x},${p.y}`).join(' ')+` L${pts2[pts2.length-1].x},${pad.t+ch} Z`;
    out+=`<path d="${fpath}" fill="${col}" opacity="0.04"/>`;
    // line
    const lpath=`M${pts2[0].x},${pts2[0].y} `+pts2.slice(1).map(p=>`L${p.x},${p.y}`).join(' ');
    out+=`<path d="${lpath}" fill="none" stroke="${col}" stroke-width="${isPetrol?2.5:1.5}" opacity="${isPetrol?1:0.65}" stroke-linecap="round" stroke-linejoin="round"/>`;
    // dots
    pts2.forEach(p=>{
      out+=`<circle cx="${p.x}" cy="${p.y}" r="${isPetrol?5:3.5}" fill="${col}" opacity="${isPetrol?1:0.75}" class="line-dot" data-name="${fname}" data-y="${p.yr}" data-v="${p.v.toFixed(2)}" style="cursor:pointer"/>`;
    });
    // label at last point
    const lp=pts2[pts2.length-1];
    out+=`<text x="${lp.x+6}" y="${lp.y+4}" font-size="9" fill="${col}" font-weight="${isPetrol?700:400}" opacity="${isPetrol?1:0.8}">${fname==='Electric (EV)'?'EV':fname.replace(' (Flex-Fuel)','').replace(' (E20)','')}</text>`;
  });

  // X label
  out+=`<text x="${pad.l+cw/2}" y="${H-4}" text-anchor="middle" font-size="10" fill="#64748b">Vehicle Age (years)</text>`;

  svg.innerHTML=out;
  svg.querySelectorAll('.line-dot').forEach(el=>{
    el.addEventListener('mouseenter',e=>showTip(e,`<b>${el.dataset.name}</b><br>Age: ${el.dataset.y}y<br>Cost/km: <span style="color:#f59e0b">₹${el.dataset.v}</span>`));
    el.addEventListener('mousemove',moveTip);
    el.addEventListener('mouseleave',hideTip);
  });
}

// ── GAUGE ─────────────────────────────────────────────────────────────────────
function drawGauge(score) {
  const svg = document.getElementById('gaugeChart');
  const cx=100, cy=110, r=80;
  const startA=Math.PI, endA=2*Math.PI;
  const fillA=startA+(endA-startA)*(score/10);

  const sx=cx+r*Math.cos(startA), sy=cy+r*Math.sin(startA);
  const ex=cx+r*Math.cos(endA), ey=cy+r*Math.sin(endA);
  const fx=cx+r*Math.cos(fillA), fy=cy+r*Math.sin(fillA);
  const lg=fillA-startA>Math.PI?1:0;

  // inner ring radii
  const ir=62;
  const isx=cx+ir*Math.cos(startA), isy=cy+ir*Math.sin(startA);
  const iex=cx+ir*Math.cos(endA), iey=cy+ir*Math.sin(endA);
  const ifx=cx+ir*Math.cos(fillA), ify=cy+ir*Math.sin(fillA);

  const bgPath=`M${sx},${sy} A${r},${r} 0 1 1 ${ex},${ey} L${iex},${iey} A${ir},${ir} 0 1 0 ${isx},${isy} Z`;
  const fillPath=`M${sx},${sy} A${r},${r} 0 ${lg} 1 ${fx},${fy} L${ifx},${ify} A${ir},${ir} 0 ${lg} 0 ${isx},${isy} Z`;

  svg.innerHTML=`
    <defs>
      <linearGradient id="gaugeGrad" x1="0" y1="0" x2="1" y2="0">
        <stop offset="0%" stop-color="#ef4444"/>
        <stop offset="50%" stop-color="#f59e0b"/>
        <stop offset="100%" stop-color="#22c55e"/>
      </linearGradient>
    </defs>
    <path d="${bgPath}" fill="rgba(255,255,255,0.04)" stroke="rgba(255,255,255,0.06)" stroke-width="1"/>
    <path d="${fillPath}" fill="url(#gaugeGrad)" opacity="0.9"/>
    <text x="${cx}" y="${cy-10}" text-anchor="middle" font-size="9" fill="#64748b">0</text>
    <text x="${cx-r-8}" y="${cy+4}" text-anchor="end" font-size="9" fill="#64748b">0</text>
    <text x="${cx+r+8}" y="${cy+4}" font-size="9" fill="#64748b">10</text>
  `;

  // Animate score counter
  let current=0;
  const steps=60, dur=1200;
  const interval=setInterval(()=>{
    current+=score/steps;
    if(current>=score){current=score;clearInterval(interval);}
    document.getElementById('gaugeScore').textContent=current.toFixed(1);
  },dur/steps);

  // Animate score bars
  setTimeout(()=>{
    document.getElementById('sb-cost').style.width='0%';
    document.getElementById('sb-co2').style.width='100%';
    document.getElementById('sb-refuel').style.width='75%';
    document.getElementById('sb-maint').style.width='75%';
  },300);
}

// ── PARADOX BAR ───────────────────────────────────────────────────────────────
function drawParadox() {
  const svg = document.getElementById('paradoxBar');
  const W=520, H=100, pad={l:110,r:30,t:10,b:10};
  const cw=W-pad.l-pad.r, ch=H-pad.t-pad.b;

  const items=[
    {label:'Pump Saving', val:18.0, max:30, color:'#22c55e', fmt:'-18.0%'},
    {label:'Running Penalty', val:3.6, max:30, color:'#ef4444', fmt:'+3.6%'},
    {label:'Break-even', val:79.11, max:120, color:'#f59e0b', fmt:'₹79.11/L'},
  ];
  const rowH=ch/items.length;

  let out=`<rect width="${W}" height="${H}" fill="none"/>`;
  items.forEach((it,i)=>{
    const y=pad.t+i*rowH;
    const bw=cw*(it.val/it.max);
    out+=`<text x="${pad.l-8}" y="${y+rowH/2+4}" text-anchor="end" font-size="10" fill="#94a3b8">${it.label}</text>`;
    out+=`<rect x="${pad.l}" y="${y+rowH*0.2}" width="${cw}" height="${rowH*0.6}" rx="3" fill="rgba(255,255,255,0.04)"/>`;
    out+=`<rect x="${pad.l}" y="${y+rowH*0.2}" width="${bw}" height="${rowH*0.6}" rx="3" fill="${it.color}" opacity="0.8"/>`;
    out+=`<text x="${pad.l+bw+6}" y="${y+rowH/2+4}" font-size="10" fill="${it.color}" font-weight="600">${it.fmt}</text>`;
  });
  svg.innerHTML=out;
}

// ── FUEL CARDS ────────────────────────────────────────────────────────────────
function buildFuelCards() {
  const container=document.getElementById('fuelCards');
  FUELS.forEach(f=>{
    const isPetrol=f.name==='Petrol (E20)';
    const div=document.createElement('div');
    div.className=`fuel-card${isPetrol?' petrol-glow':''}`;
    div.innerHTML=`
      <div class="fuel-name">
        <div class="fuel-dot" style="background:${f.color};box-shadow:0 0 6px ${f.color}"></div>
        <span style="color:${f.color}">${f.name}${isPetrol?' ⭐':''}</span>
      </div>
      <div class="fuel-stats">
        <div class="fuel-stat">
          <div class="fuel-stat-label">COST/KM</div>
          <div class="fuel-stat-val" style="color:${f.color}">₹${f.cost.toFixed(2)}</div>
        </div>
        <div class="fuel-stat">
          <div class="fuel-stat-label">CO₂/KM</div>
          <div class="fuel-stat-val">${f.co2.toFixed(4)} kg</div>
        </div>
        <div class="fuel-stat">
          <div class="fuel-stat-label">MAINT/KM</div>
          <div class="fuel-stat-val">₹${f.maint.toFixed(2)}</div>
        </div>
        <div class="fuel-stat">
          <div class="fuel-stat-label">REFUEL TIME</div>
          <div class="fuel-stat-val">${f.refuel} min</div>
        </div>
      </div>
      <div class="fuel-pros">${f.pros.map(p=>`<div>${p}</div>`).join('')}</div>
      <div class="fuel-cons">${f.cons.map(c=>`<div>${c}</div>`).join('')}</div>
      <div class="fuel-best">${f.best}</div>
    `;
    container.appendChild(div);
  });
}

// ── INIT ──────────────────────────────────────────────────────────────────────
window.addEventListener('DOMContentLoaded',()=>{
  drawBar();
  drawDonut();
  drawLine();
  drawGauge(5.25);
  drawParadox();
  buildFuelCards();
});
</script>
</body>
</html>


---

# Dashboard Screenshots

## Dashboard Home

<img width="806" height="416" alt="Screenshot1" src="https://github.com/user-attachments/assets/2b299b98-4dfd-446a-a2d4-f3282e37b3f4" />



## Fuel Cost Analysis

<img width="683" height="434" alt="Screenshot2" src="https://github.com/user-attachments/assets/3578b368-c2a7-4661-8881-43b4b14deea6" />



## Cost Comparison Charts

<img width="1620" height="2094" alt="Screenshot4" src="https://github.com/user-attachments/assets/cd4d0c95-2a50-4099-9121-1630735a3174" />


---

# Key Analysis Findings

## Fuel Expenses

- Monthly fuel spending identified from CSV data.
- Annual fuel expenditure projected using average usage.

## Cost Per Kilometer

- Dashboard calculated operating cost per KM.
- Useful for comparing vehicle efficiency over time.

## Maintenance Insights

- Maintenance expenses visualized separately from fuel costs.
- Helped identify recurring vehicle ownership costs.

## Environmental Analysis

- Estimated emissions impact based on fuel usage.
- Provided sustainability-related insights.

## Business Intelligence Value

- Raw CSV converted into actionable insights.
- Metrics presented through visual dashboards.
- Suitable for reporting and decision making.

---

# Learnings

### 1. CSV Analytics
Learned how AI can process structured datasets automatically.

### 2. Dashboard Generation
Generated a complete interactive HTML dashboard without manual coding.

### 3. KPI Design
Understood how key business metrics are displayed using dashboard cards.

### 4. Data Visualization
Learned the importance of charts and visual reporting for decision making.

### 5. Real-World Analytics Workflow
Experienced a workflow similar to business intelligence and consulting projects.


---

# Conclusion

This exercise demonstrated how AI can transform CSV data into a professional analytics dashboard by automatically calculating metrics, generating visualizations, and presenting actionable insights through an HTML application.
