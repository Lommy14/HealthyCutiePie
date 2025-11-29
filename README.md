<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>เครื่องมือออกแบบการพัฒนาสุขภาพของนักเรียน — สวยงาม</title>

<!-- Google Font (online) - ถ้าต้องการออฟไลน์ให้เปลี่ยนเป็นระบบฟอนต์ -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&family=Sarabun:wght@300;400;600;700&display=swap" rel="stylesheet">

<style>
  :root{
    --bg:#f4f7fb; --card:#ffffff; --muted:#6b7280; --accent:#0f4bd8; --accent-2:#06b6d4;
    --glass: rgba(255,255,255,0.6);
    --success:#10b981; --danger:#ef4444;
    --soft-shadow: 0 6px 20px rgba(15,23,42,0.08);
    --glass-border: rgba(15,23,42,0.06);
  }
  *{box-sizing:border-box}
  html,body{height:100%}
  body{
    margin:0;
    font-family:"Sarabun", "Inter", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    background: linear-gradient(180deg,#eef6ff 0%,#f8fbff 100%);
    color:#0f172a;
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
    padding:28px;
    display:flex;
    justify-content:center;
  }

  .wrap{
    width:100%;
    max-width:1200px;
    margin:0 auto;
  }

  header.top{
    display:flex;
    align-items:center;
    gap:16px;
    margin-bottom:20px;
  }
  .brand{
    display:flex;
    gap:12px;
    align-items:center;
  }
  .logo{
    width:64px;height:64px;border-radius:12px;
    background:linear-gradient(135deg,var(--accent),var(--accent-2));
    display:flex;align-items:center;justify-content:center;color:#fff;font-weight:800;
    box-shadow: 0 6px 18px rgba(11,84,170,0.18);
  }
  h1{margin:0;font-size:20px}
  p.lead{margin:0;color:var(--muted);font-size:13px}

  .grid{
    display:grid;
    grid-template-columns: 1fr 420px;
    gap:20px;
    align-items:start;
  }
  @media(max-width:980px){
    .grid{grid-template-columns:1fr; padding-bottom:40px}
  }

  /* Card */
  .card{
    background:var(--card);
    border-radius:14px;
    padding:18px;
    box-shadow:var(--soft-shadow);
    border:1px solid var(--glass-border);
  }

  /* left column layout */
  .cols{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:14px;
  }
  @media(max-width:880px){ .cols{grid-template-columns:1fr} }

  label{display:block;font-weight:600;font-size:13px;margin-bottom:8px;color:#0f172a}
  input,select,textarea{
    width:100%;
    padding:10px 12px;
    border-radius:10px;
    border:1px solid #e6eefb;
    background:linear-gradient(180deg,#fff,#fbfdff);
    font-size:14px;
    outline:none;
  }
  textarea{min-height:88px;resize:vertical}

  .pill{display:inline-block;background:#eef2ff;color:var(--accent);padding:6px 10px;border-radius:999px;font-weight:600;font-size:13px;margin-right:8px}
  .muted{color:var(--muted);font-size:13px}

  .action-row{display:flex;gap:8px;flex-wrap:wrap;margin-top:10px}
  button{cursor:pointer;border:0;padding:10px 14px;border-radius:999px;font-weight:700;background:var(--accent);color:#fff;box-shadow:0 6px 18px rgba(15,75,216,0.12)}
  button.ghost{background:transparent;color:var(--accent);border:1px solid rgba(15,75,216,0.12);box-shadow:none}
  button.small{padding:8px 12px;font-size:13px;border-radius:10px}
  button.danger{background:linear-gradient(90deg,#fb7185,#ef4444)}
  button.success{background:linear-gradient(90deg,#34d399,#10b981)}

  /* library list */
  .list{list-style:none;padding:0;margin:0}
  .list li{
    display:flex;justify-content:space-between;gap:10px;align-items:center;
    background:linear-gradient(180deg,#fff,#fbfdff);
    border:1px solid #f0f6ff;padding:12px;border-radius:10px;margin-bottom:10px;
    transition:transform .14s ease,box-shadow .14s ease;
  }
  .list li:hover{transform:translateY(-4px);box-shadow:0 10px 30px rgba(15,23,42,0.06)}
  .meta{font-size:13px;color:var(--muted)}

  .right-col{position:relative;top:0}
  .kpi{
    display:flex;gap:12px;align-items:center;margin-top:12px;
  }
  .kpi .item{
    background:linear-gradient(90deg,#f8fbff,#ffffff);
    padding:10px;border-radius:10px;flex:1;border:1px solid #eef6ff;text-align:center;
  }
  .kpi .val{font-weight:700;color:var(--accent);font-size:18px}

  /* plan list */
  .plan-list .entry{display:flex;justify-content:space-between;gap:8px;align-items:center;padding:10px;border-radius:10px;border:1px solid #eef6ff;background:#fff;margin-bottom:10px}
  .plan-list .meta{font-size:13px;color:var(--muted)}

  /* template box */
  .template{background:linear-gradient(180deg,#f8fbff,#ffffff);padding:12px;border-radius:10px;border:1px dashed #e6eefb}

  /* footer */
  .footer{margin-top:18px;text-align:center;color:var(--muted);font-size:13px}

  /* subtle animations */
  .fade-in{animation:fadeIn .4s ease both}
  @keyframes fadeIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:none}}
</style>
</head>
<body>
  <div class="wrap">
    <header class="top">
      <div class="brand">
        <div class="logo">SH</div>
        <div>
          <h1>การพัฒนาสุขภาพนักเรียน — Designer</h1>
          <p class="lead">เครื่องมือช่วยออกแบบกิจกรรมสุขภาพสำหรับครูและผู้บริหาร — โภชนาการ กาย จิตใจ และทักษะชีวิต</p>
        </div>
      </div>

      <div style="margin-left:auto;display:flex;gap:10px;align-items:center">
        <div class="pill">Template Ready</div>
        <button class="small ghost" id="btnThemeToggle">ธีมสว่าง/มืด</button>
      </div>
    </header>

    <main class="grid">
      <!-- LEFT: editor & library -->
      <section>
        <div class="card fade-in">
          <div style="display:flex;justify-content:space-between;align-items:center">
            <div>
              <div class="muted">เป้าหมายปัจจุบัน</div>
              <div style="font-weight:800;font-size:16px">เลือกกลุ่มเป้าหมายและจัดกิจกรรมที่ตอบโจทย์</div>
            </div>
            <div style="text-align:right">
              <div class="meta">สถานะ: <strong style="color:var(--accent)">Draft</strong></div>
              <div class="meta">บันทึกล่าสุด: <small id="lastSaved">ไม่เคยบันทึก</small></div>
            </div>
          </div>

          <div style="margin-top:14px" class="cols">
            <div>
              <label for="ageGroup">ช่วงอายุ / ระดับชั้น</label>
              <select id="ageGroup">
                <option value="primary">ป.1–ป.6</option>
                <option value="lower-sec">ม.1–ม.3</option>
                <option value="upper-sec">ม.4–ม.6</option>
                <option value="voc">อาชีวะ/นักศึกษา</option>
              </select>

              <div style="margin-top:10px">
                <label>พิมพ์ชื่อแผน (Title)</label>
                <input id="planTitle" placeholder="เช่น แผนเสริมสร้างสุขภาพเรียนรู้-สนุก-ยาว 1 เดือน">
              </div>

              <div style="margin-top:10px">
                <label>คำอธิบายสั้น ๆ</label>
                <textarea id="planDesc" placeholder="สรุปเป้าหมายและแนวทางแบบย่อ"></textarea>
              </div>

            </div>

            <div>
              <label>KPIs (เช่น จำนวนวันออกกำลังกาย/สัปดาห์)</label>
              <input id="kpiInput" placeholder="เช่น ออกกำลังกาย ≥3 วัน/สัปดาห์">
              <div class="kpi" style="margin-top:12px">
                <div class="item"><div class="meta">กิจกรรมในไลบรารี</div><div class="val" id="libCount">0</div></div>
                <div class="item"><div class="meta">รายการในแผน</div><div class="val" id="planCount">0</div></div>
              </div>
            </div>
          </div>

        </div>

        <!-- library -->
        <div class="card fade-in" style="margin-top:16px">
          <div style="display:flex;justify-content:space-between;align-items:center">
            <div>
              <div class="muted">ไลบรารีกิจกรรม</div>
              <div style="font-weight:700">สร้างกิจกรรมที่ใช้งานจริง</div>
            </div>
            <div class="muted">เก็บได้ไม่จำกัด</div>
          </div>

          <div style="margin-top:12px;display:flex;gap:10px;flex-wrap:wrap">
            <select id="activityCategory" style="width:180px">
              <option value="physical">การเคลื่อนไหว/กีฬา</option>
              <option value="nutrition">โภชนาการ</option>
              <option value="mental">สุขภาพจิต</option>
              <option value="life-skill">ทักษะชีวิต</option>
              <option value="screen">ลดเวลาใช้จอ</option>
            </select>
            <input id="activityName" placeholder="ชื่อกิจกรรม (เช่น เดินเร็ว 20 นาที)" style="flex:1">
            <input id="activityDuration" type="number" min="1" value="30" style="width:96px">
            <button id="btnAddActivity" class="small">+ เพิ่ม</button>
            <button id="btnAutoSuggestions" class="small success">แนะนำอัตโนมัติ</button>
          </div>

          <div style="margin-top:12px">
            <ul id="activityList" class="list"></ul>
          </div>
        </div>

        <!-- Template -->
        <div class="card fade-in" style="margin-top:16px">
          <div style="display:flex;justify-content:space-between;align-items:center">
            <div>
              <div class="muted">เทมเพลตกิจกรรม</div>
              <div style="font-weight:700">กรอบที่ช่วยให้ครูเตรียมแผนได้เร็ว</div>
            </div>
            <div><button id="btnCopyTemplate" class="small ghost">คัดลอก</button></div>
          </div>

          <div class="template" style="margin-top:12px">
            <div style="font-weight:700;margin-bottom:6px">Objective</div>
            <div id="tplObjective" class="muted">เพิ่มความรู้เรื่องโภชนาการและกระตุ้นการออกกำลังกาย 3 วัน/สัปดาห์</div>

            <div style="font-weight:700;margin-top:8px;margin-bottom:6px">Materials</div>
            <div id="tplMaterials" class="muted">ใบงาน, ตัวอย่างฉลาก, อุปกรณ์กีฬาเบื้องต้น</div>

            <div style="font-weight:700;margin-top:8px;margin-bottom:6px">Steps</div>
            <div id="tplSteps" class="muted">1) ดึงความสนใจ 10 นาที 2) กิจกรรมกลุ่ม 20–30 นาที 3) สรุปและมอบหมายงานบ้าน 10 นาที</div>

            <div style="font-weight:700;margin-top:8px;margin-bottom:6px">Evaluation</div>
            <div id="tplEval" class="muted">pre/post quiz, checklist พฤติกรรม, บันทึกกิจกรรม</div>
          </div>
        </div>

      </section>

      <!-- RIGHT: planner & summary -->
      <aside class="right-col">
        <div class="card fade-in">
          <div style="display:flex;justify-content:space-between;align-items:center">
            <div>
              <div class="muted">สร้างแผนกิจกรรม</div>
              <div style="font-weight:800">ปฏิทิน & รายการ (สั้น)</div>
            </div>
            <div class="muted">ส่งออก/พิมพ์ได้</div>
          </div>

          <div style="margin-top:12px">
            <label>วันที่</label>
            <input id="planDate" type="date">
            <label style="margin-top:8px">เวลา</label>
            <input id="planTime" type="time" value="09:00">
            <label style="margin-top:8px">กิจกรรม</label>
            <select id="planActivity"></select>
            <label style="margin-top:8px">ผู้รับผิดชอบ</label>
            <input id="planTeacher" placeholder="เช่น ครูสมชาย">
            <div class="action-row" style="margin-top:10px">
              <button id="btnAddToPlan" class="small">+ ใส่แผน</button>
              <button id="btnClearPlan" class="small danger">ล้างแผน</button>
            </div>
          </div>

          <div style="margin-top:12px">
            <div class="muted">รายการแผน</div>
            <div class="plan-list" id="planList" style="margin-top:8px"></div>
          </div>

          <div style="margin-top:12px;display:flex;gap:8px">
            <button id="btnPrintPlan" class="small ghost">พิมพ์สรุป</button>
            <button id="btnExportJSON" class="small ghost">ดาวน์โหลด JSON</button>
            <button id="btnSaveLocal" class="small">บันทึกเครื่องนี้</button>
          </div>

        </div>

        <div class="card fade-in" style="margin-top:14px">
          <div style="display:flex;justify-content:space-between;align-items:center">
            <div>
              <div class="muted">คำแนะนำติดตามผล</div>
              <div style="font-weight:700">แนวปฏิบัติสั้น ๆ สำหรับครู</div>
            </div>
          </div>

          <ul style="padding-left:18px;margin-top:10px;color:var(--muted)">
            <li>แบบสำรวจก่อน-หลัง (pre/post)</li>
            <li>บันทึกกิจกรรมรายสัปดาห์</li>
            <li>เช็คลิสต์การปฏิบัติ (ครูประเมิน)</li>
            <li>สรุปรายเดือนเพื่อนำเสนอผู้บริหาร</li>
          </ul>

          <div style="margin-top:12px">
            <button id="btnShareTips" class="small ghost">คำแนะนำเชิงปฏิบัติ</button>
          </div>
        </div>

        <div class="footer">© การพัฒนาสุขภาพนักเรียน — สร้างโดยเครื่องมือช่วยออกแบบ</div>
      </aside>
    </main>
  </div>

<script>
/* ===========================
   Data & Initial sample library
   =========================== */
function idGen(){ return 'id_'+Math.random().toString(36).slice(2,9); }

let library = [
  { id:idGen(), category:'physical', name:'เดินเร็ว 20 นาที', duration:20, objective:'เพิ่มการเคลื่อนไหว', materials:'รองเท้ากีฬา', evaluation:'บันทึกจำนวนครั้ง' },
  { id:idGen(), category:'physical', name:'Circuit 6 ท่า 30 นาที', duration:30, objective:'เพิ่มความแข็งแรง', materials:'พรม, ดัมเบล', evaluation:'ครูสังเกต' },
  { id:idGen(), category:'nutrition', name:'เวิร์กช็อปอ่านฉลาก 45 นาที', duration:45, objective:'รู้เท่าทันโภชนาการ', materials:'ฉลากอาหาร', evaluation:'pre/post quiz' },
  { id:idGen(), category:'mental', name:'หายใจผ่อนคลาย 10 นาที', duration:10, objective:'ลดความเครียด', materials:'พื้นที่สงบ', evaluation:'แบบสำรวจสั้น' },
  { id:idGen(), category:'life-skill', name:'วางแผนมื้ออาหาร', duration:40, objective:'ฝึกวางแผน', materials:'ใบงาน', evaluation:'งานนำเสนอ' },
];

/* ===========================
   DOM refs
   =========================== */
const activityList = document.getElementById('activityList');
const activityCategory = document.getElementById('activityCategory');
const activityName = document.getElementById('activityName');
const activityDuration = document.getElementById('activityDuration');
const btnAddActivity = document.getElementById('btnAddActivity');
const btnAutoSuggestions = document.getElementById('btnAutoSuggestions');
const libCount = document.getElementById('libCount');

const planActivity = document.getElementById('planActivity');
const planDate = document.getElementById('planDate');
const planTime = document.getElementById('planTime');
const planTeacher = document.getElementById('planTeacher');
const btnAddToPlan = document.getElementById('btnAddToPlan');
const planList = document.getElementById('planList');
const planCount = document.getElementById('planCount');
const btnPrintPlan = document.getElementById('btnPrintPlan');
const btnExportJSON = document.getElementById('btnExportJSON');
const btnSaveLocal = document.getElementById('btnSaveLocal');
const btnCopyTemplate = document.getElementById('btnCopyTemplate');
const tplObjective = document.getElementById('tplObjective');

/* ===========================
   Planner state
   =========================== */
let plan = [];

/* ===========================
   Render functions
   =========================== */
function renderLibrary(){
  activityList.innerHTML = '';
  if(library.length===0){
    activityList.innerHTML = '<div class="muted">ไม่มีกิจกรรมในไลบรารี</div>';
  }
  library.forEach(item=>{
    const li = document.createElement('li');
    li.innerHTML = `
      <div style="flex:1">
        <div style="font-weight:700">${escapeHtml(item.name)}</div>
        <div class="meta">${item.category} • ${item.duration} นาที • ${escapeHtml(item.objective||'')}</div>
      </div>
      <div style="display:flex;gap:8px;align-items:center">
        <button class="small ghost" data-id="${item.id}" onclick="useInPlan(event)">ใช้</button>
        <button class="small" data-id="${item.id}" onclick="removeLib(event)" style="background:#f97316">ลบ</button>
      </div>
    `;
    activityList.appendChild(li);
  });
  libCount.textContent = library.length;
  renderPlanActivityOptions();
}

function renderPlanActivityOptions(){
  planActivity.innerHTML = '';
  library.forEach(it=>{
    const opt = document.createElement('option');
    opt.value = it.id;
    opt.textContent = `${it.name} (${it.duration} นาที)`;
    planActivity.appendChild(opt);
  });
}

/* ===========================
   Library actions
   =========================== */
btnAddActivity.addEventListener('click',()=>{
  const name = activityName.value.trim();
  if(!name){ alert('กรุณากรอกชื่อกิจกรรม'); return; }
  const item = { id:idGen(), category: activityCategory.value, name, duration: Number(activityDuration.value)||30, objective:'', materials:'', evaluation:'' };
  library.unshift(item);
  activityName.value=''; activityDuration.value=30;
  renderLibrary();
});

window.removeLib = function(ev){
  const id = ev.currentTarget.dataset.id;
  if(!confirm('ลบกิจกรรมนี้จากไลบรารี?')) return;
  library = library.filter(i=>i.id!==id);
  renderLibrary();
};

window.useInPlan = function(ev){
  const id = ev.currentTarget.dataset.id;
  const act = library.find(l=>l.id===id);
  if(!act) return;
  // default date to today
  const d = new Date().toISOString().slice(0,10);
  plan.push({ id:idGen(), activityId:act.id, name:act.name, date:d, time:'09:00', teacher:'ไม่ระบุ', duration:act.duration, category:act.category });
  renderPlan();
};

/* ===========================
   Plan actions
   =========================== */
btnAddToPlan.addEventListener('click',()=>{
  const aid = planActivity.value;
  if(!aid){ alert('เลือกกิจกรรมก่อน'); return; }
  const act = library.find(l=>l.id===aid);
  const date = planDate.value || new Date().toISOString().slice(0,10);
  const time = planTime.value || '09:00';
  const teacher = planTeacher.value || 'ไม่ระบุ';
  plan.push({ id:idGen(), activityId:aid, name:act.name, date, time, teacher, duration:act.duration, category:act.category });
  renderPlan();
});

function renderPlan(){
  planList.innerHTML = '';
  if(plan.length===0){
    planList.innerHTML = '<div class="muted">ยังไม่มีรายการแผน</div>';
    planCount.textContent = 0;
    return;
  }
  // sort
  plan.sort((a,b)=> (a.date+a.time).localeCompare(b.date+b.time));
  plan.forEach(p=>{
    const div = document.createElement('div');
    div.className = 'entry';
    div.innerHTML = `
      <div style="flex:1">
        <div style="font-weight:700">${escapeHtml(p.name)}</div>
        <div class="meta">${p.date} ${p.time} • ${p.duration} นาที • ครู: ${escapeHtml(p.teacher)}</div>
      </div>
      <div style="display:flex;gap:6px;align-items:center">
        <button class="small ghost" data-id="${p.id}" onclick="editPlan(event)">แก้ไข</button>
        <button class="small" data-id="${p.id}" onclick="removePlan(event)" style="background:#ef4444">ลบ</button>
      </div>
    `;
    planList.appendChild(div);
  });
  planCount.textContent = plan.length;
  // update last saved hint
  document.getElementById('lastSaved').textContent = new Date().toLocaleString();
}

window.removePlan = function(ev){
  const id = ev.currentTarget.dataset.id;
  if(!confirm('ลบรายการนี้ออกจากแผน?')) return;
  plan = plan.filter(x=>x.id!==id);
  renderPlan();
};

window.editPlan = function(ev){
  const id = ev.currentTarget.dataset.id;
  const p = plan.find(x=>x.id===id);
  if(!p) return;
  const nd = prompt('วันที่ (YYYY-MM-DD)', p.date);
  if(nd===null) return;
  const nt = prompt('เวลา (HH:MM)', p.time);
  if(nt===null) return;
  const ntc = prompt('ผู้รับผิดชอบ', p.teacher);
  if(ntc===null) return;
  p.date=nd; p.time=nt; p.teacher=ntc;
  renderPlan();
};

/* ===========================
   Utilities
   =========================== */
function escapeHtml(s){ return String(s).replace(/[&<>"']/g, m => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[m])); }

/* ===========================
   Export / Save
   =========================== */
btnPrintPlan.addEventListener('click',()=>{
  const w = window.open('','_blank','width=900,height=700');
  w.document.write(`<html><head><meta charset="utf-8"><title>สรุปแผนกิจกรรม</title></head><body><h2>สรุปแผนกิจกรรม</h2>`);
  if(plan.length===0) w.document.write('<p>ไม่มีรายการ</p>');
  else{
    w.document.write('<ul>');
    plan.forEach(p=> w.document.write(`<li>${p.date} ${p.time} — ${p.name} (${p.duration} นาที) — ครู: ${p.teacher}</li>`));
    w.document.write('</ul>');
  }
  w.document.write('</body></html>');
  w.document.close();
  w.print();
});

btnExportJSON.addEventListener('click',()=>{
  const payload = { meta:{title: document.getElementById('planTitle').value || 'Plan', ageGroup: document.getElementById('ageGroup').value, createdAt:new Date().toISOString()}, library, plan };
  const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(payload,null,2));
  const a = document.createElement('a'); a.href=dataStr; a.download = `school_health_plan_${new Date().toISOString().slice(0,10)}.json`;
  document.body.appendChild(a); a.click(); a.remove();
});

btnSaveLocal.addEventListener('click',()=>{
  const key = 'school_health_saved_plan';
  const payload = { meta:{title: document.getElementById('planTitle').value || '', createdAt:new Date().toISOString()}, library, plan };
  localStorage.setItem(key, JSON.stringify(payload));
  alert('บันทึกไว้บนเครื่องเรียบร้อย');
});

/* ===========================
   Template copy
   =========================== */
btnCopyTemplate.addEventListener('click', async ()=>{
  const txt = `Objective:\n${tplObjective.textContent}\n\nSteps:\n${document.getElementById('tplSteps').textContent}\n\nEvaluation:\n${document.getElementById('tplEval').textContent}`;
  try{
    await navigator.clipboard.writeText(txt);
    alert('คัดลอกเทมเพลตไปยังคลิปบอร์ดแล้ว');
  }catch(e){ alert('ไม่สามารถคัดลอกได้'); }
});

/* ===========================
   Auto suggestions (fill sample plan)
   =========================== */
btnAutoSuggestions.addEventListener('click',()=>{
  if(!confirm('สร้างแผนตัวอย่าง 5 วันจากไลบรารี?')) return;
  plan = [];
  const picks = library.slice(0,5);
  const today = new Date();
  for(let i=0;i<picks.length;i++){
    const d = new Date(today); d.setDate(today.getDate()+i);
    plan.push({ id:idGen(), activityId:picks[i].id, name:picks[i].name, date: d.toISOString().slice(0,10), time:'09:00', teacher:'ครูผู้สอน', duration:picks[i].duration, category:picks[i].category });
  }
  renderPlan();
});

/* ===========================
   Theme toggle (simple demo)
   =========================== */
document.getElementById('btnThemeToggle').addEventListener('click',()=>{
  const b = document.body;
  if(b.style.background.includes('linear-gradient')){ // switch to dark-ish
    b.style.background = '#0b1220';
    b.style.color = '#e6eefb';
    document.querySelectorAll('.card').forEach(c=> c.style.background = 'linear-gradient(180deg,#071025,#071025)');
  }else{
    b.style.background = 'linear-gradient(180deg,#eef6ff 0%,#f8fbff 100%)';
    b.style.color = '#0f172a';
    document.querySelectorAll('.card').forEach(c=> c.style.background = 'var(--card)');
  }
});

/* ===========================
   Init
   =========================== */
renderLibrary();
renderPlan();
document.getElementById('lastSaved').textContent = 'ยังไม่ได้บันทึก';
document.getElementById('tplObjective').textContent = 'เพิ่มความรู้ด้านโภชนาการและส่งเสริมกิจกรรมทางกายให้เกิดเป็นพฤติกรรม';
</script>
</body>
</html>
