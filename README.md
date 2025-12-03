<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>กระดานข่าวโรงเรียน</title>
<link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#f5f8ff;
    --card:#ffffff;
    --accent-1:#2563eb;
    --accent-2:#06b6d4;
    --muted:#6b7280;
    --glass: rgba(15,23,42,0.06);
    --radius:14px;
  }
  *{box-sizing:border-box;font-family:"Sarabun",system-ui,-apple-system,"Segoe UI",sans-serif}
  body{
    margin:0;background:var(--bg);padding:28px;display:flex;justify-content:center;
  }
  .wrap{width:100%;max-width:1000px}
  header{display:flex;align-items:center;gap:12px;padding:14px;border-radius:12px;background:linear-gradient(90deg,#eef6ff,#fbffff);box-shadow:0 8px 30px var(--glass);border:1px solid rgba(37,99,235,0.05)}
  .logo{width:56px;height:56px;border-radius:10px;background:linear-gradient(135deg,var(--accent-1),var(--accent-2));display:flex;align-items:center;justify-content:center;color:white;font-weight:700;font-size:18px}
  .brand h1{margin:0;font-size:18px;color:#0b3a8a}
  .brand p{margin:0;color:var(--muted);font-size:13px}

  main{display:grid;grid-template-columns:360px 1fr;gap:18px;margin-top:18px}
  @media(max-width:920px){main{grid-template-columns:1fr}}

  /* Card */
  .card{background:var(--card);border-radius:var(--radius);padding:14px;border:1px solid #eef4ff;box-shadow:0 6px 22px var(--glass)}
  .card h2{margin:0 0 8px 0;color:#0f172a;font-size:16px}

  /* Form */
  label{display:block;font-weight:600;margin-top:10px;color:#0b2447}
  input[type="text"], input[type="date"], select, textarea{width:100%;padding:10px;border-radius:10px;border:1px solid #e6eefc;background:#fff;margin-top:6px;font-size:14px}
  textarea{min-height:100px;resize:vertical}
  .checkbox-row{display:flex;flex-wrap:wrap;gap:8px;margin-top:8px}
  .checkbox-row label{display:flex;gap:6px;align-items:center;font-weight:500;color:#374151}

  .btn-row{display:flex;gap:8px;margin-top:12px}
  .btn{padding:10px 12px;border-radius:999px;border:0;font-weight:700;cursor:pointer;display:inline-flex;align-items:center;gap:8px}
  .btn.primary{background:linear-gradient(90deg,var(--accent-1),var(--accent-2));color:white;box-shadow:0 8px 20px rgba(37,99,235,0.12)}
  .btn.ghost{background:#f1f5f9;color:#0b1220;border:1px solid #e6eefc}
  .hint{font-size:13px;color:var(--muted);margin-top:8px}

  /* Right: list */
  .controls{display:flex;gap:8px;align-items:center;margin-bottom:12px;flex-wrap:wrap}
  .controls input[type="search"]{flex:1;padding:8px 10px;border-radius:10px;border:1px solid #e6eefc;background:#fff}
  .controls select{padding:8px 10px;border-radius:10px;border:1px solid #e6eefc;background:#fff}

  .pinned{margin-bottom:12px}
  .pinned h3{margin:0;font-size:15px;color:#0b2447}
  .pinned-list{display:flex;flex-direction:column;gap:10px}

  .news-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:12px}
  @media(max-width:720px){.news-grid{grid-template-columns:1fr}}

  .news-card{background:#fff;border-radius:12px;padding:12px;border:1px solid #eef4ff;box-shadow:0 6px 18px rgba(15,23,42,0.03);transition:transform .15s ease,box-shadow .15s ease}
  .news-card:hover{transform:translateY(-6px);box-shadow:0 16px 38px rgba(15,23,42,0.08)}
  .news-title{font-weight:700;color:#0b1220;font-size:15px}
  .meta-row{display:flex;gap:8px;align-items:center;flex-wrap:wrap;font-size:13px;color:var(--muted);margin-top:6px}
  .badge{padding:4px 8px;border-radius:999px;font-weight:700;font-size:12px}
  .badge.cat{background:#eef2ff;color:#1d4ed8}
  .badge.tgt{background:#ecfdf5;color:#15803d}
  .badge.pin{background:#fff7ed;color:#92400e}

  .news-body{font-size:14px;color:#374151;white-space:pre-line;margin-top:8px}
  .card-actions{display:flex;gap:8px;justify-content:flex-end;margin-top:10px}
  .action{padding:6px 8px;border-radius:999px;border:1px solid #eef4ff;background:#f8fafc;cursor:pointer;font-weight:600}
  .action.danger{background:#fff1f2;border-color:#fed7d7;color:var(--accent-1)}
  .empty{padding:18px;text-align:center;color:var(--muted);font-size:14px}

  footer{margin-top:18px;text-align:right;color:var(--muted);font-size:13px}
</style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="logo">สข</div>
      <div class="brand">
        <h1>กระดานข่าวโรงเรียน</h1>
        <p>บันทึก-แสดงข่าวสารภายในโรงเรียน (เก็บในเครื่อง)</p>
      </div>
    </header>

    <main>
      <!-- Left: form -->
      <section class="card">
        <h2>บันทึกข่าวใหม่</h2>

        <label for="title">หัวข้อข่าว</label>
        <input id="title" type="text" placeholder="เช่น ประกาศหยุดเรียน">

        <label for="date">วันที่ประกาศ</label>
        <input id="date" type="date">

        <label for="category">หมวดหมู่</label>
        <select id="category">
          <option>ทั่วไป</option>
          <option>การเรียนการสอน</option>
          <option>กิจกรรม</option>
          <option>ประชุม/อบรม</option>
          <option>งานวิชาการ</option>
          <option>อื่น ๆ</option>
        </select>

        <label>กลุ่มเป้าหมาย</label>
        <div class="checkbox-row" id="targets">
          <label><input type="checkbox" value="นักเรียน"> นักเรียน</label>
          <label><input type="checkbox" value="ครู"> ครู</label>
          <label><input type="checkbox" value="ผู้ปกครอง"> ผู้ปกครอง</label>
          <label><input type="checkbox" value="บุคลากร"> บุคลากร</label>
        </div>

        <label for="content">รายละเอียด</label>
        <textarea id="content" placeholder="ระบุเวลา สถานที่ หรือรายละเอียดเพิ่มเติม"></textarea>

        <div class="btn-row">
          <button class="btn primary" id="saveBtn">💾 บันทึก</button>
          <button class="btn ghost" id="resetBtn">🧹 ล้าง</button>
        </div>

        <p class="hint">ข่าวจะเก็บไว้ในเบราว์เซอร์นี้เท่านั้น (LocalStorage)</p>
      </section>

      <!-- Right: list -->
      <section class="card">
        <div class="controls">
          <input id="search" type="search" placeholder="ค้นหา หัวข้อหรือเนื้อหา">
          <select id="filter">
            <option value="">ทุกหมวดหมู่</option>
            <option>ทั่วไป</option>
            <option>การเรียนการสอน</option>
            <option>กิจกรรม</option>
            <option>ประชุม/อบรม</option>
            <option>งานวิชาการ</option>
            <option>อื่น ๆ</option>
          </select>
          <div style="margin-left:auto;display:flex;gap:8px">
            <button class="btn ghost" id="clearAll">🗑️ ลบทั้งหมด</button>
          </div>
        </div>

        <div class="pinned">
          <h3>ข่าวปักหมุด</h3>
          <div id="pinnedList" class="pinned-list"></div>
        </div>

        <hr style="border:none;border-top:1px solid #eef4ff;margin:8px 0">

        <div id="newsGrid" class="news-grid"></div>
        <div id="noNews" class="empty" style="display:none">ยังไม่มีข่าว</div>
      </section>
    </main>

    <footer>© กระดานข่าวโรงเรียน</footer>
  </div>

<script>
  // key for storage
  const STORAGE = 'schoolNews_simple_v1';

  // DOM
  const titleEl = document.getElementById('title');
  const dateEl = document.getElementById('date');
  const categoryEl = document.getElementById('category');
  const contentEl = document.getElementById('content');
  const targetsEl = document.getElementById('targets');

  const saveBtn = document.getElementById('saveBtn');
  const resetBtn = document.getElementById('resetBtn');
  const newsGrid = document.getElementById('newsGrid');
  const pinnedList = document.getElementById('pinnedList');
  const noNews = document.getElementById('noNews');

  const searchEl = document.getElementById('search');
  const filterEl = document.getElementById('filter');
  const clearAllBtn = document.getElementById('clearAll');

  let items = [];

  // init date default
  function setToday(){
    const t = new Date();
    dateEl.value = t.toISOString().slice(0,10);
  }

  // load/save
  function load(){
    const s = localStorage.getItem(STORAGE);
    if(s){
      try{ items = JSON.parse(s); }catch(e){ items = []; }
    } else items = [];
  }
  function save(){
    localStorage.setItem(STORAGE, JSON.stringify(items));
  }

  // helpers
  function formatDate(d){
    if(!d) return '-';
    const dt = new Date(d);
    return dt.toLocaleDateString();
  }
  function escape(s){
    if(!s && s !== 0) return '';
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/\n/g,'<br>');
  }

  // render lists
  function render(){
    // pinned first
    pinnedList.innerHTML = '';
    newsGrid.innerHTML = '';

    // sort pinned on top by pinned flag then date desc
    const sorted = items.slice().sort((a,b)=>{
      if(a.pinned && !b.pinned) return -1;
      if(!a.pinned && b.pinned) return 1;
      return (b.created || 0) - (a.created || 0);
    });

    // pinned
    const pinned = sorted.filter(i=>i.pinned);
    if(pinned.length === 0){
      pinnedList.innerHTML = '<div class="empty">ไม่มีข่าวปักหมุด</div>';
    } else {
      pinned.forEach(i=>{
        const el = document.createElement('div');
        el.className = 'news-card';
        el.innerHTML = `
          <div style="display:flex;justify-content:space-between;align-items:flex-start;gap:8px">
            <div style="min-width:0">
              <div class="news-title">${escape(i.title)}</div>
              <div class="meta-row"><span class="badge cat">${escape(i.category)}</span>
                <span style="color:var(--muted);margin-left:8px">${formatDate(i.date)}</span>
              </div>
            </div>
            <div style="display:flex;flex-direction:column;gap:8px">
              <button class="action" onclick="unpin(${i.id})">ยกเลิกปักหมุด</button>
              <button class="action" onclick="del(${i.id})">ลบ</button>
            </div>
          </div>
        `;
        pinnedList.appendChild(el);
      });
    }

    // filter/search for non-pinned (so pinned shown above)
    const q = (searchEl.value || '').trim().toLowerCase();
    const catFilter = filterEl.value || '';

    const list = sorted.filter(i=>{
      const text = (i.title + ' ' + i.content + ' ' + (i.targets||[]).join(' ')).toLowerCase();
      const okQ = !q || text.includes(q);
      const okCat = !catFilter || i.category === catFilter;
      return okQ && okCat && !i.pinned;
    });

    if(list.length === 0){
      noNews.style.display = 'block';
    } else {
      noNews.style.display = 'none';
      list.forEach(i=>{
        const card = document.createElement('div');
        card.className = 'news-card';
        card.innerHTML = `
          <div>
            <div class="news-title">${escape(i.title)}</div>
            <div class="meta-row">
              <span class="badge cat">${escape(i.category)}</span>
              <span class="badge tgt">${(i.targets && i.targets.length) ? escape(i.targets.join(', ')) : 'กลุ่มเป้าหมาย: ไม่ระบุ'}</span>
              <span style="margin-left:auto;color:var(--muted);font-weight:600">${formatDate(i.date)}</span>
            </div>
          </div>
          <div class="news-body">${escape(i.content)}</div>
          <div class="card-actions">
            <button class="action" onclick="pin(${i.id})">ปักหมุด</button>
            <button class="action" onclick="del(${i.id})">ลบ</button>
          </div>
        `;
        newsGrid.appendChild(card);
      });
    }
  }

  // actions
  function add(){
    const title = titleEl.value.trim();
    const date = dateEl.value;
    const category = categoryEl.value;
    const content = contentEl.value.trim();
    const checkboxes = targetsEl.querySelectorAll('input[type="checkbox"]');
    const targets = [];
    checkboxes.forEach(cb => { if(cb.checked) targets.push(cb.value) });

    if(!title){ alert('กรุณากรอกหัวข้อข่าว'); return; }

    const obj = {
      id: Date.now(),
      title, date, category, content, targets,
      pinned: false,
      created: Date.now()
    };
    items.push(obj);
    save();
    render();
    clearForm();
  }

  function del(id){
    if(!confirm('ต้องการลบข่าวนี้หรือไม่?')) return;
    items = items.filter(i=>i.id !== id);
    save(); render();
  }

  function pin(id){
    const idx = items.findIndex(i=>i.id===id);
    if(idx !== -1){ items[idx].pinned = true; save(); render(); }
  }
  function unpin(id){
    const idx = items.findIndex(i=>i.id===id);
    if(idx !== -1){ items[idx].pinned = false; save(); render(); }
  }

  function clearForm(){
    titleEl.value = '';
    contentEl.value = '';
    categoryEl.value = 'ทั่วไป';
    const cbs = targetsEl.querySelectorAll('input[type="checkbox"]');
    cbs.forEach(cb=>cb.checked=false);
    setToday();
  }

  function clearAll(){
    if(!confirm('ต้องการลบข่าวทั้งหมดหรือไม่?')) return;
    items = []; save(); render();
  }

  // attach to window for inline onclick
  window.del = del;
  window.pin = pin;
  window.unpin = unpin;

  // events
  saveBtn.addEventListener('click', add);
  resetBtn.addEventListener('click', clearForm);
  searchEl.addEventListener('input', render);
  filterEl.addEventListener('change', render);
  clearAllBtn.addEventListener('click', clearAll);

  // init
  setToday();
  load();
  render();
</script>
</body>
</html>
