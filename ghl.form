<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Telex Online Examination</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body { font-family: Arial, sans-serif; background: #fff5f5; }

    /* GLOW BACKGROUND */
    .glow-bg {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      pointer-events: none;
      z-index: 0;
      overflow: hidden;
    }
    .glow-bg span {
      position: absolute;
      border-radius: 50%;
    }
    .glow-bg .g1 {
      width: 600px; height: 600px;
      background: radial-gradient(circle, rgba(210,50,50,0.18) 0%, transparent 70%);
      top: -150px; left: -100px;
    }
    .glow-bg .g2 {
      width: 500px; height: 500px;
      background: radial-gradient(circle, rgba(210,50,50,0.13) 0%, transparent 70%);
      top: 300px; right: -100px;
    }
    .glow-bg .g3 {
      width: 420px; height: 420px;
      background: radial-gradient(circle, rgba(210,50,50,0.10) 0%, transparent 70%);
      bottom: 100px; left: 30%;
    }

    .page-wrap { position: relative; z-index: 1; max-width: 860px; margin: 0 auto; padding: 0 0 60px; }

    /* HEADER */
    .exam-header {
      background: radial-gradient(ellipse at top left, #cc1a1a 0%, #8b0000 45%, #5a0000 100%);
      color: #fff;
      padding: 2rem 2rem 1.75rem;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    .exam-header::before {
      content: '';
      position: absolute;
      width: 420px; height: 420px;
      background: radial-gradient(circle, rgba(255,80,80,0.22) 0%, transparent 70%);
      top: -120px; left: -80px;
      border-radius: 50%;
    }
    .exam-header::after {
      content: '';
      position: absolute;
      width: 360px; height: 360px;
      background: radial-gradient(circle, rgba(255,60,60,0.16) 0%, transparent 70%);
      top: -80px; right: -60px;
      border-radius: 50%;
    }
    .logo-wrap {
      display: flex;
      justify-content: center;
      margin-bottom: 10px;
      position: relative;
      z-index: 1;
    }
    .logo-wrap img {
      height: 90px;
      object-fit: contain;
      filter: drop-shadow(0 0 14px rgba(255,255,255,0.45)) drop-shadow(0 0 28px rgba(255,100,100,0.4));
    }
    .exam-header h1 {
      font-size: 28px;
      font-weight: 700;
      color: #fff;
      position: relative;
      z-index: 1;
      margin-bottom: 6px;
    }
    .exam-header p {
      font-size: 13px;
      color: rgba(255,255,255,0.75);
      position: relative;
      z-index: 1;
      margin-bottom: 1.25rem;
    }
    .exam-meta {
      display: flex;
      justify-content: center;
      gap: 1rem;
      flex-wrap: wrap;
      position: relative;
      z-index: 1;
    }
    .meta-badge {
      background: rgba(0,0,0,0.25);
      border: 1px solid rgba(255,255,255,0.25);
      border-radius: 6px;
      padding: 8px 22px;
      font-size: 12px;
      color: rgba(255,255,255,0.85);
      min-width: 110px;
    }
    .meta-badge span {
      font-weight: 700;
      font-size: 16px;
      display: block;
      color: #fff;
      margin-top: 2px;
    }

    /* STUDENT INFO */
    .student-info {
      background: rgba(255,255,255,0.95);
      border-bottom: 2px solid #f0c0c0;
      padding: 1.25rem 2rem;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }
    .info-field label {
      font-size: 11px;
      font-weight: 700;
      color: #999;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      display: block;
      margin-bottom: 4px;
    }
    .info-field input {
      width: 100%;
      border: 1.5px solid #e8c4c4;
      border-radius: 6px;
      padding: 8px 10px;
      font-size: 13px;
      color: #222;
      background: #fff;
      outline: none;
      transition: border-color 0.2s;
    }
    .info-field input:focus {
      border-color: #b03020;
      box-shadow: 0 0 0 3px rgba(176,48,32,0.10);
    }

    /* QUESTIONS */
    .questions-area {
      padding: 1.5rem 2rem;
    }
    .section-header {
      background: linear-gradient(90deg, #b03020, #d94030);
      color: #fff;
      padding: 8px 16px;
      border-radius: 6px;
      font-size: 13px;
      font-weight: 700;
      margin-bottom: 1rem;
      display: flex;
      align-items: center;
      gap: 8px;
      box-shadow: 0 2px 12px rgba(176,48,32,0.28);
    }
    .section-dot {
      width: 8px; height: 8px;
      background: #fff;
      border-radius: 50%;
      flex-shrink: 0;
    }
    .question-card {
      background: rgba(255,255,255,0.92);
      border-radius: 8px;
      border-left: 4px solid #d94030;
      padding: 1rem 1.25rem;
      margin-bottom: 10px;
      border-top: 0.5px solid #f0c8c8;
      border-right: 0.5px solid #f0c8c8;
      border-bottom: 0.5px solid #f0c8c8;
      transition: box-shadow 0.2s;
    }
    .question-card:nth-child(even) { border-left-color: #8b2318; }
    .question-card:hover { box-shadow: 0 2px 16px rgba(176,48,32,0.13); }
    .q-header {
      display: flex;
      align-items: flex-start;
      gap: 10px;
      margin-bottom: 10px;
    }
    .q-num {
      background: #d94030;
      color: #fff;
      border-radius: 50%;
      width: 26px; height: 26px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 11px;
      font-weight: 700;
      flex-shrink: 0;
    }
    .question-card:nth-child(even) .q-num { background: #8b2318; }
    .q-text {
      font-size: 13px;
      color: #2c2c2c;
      line-height: 1.5;
      padding-top: 3px;
    }
    .options-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6px;
    }
    .option-label {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 7px 10px;
      border: 1.5px solid #f0d0d0;
      border-radius: 6px;
      cursor: pointer;
      font-size: 12px;
      color: #333;
      transition: all 0.15s;
      background: #fff;
    }
    .option-label:hover { border-color: #d94030; background: #fff5f5; color: #b03020; }
    .option-label input[type="radio"] { accent-color: #b03020; width: 14px; height: 14px; flex-shrink: 0; }
    .option-label:has(input:checked) { border-color: #b03020; background: #fff0f0; }

    /* FOOTER */
    .exam-footer {
      background: linear-gradient(135deg, #6e1c14 0%, #8b2318 50%, #b03020 100%);
      padding: 1.25rem 2rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      flex-wrap: wrap;
      border-top: 3px solid rgba(255,255,255,0.18);
      box-shadow: 0 -4px 20px rgba(176,48,32,0.25);
      position: sticky;
      bottom: 0;
      z-index: 10;
    }
    .score-display { color: #fff; font-size: 13px; }
    .score-display strong { font-size: 20px; color: #ffd5d5; }
    .progress-bar-wrap {
      background: rgba(255,255,255,0.2);
      border-radius: 4px;
      height: 5px;
      width: 180px;
      margin-top: 6px;
    }
    .progress-bar-fill {
      background: #fff;
      border-radius: 4px;
      height: 5px;
      transition: width 0.3s;
    }
    .btn-group { display: flex; gap: 10px; }
    .btn {
      padding: 10px 22px;
      border-radius: 6px;
      font-size: 13px;
      font-weight: 700;
      cursor: pointer;
      border: none;
      transition: all 0.15s;
    }
    .btn-clear {
      background: rgba(255,255,255,0.15);
      color: #fff;
      border: 1px solid rgba(255,255,255,0.35);
    }
    .btn-clear:hover { background: rgba(255,255,255,0.25); }
    .btn-submit { background: #fff; color: #b03020; }
    .btn-submit:hover { background: #fff0f0; }

    /* RESULT MODAL */
    .result-overlay {
      display: none;
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background: rgba(0,0,0,0.65);
      z-index: 999;
      align-items: center;
      justify-content: center;
    }
    .result-box {
      background: #fff;
      border-radius: 14px;
      padding: 2rem;
      text-align: center;
      max-width: 320px;
      width: 90%;
      border-top: 6px solid #b03020;
      box-shadow: 0 8px 40px rgba(176,48,32,0.3);
    }
    .result-box h2 { font-size: 18px; color: #6e1c14; margin-bottom: 6px; }
    .result-score { font-size: 52px; font-weight: 700; color: #b03020; line-height: 1; margin: 1rem 0; }
    .result-label { font-size: 13px; color: #666; }
    .result-grade { font-size: 16px; font-weight: 700; margin-top: 8px; }
    .btn-close {
      margin-top: 1.25rem;
      background: #b03020;
      color: #fff;
      padding: 10px 28px;
      border-radius: 6px;
      border: none;
      cursor: pointer;
      font-size: 13px;
      font-weight: 700;
    }
    .btn-close:hover { background: #8b2318; }

    @media (max-width: 600px) {
      .student-info { grid-template-columns: 1fr; }
      .options-grid { grid-template-columns: 1fr; }
      .exam-footer { flex-direction: column; align-items: flex-start; }
      .progress-bar-wrap { width: 100%; }
    }
  </style>
</head>
<body>

<!-- GLOW BACKGROUND -->
<div class="glow-bg">
  <span class="g1"></span>
  <span class="g2"></span>
  <span class="g3"></span>
</div>

<div class="page-wrap">

  <!-- HEADER -->
  <div class="exam-header">
    <div class="logo-wrap">
      <img src="https://assets.cdn.filesafe.space/KlBL9XEG0eVNlAqE7m5V/media/69a107efbee50595b5a1b6e4.png" alt="Telex Logo">
    </div>
    <h1>Online Examination</h1>
    <p>Read each question carefully and choose the best answer.</p>
    <div class="exam-meta">
      <div class="meta-badge">Total Items<span>50</span></div>
      <div class="meta-badge">Time Limit<span>60 min</span></div>
      <div class="meta-badge">Passing Score<span>75%</span></div>
    </div>
  </div>

  <!-- STUDENT INFO -->
  <div class="student-info">
    <div class="info-field">
      <label>Full Name</label>
      <input type="text" placeholder="Enter your full name">
    </div>
    <div class="info-field">
      <label>Student ID / Section</label>
      <input type="text" placeholder="e.g. 2024-00123 / Section A">
    </div>
    <div class="info-field">
      <label>Subject / Course</label>
      <input type="text" placeholder="e.g. General Science">
    </div>
    <div class="info-field">
      <label>Date</label>
      <input type="date" id="examDate">
    </div>
  </div>

  <!-- QUESTIONS -->
  <div class="questions-area">
    <div class="section-header">
      <div class="section-dot"></div>
      Multiple Choice — Choose the letter of the correct answer.
    </div>
    <div id="questionsList"></div>
  </div>

  <!-- FOOTER -->
  <div class="exam-footer">
    <div class="score-display">
      <div>Answered: <strong id="answeredCount">0</strong> / 50</div>
      <div class="progress-bar-wrap">
        <div class="progress-bar-fill" id="progressBar" style="width:0%"></div>
      </div>
    </div>
    <div class="btn-group">
      <button class="btn btn-clear" onclick="clearAll()">Clear All</button>
      <button class="btn btn-submit" onclick="submitExam()">Submit Exam</button>
    </div>
  </div>

</div>

<!-- RESULT MODAL -->
<div class="result-overlay" id="resultOverlay">
  <div class="result-box">
    <h2>Exam Submitted!</h2>
    <div class="result-score" id="resultScore">0/50</div>
    <div class="result-label">Percentage: <strong id="resultPct">0%</strong></div>
    <div class="result-grade" id="resultGrade"></div>
    <button class="btn-close" onclick="document.getElementById('resultOverlay').style.display='none'">Close</button>
  </div>
</div>

<script>
  const questions = [
    "The powerhouse of the cell is the ___.",
    "Which planet is known as the Red Planet?",
    "Water is composed of hydrogen and ___ atoms.",
    "The speed of light is approximately ___ km/s.",
    "Who is known as the father of modern physics?",
    "Which organ pumps blood through the body?",
    "The chemical symbol for gold is ___.",
    "Photosynthesis occurs in the ___ of plant cells.",
    "How many bones are in the adult human body?",
    "The Earth revolves around the Sun in approximately ___ days.",
    "Which gas is most abundant in Earth's atmosphere?",
    "The boiling point of water at sea level is ___ °C.",
    "DNA stands for ___.",
    "Which planet has the most moons?",
    "The process of a solid turning directly into gas is called ___.",
    "What is the chemical formula for table salt?",
    "The smallest unit of matter is the ___.",
    "Which vitamin is produced when skin is exposed to sunlight?",
    "The force that attracts objects toward the Earth is called ___.",
    "Which part of the plant absorbs water from the soil?",
    "The human heart has ___ chambers.",
    "Sound cannot travel through ___.",
    "Which element has the atomic number 1?",
    "The pH of pure water is ___.",
    "Which organelle controls cell activities?",
    "The process of cell division is called ___.",
    "Light-years are used to measure ___.",
    "The study of fossils is called ___.",
    "Which blood type is the universal donor?",
    "The respiratory organ of fish is the ___.",
    "An object at rest tends to stay at rest — this is Newton's ___ law.",
    "Which part of the brain controls balance?",
    "The chemical formula for carbon dioxide is ___.",
    "Electricity is measured in units called ___.",
    "Which continent is the largest by area?",
    "The process of water changing to vapor is called ___.",
    "Which nutrient provides the most energy per gram?",
    "The outermost layer of the Earth is called the ___.",
    "Which sense organ is responsible for hearing?",
    "A group of stars forming a pattern is called a ___.",
    "The basic unit of heredity is the ___.",
    "Which gas do plants absorb during photosynthesis?",
    "The freezing point of water is ___ °C.",
    "Which organ produces insulin?",
    "The speed of sound in air is approximately ___ m/s.",
    "Humans belong to the class ___.",
    "The study of weather is called ___.",
    "Which particle has a negative charge?",
    "The Earth's axis is tilted at approximately ___ degrees.",
    "The largest organ of the human body is the ___."
  ];

  const choices = [
    ["A. Mitochondria","B. Nucleus","C. Ribosome","D. Vacuole"],
    ["A. Mars","B. Jupiter","C. Venus","D. Saturn"],
    ["A. Carbon","B. Oxygen","C. Nitrogen","D. Helium"],
    ["A. 300,000","B. 150,000","C. 500,000","D. 100,000"],
    ["A. Einstein","B. Newton","C. Bohr","D. Curie"],
    ["A. Heart","B. Liver","C. Lungs","D. Kidney"],
    ["A. Au","B. Ag","C. Fe","D. Cu"],
    ["A. Chloroplast","B. Mitochondria","C. Nucleus","D. Cell wall"],
    ["A. 206","B. 180","C. 212","D. 198"],
    ["A. 365","B. 300","C. 400","D. 250"],
    ["A. Nitrogen","B. Oxygen","C. Carbon dioxide","D. Argon"],
    ["A. 100","B. 50","C. 212","D. 75"],
    ["A. Deoxyribonucleic acid","B. Dynamic nucleic acid","C. Dual nitrogen acid","D. Dense nuclear acid"],
    ["A. Saturn","B. Jupiter","C. Uranus","D. Neptune"],
    ["A. Sublimation","B. Evaporation","C. Condensation","D. Deposition"],
    ["A. NaCl","B. KCl","C. CaCl2","D. MgCl2"],
    ["A. Atom","B. Molecule","C. Proton","D. Electron"],
    ["A. Vitamin D","B. Vitamin C","C. Vitamin A","D. Vitamin B"],
    ["A. Gravity","B. Friction","C. Inertia","D. Momentum"],
    ["A. Roots","B. Leaves","C. Stem","D. Flowers"],
    ["A. 4","B. 2","C. 3","D. 6"],
    ["A. Vacuum","B. Water","C. Air","D. Metal"],
    ["A. Hydrogen","B. Helium","C. Carbon","D. Oxygen"],
    ["A. 7","B. 5","C. 9","D. 3"],
    ["A. Nucleus","B. Ribosome","C. Vacuole","D. Chloroplast"],
    ["A. Mitosis","B. Osmosis","C. Diffusion","D. Respiration"],
    ["A. Distance in space","B. Speed of light","C. Time on Earth","D. Mass of stars"],
    ["A. Paleontology","B. Ecology","C. Geology","D. Zoology"],
    ["A. O","B. A","C. B","D. AB"],
    ["A. Gills","B. Lungs","C. Skin","D. Fins"],
    ["A. First","B. Second","C. Third","D. Fourth"],
    ["A. Cerebellum","B. Cerebrum","C. Medulla","D. Thalamus"],
    ["A. CO2","B. CO","C. C2O","D. C2O2"],
    ["A. Watts","B. Amperes","C. Ohms","D. Volts"],
    ["A. Asia","B. Africa","C. Europe","D. Antarctica"],
    ["A. Evaporation","B. Condensation","C. Precipitation","D. Sublimation"],
    ["A. Fat","B. Protein","C. Carbohydrate","D. Vitamin"],
    ["A. Crust","B. Mantle","C. Core","D. Lithosphere"],
    ["A. Ears","B. Eyes","C. Nose","D. Skin"],
    ["A. Constellation","B. Galaxy","C. Nebula","D. Cluster"],
    ["A. Gene","B. Chromosome","C. Cell","D. Protein"],
    ["A. Carbon dioxide","B. Oxygen","C. Nitrogen","D. Water vapor"],
    ["A. 0","B. 32","C. 10","D. -10"],
    ["A. Pancreas","B. Liver","C. Kidney","D. Stomach"],
    ["A. 343","B. 150","C. 500","D. 700"],
    ["A. Mammalia","B. Reptilia","C. Amphibia","D. Aves"],
    ["A. Meteorology","B. Ecology","C. Geology","D. Hydrology"],
    ["A. Electron","B. Proton","C. Neutron","D. Nucleus"],
    ["A. 23.5","B. 45","C. 90","D. 10"],
    ["A. Skin","B. Heart","C. Liver","D. Lungs"]
  ];

  const answered = new Array(50).fill(null);

  function buildQuestions() {
    const list = document.getElementById('questionsList');
    questions.forEach((q, i) => {
      const card = document.createElement('div');
      card.className = 'question-card';
      card.innerHTML = `
        <div class="q-header">
          <div class="q-num">${i + 1}</div>
          <div class="q-text">${q}</div>
        </div>
        <div class="options-grid">
          ${choices[i].map((opt, j) => `
            <label class="option-label">
              <input type="radio" name="q${i}" value="${j}" onchange="recordAnswer(${i}, ${j})">
              <span>${opt}</span>
            </label>
          `).join('')}
        </div>
      `;
      list.appendChild(card);
    });
  }

  function recordAnswer(qIdx, val) {
    answered[qIdx] = val;
    updateProgress();
  }

  function updateProgress() {
    const count = answered.filter(a => a !== null).length;
    document.getElementById('answeredCount').textContent = count;
    document.getElementById('progressBar').style.width = Math.round(count / 50 * 100) + '%';
  }

  function clearAll() {
    if (!confirm('Clear all answers?')) return;
    answered.fill(null);
    document.querySelectorAll('input[type="radio"]').forEach(r => r.checked = false);
    updateProgress();
  }

  function submitExam() {
    const count = answered.filter(a => a !== null).length;
    if (count < 50 && !confirm(`You have ${50 - count} unanswered item(s). Submit anyway?`)) return;
    const correct = answered.filter(a => a === 0).length;
    const pct = Math.round(correct / 50 * 100);
    let grade = '';
    if (pct >= 90) grade = 'Excellent — A';
    else if (pct >= 80) grade = 'Very Good — B';
    else if (pct >= 75) grade = 'Passed — C';
    else grade = 'Failed — Below Passing';
    document.getElementById('resultScore').textContent = correct + '/50';
    document.getElementById('resultPct').textContent = pct + '%';
    const gradeEl = document.getElementById('resultGrade');
    gradeEl.textContent = grade;
    gradeEl.style.color = pct >= 75 ? '#1a7a1a' : '#b03020';
    document.getElementById('resultOverlay').style.display = 'flex';
  }

  document.getElementById('examDate').valueAsDate = new Date();
  buildQuestions();
</script>

</body>
</html>
