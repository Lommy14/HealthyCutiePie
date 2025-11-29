<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="utf-8" />
  <title>เครื่องมือออกแบบแนวทางเสริมสร้างสุขภาพของนักเรียน</title>
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <style>
    :root{
      --bg:#f3f6fb; --card:#fff; --accent:#1f3b70; --muted:#64748b;
    }
    *{box-sizing:border-box;font-family:"Sarabun",system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif}
    body{margin:0;background:var(--bg);padding:20px;display:flex;justify-content:center}
    .container{width:100%;max-width:1150px;background:var(--card);border-radius:12px;padding:20px;box-shadow:0 10px 30px rgba(0,0,0,0.08)}
    h1{margin:0 0 8px;color:var(--accent);font-size:22px}
    p.lead{margin:0 0 12px;color:var(--muted);font-size:13px}
    .flex{display:flex;gap:16px;flex-wrap:wrap}
    .card{background:#f9fbff;border-radius:10px;padding:14px;border:1px solid #e6eefb;flex:1;min-width:280px}
    label{font-size:13px;font-weight:600;color:#0f172a;display:block;margin-bottom:6px}
    select,input,textarea{width:100%;padding:8px;border-radius:8px;border:1px solid #cbd5e1;font-size:14px}
    textarea{min-height:80px;resize:vertical}
    button{background:#2563eb;color:#fff;border:0;padding:8px 12px;border-radius:999px;cursor:pointer;font-weight:600}
    .small{padding:6px 10px;font-size:13px;border-radius:8px}
    .pill{display:inline-block;background:#eef2ff;color:#1d4ed8;padding:6px 10px;border-radius:999px;font-size:13px;margin-right:6px}
    .list{margin:8px 0 0;padding:0;list-style:none}
    .list li{background:#fff;padding:10px;border-radius:8px;margin-bottom:8px;border:1px solid #e6eefb;display:flex;justify-content:space-between;gap:8px;align-items:center}
    .muted{color:var(--muted);font-size:13px}
    .meta{font-size:12px;color:#475569}
    .template{background:#fff;padding:10px;border-radius:8px;border:1px dashed #e6eefb;margin-top:8px}
    .tools{display:flex;gap:8px;flex-wrap:wrap;margin-top:10px}
    .danger{background:#ef4444}
    .success{background:#10b981}
    .hide{display:none}
    .summary{background:#f1f5f9;padding:10px;border-radius:8px;margin-top:10px;color:#0f172a}
    .grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}
    @media(max-width:880px){.grid{grid-template-columns:1fr}}
    .right-col{min-width:320px;max-width:420px}
    .badge{display:inline-block;padding:4px 8px;border-radius:999px;background:#e0edff;color:#1d4ed8;font-size:12px}
    .action-row{display:flex;gap:8px}
  </style>
</head>
<body>
  <div class="container">
    <h1>🧭 เครื่องมือออกแบบแนวทางเสริมสร้างสุขภาพของนักเรียน</h1>
    <p class="lead">สร้างแผนกิจกรรมสุขภาพที่เหมาะกับช่วงอายุ/ระดับชั้น — รวมกิจกรรมทางกาย โภชนาการ สุขภาพจิต และการติดตามผล แบบใช้งานได้จริงสำหรับครูและผู้บริหาร</p>

    <div class="grid">
      <!-- LEFT: settings & library -->
      <div>
        <div class="card">
          <h2 style="margin:0 0 8px">1) ข้อมูลพื้นฐาน / เลือกกลุ่มเป้าหมาย</h2>
          <label for="ageGroup">ช่วงอายุ / ระดับชั้น</label>
          <select id="ageGroup">
            <option value="primary">ป.1–ป.6 (ประถมศึกษา)</option>
            <option value="lower-sec">ม.1–ม.3 (มัธยมต้น)</option>
            <option value="upper-sec">ม.4–ม.6 (มัธยมปลาย)</option>
            <option value="voc">อาชีวะ / นักศึกษา</option>
          </select>
          <div style="margin-top:8px" id="groupInfo" class="muted"></div>
        </div>

        <div class="card" style="margin-top:12px">
          <h2 style="margin:0 0 8px">2) ไลบรารีกิจกรรม (ตัวอย่าง)</h2>
          <p class="muted">ลากความคิดจากรายการตัวอย่าง หรือกดเพิ่มแล้วปรับเป็นของคุณ</p>

          <div style="display:flex;gap:8px;margin-bottom:8px;flex-wrap:wrap">
            <span class="pill">โภชนาการ: เวิร์กช็อปอ่านฉลาก</span>
            <span class="pill">กาย: เดินเร็ว 20 นาที</span>
            <span class="pill">จิตใจ: เทคนิคหายใจ 5-5-5</span>
            <span class="pill">ทักษะชีวิต: วางแผนมื้ออาหาร</span>
          </div>

          <label for="activityCategory">ประเภทกิจกรรม</label>
          <select id="activityCategory">
            <option value="physical">การเคลื่อนไหว/กีฬา</option>
            <option value="nutrition">โภชนาการ</option>
            <option value="mental">สุขภาพจิต</option>
            <option value="life-skill">ทักษะชีวิต</option>
            <option value="screen">ลดเวลาใช้จอ</option>
          </select>

          <label for="activityName" style="margin-top:8px">ชื่อกิจกรรม (ตัวอย่าง)</label>
          <input id="activityName" placeholder="เช่น เดินเร็ว 20 นาที / เวิร์กช็อปสอนอ่านฉลาก">

          <label for="activityDuration" style="margin-top:8px">ระยะเวลา (นาที)</label>
          <input id="activityDuration" type="number" min="5" value="30">

          <label for="activityObjective" style="margin-top:8px">วัตถุประสงค์ (สั้น ๆ)</label>
          <input id="activityObjective" placeholder="เช่น เพิ่มความรู้เรื่องโภชนาการ / เพิ่มความอดทน">

          <label for="activityMaterials" style="margin-top:8px">อุปกรณ์/วัสดุ</label>
          <input id="activityMaterials" placeholder="เช่น ลูกเชือก, ใบงาน, ป้ายฉลากอาหาร">

          <div class="tools">
            <button id="btnAddActivity" class="small">เพิ่มลงไลบรารี</button>
            <button id="btnResetLib" class="small danger">รีเซ็ทตัวอย่าง</button>
          </div>

          <ul id="activityList" class="list" style="margin-top:10px"></ul>
        </div>

        <div class="card" style="margin-top:12px">
          <h2 style="margin:0 0 8px">3) เทมเพลตแผนการสอน / กิจกรรม</h2>
          <p class="muted">คัดลอกไปใช้เป็นกรอบเมื่อต้องการส่งแผนให้ผู้บริหารหรือครูร่วม</p>
          <div class="template">
            <strong>Objective:</strong>
            <div id="tplObjective" class="meta">[วัตถุประสงค์เช่น เพิ่มความรู้เรื่องโภชนาการ]</div>
            <strong>Materials:</strong>
            <div id="tplMaterials" class="meta">[อุปกรณ์ เช่น ใบงาน ป้ายฉลาก]</div>
            <strong>Steps:</strong>
            <div id="tplSteps" class="meta">1) นำเสนอ 10 นาที 2) กิจกรรมกลุ่ม 15 นาที 3) สรุปและประเมิน 5 นาที</div>
            <strong>Evaluation:</strong>
            <div id="tplEval" class="meta">แบบสอบถามก่อน/หลังหรือสังเกตพฤติกรรม</div>
            <div style="margin-top:8px"><button id="btnCopyTemplate" class="small">คัดลอกเทมเพลต</button></div>
          </div>
        </div>
      </div>

      <!-- RIGHT: planner & summary -->
      <div class="right-col">
        <div class="card">
          <h2 style="margin:0 0 8px">4) สร้างแผนกิจกรรม (แผนรายสัปดาห์/รายเดือน)</h2>

          <label for="planDate">วันที่ของกิจกรรม</label>
          <input id="planDate" type="date">

          <label for="planTime" style="margin-top:8px">เวลา (เริ่ม)</label>
          <input id="planTime" type="time">

          <label for="planActivity" style="margin-top:8px">เลือกกิจกรรมจากไลบรารี</label>
          <select id="planActivity"></select>

          <label for="planTeacher" style="margin-top:8px">ผู้รับผิดชอบ / ครู</label>
          <input id="planTeacher" placeholder="เช่น ครูพลอย">

          <div class="action-row" style="margin-top:10px">
            <button id="btnAddToPlan" class="small">เพิ่มเข้าแผน</button>
            <button id="btnClearPlan" class="small danger">ล้างแผนทั้งหมด</button>
          </div>

          <ul id="planList" class="list" style="margin-top:10px"></ul>

          <div style="margin-top:8px">
            <button id="btnPrintPlan" class="small">พิมพ์/ดาวน์โหลดสรุปแผน</button>
            <button id="btnExportJSON" class="small">ดาวน์โหลด JSON (แผน)</button>
          </div>

          <div class="summary" id="planSummary" style="display:none"></div>
        </div>

        <div class="card" style="margin-top:12px">
          <h2 style="margin:0 0 8px">คำแนะนำการวัดผล & ติดตาม</h2>
          <p class="muted">ตัวอย่างวิธีการติดตามผลที่ครูสามารถใช้ได้จริง</p>
          <ul class="muted" style="padding-left:18px;margin:6px 0 0">
            <li>แบบสำรวจความรู้ก่อน-หลัง (pre/post test)</li>
            <li>บันทึกความถี่กิจกรรม (เช่น จำนวนวันออกกำลังกาย/สัปดาห์)</li>
            <li>การสังเกตพฤติกรรม (ครูประเมินเป็น checklist)</li>
            <li>บันทึกความรู้สึก/สุขภาพจิต (สั้น ๆ เป็นไดอารี่ 1–3 ข้อ)</li>
            <li>สรุปเชิงปริมาณเป็นรายเดือนเพื่อเสนอผู้บริหาร</li>
          </ul>
          <div style="margin-top:8px">
            <button id="btnAutoSuggestions" class="small success">สร้างแผนตัวอย่างอัตโนมัติ</button>
          </div>
        </div>
      </div>
    </div>

    <div style="margin-top:12px" class="muted">
      ⚠️ เครื่องมือนี้เป็นเครื่องมือช่วยออกแบบและให้คำแนะนำเชิงการศึกษา ไม่ใช่คำแนะนำทางการแพทย์โดยตรง หากต้องการจัดโปรแกรมเชิงคลินิกหรือสำหรับเด็กที่มีภาวะสุขภาพพิเศษ ควรปรึกษาผู้เชี่ยวชาญ
    </div>
  </div>

  <script>
    // ---------- ข้อมูลอ้างอิงช่วงอายุ ----------
    const ageHints = {
      "primary":"เน้นกิจกรรมสนุก สั้น ๆ 10-20 นาที ควบคุมอาหารที่พกมาโรงเรียน",
      "lower-sec":"เพิ่มความเข้มข้นมากขึ้น ฝึกทักษะกลุ่มและการรู้เท่าทันสื่อ",
      "upper-sec":"เสริมทักษะดูแลตัวเอง วางแผนมื้ออาหาร และฝึกการออกกำลังกายแบบมีเป้าหมาย",
      "voc":"ปรับเป็นกิจกรรมที่เชื่อมโยงอาชีพ เน้นสุขภาพการทำงาน"
    };
    const ageGroupSelect = document.getElementById('ageGroup');
    const groupInfo = document.getElementById('groupInfo');
    function updateAgeInfo(){ groupInfo.textContent = ageHints[ageGroupSelect.value] || ''; }
    ageGroupSelect.addEventListener('change',updateAgeInfo);
    updateAgeInfo();

    // ---------- ไลบรารีกิจกรรม (เริ่มต้นตัวอย่าง) ----------
    let library = [
      { id: idGen(), category:'physical', name:'เดินเร็ว 20 นาที', duration:20, objective:'เพิ่มการออกกำลังกายต่อวัน', materials:'รองเท้ากีฬา', evaluation:'จดจำนวนก้าว/ความรู้สึก' },
      { id: idGen(), category:'physical', name:'Circuit สลับ 6 ท่า (30 นาที)', duration:30, objective:'เพิ่มความแข็งแรงและความทนทาน', materials:'พรมออกกำลังกาย', evaluation:'count reps/ครูสังเกต' },
      { id: idGen(), category:'nutrition', name:'เวิร์กช็อปอ่านฉลากอาหาร (45 นาที)', duration:45, objective:'รู้เท่าทันฉลากโภชนาการ', materials:'ตัวอย่างฉลาก ใบงาน', evaluation:'pre/post quiz' },
      { id: idGen(), category:'mental', name:'ฝึกหายใจ 5-5-5 + ตระหนักรู้ (15 นาที)', duration:15, objective:'ลดความเครียดระหว่างเรียน', materials:'พื้นที่สงบ', evaluation:'แบบประเมินความเครียดสั้น' },
      { id: idGen(), category:'life-skill', name:'วางแผนมื้ออาหารสำหรับนักเรียน', duration:40, objective:'ฝึกการวางแผนโภชนาการ', materials:'ใบงาน ปากกา', evaluation:'งานเสนอแผน' },
      { id: idGen(), category:'screen', name:'ชาเลนจ์ลดเวลาใช้จอ 1 สัปดาห์', duration:7*24*60, objective:'ลดเวลาใช้จอ', materials:'บันทึกกิจกรรม', evaluation:'บันทึกและสรุป' }
    ];

    // ---------- DOM อ้างอิง ----------
    const activityList = document.getElementById('activityList');
    const activityCategory = document.getElementById('activityCategory');
    const activityName = document.getElementById('activityName');
    const activityDuration = document.getElementById('activityDuration');
    const activityObjective = document.getElementById('activityObjective');
    const activityMaterials = document.getElementById('activityMaterials');
    const btnAddActivity = document.getElementById('btnAddActivity');
    const btnResetLib = document.getElementById('btnResetLib');
    const planActivity = document.getElementById('planActivity');

    // ---------- Planner ----------
    const planDate = document.getElementById('planDate');
    const planTime = document.getElementById('planTime');
    const planTeacher = document.getElementById('planTeacher');
    const btnAddToPlan = document.getElementById('btnAddToPlan');
    const planList = document.getElementById('planList');
    const planSummary = document.getElementById('planSummary');
    const btnPrintPlan = document.getElementById('btnPrintPlan');
    const btnExportJSON = document.getElementById('btnExportJSON');
    const btnCopyTemplate = document.getElementById('btnCopyTemplate');
    const tplObjective = document.getElementById('tplObjective');
    const tplMaterials = document.getElementById('tplMaterials');
    const tplSteps = document.getElementById('tplSteps');
    const tplEval = document.getElementById('tplEval');
    const btnAutoSuggestions = document.getElementById('btnAutoSuggestions');
    const btnClearPlan = document.getElementById('btnClearPlan');

    // ---------- Utility ----------
    function idGen(){ return 'id_'+Math.random().toString(36).slice(2,9); }

    // ---------- Render library ----------
    function renderLibrary(){
      activityList.innerHTML = '';
      library.forEach(item=>{
        const li = document.createElement('li');
        li.innerHTML = `<div style="flex:1">
          <div style="font-weight:600">${item.name}</div>
          <div class="meta">${item.category} • ${item.duration} นาที • ${item.objective}</div>
        </div>
        <div style="display:flex;gap:6px;align-items:center">
          <button class="small" data-id="${item.id}" onclick="addToPlanFromLib(event)">ใช้ในแผน</button>
          <button class="small" data-id="${item.id}" onclick="removeFromLib(event)" style="background:#ef4444">ลบ</button>
        </div>`;
        activityList.appendChild(li);
      });
      // update planActivity select
      renderPlanActivityOptions();
    }

    // เพิ่มกิจกรรมใหม่เข้าไลบรารี
    btnAddActivity.addEventListener('click',()=>{
      const name = activityName.value.trim();
      if(!name){ alert('กรุณาใส่ชื่อกิจกรรม'); return; }
      const item = {
        id: idGen(),
        category: activityCategory.value,
        name,
        duration: Number(activityDuration.value)||30,
        objective: activityObjective.value||'',
        materials: activityMaterials.value||'',
        evaluation: 'แบบประเมิน/สังเกต'
      };
      library.unshift(item);
      activityName.value=''; activityObjective.value=''; activityMaterials.value=''; activityDuration.value=30;
      renderLibrary();
    });

    // รีเซ็ทไลบรารีเป็นค่าเริ่มต้น
    btnResetLib.addEventListener('click',()=>{
      if(!confirm('ต้องการรีเซ็ทไลบรารีตัวอย่างหรือไม่? จะลบรายการที่เพิ่มทั้งหมด')) return;
      // simple reset by reloading page state (or reassign default)
      location.reload();
    });

    window.removeFromLib = function(ev){
      const id = ev.currentTarget.dataset.id;
      library = library.filter(i=>i.id!==id);
      renderLibrary();
    };

    // ---------- Planner data ----------
    let plan = []; // array of {id, activityId, date, time, teacher}

    function renderPlanActivityOptions(){
      planActivity.innerHTML = '';
      library.forEach(it=>{
        const opt = document.createElement('option');
        opt.value = it.id;
        opt.textContent = `${it.name} (${it.duration} นาที)`;
        planActivity.appendChild(opt);
      });
    }

    // add to plan (from planner form)
    btnAddToPlan.addEventListener('click',()=>{
      const aid = planActivity.value;
      if(!aid){ alert('เลือกกิจกรรมก่อน'); return; }
      const date = planDate.value;
      const time = planTime.value || '09:00';
      const teacher = planTeacher.value || 'ไม่ระบุ';
      const act = library.find(l=>l.id===aid);
      const entry = { id: idGen(), activityId:aid, name:act.name, date, time, teacher, duration:act.duration, category:act.category };
      plan.push(entry);
      renderPlan();
    });

    // add to plan directly from lib button
    window.addToPlanFromLib = function(e){
      const id = e.currentTarget.dataset.id;
      const act = library.find(l=>l.id===id);
      const date = planDate.value || new Date().toISOString().slice(0,10);
      const time = planTime.value || '10:00';
      plan.push({ id:idGen(), activityId: id, name: act.name, date, time, teacher: planTeacher.value||'ไม่ระบุ', duration:act.duration, category:act.category });
      renderPlan();
    };

    // render plan list
    function renderPlan(){
      planList.innerHTML = '';
      if(plan.length===0){
        planList.innerHTML = '<div class="muted" style="padding:8px">ยังไม่มีรายการแผน</div>';
        planSummary.style.display='none';
        return;
      }
      // sort by date+time
      plan.sort((a,b)=>{
        const ta = (a.date||'')+' '+(a.time||'');
        const tb = (b.date||'')+' '+(b.time||'');
        return ta.localeCompare(tb);
      });
      plan.forEach(item=>{
        const li = document.createElement('li');
        li.innerHTML = `<div style="flex:1">
          <div style="font-weight:600">${item.name}</div>
          <div class="meta">${item.date||'ไม่ระบุ'} ${item.time||''} • ${item.duration} นาที • ครู: ${item.teacher}</div>
        </div>
        <div style="display:flex;gap:6px;align-items:center">
          <button class="small" data-id="${item.id}" onclick="editPlanItem(event)">แก้ไข</button>
          <button class="small" data-id="${item.id}" onclick="removePlanItem(event)" style="background:#ef4444">ลบ</button>
        </div>`;
        planList.appendChild(li);
      });
      // update summary
      renderPlanSummary();
    }

    window.removePlanItem = function(e){
      const id = e.currentTarget.dataset.id;
      plan = plan.filter(p=>p.id!==id);
      renderPlan();
    };

    window.editPlanItem = function(e){
      const id = e.currentTarget.dataset.id;
      const item = plan.find(p=>p.id===id);
      if(!item) return;
      // simple inline edit using prompt (keeps code short)
      const newDate = prompt('วันที่ (YYYY-MM-DD)', item.date||'');
      if(newDate===null) return;
      const newTime = prompt('เวลา (HH:MM)', item.time||'09:00');
      if(newTime===null) return;
      const newTeacher = prompt('ผู้รับผิดชอบ', item.teacher||'');
      if(newTeacher===null) return;
      item.date = newDate; item.time = newTime; item.teacher = newTeacher;
      renderPlan();
    };

    function renderPlanSummary(){
      if(plan.length===0){ planSummary.style.display='none'; return; }
      planSummary.style.display='block';
      // group by date
      const byDate = {};
      plan.forEach(p=>{
        const d = p.date || 'ไม่ระบุวันที่';
        if(!byDate[d]) byDate[d]=[];
        byDate[d].push(p);
      });
      let html = '<strong>สรุปแผนกิจกรรม</strong><br>';
      for(const d of Object.keys(byDate)){
        html += `<div style="margin-top:8px"><em>${d}</em><ul style="padding-left:16px">`;
        byDate[d].forEach(it=>{ html += `<li>${it.time||''} - ${it.name} (${it.duration} นาที) • ครู: ${it.teacher}</li>`; });
        html += '</ul></div>';
      }
      planSummary.innerHTML = html;
    }

    // print plan (opens print dialog)
    btnPrintPlan.addEventListener('click',()=>{
      // prepare print-friendly view: open new window with summary
      const w = window.open('','_blank','width=900,height=700');
      const title = document.querySelector('h1').textContent;
      w.document.write(`<html><head><title>${title} - สรุปแผน</title><meta charset="utf-8"></head><body><h2>${title}</h2>`);
      w.document.write(document.getElementById('planSummary').innerHTML || '<p>ไม่มีแผน</p>');
      w.document.write('</body></html>');
      w.document.close();
      w.print();
    });

    // export JSON
    btnExportJSON.addEventListener('click',()=>{
      const payload = { meta:{ageGroup:ageGroupSelect.value, createdAt:new Date().toISOString()}, library, plan };
      const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(payload,null,2));
      const a = document.createElement('a');
      a.href = dataStr;
      a.download = `school_health_plan_${new Date().toISOString().slice(0,10)}.json`;
      document.body.appendChild(a); a.click(); a.remove();
    });

    // populate initial UI
    renderLibrary();

    // copy template into clipboard
    btnCopyTemplate.addEventListener('click',()=>{
      const tpl = `Objective:\n${tplObjective.textContent}\n\nMaterials:\n${tplMaterials.textContent}\n\nSteps:\n${tplSteps.textContent}\n\nEvaluation:\n${tplEval.textContent}`;
      navigator.clipboard?.writeText(tpl).then(()=> alert('คัดลอกเทมเพลตเรียบร้อย')) .catch(()=> alert('ไม่สามารถคัดลอกได้'));
    });

    // auto suggestions (สร้างแผนตัวอย่างสั้น)
    btnAutoSuggestions.addEventListener('click',()=>{
      if(!confirm('สร้างแผนตัวอย่าง 1 สัปดาห์? จะเติมกิจกรรมจากไลบรารีอัตโนมัติ')) return;
      // clear plan
      plan = [];
      // choose up to 7 activities (or fewer if library small)
      const picks = library.slice(0,7);
      const today = new Date();
      for(let i=0;i<picks.length;i++){
        const d = new Date(today); d.setDate(today.getDate()+i);
        const dateStr = d.toISOString().slice(0,10);
        plan.push({ id:idGen(), activityId:picks[i].id, name:picks[i].name, date:dateStr, time:'09:00', teacher:'ครูผู้สอน', duration:picks[i].duration, category:picks[i].category});
      }
      renderPlan();
    });

    // clear plan
    btnClearPlan.addEventListener('click',()=>{
      if(!confirm('ล้างแผนทั้งหมดหรือไม่?')) return;
      plan = []; renderPlan();
    });

    // initial basic template text (editable in DOM if needed)
    tplObjective.textContent = 'เพิ่มความรู้และทักษะด้านโภชนาการ และกระตุ้นให้มีการออกกำลังกายเป็นประจำ';
    tplMaterials.textContent = 'ใบงาน ตัวอย่างฉลากอาหาร ไมโครโฟน (ถ้าจำเป็น) อุปกรณ์กีฬาเบื้องต้น';
    tplSteps.textContent = '1. แนะนำหัวข้อ/เกริ่น 2. กิจกรรมกลุ่ม/ทดลอง 3. สรุปและบ้านการบ้าน 4. ประเมินผลสั้น ๆ';
    tplEval.textContent = 'แบบสอบถามก่อน/หลัง และ checklist พฤติกรรม (เช่น ออกกำลังกาย 3 วัน/สัปดาห์)';

    // optional: when library is empty, show placeholder
    if(library.length===0) activityList.innerHTML = '<div class="muted">ยังไม่มีกิจกรรมในไลบรารี</div>';
  </script>
</body>
</html>
