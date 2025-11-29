<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="utf-8" />
  <title>เครื่องมือสุขภาพ — คำนวณ BMI & อัตราการเต้นหัวใจตามช่วงอายุ</title>
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;600;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#f3f6fb; --card:#ffffff; --accent:#1f3b70; --muted:#6b7280;
    }
    *{box-sizing:border-box;font-family:"Sarabun",system-ui,-apple-system,"Segoe UI",sans-serif}
    body{margin:0;background:var(--bg);display:flex;justify-content:center;padding:28px 12px}
    .container{max-width:1100px;width:100%;background:var(--card);border-radius:14px;padding:20px;box-shadow:0 12px 30px rgba(15,23,42,0.06)}
    h1{margin:0;font-size:22px;color:var(--accent)}
    p.lead{margin:6px 0 16px;color:var(--muted);font-size:14px}
    .grid{display:grid;grid-template-columns:1fr 420px;gap:16px}
    @media(max-width:980px){.grid{grid-template-columns:1fr}}
    .card{background:#f9fbff;border-radius:10px;padding:14px;border:1px solid #e6eefb}
    label{display:block;font-weight:700;margin-bottom:6px}
    input,select,button{font-size:14px}
    input,select{width:100%;padding:8px;border-radius:8px;border:1px solid #dbeafe}
    button{background:linear-gradient(90deg,#2563eb,#06b6d4);color:#fff;border:0;padding:8px 12px;border-radius:999px;cursor:pointer;font-weight:700}
    .small{padding:6px 10px;font-size:13px}
    .secondary{background:#64748b}
    .muted{color:var(--muted);font-size:13px}
    .result{margin-top:10px;padding:12px;border-radius:8px;background:#eef6ff;border:1px solid #dbeafe}
    .error{background:#fef2f2;border:1px solid #fee2e2;color:#b91c1c}
    table{width:100%;border-collapse:collapse;margin-top:8px}
    th,td{padding:8px;border:1px solid #eef6ff;text-align:left;font-size:13px}
    .pill{display:inline-block;background:#eef2ff;color:#1d4ed8;padding:4px 8px;border-radius:999px;font-weight:700;margin-right:6px}
    .hint{font-size:12px;color:#475569;margin-top:8px}
  </style>
</head>
<body>
  <div class="container">
    <h1>เครื่องมือสุขภาพ — BMI และอัตราการเต้นของหัวใจ (ตามช่วงอายุ)</h1>
    <p class="lead">เลือกช่วงอายุเพื่อดูค่าประมาณของ Max HR และ Target Zones โดยอัตโนมัติ — หรือกรอกข้อมูลจริง (น้ำหนัก/ส่วนสูง/อายุ/Resting HR) เพื่อคำนวณแบบละเอียด (BMI และ Karvonen)</p>

    <div class="grid">
      <!-- LEFT: Calculators -->
      <div>
        <div class="card">
          <h2>1) เลือกช่วงอายุ (ระบบจะเติมค่าตัวอย่างอายุให้)</h2>
          <label>ช่วงอายุ</label>
          <select id="ageGroup">
            <option value="child">7–12 ปี (เด็ก)</option>
            <option value="teen">13–18 ปี (วัยรุ่น)</option>
            <option value="adult">19–59 ปี (ผู้ใหญ่)</option>
            <option value="senior">60 ปีขึ้นไป (ผู้สูงอายุ)</option>
          </select>

          <div class="muted" style="margin-top:8px;">
            เมื่อเลือกช่วงอายุ ระบบจะตั้งค่าอายุตัวอย่างที่ใช้คำนวณ Max HR & Target Zones ให้ (คุณสามารถแก้ไขอายุจริงได้ด้านล่าง)
          </div>
        </div>

        <div class="card" style="margin-top:12px;">
          <h2>2) ข้อมูลผู้ใช้ (ใส่เพื่อคำนวณแบบแม่นยำ)</h2>
          <label>อายุ (ปี)</label>
          <input id="inputAge" type="number" min="5" value="30">

          <label style="margin-top:8px;">น้ำหนัก (กก.)</label>
          <input id="inputWeight" type="number" min="10" value="60">

          <label style="margin-top:8px;">ส่วนสูง (ซม.)</label>
          <input id="inputHeight" type="number" min="50" value="165">

          <label style="margin-top:8px;">อัตราการเต้นหัวใจขณะพัก (Resting HR) — ถ้าทราบ</label>
          <input id="inputRestHR" type="number" min="30" placeholder="เช่น 60">

          <div style="display:flex;gap:8px;margin-top:10px">
            <button id="btnCalcAll" class="small">คำนวณ BMI & HR</button>
            <button id="btnReset" class="small secondary">รีเซ็ต</button>
          </div>

          <div id="calcResult" class="result" style="display:none;"></div>
        </div>

        <div class="card" style="margin-top:12px;">
          <h2>3) สูตรที่ใช้</h2>
          <ul class="muted">
            <li><strong>BMI</strong> = น้ำหนัก (kg) ÷ (ส่วนสูง (m))²</li>
            <li><strong>Max HR (สูตรมาตรฐาน)</strong> ≔ 220 − อายุ</li>
            <li><strong>Max HR (Tanaka)</strong> ≔ 208 − 0.7 × อายุ (ทางเลือก)</li>
            <li><strong>Target zone (ตาม % ของ Max HR)</strong> — เบา 50–60%, ปานกลาง 60–70%, หนัก 70–85%</li>
            <li><strong>Karvonen (ถ้ามี Resting HR)</strong> — Target = ((MaxHR − RestHR) × intensity) + RestHR</li>
          </ul>
          <div class="hint">คำเตือน: ค่า Max HR เป็นการประมาณ — หากต้องการค่าที่แม่นยำ ควรทดสอบภายใต้การดูแลของผู้เชี่ยวชาญ</div>
        </div>
      </div>

      <!-- RIGHT: Results & Age-group summary -->
      <aside>
        <div class="card">
          <h2>สรุปตามช่วงอายุ (ค่าประมาณ)</h2>
          <div class="muted" id="ageSummary">
            เลือกช่วงอายุด้านซ้ายเพื่อดูสรุป — ระบบจะคำนวณ Max HR และโซนตามอายุตัวอย่างของช่วงนั้น
          </div>
        </div>

        <div class="card" style="margin-top:12px;">
          <h2>ตารางอ้างอิงโซน HR (ตัวอย่าง)</h2>
          <table>
            <thead><tr><th>โซน</th><th>ความเข้มข้น (% ของ Max)</th><th>คำอธิบายสั้น</th></tr></thead>
            <tbody>
              <tr><td>โซนเบา</td><td>50–60%</td><td>กิจกรรมบำรุงสุขภาพ, เดินเร็ว</td></tr>
              <tr><td>โซนปานกลาง</td><td>60–70%</td><td>เพิ่มความอดทน แนะนำสำหรับ cardio ปานกลาง</td></tr>
              <tr><td>โซนหนัก</td><td>70–85%</td><td>เพิ่มความฟิตสูง เหมาะสำหรับ interval</td></tr>
            </tbody>
          </table>
        </div>
      </aside>
    </div>
  </div>

<script>
  // Age group midpoints (ใช้เป็นค่าอายุตัวอย่างเมื่อเลือกช่วง)
  const ageGroupMid = {
    child: 10,   // 7-12 -> 10
    teen: 16,    // 13-18 -> 16
    adult: 39,   // 19-59 -> midpoint 39
    senior: 70   // 60+ -> use 70 as example
  };

  // UI refs
  const ageGroup = document.getElementById('ageGroup');
  const inputAge = document.getElementById('inputAge');
  const inputWeight = document.getElementById('inputWeight');
  const inputHeight = document.getElementById('inputHeight');
  const inputRestHR = document.getElementById('inputRestHR');
  const btnCalcAll = document.getElementById('btnCalcAll');
  const btnReset = document.getElementById('btnReset');
  const calcResult = document.getElementById('calcResult');
  const ageSummary = document.getElementById('ageSummary');

  // helpers
  function round1(n){ return Math.round(n*10)/10; }
  function showAgeSummaryFor(groupKey){
    const sampleAge = ageGroupMid[groupKey];
    const maxHR = 220 - sampleAge;
    const tanaka = Math.round(208 - 0.7 * sampleAge);
    const zones = [
      {name:'โซนเบา (50–60%)', low:Math.round(0.5*maxHR), high:Math.round(0.6*maxHR)},
      {name:'โซนปานกลาง (60–70%)', low:Math.round(0.6*maxHR), high:Math.round(0.7*maxHR)},
      {name:'โซนหนัก (70–85%)', low:Math.round(0.7*maxHR), high:Math.round(0.85*maxHR)}
    ];
    let html = `<strong>ตัวอย่างอายุในช่วงนี้:</strong> ${sampleAge} ปี<br>`;
    html += `<strong>Max HR (220 − อายุ):</strong> ${maxHR} bpm<br>`;
    html += `<strong>Max HR (Tanaka):</strong> ${tanaka} bpm<br><br>`;
    html += `<strong>Target zones (ตาม % ของ Max HR)</strong><br>`;
    zones.forEach(z=>{
      html += `${z.name}: ${z.low} – ${z.high} bpm<br>`;
    });
    ageSummary.innerHTML = html;
  }

  // on load set summary
  showAgeSummaryFor(ageGroup.value);

  // when user selects age group, set age input to sample age and update summary
  ageGroup.addEventListener('change', ()=>{
    const key = ageGroup.value;
    const sample = ageGroupMid[key];
    inputAge.value = sample;
    showAgeSummaryFor(key);
  });

  // calculation main
  btnCalcAll.addEventListener('click', ()=>{
    calcResult.style.display = 'block';
    const age = parseFloat(inputAge.value);
    const weight = parseFloat(inputWeight.value);
    const heightCm = parseFloat(inputHeight.value);
    const restHR = parseFloat(inputRestHR.value);

    // validate basic
    if(isNaN(age) || age <= 0){
      calcResult.className = 'result error';
      calcResult.innerHTML = 'กรุณากรอกอายุที่ถูกต้อง';
      return;
    }
    if(isNaN(weight) || weight <= 0 || isNaN(heightCm) || heightCm <= 0){
      calcResult.className = 'result error';
      calcResult.innerHTML = 'กรุณากรอกน้ำหนักและส่วนสูงให้ถูกต้อง';
      return;
    }

    // BMI
    const heightM = heightCm / 100;
    const bmi = weight / (heightM * heightM);
    let bmiCat = '';
    if(bmi < 18.5) bmiCat = 'น้ำหนักน้อย (Underweight)';
    else if(bmi < 25) bmiCat = 'ปกติ (Normal weight)';
    else if(bmi < 30) bmiCat = 'น้ำหนักเกิน (Overweight)';
    else bmiCat = 'อ้วน (Obesity)';

    // Max HR formulas
    const maxHR_standard = Math.round(220 - age);
    const maxHR_tanaka = Math.round(208 - 0.7 * age);

    // target zones based on standard MaxHR
    const zonesPerc = [
      {name:'โซนเบา', lowP:0.50, highP:0.60},
      {name:'โซนปานกลาง', lowP:0.60, highP:0.70},
      {name:'โซนหนัก', lowP:0.70, highP:0.85}
    ];
    const zonesStandard = zonesPerc.map(z=>({
      name: z.name,
      low: Math.round(z.lowP * maxHR_standard),
      high: Math.round(z.highP * maxHR_standard),
      lowP: z.lowP, highP: z.highP
    }));
    const zonesTanaka = zonesPerc.map(z=>({
      name: z.name,
      low: Math.round(z.lowP * maxHR_tanaka),
      high: Math.round(z.highP * maxHR_tanaka)
    }));

    // Karvonen if resting HR provided
    let karvonenHtml = '';
    if(!isNaN(restHR) && restHR > 20){
      karvonenHtml += `<strong>Karvonen (ใช้ Resting HR = ${restHR} bpm)</strong><br>`;
      zonesPerc.forEach(z=>{
        const low = Math.round(((maxHR_standard - restHR) * z.lowP) + restHR);
        const high = Math.round(((maxHR_standard - restHR) * z.highP) + restHR);
        karvonenHtml += `${z.name} (${Math.round(z.lowP*100)}–${Math.round(z.highP*100)}%): ${low} – ${high} bpm<br>`;
      });
    } else {
      karvonenHtml = `<div class="muted">หากทราบ Resting HR ให้กรอกเพื่อคำนวณ Karvonen (แม่นขึ้น)</div>`;
    }

    // Compose result HTML
    let html = `<strong>BMI</strong>: ${round1(bmi)} kg/m² — <em>${bmiCat}</em><br><br>`;
    html += `<strong>Max HR</strong> (สูตรมาตรฐาน 220−อายุ): <strong>${maxHR_standard} bpm</strong><br>`;
    html += `<strong>Max HR</strong> (Tanaka 208 − 0.7×อายุ): <strong>${maxHR_tanaka} bpm</strong><br><br>`;

    html += `<strong>Target zones (ตาม % ของ Max HR — สูตรมาตรฐาน)</strong><br>`;
    zonesStandard.forEach(z=>{
      html += `${z.name} (${Math.round(z.lowP*100 || 0)}–${Math.round(z.highP*100 || 0)}%): ${z.low} – ${z.high} bpm<br>`;
    });

    html += `<br><strong>Target zones (อ้างอิง Tanaka)</strong><br>`;
    zonesTanaka.forEach(z=>{
      html += `${z.name}: ${z.low} – ${z.high} bpm<br>`;
    });

    html += `<br>${karvonenHtml}`;

    // Add quick tips based on age group
    const groupKey = (() => {
      if(age >= 60) return 'senior';
      if(age >= 19) return 'adult';
      if(age >= 13) return 'teen';
      return 'child';
    })();

    const tipsByGroup = {
      child: 'เด็กควรเน้นกิจกรรมหลากหลายและไม่ฝึกหนักเกินไป ต่อเนื่อง-เล่นกลางแจ้ง เพื่อพัฒนาความแข็งแรงและสมรรถภาพ',
      teen: 'วัยรุ่นควรส่งเสริมกิจกรรมแอโรบิกปานกลางอย่างน้อย 60 นาทีต่อวัน ผสมกิจกรรมเสริมความแข็งแรง 3 ครั้ง/สัปดาห์',
      adult: 'ผู้ใหญ่ควรพยายามออกกำลังกายแบบแอโรบิกปานกลาง 150 นาที/สัปดาห์ หรือหนัก 75 นาที/สัปดาห์ รวมการฝึกความแข็งแรง 2 ครั้ง/สัปดาห์',
      senior: 'ผู้สูงอายุเน้นแอโรบิกเบา-ปานกลาง และฝึกการทรงตัว/ความแข็งแรงตามความสามารถ ปรึกษาแพทย์เมื่อต้องการเพิ่มความเข้มข้น'
    };

    html += `<hr style="border:none;border-top:1px solid #e6f0ff;margin:10px 0">`;
    html += `<div class="muted"><strong>คำแนะนำสั้น ๆ:</strong> ${tipsByGroup[groupKey]}</div>`;

    calcResult.className = 'result';
    calcResult.innerHTML = html;
  });

  // reset
  btnReset.addEventListener('click', ()=>{
    // set to defaults and update summary
    ageGroup.value = 'adult';
    inputAge.value = 39;
    inputWeight.value = 60;
    inputHeight.value = 165;
    inputRestHR.value = '';
    showAgeSummaryFor('adult');
    calcResult.style.display = 'none';
  });

  // init: set age based on initial group and summary
  (function init(){
    const g = ageGroup.value;
    inputAge.value = ageGroupMid[g];
    showAgeSummaryFor(g);
  })();

  // update when group changes (also sets sample age)
  ageGroup.addEventListener('change', ()=>{
    const g = ageGroup.value;
    inputAge.value = ageGroupMid[g];
    showAgeSummaryFor(g);
  });

  // helper function referenced earlier (must be declared before use)
  function showAgeSummaryFor(groupKey){
    const sampleAge = ageGroupMid[groupKey];
    const maxHR = 220 - sampleAge;
    const tanaka = Math.round(208 - 0.7 * sampleAge);
    const zones = [
      { name: 'โซนเบา (50–60%)', low: Math.round(0.5*maxHR), high: Math.round(0.6*maxHR) },
      { name: 'โซนปานกลาง (60–70%)', low: Math.round(0.6*maxHR), high: Math.round(0.7*maxHR) },
      { name: 'โซนหนัก (70–85%)', low: Math.round(0.7*maxHR), high: Math.round(0.85*maxHR) }
    ];
    let html = `<strong>ตัวอย่างอายุในช่วงนี้:</strong> ${sampleAge} ปี<br>`;
    html += `<strong>Max HR (220 − อายุ):</strong> ${maxHR} bpm<br>`;
    html += `<strong>Max HR (Tanaka):</strong> ${tanaka} bpm<br><br>`;
    html += `<strong>Target zones (ตาม % ของ Max HR)</strong><br>`;
    zones.forEach(z=>{
      html += `${z.name}: ${z.low} – ${z.high} bpm<br>`;
    });
    ageSummary.innerHTML = html;
  }
</script>
</body>
</html>
