<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="utf-8" />
  <title>กระดานข่าวโรงเรียน — ระบบประกาศข่าวสาร</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;600;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg: #f4f8ff;
      --card: #ffffff;
      --accent: linear-gradient(90deg,#2563eb 0%, #06b6d4 100%);
      --muted: #6b7280;
      --glass: rgba(15,23,42,0.06);
      --success: #10b981;
      --danger: #ef4444;
      --radius: 14px;
    }

    *{box-sizing:border-box;font-family:"Sarabun",system-ui,-apple-system,"Segoe UI",sans-serif}
    body{
      margin:0;
      background:var(--bg);
      padding:28px;
      display:flex;
      justify-content:center;
    }

    .wrap{
      width:100%;
      max-width:1180px;
      margin:0 auto;
    }

    header.app-header{
      display:flex;
      align-items:center;
      gap:16px;
      padding:18px 20px;
      border-radius:12px;
      background: linear-gradient(90deg,#eef6ff, #fbffff);
      box-shadow: 0 8px 30px var(--glass);
      border:1px solid rgba(99,102,241,0.06);
    }

    .logo{
      width:64px;height:64px;border-radius:12px;
      background:linear-gradient(135deg,#2563eb,#06b6d4);
      display:flex;align-items:center;justify-content:center;color:white;font-weight:700;
      box-shadow: 0 6px 18px rgba(37,99,235,0.12);
      flex-shrink:0;
    }
    .brand{
      display:flex;flex-direction:column;
    }
    .brand h1{margin:0;font-size:18px;color:#0b3a8a}
    .brand p{margin:0;font-size:13px;color:var(--muted)}

    main.container{
      margin-top:18px;
      display:grid;
      grid-template-columns:360px 1fr;
      gap:18px;
    }
    @media(max-width:980px){ main.container{grid-template-columns:1fr} .left, .right{min-width:0;} }

    /* LEFT PANEL: form */
    .card{
      background:var(--card);
      border-radius:var(--radius);
      padding:16px;
      box-shadow: 0 6px 22px var(--glass);
      border:1px solid #eef4ff;
    }

    .card h2{margin:0 0 8px 0;color:#0f172a;font-size:16px}
    label{display:block;font-weight:600;margin-top:10px;color:#0b2447}
    input[type="text"], input[type="date"], select, textarea, input[type="search"]{
      width:100%;padding:10px;border-radius:10px;border:1px solid #e6eefc;background:#fff;font-size:14px;margin-top:6px;
    }
    textarea{min-height:100px;resize:vertical}

    .checkbox-row{display:flex;flex-wrap:wrap;gap:8px;margin-top:8px}
    .checkbox-row label{display:flex;gap:6px;align-items:center;font-weight:500;color:#374151}

    .btn-row{display:flex;gap:10px;margin-top:12px}
    .btn {
      padding:10px 12px;border-radius:999px;border:none;font-weight:700;cursor:pointer;
      display:inline-flex;gap:8px;align-items:center;
    }
    .btn.primary{background:var(--accent);color:#fff;box-shadow: 0 8px 20px rgba(37,99,235,0.12)}
    .btn.ghost{background:#f1f5f9;color:#0b1220}
    .btn.warn{background:#fef3c7;color:#92400e}
    .hint{font-size:13px;color:var(--muted);margin-top:8px}

    /* RIGHT PANEL: list and filters */
    .controls{
      display:flex;gap:10px;align-items:center;margin-bottom:12px;flex-wrap:wrap;
    }
    .controls input[type="search"]{max-width:360px}
    .controls select{max-width:160px;padding:8px 10px;border-radius:10px;border:1px solid #e6eefc;background:#fff}

    .pinned-section{margin-bottom:12px}
    .pinned-title{display:flex;align-items:center;gap:8px;margin-bottom:8px}
    .pinned-title h3{margin:0;font-size:15px;color:#0b2447}
    .pinned-list{display:flex;flex-direction:column;gap:10px}

    .news-list{display:grid;grid-template-columns:repeat(2,1fr);gap:12px}
    @media(max-width:980px){.news-list{grid-template-columns:1fr}}
    .news-card{
      background:#fff;border-radius:12px;padding:12px;border:1px solid #eef4ff;box-shadow:0 6px 18px rgba(15,23,42,0.03);
      transition:transform .15s ease, box-shadow .15s ease;
      display:flex;flex-direction:column;gap:8px;
    }
    .news-card:hover{transform:translateY(-6px);box-shadow:0 16px 38px rgba(15,23,42,0.08)}
    .news-title{font-weight:700;color:#0b1220;font-size:15px}
    .meta-row{display:flex;gap:8px;align-items:center;flex-wrap:wrap;font-size:13px;color:var(--muted)}
    .badge{padding:4px 8px;border-radius:999px;font-weight:700;font-size:12px}
    .badge.category{background:#eef2ff;color:#1d4ed8}
    .badge.target{background:#ecfdf5;color:#15803d}
    .badge.pinned{background:#fff7ed;color:#92400e}

    .news-body{font-size:14px;color:#374151;white-space:pre-line}
    .card-actions{display:flex;gap:8px;justify-content:flex-end;margin-top:6px}
    .action-btn{background:#f1f5f9;border-radius:999px;padding:6px 8px;border:1px solid #e6eefc;cursor:pointer;font-weight:600}
    .action-btn.danger{background:#fff1f2;border-color:#fed7d7;color:var(--danger)}
    .small{font-size:13px;padding:6px 8px}

    .empty{padding:18px;text-align:center;color:var(--muted);font-size:14px}

    /* footer */
    footer{margin-top:18px;text-align:right;color:var(--muted);font-size:13px}

  </style>
</head>
<body>
  <div class="wrap">
    <header class="app-header">
      <div class="logo">โรง</div>
      <div class="brand">
        <h1>กระดานข่าวโรงเรียน</h1>
        <p>ระบบประกาศข่าวสารภายใน — เก็บข้อมูลบนเครื่อง (LocalStorage)</p>
      </div>
    </header>

    <main class="container">
      <!-- LEFT: form -->
      <section class="left card">
        <h2 id="formTitle">บันทึกข่าวใหม่</h2>

        <label>หัวข้อข่าว</label>
        <input id="newsTitle" type="text" placeholder="หัวข้อข่าว เช่น ประกาศวันหยุด">

        <label>วันที่ประกาศ</label>
        <input id="newsDate" type="date">

        <label>หมวดหมู่</label>
        <select id="newsCategory">
          <option>ทั่วไป</option>
          <option>การเรียนการสอน</option>
          <option>กิจกรรม</option>
          <option>ประชุม/อบรม</option>
          <option>งานวิชาการ</option>
          <option>อื่น ๆ</option>
        </select>

        <label>กลุ่มเป้าหมาย</label>
        <div class="checkbox-row" id="targetGroup">
          <label><input type="checkbox" value="นักเรียน"> นักเรียน</label>
          <label><input type="checkbox" value="ครู"> ครู</label>
          <label><input type="checkbox" value="ผู้ปกครอง"> ผู้ปกครอง</label>
          <label><input type="checkbox" value="บุคลากร"> บุคลากร</label>
        </div>

        <label>รายละเอียด</label>
        <textarea id="newsContent" placeholder="ระบุวันเวลา สถานที่ หรือรายละเอียดเพิ่มเติม"></textarea>

        <div class="btn-row">
          <button class="btn primary" id="btnSave"><span>💾</span>บันทึกข่าว</button>
          <button class="btn ghost" id="btnClearForm"><span>🧹</span>ล้างฟอร์ม</button>
          <button class="btn warn" id="btnPreview" title="แสดงตัวอย่าง"><span>👁️</span>ตัวอย่าง</button>
        </div>

        <p class="hint">ข่าวจะเก็บไว้ที่เบราว์เซอร์นี้เท่านั้น — หากต้องการแชร์ ให้ส่งไฟล์ JSON หรือถ่ายภาพหน้าจอ</p>
      </section>

      <!-- RIGHT: list -->
      <section class="right card">
        <div class="controls">
          <input id="searchInput" type="search" placeholder="ค้นหา หัวข้อหรือเนื้อหา...">
          <select id="filterCategory">
            <option value="">ทุกหมวดหมู่</option>
            <option>ทั่วไป</option>
            <option>การเรียนการสอน</option>
            <option>กิจกรรม</option>
            <option>ประชุม/อบรม</option>
            <option>งานวิชาการ</option>
            <option>อื่น ๆ</option>
          </select>
          <div style="margin-left:auto;display:flex;gap:8px;">
            <button class="btn ghost small" id="btnSortDate">เรียงล่าสุด</button>
            <button class="btn ghost small" id="btnClearAll">ลบทั้งหมด</button>
          </div>
        </div>

        <div class="pinned-section">
          <div class="pinned-title">
            <h3>ข่าวปักหมุด</h3>
            <div style="margin-left:auto;font-size:13px;color:var(--muted)">แสดงข่าวที่ปักหมุดไว้</div>
          </div>
          <div id="pinnedList" class="pinned-list"></div>
        </div>

        <hr style="border:none;border-top:1px solid #eef4ff;margin:8px 0 12px">

        <div id="newsList" class="news-list"></div>
        <div id="emptyState" class="empty" style="display:none">ยังไม่มีข่าวที่บันทึก</div>
      </section>
    </main>

    <footer>© ระบบประกาศข่าวสารโรงเรียน</footer>
  </div>

<script>
  const STORAGE_KEY = "schoolNewsList_v2";

  // DOM
  const newsTitle = document.getElementById("newsTitle");
  const newsDate = document.getElementById("newsDate");
  const newsCategory = document.getElementById("newsCategory");
  const newsContent = document.getElementById("newsContent");
  const targetGroup = document.getElementById("targetGroup");
  const btnSave = document.getElementById("btnSave");
  const btnClearForm = document.getElementById("btnClearForm");
  const btnPreview = document.getElementById("btnPreview");
  const btnClearAll = document.getElementById("btnClearAll");
  const btnSortDate = document.getElementById("btnSortDate");

  const searchInput = document.getElementById("searchInput");
  const filterCategory = document.getElementById("filterCategory");

  const newsListDiv = document.getElementById("newsList");
  const pinnedListDiv = document.getElementById("pinnedList");
  const emptyState = document.getElementById("emptyState");
  const formTitle = document.getElementById("formTitle");

  let newsItems = [];
  let editingId = null;
  let sortNewestFirst = true;

  // Set today's date default
  function setTodayDefault(){
    const t = new Date();
    newsDate.value = t.toISOString().slice(0,10);
  }

  // Load/save
  function loadNews(){
    const s = localStorage.getItem(STORAGE_KEY);
    if (s) {
      try { newsItems = JSON.parse(s); }
      catch(e){ newsItems = []; }
    } else newsItems = [];
  }
  function saveNews(){
    localStorage.setItem(STORAGE_KEY, JSON.stringify(newsItems));
  }

  // Utilities
  function formatDate(d){
    if(!d) return "-";
    const dt = new Date(d);
    return dt.toLocaleDateString();
  }
  function timeAgo(timestamp){
    if(!timestamp) return "";
    const diff = Date.now() - timestamp;
    const mins = Math.floor(diff / 60000);
    if(mins < 1) return "เมื่อสักครู่";
    if(mins < 60) return `${mins} นาทีที่แล้ว`;
    const hours = Math.floor(mins/60);
    if(hours < 24) return `${hours} ชั่วโมงที่แล้ว`;
    const days = Math.floor(hours/24);
    return `${days} วันก่อน`;
  }

  // Render
  function renderNews(){
    // filter & sort
    const q = (searchInput.value || "").trim().toLowerCase();
    const cat = filterCategory.value || "";

    // sort: pinned first, then date/created
    let items = [...newsItems];

    items.sort((a,b) => {
      if(a.pinned && !b.pinned) return -1;
      if(!a.pinned && b.pinned) return 1;
      if(sortNewestFirst) return (b.createdAt || 0) - (a.createdAt || 0);
      return (a.createdAt || 0) - (b.createdAt || 0);
    });

    // pinned list
    const pinned = items.filter(it => it.pinned);
    pinnedListDiv.innerHTML = "";
    if(pinned.length === 0){
      pinnedListDiv.innerHTML = `<div class="empty">ไม่มีข่าวปักหมุด</div>`;
    } else {
      pinned.forEach(it => {
        const el = document.createElement("div");
        el.className = "news-card";
        el.style.display = "flex";
        el.style.flexDirection = "column";
        el.innerHTML = `
          <div style="display:flex;justify-content:space-between;align-items:flex-start;gap:10px">
            <div style="flex:1;min-width:0">
              <div class="news-title">${escapeHtml(it.title)}</div>
              <div class="meta-row"><span class="badge category">${escapeHtml(it.category)}</span> <span style="color:var(--muted);font-size:13px;margin-left:6px">${formatDate(it.date)}</span></div>
            </div>
            <div style="margin-left:8px;display:flex;flex-direction:column;gap:6px">
              <button class="action-btn small" onclick="unpin(${it.id})">ยกเลิกปักหมุด</button>
              <button class="action-btn small" onclick="editNews(${it.id})">แก้ไข</button>
            </div>
          </div>
        `;
        pinnedListDiv.appendChild(el);
      });
    }

    // main list (filtered by search & category)
    const filtered = items.filter(it => {
      const text = (it.title + " " + it.content + " " + (it.targets||[]).join(" ")).toLowerCase();
      const matchQ = q === "" || text.includes(q);
      const matchCat = !cat || it.category === cat;
      return matchQ && matchCat && !it.pinned; // exclude pinned from main list (already shown)
    });

    newsListDiv.innerHTML = "";
    if(filtered.length === 0){
      emptyState.style.display = "block";
    } else {
      emptyState.style.display = "none";
      filtered.forEach(it => {
        const card = document.createElement("div");
        card.className = "news-card";
        card.innerHTML = `
          <div>
            <div class="news-title">${escapeHtml(it.title)}</div>
            <div class="meta-row" style="margin-top:6px">
              <span class="badge category">${escapeHtml(it.category)}</span>
              <span class="badge target">${(it.targets && it.targets.length)? escapeHtml(it.targets.join(", ")) : "กลุ่มเป้าหมาย: ไม่ระบุ"}</span>
              <span style="margin-left:auto;color:var(--muted);font-weight:600">${formatDate(it.date)}</span>
            </div>
          </div>
          <div class="news-body">${escapeHtml(it.content)}</div>
          <div class="card-actions">
            <button class="action-btn" onclick="pin(${it.id})">${it.pinned ? "ยกเลิกปักหมุด" : "ปักหมุด"}</button>
            <button class="action-btn" onclick="editNews(${it.id})">แก้ไข</button>
            <button class="action-btn danger" onclick="deleteNews(${it.id})">ลบ</button>
          </div>
        `;
        newsListDiv.appendChild(card);
      });
    }
  }

  // escape for safety
  function escapeHtml(s){
    if(!s && s !== 0) return "";
    return String(s)
      .replace(/&/g,'&amp;')
      .replace(/</g,'&lt;')
      .replace(/>/g,'&gt;')
      .replace(/"/g,'&quot;')
      .replace(/'/g,'&#039;')
      .replace(/\n/g, '<br>');
  }

  // actions
  function addOrUpdateNews(){
    const title = newsTitle.value.trim();
    const date = newsDate.value;
    const category = newsCategory.value;
    const content = newsContent.value.trim();

    if(!title){
      alert("กรุณากรอกหัวข้อข่าว");
      return;
    }

    const cbs = targetGroup.querySelectorAll("input[type='checkbox']");
    const targets = [];
    cbs.forEach(cb => { if(cb.checked) targets.push(cb.value); });

    if(editingId){
      // update
      const idx = newsItems.findIndex(i=>i.id === editingId);
      if(idx !== -1){
        newsItems[idx].title = title;
        newsItems[idx].date = date;
        newsItems[idx].category = category;
        newsItems[idx].content = content;
        newsItems[idx].targets = targets;
        newsItems[idx].updatedAt = Date.now();
      }
      editingId = null;
      formTitle.textContent = "บันทึกข่าวใหม่";
      btnSave.innerHTML = "💾 บันทึกข่าว";
    } else {
      const item = {
        id: Date.now(),
        title, date, category, content, targets,
        pinned: false,
        createdAt: Date.now()
      };
      newsItems.push(item);
    }
    saveNews();
    renderNews();
    clearForm();
  }

  function pin(id){
    const idx = newsItems.findIndex(i=>i.id === id);
    if(idx !== -1){
      newsItems[idx].pinned = true;
      saveNews(); renderNews();
    }
  }
  function unpin(id){
    const idx = newsItems.findIndex(i=>i.id === id);
    if(idx !== -1){
      newsItems[idx].pinned = false;
      saveNews(); renderNews();
    }
  }

  function editNews(id){
    const it = newsItems.find(i=>i.id === id);
    if(!it) return;
    editingId = id;
    formTitle.textContent = "แก้ไขข่าว";
    newsTitle.value = it.title;
    newsDate.value = it.date || "";
    newsCategory.value = it.category || "ทั่วไป";
    newsContent.value = it.content || "";
    // targets
    const cbs = targetGroup.querySelectorAll("input[type='checkbox']");
    cbs.forEach(cb => { cb.checked = (it.targets || []).includes(cb.value); });
    window.scrollTo({ top: 0, behavior: 'smooth' });
    btnSave.innerHTML = "💾 บันทึกการแก้ไข";
  }

  function deleteNews(id){
    if(!confirm("ต้องการลบข่าวนี้หรือไม่?")) return;
    newsItems = newsItems.filter(i=>i.id !== id);
    saveNews(); renderNews();
  }

  function clearForm(){
    editingId = null;
    formTitle.textContent = "บันทึกข่าวใหม่";
    btnSave.innerHTML = "💾 บันทึกข่าว";
    newsTitle.value = "";
    newsDate.value = "";
    newsCategory.value = "ทั่วไป";
    newsContent.value = "";
    const cbs = targetGroup.querySelectorAll("input[type='checkbox']");
    cbs.forEach(cb=>cb.checked=false);
    setTodayDefault();
  }

  function clearAll(){
    if(!confirm("ต้องการลบข่าวทั้งหมดหรือไม่?")) return;
    newsItems = [];
    saveNews(); renderNews();
  }

  // helpers for UI buttons bound inline
  window.pin = pin;
  window.unpin = unpin;
  window.editNews = editNews;
  window.deleteNews = deleteNews;

  // Preview
  function previewCard(){
    const title = newsTitle.value.trim() || "(หัวข้อ)";
    const date = newsDate.value || new Date().toISOString().slice(0,10);
    const category = newsCategory.value || "ทั่วไป";
    const content = newsContent.value.trim() || "(รายละเอียด...)";
    alert(`ตัวอย่างข่าว\n\nหัวข้อ: ${title}\nวันที่: ${date}\nหมวดหมู่: ${category}\n\n${content}`);
  }

  // events
  btnSave.addEventListener("click", addOrUpdateNews);
  btnClearForm.addEventListener("click", clearForm);
  btnPreview.addEventListener("click", previewCard);
  btnClearAll.addEventListener("click", clearAll);
  searchInput.addEventListener("input", renderNews);
  filterCategory.addEventListener("change", renderNews);
  btnSortDate.addEventListener("click", () => { sortNewestFirst = !sortNewestFirst; renderNews(); });

  // init
  setTodayDefault();
  loadNews();
  renderNews();

  // ensure UI shows correct defaults
  (function ensureDefaults(){
    if(!newsDate.value) setTodayDefault();
  })();
</script>
</body>
</html>
