<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="utf-8" />
  <title>เครื่องมือสุขภาพสำหรับนักเรียน — BMI และอัตราการเต้นของหัวใจ</title>
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;600;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#f5f9ff; --card:#ffffff; --accent:#0f4fd8; --muted:#556077;
    }
    *{box-sizing:border-box;font-family:"Sarabun",system-ui,-apple-system,"Segoe UI",sans-serif}
    body{margin:0;background:var(--bg);display:flex;justify-content:center;padding:28px 12px}
    .container{max-width:1000px;width:100%;background:var(--card);border-radius:14px;padding:20px;border:1px solid rgba(15,23,42,0.04);box-shadow:0 12px 30px rgba(15,23,42,0.04)}
    h1{margin:0;font-size:22px;color:var(--accent)}
    p.lead{margin:8px 0 16px;color:var(--muted);font-size:14px}
    .grid{display:grid;grid-template-columns:1fr 380px;gap:16px}
    @media(max-width:980px){.grid{grid-template-columns:1fr}}
    .card{background:#fcfeff;border-radius:12px;padding:14px;border:1px solid #e6f0ff}
    label{display:block;font-weight:700;margin-bottom:6px;color:#0b2447}
    input,select,button{font-size:14px}
    input,select{width:100%;padding:10px;border-radius:10px;border:1px solid #dbeafe;background:#fff}
    button{background:linear-gradient(90deg,#2563eb,#06b6d4);color:#fff;border:0;padding:8px 14px;border-radius:999px;cursor:pointer;font-weight:700}
    button.secondary{background:#64748b}
    .small{padding:6px 10px;font-size:13px}
    .muted{color:var(--muted);font-size:13px}
    .result{margin-top:12px;padding:12px;border-radius:10px;background:#eef6ff;border:1px solid #dbeafe}
    .error{background:#fff1f2;border:1px solid #fed7d7;color:#b91c1c}
    table{width:100%;border-collapse:collapse;margin-top:8px}
    th,td{padding:8px;border:1px solid #eef6ff;text-align:left;font-size:13px}
    .pill{display:inline-block;background:#eef2ff;color:#1d4ed8;padding:5px 10px;border-radius:999px;font-weight:700;margin-right:6px}
    .hint{font-size:13px;color:#475569;margin-top:8px}
    .step { background:#ffffff;border:1px dashed #dbeafe;padding:10px;border-radius:8px;margin-top:8px;font-size:13px;color:#263348 }
    footer{margin-top:14px;font-size:12px;color:var(--muted);text-align:right}
  </style>
</head>
<body>
  <div class="container" role="main">
    <h1>เครื่องมือสุขภาพสำหรับนักเรียน — BMI และอัตราการเต้นหัวใจ</h1>
    <p class="lead">ง่ายและเป็นมิตร: เลือกช่วงอายุหรือกรอกข้อมูลจริง แล้วกด "คำนวณ" เพื่อดูผลแบบเข้าใจง่าย</p>

    <div class="grid">
      <!-- LEFT: Inputs & calculators -->
      <div>
        <div class="card" aria-labelledby="age-group-title">
          <h2 id="age-group-title">1. เลือกช่วงอายุ (ระบบใส่อายุตัวอย่างให้)</h2>
          <label for="ageGroup">ช่วงอายุ</label>
          <select id="ageGroup" aria-describedby="ageHint">
            <option value="child">7–12 ปี (เด็ก)</option>
            <option value="teen">13–18 ปี (วัยรุ่น)</option>
            <option value="adult">19–59 ปี (ผู้ใหญ่)</option>
            <option value="senior">60 ปีขึ้นไป (ผู้สูงอายุ)</option>
          </select>
          <div id="ageHint" class="muted hint">เมื่อเลือกช่วงอายุ ระบบจะใส่อายุตัวอย่างให้ในช่องอายุ — สามารถแก้เป็นอายุจริงได้</div>
        </div>

        <div class="card" style="margin-top:12px;">
          <h2>2. ใส่ข้อมูลของนักเรียน</h2>

          <label for="inputAge">อายุ (ปี)</label>
          <input id="inputAge" type="number" min="5" step="1" value="39">

          <label for="inputWeight" style="margin-top:8px;">น้ำหนัก (กิโลกรัม)</label>
          <input id="inputWeight" type="number" min="10" step="0.1" value="60">

          <label for="inputHeight" style="margin-top:8px;">ส่วนสูง (เซนติเมตร)</label>
          <input id="inputHeight" type="number" min="50" step="0.1" value="165">

          <label for="inputRestHR" style="margin-top:8px;">อัตราการเต้นหัวใจขณะพัก (Resting HR) — ถ้าทราบ</label>
          <input id="inputRestHR" type="number" min="20" step="1" placeholder="เช่น 60">

          <div style="display:flex;gap:8px;margin-top:12px;">
            <button id="btnCalc" class="small">คำนวณ BMI และ HR</button>
            <button id="btnReset" class="small secondary">รีเซ็ต</button>
          </div>

          <!-- Result: friendly -->
          <div id="calcResult" class="result" style="display:none;" aria-live="polite"></div>

          <!-- Step-by-step BMI calculation -->
          <div id="bmiSteps" class="step" style="display:none;">
            <strong>ตัวอย่างวิธีคิด BMI แบบทีละขั้นตอน:</strong>
            <div id="bmiStepsContent" style="margin-top:6px;"></div>
          </div>
        </div>

        <div class="card" style="margin-top:12px;">
          <h2>3. สูตรง่าย ๆ ที่ใช้อธิบาย</h2>
          <ul class="muted" style="margin:6px 0 0 18px;">
            <li><strong>BMI</strong> = น้ำหนัก (กก.) ÷ (ส่วนสูง (ม.))² — เป็นตัววัดง่าย ๆ เพื่อดูว่า "น้ำหนักเหมาะสม" หรือไม่</li>
            <li><strong>Max HR (ง่าย)</strong> = 220 − อายุ</li>
            <li><strong>Target zone</strong> — เบา 50–60%, ปานกลาง 60–70%, หนัก 70–85% ของ Max HR</li>
            <li><strong>Karvonen</strong> — ถ้ารู้ Resting HR จะคำนวณเป้าหมายได้แม่นขึ้น</li>
          </ul>
          <div class="hint">คำเตือน: นี่เป็นการประเมินเบื้องต้น เหมาะสำหรับการเรียนรู้เท่านั้น ถ้าจะใช้จริง ควรปรึกษาอาจารย์หรือนักวิชาการด้านสุขภาพ</div>
        </div>
      </div>

      <!-- RIGHT: Age-summary & reference -->
      <aside>
        <div class="card">
          <h2>สรุปตามช่วงอายุ (ค่าประมาณ)</h2>
          <div id="ageSummary" class="muted">เลือกช่วงอายุด้านซ้ายเพื่อดูสรุป (ระบบจะใช้อายุตัวอย่าง)</div>
        </div>

        <div class="card" style="margin-top:12px;">
          <h2>ตารางโซนอัตราการเต้นหัวใจ</h2>
          <table>
            <thead><tr><th>โซน</th><th>ความเข้มข้น</th><th>เหมาะสำหรับ</th></tr></thead>
            <tbody>
              <tr><td>โซนเบา</td><td>50–60% ของ Max HR</td><td>ออกกำลังกายเบา เช่น เดินเร็ว</td></tr>
              <tr><td>โซนปานกลาง</td><td>60–70% ของ Max HR</td><td>เพิ่มความฟิต เหมาะสำหรับวิ่งสบายๆ</td></tr>
              <tr><td>โซนหนัก</td><td>70–85% ของ Max HR</td><td>ฝึก HIIT หรือช่วงเร่งความเร็ว</td></tr>
            </tbody>
          </table>
        </div>

        <div class="card" style="margin-top:12px;">
          <h2>คำแนะนำสั้น ๆ</h2>
          <div id="tipsBox" class="muted">เลือกช่วงอายุหรือคำนวณเพื่อดูคำแนะนำสำหรับแต่ละวัย</div>
        </div>
      </aside>
    </div>

    <footer>© เครื่องมือเพื่อการเรียนรู้ — ค่าเป็นการประมาณเท่านั้น</footer>
  </div>

<script>
  // ค่าอายุตัวอย่างสำหรับแต่ละช่วง
  const ageGroupMid = { child: 10, teen: 16, adult: 39, senior: 70 };

  // DOM refs
  const ageGroup = document.getElementById('ageGroup');
  const inputAge = document.getElementById('inputAge');
  const inputWeight = document.getElementById('inputWeight');
  const inputHeight = document.getElementById('inputHeight');
  const inputRestHR = document.getElementById('inputRestHR');
  const btnCalc = document.getElementById('btnCalc');
  const btnReset = document.getElementById('btnReset');
  const calcResult = document.getElementById('calcResult');
  const ageSummary = document.getElementById('ageSummary');
  const tipsBox = document.getElementById('tipsBox');
  const bmiSteps = document.getElementById('bmiSteps');
  const bmiStepsContent = document.getElementById('bmiStepsContent');

  // helper
  const round1 = n => Math.round(n*10)/10;

  // แสดงสรุปตามช่วงอายุ (ค่าประมาณ)
  function showAgeSummaryFor(key){
    const sampleAge = ageGroupMid[key];
    const maxStd = 220 - sampleAge;
    const maxTanaka = Math.round(208 - 0.7 * sampleAge);
    const zones = [
      {name:'โซนเบา (50–60%)', low: Math.round(0.5*maxStd), high: Math.round(0.6*maxStd)},
      {name:'โซนปานกลาง (60–70%)', low: Math.round(0.6*maxStd), high: Math.round(0.7*maxStd)},
      {name:'โซนหนัก (70–85%)', low: Math.round(0.7*maxStd), high: Math.round(0.85*maxStd)}
    ];
    let html = `<strong>ตัวอย่างอายุ:</strong> ${sampleAge} ปี<br>`;
    html += `<strong>Max HR (สูตรง่าย 220 − อายุ):</strong> ${maxStd} bpm<br>`;
    html += `<strong>Max HR (Tanaka):</strong> ${maxTanaka} bpm<br><br>`;
    html += `<strong>Target zones (ตามสูตรง่าย):</strong><br>`;
    zones.forEach(z => html += `${z.name}: ${z.low} – ${z.high} bpm<br>`);
    ageSummary.innerHTML = html;

    const tips = {
      child: 'เด็ก: เล่นให้หลากหลาย ชอบวิ่ง-กระโดด-ปีน เพื่อพัฒนากล้ามเนื้อและทักษะการเคลื่อนไหว',
      teen: 'วัยรุ่น: ควรออกกำลังกายทุกวันประมาณ 60 นาที ผสมการฝึกความแข็งแรง 2–3 วัน/สัปดาห์',
      adult: 'ผู้ใหญ่: พยายามทำกิจกรรมแอโรบิกปานกลางสัปดาห์ละ 150 นาที หรือหนัก 75 นาที พร้อมฝึกความแข็งแรง 2 ครั้ง/สัปดาห์',
      senior: 'ผู้สูงอายุ: เน้นกิจกรรมเบา-ปานกลาง ฝึกทรงตัวและความแข็งแรงตามความสามารถ'
    };
    tipsBox.textContent = tips[key];
  }

  // เริ่มต้นตั้งค่า
  (function init(){
    const g = ageGroup.value;
    inputAge.value = ageGroupMid[g];
    showAgeSummaryFor(g);
  })();

  // เปลี่ยนช่วงอายุ -> กำหนดอายุตัวอย่าง & สรุป
  ageGroup.addEventListener('change', ()=>{
    const g = ageGroup.value;
    inputAge.value = ageGroupMid[g];
    showAgeSummaryFor(g);
    calcResult.style.display = 'none';
    bmiSteps.style.display = 'none';
  });

  // คำนวณหลัก
  btnCalc.addEventListener('click', ()=>{
    calcResult.style.display = 'block';
    bmiSteps.style.display = 'none';
    const age = parseFloat(inputAge.value);
    const weight = parseFloat(inputWeight.value);
    const heightCm = parseFloat(inputHeight.value);
    const restHR = parseFloat(inputRestHR.value);

    // ตรวจความถูกต้องของข้อมูล
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

    // คำนวณ BMI
    const heightM = heightCm / 100;
    const bmi = weight / (heightM * heightM);
    let bmiCat = '';
    if(bmi < 18.5) bmiCat = 'น้ำหนักน้อย';
    else if(bmi < 25) bmiCat = 'ปกติ (สมดุล)';
    else if(bmi < 30) bmiCat = 'น้ำหนักเกิน';
    else bmiCat = 'อ้วน';

    // แสดงขั้นตอนการคำนวณ BMI แบบง่าย
    bmiSteps.style.display = 'block';
    const stepHtml =
      `น้ำหนัก = ${weight} กก.<br>` +
      `ส่วนสูง = ${heightCm} ซม. = ${round1(heightM)} เมตร<br>` +
      `BMI = น้ำหนัก ÷ (ส่วนสูง(ม.) × ส่วนสูง(ม.))<br>` +
      `BMI = ${weight} ÷ (${round1(heightM)} × ${round1(heightM)}) = ${round1(bmi)} (กก./ม²)<br>` +
      `<strong>สรุป: BMI = ${round1(bmi)} → ${bmiCat}</strong>`;
    bmiStepsContent.innerHTML = stepHtml;

    // Max HR (สูตรมาตรฐาน) และ Tanaka
    const maxStd = Math.round(220 - age);
    const maxTanaka = Math.round(208 - 0.7 * age);

    // Target zones (สูตรมาตรฐาน)
    const zonesPerc = [
      {name:'โซนเบา', lowP:0.50, highP:0.60},
      {name:'โซนปานกลาง', lowP:0.60, highP:0.70},
      {name:'โซนหนัก', lowP:0.70, highP:0.85}
    ];
    const zonesStd = zonesPerc.map(z => ({
      name: z.name,
      low: Math.round(z.lowP * maxStd),
      high: Math.round(z.highP * maxStd),
      lowP: z.lowP, highP: z.highP
    }));
    const zonesTanaka = zonesPerc.map(z => ({
      name: z.name,
      low: Math.round(z.lowP * maxTanaka),
      high: Math.round(z.highP * maxTanaka)
    }));

    // Karvonen (ถ้ามี Resting HR)
    let karvonenHtml = '';
    if(!isNaN(restHR) && restHR > 20){
      karvonenHtml += `<strong>Karvonen (ใช้ Resting HR = ${restHR} bpm)</strong><br>`;
      zonesPerc.forEach(z=>{
        const low = Math.round(((maxStd - restHR) * z.lowP) + restHR);
        const high = Math.round(((maxStd - restHR) * z.highP) + restHR);
        karvonenHtml += `${z.name} (${Math.round(z.lowP*100)}–${Math.round(z.highP*100)}%): ${low} – ${high} bpm<br>`;
      });
    } else {
      karvonenHtml = `<div class="muted">ถ้าทราบอัตราการเต้นขณะพัก (Resting HR) ให้ใส่เพื่อคำนวณ Karvonen (แม่นขึ้น)</div>`;
    }

    // สรุปเป็นภาษาง่าย ๆ สำหรับนักเรียน
    let html = `<strong>ผลการคำนวณ</strong><br><br>`;
    html += `<strong>BMI:</strong> ${round1(bmi)} — <em>${bmiCat}</em><br><br>`;
    html += `<strong>Max HR (สูตรง่าย 220 − อายุ):</strong> ${maxStd} bpm<br>`;
    html += `<strong>Max HR (Tanaka):</strong> ${maxTanaka} bpm<br><br>`;

    html += `<strong>โซนการเต้นหัวใจ (อ้างอิงสูตร 220 − อายุ)</strong><br>`;
    zonesStd.forEach(z => {
      html += `${z.name} (${Math.round(z.lowP*100)}–${Math.round(z.highP*100)}%): ${z.low} – ${z.high} bpm<br>`;
    });

    html += `<br><strong>โซนตามสูตร Tanaka</strong><br>`;
    zonesTanaka.forEach(z => {
      html += `${z.name}: ${z.low} – ${z.high} bpm<br>`;
    });

    html += `<br>${karvonenHtml}`;

    // คำแนะนำสั้นตามช่วงอายุ
    const groupKey = (age>=60)?'senior':(age>=19)?'adult':(age>=13)?'teen':'child';
    const tips = {
      child: 'เด็ก: เล่นให้สนุก หลากหลาย อย่าฝึกหนักเกินไป',
      teen: 'วัยรุ่น: พยายามเคลื่อนไหววันละ ~60 นาที และฝึกความแข็งแรงเป็นครั้งคราว',
      adult: 'ผู้ใหญ่: ออกกำลังกายสม่ำเสมอ ผสม cardio กับการฝึกความแข็งแรง',
      senior: 'ผู้สูงอายุ: ทำกิจกรรมเบา-ปานกลาง เน้นความปลอดภัยและทรงตัว'
    };
    html += `<hr style="border:none;border-top:1px solid #e6f0ff;margin:10px 0">`;
    html += `<div class="muted"><strong>ข้อแนะนำสั้น ๆ:</strong> ${tips[groupKey]}</div>`;

    calcResult.className = 'result';
    calcResult.innerHTML = html;
  });

  // รีเซ็ตเป็นค่าเริ่มต้น
  btnReset.addEventListener('click', ()=>{
    ageGroup.value = 'adult';
    inputAge.value = ageGroupMid['adult'];
    inputWeight.value = 60;
    inputHeight.value = 165;
    inputRestHR.value = '';
    calcResult.style.display = 'none';
    bmiSteps.style.display = 'none';
    showAgeSummaryFor('adult');
  });

  // เมื่อเปลี่ยนช่วงอายุ ให้ใส่อายุตัวอย่างและสรุป
  ageGroup.addEventListener('change', ()=>{
    const g = ageGroup.value;
    inputAge.value = ageGroupMid[g];
    showAgeSummaryFor(g);
    calcResult.style.display = 'none';
    bmiSteps.style.display = 'none';
  });

  // ฟังก์ชันแสดงสรุปช่วงอายุ (ประกาศหลังเพื่อเรียกใช้ง่าย)
  function showAgeSummaryFor(key){
    const sampleAge = ageGroupMid[key];
    const maxStd = 220 - sampleAge;
    const maxTanaka = Math.round(208 - 0.7 * sampleAge);
    const zones = [
      { name: 'โซนเบา (50–60%)', low: Math.round(0.5*maxStd), high: Math.round(0.6*maxStd) },
      { name: 'โซนปานกลาง (60–70%)', low: Math.round(0.6*maxStd), high: Math.round(0.7*maxStd) },
      { name: 'โซนหนัก (70–85%)', low: Math.round(0.7*maxStd), high: Math.round(0.85*maxStd) }
    ];
    let html = `<strong>ตัวอย่างอายุ:</strong> ${sampleAge} ปี<br>`;
    html += `<strong>Max HR (220 − อายุ):</strong> ${maxStd} bpm<br>`;
    html += `<strong>Max HR (Tanaka):</strong> ${maxTanaka} bpm<br><br>`;
    html += `<strong>Target zones (ตามสูตรง่าย):</strong><br>`;
    zones.forEach(z=> html += `${z.name}: ${z.low} – ${z.high} bpm<br>`);
    ageSummary.innerHTML = html;

    const tipsByGroup = {
      child: 'เด็ก: เล่นเยอะ ๆ สนุกกับการเคลื่อนไหว',
      teen: 'วัยรุ่น: เน้นกิจกรรมทุกวันและฝึกความแข็งแรงเป็นช่วงๆ',
      adult: 'ผู้ใหญ่: เคลื่อนไหวสม่ำเสมอและฝึกความแข็งแรง',
      senior: 'ผู้สูงอายุ: ออกกำลังกายแบบปลอดภัยและฝึกทรงตัว'
    };
    tipsBox.textContent = tipsByGroup[key];
  }

  // เริ่มต้น
  (function boot(){
    const g = ageGroup.value;
    inputAge.value = ageGroupMid[g];
    showAgeSummaryFor(g);
  })();
</script>
</body>
</html>
