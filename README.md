# Fitness-
Genral
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>92kg to 67kg | Cut Tracker</title>
  <style>
    :root {
      --bg: #090d16;
      --card: #131b2e;
      --card-inner: #1c2640;
      --accent: #38bdf8;
      --accent-green: #34d399;
      --accent-purple: #a78bfa;
      --text: #f8fafc;
      --text-muted: #94a3b8;
      --border: #23304d;
    }
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; }
    body { background: var(--bg); color: var(--text); padding: 16px; max-width: 600px; margin: auto; padding-bottom: 60px; }
    
    /* Header */
    header { background: linear-gradient(135deg, #1e293b, #0f172a); border: 1px solid var(--border); border-radius: 16px; padding: 18px; margin-bottom: 18px; display: flex; justify-content: space-between; align-items: center; }
    h1 { font-size: 1.25rem; font-weight: 800; color: #fff; }
    .header-sub { font-size: 0.75rem; color: var(--text-muted); margin-top: 2px; }
    .badge { background: rgba(52, 211, 153, 0.15); color: var(--accent-green); border: 1px solid var(--accent-green); padding: 4px 10px; border-radius: 20px; font-weight: 700; font-size: 0.8rem; text-align: center; }

    /* Cards */
    .card { background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 18px; margin-bottom: 18px; }
    .card-title { font-size: 1rem; font-weight: 700; margin-bottom: 12px; display: flex; justify-content: space-between; align-items: center; }
    
    /* Inputs */
    label { display: block; font-size: 0.8rem; color: var(--text-muted); margin-bottom: 4px; font-weight: 600; }
    .input-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
    input[type="number"] {
      width: 100%; background: var(--bg); border: 1px solid var(--border);
      color: #fff; padding: 10px 12px; border-radius: 8px; font-size: 0.95rem; margin-bottom: 12px; outline: none;
    }
    input[type="number"]:focus { border-color: var(--accent); }
    .btn-save {
      background: var(--accent); color: #090d16; border: none; padding: 12px;
      font-weight: 700; border-radius: 8px; cursor: pointer; width: 100%; font-size: 0.95rem; transition: transform 0.1s;
    }
    .btn-save:active { transform: scale(0.98); }

    /* Interactive Checklist */
    .checklist-item {
      display: flex; align-items: center; background: var(--card-inner);
      padding: 12px; border-radius: 10px; margin-bottom: 8px; cursor: pointer;
      user-select: none; transition: background 0.2s;
    }
    .checklist-item input[type="checkbox"] { width: 18px; height: 18px; margin-right: 12px; accent-color: var(--accent-green); cursor: pointer; }
    .checklist-text { font-size: 0.85rem; font-weight: 600; }
    .checked { text-decoration: line-through; color: var(--text-muted); }

    /* Workout Tabs */
    .day-selector { display: flex; gap: 6px; overflow-x: auto; padding-bottom: 8px; margin-bottom: 14px; }
    .day-btn {
      background: var(--card-inner); border: 1px solid var(--border); color: var(--text-muted);
      padding: 6px 12px; border-radius: 8px; font-size: 0.75rem; font-weight: 700; white-space: nowrap; cursor: pointer;
    }
    .day-btn.active { background: var(--accent); color: #090d16; border-color: var(--accent); }
    .exercise-box { background: var(--card-inner); border-radius: 10px; padding: 12px; margin-bottom: 8px; display: flex; justify-content: space-between; align-items: center; }
    .ex-name { font-weight: 600; font-size: 0.85rem; color: #fff; }
    .ex-reps { font-size: 0.75rem; color: var(--text-muted); margin-top: 2px; }
    .video-tag { background: rgba(56, 189, 248, 0.15); color: var(--accent); text-decoration: none; font-size: 0.75rem; padding: 4px 8px; border-radius: 6px; font-weight: 600; }

    /* History Table */
    .history-table { width: 100%; border-collapse: collapse; font-size: 0.8rem; margin-top: 8px; }
    .history-table th { color: var(--text-muted); text-align: left; padding: 8px; border-bottom: 1px solid var(--border); }
    .history-table td { padding: 10px 8px; border-bottom: 1px solid var(--border); }
  </style>
</head>
<body>

  <!-- Header -->
  <header>
    <div>
      <h1>Target: 67 kg Cut</h1>
      <div class="header-sub">Start: 92 kg | Goal: -25 kg</div>
    </div>
    <div class="badge">1,800 kcal Cap</div>
  </header>

  <!-- Daily Non-Negotiables Checklist -->
  <div class="card">
    <div class="card-title">
      <span>Daily Non-Negotiables</span>
      <span id="check-counter" style="font-size:0.8rem; color:var(--accent-green);">0/5 Done</span>
    </div>
    <div class="checklist-item" onclick="toggleCheck('chk1')">
      <input type="checkbox" id="chk1" onclick="event.stopPropagation(); updateCounter();">
      <span class="checklist-text" id="t-chk1">Morning 30-min walk (~3,500 steps)</span>
    </div>
    <div class="checklist-item" onclick="toggleCheck('chk2')">
      <input type="checkbox" id="chk2" onclick="event.stopPropagation(); updateCounter();">
      <span class="checklist-text" id="t-chk2">Evening 30-min walk (~3,500 steps)</span>
    </div>
    <div class="checklist-item" onclick="toggleCheck('chk3')">
      <input type="checkbox" id="chk3" onclick="event.stopPropagation(); updateCounter();">
      <span class="checklist-text" id="t-chk3">Hit ≥ 140g protein (paneer / soy / whey)</span>
    </div>
    <div class="checklist-item" onclick="toggleCheck('chk4')">
      <input type="checkbox" id="chk4" onclick="event.stopPropagation(); updateCounter();">
      <span class="checklist-text" id="t-chk4">Cooking oil strictly ≤ 1.5 tbsp total</span>
    </div>
    <div class="checklist-item" onclick="toggleCheck('chk5')">
      <input type="checkbox" id="chk5" onclick="event.stopPropagation(); updateCounter();">
      <span class="checklist-text" id="t-chk5">Drank 3.5 – 4.0 Liters of water</span>
    </div>
  </div>

  <!-- Interactive Workout Plan -->
  <div class="card">
    <div class="card-title">Week 1 Movement Plan</div>
    <div class="day-selector">
      <button class="day-btn active" onclick="loadDay(1)">Day 1 (Push/Pull)</button>
      <button class="day-btn" onclick="loadDay(2)">Day 2 (Legs/Core)</button>
      <button class="day-btn" onclick="loadDay(3)">Day 3 (Rest)</button>
      <button class="day-btn" onclick="loadDay(4)">Day 4 (Shoulders)</button>
      <button class="day-btn" onclick="loadDay(5)">Day 5 (Legs 2)</button>
      <button class="day-btn" onclick="loadDay(6)">Day 6 (Active Rest)</button>
      <button class="day-btn" onclick="loadDay(7)">Day 7 (Review)</button>
    </div>
    <div id="workout-content">
      <!-- Injected via JavaScript -->
    </div>
  </div>

  <!-- Metric Logger -->
  <div class="card">
    <div class="card-title">Log Today's Numbers</div>
    <div class="input-grid">
      <div>
        <label>Morning Weight (kg)</label>
        <input type="number" step="0.1" id="in-weight" placeholder="92.0" />
      </div>
      <div>
        <label>Fire-Boltt Steps</label>
        <input type="number" id="in-steps" placeholder="Target 10k" />
      </div>
    </div>
    <div class="input-grid">
      <div>
        <label>Calories (kcal)</label>
        <input type="number" id="in-calories" placeholder="Max 1850" />
      </div>
      <div>
        <label>Protein (g)</label>
        <input type="number" id="in-protein" placeholder="Target 140g" />
      </div>
    </div>
    <button class="btn-save" onclick="saveDailyLog()">Save Daily Entry</button>
  </div>

  <!-- History Log -->
  <div class="card">
    <div class="card-title">Recent Logs</div>
    <table class="history-table">
      <thead>
        <tr>
          <th>Date</th>
          <th>Weight</th>
          <th>Steps</th>
          <th>Calories</th>
          <th>Protein</th>
        </tr>
      </thead>
      <tbody id="history-rows"></tbody>
    </table>
  </div>

  <script>
    // Routine Data
    const workouts = {
      1: [
        { name: "Incline / Knee Push-Ups", reps: "3 sets × 8–12 reps", query: "push+up+proper+form" },
        { name: "Doorframe / Towel Row", reps: "3 sets × 10–12 reps", query: "doorframe+bodyweight+row" },
        { name: "Chair Tricep Dips", reps: "3 sets × 8–10 reps", query: "chair+tricep+dips+form" },
        { name: "Prone Cobra / Superman", reps: "3 sets × 10 reps (2s hold)", query: "prone+cobra+exercise" },
        { name: "Forearm Plank", reps: "3 sets × 30-sec hold", query: "forearm+plank+form" }
      ],
      2: [
        { name: "Bulgarian Split Squats", reps: "3 sets × 6–8 reps/leg", query: "bulgarian+split+squat+form" },
        { name: "Bodyweight Squats (Slow Tempo)", reps: "3 sets × 12 reps", query: "bodyweight+squat+tempo" },
        { name: "Single-Leg Glute Bridge", reps: "3 sets × 10 reps/leg", query: "single+leg+glute+bridge" },
        { name: "Calf Raises on a Step", reps: "3 sets × 15 reps", query: "standing+calf+raise" },
        { name: "Deadbugs / Knee Tucks", reps: "3 sets × 10 reps/side", query: "deadbug+exercise+form" }
      ],
      3: [
        { name: "10,000 Step Walk Outside", reps: "Continuous pacing", query: "walking+for+fat+loss" },
        { name: "Hamstring & Hip Mobility", reps: "10 mins stretching", query: "lower+body+stretching+routine" }
      ],
      4: [
        { name: "Pike Push-Ups", reps: "3 sets × 6–8 reps", query: "pike+push+up+form" },
        { name: "Backpack Bent-Over Row", reps: "3 sets × 10–12 reps", query: "backpack+bent+over+row" },
        { name: "Diamond Push-Ups (or Close Grip)", reps: "3 sets × 6–8 reps", query: "diamond+push+up+form" },
        { name: "Backpack Bicep Curls", reps: "3 sets × 12 reps", query: "bicep+curl+form" },
        { name: "Side Plank", reps: "2 sets × 20–30s/side", query: "side+plank+form" }
      ],
      5: [
        { name: "Reverse Lunges", reps: "3 sets × 10 reps/leg", query: "reverse+lunge+form" },
        { name: "Backpack Romanian Deadlift", reps: "3 sets × 10–12 reps", query: "romanian+deadlift+with+backpack" },
        { name: "Wall Sit", reps: "3 sets × 30–45 sec hold", query: "wall+sit+exercise" },
        { name: "Standing Calf Raises", reps: "3 sets × 12 reps/leg", query: "single+leg+calf+raise" },
        { name: "Slow Bicycle Crunches", reps: "3 sets × 15 slow reps", query: "bicycle+crunches+proper+form" }
      ],
      6: [
        { name: "Active Recovery Walk", reps: "10,000 steps baseline", query: "neat+steps+weight+loss" },
        { name: "Chest & Shoulder Doorway Stretch", reps: "5–10 minutes", query: "doorway+chest+stretch" }
      ],
      7: [
        { name: "Weekly Weigh-In Average Review", reps: "Calculate 7-day mean", query: "how+to+calculate+weekly+average+weight" },
        { name: "Meal Prep High-Protein Staples", reps: "Boil soy / portion paneer", query: "high+protein+vegetarian+meal+prep" }
      ]
    };

    function loadDay(dayNum) {
      document.querySelectorAll('.day-btn').forEach((btn, idx) => {
        btn.classList.toggle('active', idx + 1 === dayNum);
      });
      const exercises = workouts[dayNum];
      const container = document.getElementById('workout-content');
      container.innerHTML = exercises.map(ex => `
        <div class="exercise-box">
          <div>
            <div class="ex-name">${ex.name}</div>
            <div class="ex-reps">${ex.reps}</div>
          </div>
          <a class="video-tag" href="https://www.youtube.com/results?search_query=${ex.query}" target="_blank">Watch ↗</a>
        </div>
      `).join('');
    }

    // Checklist toggles
    function toggleCheck(id) {
      const chk = document.getElementById(id);
      chk.checked = !chk.checked;
      updateCounter();
    }

    function updateCounter() {
      let count = 0;
      ['chk1','chk2','chk3','chk4','chk5'].forEach(id => {
        const isDone = document.getElementById(id).checked;
        document.getElementById('t-' + id).classList.toggle('checked', isDone);
        if (isDone) count++;
      });
      document.getElementById('check-counter').textContent = `${count}/5 Done`;
      localStorage.setItem('daily_checklist', JSON.stringify({
        date: new Date().toLocaleDateString(),
        chk1: document.getElementById('chk1').checked,
        chk2: document.getElementById('chk2').checked,
        chk3: document.getElementById('chk3').checked,
        chk4: document.getElementById('chk4').checked,
        chk5: document.getElementById('chk5').checked
      }));
    }

    function loadChecklistState() {
      const saved = JSON.parse(localStorage.getItem('daily_checklist') || '{}');
      if (saved.date === new Date().toLocaleDateString()) {
        ['chk1','chk2','chk3','chk4','chk5'].forEach(id => {
          if (saved[id]) document.getElementById(id).checked = true;
        });
        updateCounter();
      }
    }

    // Data Storage
    function getLogs() {
      return JSON.parse(localStorage.getItem('cut_logs') || '[]');
    }

    function saveDailyLog() {
      const weight = document.getElementById('in-weight').value;
      const steps = document.getElementById('in-steps').value;
      const calories = document.getElementById('in-calories').value;
      const protein = document.getElementById('in-protein').value;

      if (!weight && !steps && !calories && !protein) return alert('Enter at least one number.');

      const newEntry = {
        date: new Date().toLocaleDateString(),
        weight: weight || '--',
        steps: steps || '--',
        calories: calories || '--',
        protein: protein || '--'
      };

      const logs = getLogs();
      logs.unshift(newEntry);
      localStorage.setItem('cut_logs', JSON.stringify(logs.slice(0, 30)));
      renderHistory();

      document.getElementById('in-weight').value = '';
      document.getElementById('in-steps').value = '';
      document.getElementById('in-calories').value = '';
      document.getElementById('in-protein').value = '';
    }

    function renderHistory() {
      const logs = getLogs();
      const tbody = document.getElementById('history-rows');
      if (logs.length === 0) {
        tbody.innerHTML = '<tr><td colspan="5" style="color:var(--text-muted); text-align:center; padding:12px;">No logs recorded yet.</td></tr>';
        return;
      }
      tbody.innerHTML = logs.map(l => `
        <tr>
          <td>${l.date}</td>
          <td><strong>${l.weight}</strong> kg</td>
          <td>${l.steps}</td>
          <td>${l.calories}</td>
          <td>${l.protein}g</td>
        </tr>
      `).join('');
    }

    // Initialize
    loadDay(1);
    loadChecklistState();
    renderHistory();
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>92kg to 67kg | Cut Tracker</title>
  <style>
    :root {
      --bg: #090d16;
      --card: #131b2e;
      --card-inner: #1c2640;
      --accent: #38bdf8;
      --accent-green: #34d399;
      --accent-purple: #a78bfa;
      --text: #f8fafc;
      --text-muted: #94a3b8;
      --border: #23304d;
    }
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; }
    body { background: var(--bg); color: var(--text); padding: 16px; max-width: 600px; margin: auto; padding-bottom: 60px; }
    
    /* Header */
    header { background: linear-gradient(135deg, #1e293b, #0f172a); border: 1px solid var(--border); border-radius: 16px; padding: 18px; margin-bottom: 18px; display: flex; justify-content: space-between; align-items: center; }
    h1 { font-size: 1.25rem; font-weight: 800; color: #fff; }
    .header-sub { font-size: 0.75rem; color: var(--text-muted); margin-top: 2px; }
    .badge { background: rgba(52, 211, 153, 0.15); color: var(--accent-green); border: 1px solid var(--accent-green); padding: 4px 10px; border-radius: 20px; font-weight: 700; font-size: 0.8rem; text-align: center; }

    /* Cards */
    .card { background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 18px; margin-bottom: 18px; }
    .card-title { font-size: 1rem; font-weight: 700; margin-bottom: 12px; display: flex; justify-content: space-between; align-items: center; }
    
    /* Inputs */
    label { display: block; font-size: 0.8rem; color: var(--text-muted); margin-bottom: 4px; font-weight: 600; }
    .input-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
    input[type="number"] {
      width: 100%; background: var(--bg); border: 1px solid var(--border);
      color: #fff; padding: 10px 12px; border-radius: 8px; font-size: 0.95rem; margin-bottom: 12px; outline: none;
    }
    input[type="number"]:focus { border-color: var(--accent); }
    .btn-save {
      background: var(--accent); color: #090d16; border: none; padding: 12px;
      font-weight: 700; border-radius: 8px; cursor: pointer; width: 100%; font-size: 0.95rem; transition: transform 0.1s;
    }
    .btn-save:active { transform: scale(0.98); }

    /* Interactive Checklist */
    .checklist-item {
      display: flex; align-items: center; background: var(--card-inner);
      padding: 12px; border-radius: 10px; margin-bottom: 8px; cursor: pointer;
      user-select: none; transition: background 0.2s;
    }
    .checklist-item input[type="checkbox"] { width: 18px; height: 18px; margin-right: 12px; accent-color: var(--accent-green); cursor: pointer; }
    .checklist-text { font-size: 0.85rem; font-weight: 600; }
    .checked { text-decoration: line-through; color: var(--text-muted); }

    /* Workout Tabs */
    .day-selector { display: flex; gap: 6px; overflow-x: auto; padding-bottom: 8px; margin-bottom: 14px; }
    .day-btn {
      background: var(--card-inner); border: 1px solid var(--border); color: var(--text-muted);
      padding: 6px 12px; border-radius: 8px; font-size: 0.75rem; font-weight: 700; white-space: nowrap; cursor: pointer;
    }
    .day-btn.active { background: var(--accent); color: #090d16; border-color: var(--accent); }
    .exercise-box { background: var(--card-inner); border-radius: 10px; padding: 12px; margin-bottom: 8px; display: flex; justify-content: space-between; align-items: center; }
    .ex-name { font-weight: 600; font-size: 0.85rem; color: #fff; }
    .ex-reps { font-size: 0.75rem; color: var(--text-muted); margin-top: 2px; }
    .video-tag { background: rgba(56, 189, 248, 0.15); color: var(--accent); text-decoration: none; font-size: 0.75rem; padding: 4px 8px; border-radius: 6px; font-weight: 600; }

    /* History Table */
    .history-table { width: 100%; border-collapse: collapse; font-size: 0.8rem; margin-top: 8px; }
    .history-table th { color: var(--text-muted); text-align: left; padding: 8px; border-bottom: 1px solid var(--border); }
    .history-table td { padding: 10px 8px; border-bottom: 1px solid var(--border); }
  </style>
</head>
<body>

  <!-- Header -->
  <header>
    <div>
      <h1>Target: 67 kg Cut</h1>
      <div class="header-sub">Start: 92 kg | Goal: -25 kg</div>
    </div>
    <div class="badge">1,800 kcal Cap</div>
  </header>

  <!-- Daily Non-Negotiables Checklist -->
  <div class="card">
    <div class="card-title">
      <span>Daily Non-Negotiables</span>
      <span id="check-counter" style="font-size:0.8rem; color:var(--accent-green);">0/5 Done</span>
    </div>
    <div class="checklist-item" onclick="toggleCheck('chk1')">
      <input type="checkbox" id="chk1" onclick="event.stopPropagation(); updateCounter();">
      <span class="checklist-text" id="t-chk1">Morning 30-min walk (~3,500 steps)</span>
    </div>
    <div class="checklist-item" onclick="toggleCheck('chk2')">
      <input type="checkbox" id="chk2" onclick="event.stopPropagation(); updateCounter();">
      <span class="checklist-text" id="t-chk2">Evening 30-min walk (~3,500 steps)</span>
    </div>
    <div class="checklist-item" onclick="toggleCheck('chk3')">
      <input type="checkbox" id="chk3" onclick="event.stopPropagation(); updateCounter();">
      <span class="checklist-text" id="t-chk3">Hit ≥ 140g protein (paneer / soy / whey)</span>
    </div>
    <div class="checklist-item" onclick="toggleCheck('chk4')">
      <input type="checkbox" id="chk4" onclick="event.stopPropagation(); updateCounter();">
      <span class="checklist-text" id="t-chk4">Cooking oil strictly ≤ 1.5 tbsp total</span>
    </div>
    <div class="checklist-item" onclick="toggleCheck('chk5')">
      <input type="checkbox" id="chk5" onclick="event.stopPropagation(); updateCounter();">
      <span class="checklist-text" id="t-chk5">Drank 3.5 – 4.0 Liters of water</span>
    </div>
  </div>

  <!-- Interactive Workout Plan -->
  <div class="card">
    <div class="card-title">Week 1 Movement Plan</div>
    <div class="day-selector">
      <button class="day-btn active" onclick="loadDay(1)">Day 1 (Push/Pull)</button>
      <button class="day-btn" onclick="loadDay(2)">Day 2 (Legs/Core)</button>
      <button class="day-btn" onclick="loadDay(3)">Day 3 (Rest)</button>
      <button class="day-btn" onclick="loadDay(4)">Day 4 (Shoulders)</button>
      <button class="day-btn" onclick="loadDay(5)">Day 5 (Legs 2)</button>
      <button class="day-btn" onclick="loadDay(6)">Day 6 (Active Rest)</button>
      <button class="day-btn" onclick="loadDay(7)">Day 7 (Review)</button>
    </div>
    <div id="workout-content">
      <!-- Injected via JavaScript -->
    </div>
  </div>

  <!-- Metric Logger -->
  <div class="card">
    <div class="card-title">Log Today's Numbers</div>
    <div class="input-grid">
      <div>
        <label>Morning Weight (kg)</label>
        <input type="number" step="0.1" id="in-weight" placeholder="92.0" />
      </div>
      <div>
        <label>Fire-Boltt Steps</label>
        <input type="number" id="in-steps" placeholder="Target 10k" />
      </div>
    </div>
    <div class="input-grid">
      <div>
        <label>Calories (kcal)</label>
        <input type="number" id="in-calories" placeholder="Max 1850" />
      </div>
      <div>
        <label>Protein (g)</label>
        <input type="number" id="in-protein" placeholder="Target 140g" />
      </div>
    </div>
    <button class="btn-save" onclick="saveDailyLog()">Save Daily Entry</button>
  </div>

  <!-- History Log -->
  <div class="card">
    <div class="card-title">Recent Logs</div>
    <table class="history-table">
      <thead>
        <tr>
          <th>Date</th>
          <th>Weight</th>
          <th>Steps</th>
          <th>Calories</th>
          <th>Protein</th>
        </tr>
      </thead>
      <tbody id="history-rows"></tbody>
    </table>
  </div>

  <script>
    // Routine Data
    const workouts = {
      1: [
        { name: "Incline / Knee Push-Ups", reps: "3 sets × 8–12 reps", query: "push+up+proper+form" },
        { name: "Doorframe / Towel Row", reps: "3 sets × 10–12 reps", query: "doorframe+bodyweight+row" },
        { name: "Chair Tricep Dips", reps: "3 sets × 8–10 reps", query: "chair+tricep+dips+form" },
        { name: "Prone Cobra / Superman", reps: "3 sets × 10 reps (2s hold)", query: "prone+cobra+exercise" },
        { name: "Forearm Plank", reps: "3 sets × 30-sec hold", query: "forearm+plank+form" }
      ],
      2: [
        { name: "Bulgarian Split Squats", reps: "3 sets × 6–8 reps/leg", query: "bulgarian+split+squat+form" },
        { name: "Bodyweight Squats (Slow Tempo)", reps: "3 sets × 12 reps", query: "bodyweight+squat+tempo" },
        { name: "Single-Leg Glute Bridge", reps: "3 sets × 10 reps/leg", query: "single+leg+glute+bridge" },
        { name: "Calf Raises on a Step", reps: "3 sets × 15 reps", query: "standing+calf+raise" },
        { name: "Deadbugs / Knee Tucks", reps: "3 sets × 10 reps/side", query: "deadbug+exercise+form" }
      ],
      3: [
        { name: "10,000 Step Walk Outside", reps: "Continuous pacing", query: "walking+for+fat+loss" },
        { name: "Hamstring & Hip Mobility", reps: "10 mins stretching", query: "lower+body+stretching+routine" }
      ],
      4: [
        { name: "Pike Push-Ups", reps: "3 sets × 6–8 reps", query: "pike+push+up+form" },
        { name: "Backpack Bent-Over Row", reps: "3 sets × 10–12 reps", query: "backpack+bent+over+row" },
        { name: "Diamond Push-Ups (or Close Grip)", reps: "3 sets × 6–8 reps", query: "diamond+push+up+form" },
        { name: "Backpack Bicep Curls", reps: "3 sets × 12 reps", query: "bicep+curl+form" },
        { name: "Side Plank", reps: "2 sets × 20–30s/side", query: "side+plank+form" }
      ],
      5: [
        { name: "Reverse Lunges", reps: "3 sets × 10 reps/leg", query: "reverse+lunge+form" },
        { name: "Backpack Romanian Deadlift", reps: "3 sets × 10–12 reps", query: "romanian+deadlift+with+backpack" },
        { name: "Wall Sit", reps: "3 sets × 30–45 sec hold", query: "wall+sit+exercise" },
        { name: "Standing Calf Raises", reps: "3 sets × 12 reps/leg", query: "single+leg+calf+raise" },
        { name: "Slow Bicycle Crunches", reps: "3 sets × 15 slow reps", query: "bicycle+crunches+proper+form" }
      ],
      6: [
        { name: "Active Recovery Walk", reps: "10,000 steps baseline", query: "neat+steps+weight+loss" },
        { name: "Chest & Shoulder Doorway Stretch", reps: "5–10 minutes", query: "doorway+chest+stretch" }
      ],
      7: [
        { name: "Weekly Weigh-In Average Review", reps: "Calculate 7-day mean", query: "how+to+calculate+weekly+average+weight" },
        { name: "Meal Prep High-Protein Staples", reps: "Boil soy / portion paneer", query: "high+protein+vegetarian+meal+prep" }
      ]
    };

    function loadDay(dayNum) {
      document.querySelectorAll('.day-btn').forEach((btn, idx) => {
        btn.classList.toggle('active', idx + 1 === dayNum);
      });
      const exercises = workouts[dayNum];
      const container = document.getElementById('workout-content');
      container.innerHTML = exercises.map(ex => `
        <div class="exercise-box">
          <div>
            <div class="ex-name">${ex.name}</div>
            <div class="ex-reps">${ex.reps}</div>
          </div>
          <a class="video-tag" href="https://www.youtube.com/results?search_query=${ex.query}" target="_blank">Watch ↗</a>
        </div>
      `).join('');
    }

    // Checklist toggles
    function toggleCheck(id) {
      const chk = document.getElementById(id);
      chk.checked = !chk.checked;
      updateCounter();
    }

    function updateCounter() {
      let count = 0;
      ['chk1','chk2','chk3','chk4','chk5'].forEach(id => {
        const isDone = document.getElementById(id).checked;
        document.getElementById('t-' + id).classList.toggle('checked', isDone);
        if (isDone) count++;
      });
      document.getElementById('check-counter').textContent = `${count}/5 Done`;
      localStorage.setItem('daily_checklist', JSON.stringify({
        date: new Date().toLocaleDateString(),
        chk1: document.getElementById('chk1').checked,
        chk2: document.getElementById('chk2').checked,
        chk3: document.getElementById('chk3').checked,
        chk4: document.getElementById('chk4').checked,
        chk5: document.getElementById('chk5').checked
      }));
    }

    function loadChecklistState() {
      const saved = JSON.parse(localStorage.getItem('daily_checklist') || '{}');
      if (saved.date === new Date().toLocaleDateString()) {
        ['chk1','chk2','chk3','chk4','chk5'].forEach(id => {
          if (saved[id]) document.getElementById(id).checked = true;
        });
        updateCounter();
      }
    }

    // Data Storage
    function getLogs() {
      return JSON.parse(localStorage.getItem('cut_logs') || '[]');
    }

    function saveDailyLog() {
      const weight = document.getElementById('in-weight').value;
      const steps = document.getElementById('in-steps').value;
      const calories = document.getElementById('in-calories').value;
      const protein = document.getElementById('in-protein').value;

      if (!weight && !steps && !calories && !protein) return alert('Enter at least one number.');

      const newEntry = {
        date: new Date().toLocaleDateString(),
        weight: weight || '--',
        steps: steps || '--',
        calories: calories || '--',
        protein: protein || '--'
      };

      const logs = getLogs();
      logs.unshift(newEntry);
      localStorage.setItem('cut_logs', JSON.stringify(logs.slice(0, 30)));
      renderHistory();

      document.getElementById('in-weight').value = '';
      document.getElementById('in-steps').value = '';
      document.getElementById('in-calories').value = '';
      document.getElementById('in-protein').value = '';
    }

    function renderHistory() {
      const logs = getLogs();
      const tbody = document.getElementById('history-rows');
      if (logs.length === 0) {
        tbody.innerHTML = '<tr><td colspan="5" style="color:var(--text-muted); text-align:center; padding:12px;">No logs recorded yet.</td></tr>';
        return;
      }
      tbody.innerHTML = logs.map(l => `
        <tr>
          <td>${l.date}</td>
          <td><strong>${l.weight}</strong> kg</td>
          <td>${l.steps}</td>
          <td>${l.calories}</td>
          <td>${l.protein}g</td>
        </tr>
      `).join('');
    }

    // Initialize
    loadDay(1);
    loadChecklistState();
    renderHistory();
  </script>
</body>
</html>
