<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>BABAYAGA — Home</title>
<style>
  :root{
    --bg:#000000;
    --amber:#ff9d2e;
    --amber-dim:#7a4408;
    --grey-dim:#2c2c2c;
  }
  *{box-sizing:border-box;margin:0;padding:0;}
  html,body{ height:100%; background:var(--bg); font-family:'Segoe UI',system-ui,-apple-system,sans-serif; }
  body{ display:flex; justify-content:center; }
  .screen{
    width:100%; max-width:420px; min-height:100vh;
    padding:16px 16px 74px;
    display:flex; flex-direction:column; align-items:center;
    position:relative;
  }
  .screen::before{
    content:""; position:absolute; inset:0;
    background:radial-gradient(circle at 50% 15%, rgba(255,157,46,0.08) 0%, rgba(255,157,46,0) 55%);
    pointer-events:none;
  }

  .tiger-header{ width:85px; margin-bottom:6px; z-index:1; filter:drop-shadow(0 0 10px rgba(255,140,20,0.3)); }
  .tiger-header img{ width:100%; height:auto; display:block; }

  .brand{ font-size:19px; font-weight:800; letter-spacing:5px; color:#eaeaea; z-index:1; }
  .brand-sub{ font-size:9.5px; letter-spacing:2.5px; color:var(--amber); margin-bottom:16px; z-index:1; }

  .box{
    width:100%; border-radius:12px; border:1.5px solid var(--grey-dim);
    padding:11px; margin-bottom:10px; z-index:1;
  }
  .box-title{ font-size:11px; letter-spacing:1.5px; font-weight:700; margin-bottom:8px; }

  .upload-box{ border-color:var(--amber-dim); }
  .upload-box .box-title{ color:var(--amber); }
  .upload-box .box-sub{ font-size:9.5px; color:#888; margin:-4px 0 8px; }

  .file-row{
    display:flex; align-items:center; gap:8px;
    background:#0a0a0a; border-radius:8px; padding:7px 10px;
  }
  .file-btn{
    background:#e8e8e8; color:#111; font-size:11px; font-weight:600;
    padding:6px 10px; border-radius:5px; border:none; cursor:pointer; white-space:nowrap;
  }
  .file-name{ font-size:11px; color:#999; overflow:hidden; text-overflow:ellipsis; white-space:nowrap; }
  input[type=file]{ display:none; }

  .doc-list{ margin-top:8px; display:flex; flex-direction:column; gap:5px; }
  .doc-item{
    display:flex; align-items:center; justify-content:space-between;
    background:#0a0a0a; border:1px solid var(--grey-dim); border-radius:6px;
    padding:6px 9px; font-size:10.5px; color:#ccc;
  }
  .doc-item .doc-name{ overflow:hidden; text-overflow:ellipsis; white-space:nowrap; margin-right:8px; }
  .doc-remove{
    background:none; border:none; color:#ff8080; font-size:12px; cursor:pointer; flex-shrink:0;
  }

  .paste-area{
    width:100%; min-height:90px; max-height:180px; resize:vertical;
    background:#0a0a0a; border:1px solid var(--grey-dim); border-radius:8px;
    color:#ccc; font-size:10.5px; font-family:monospace; padding:8px;
  }
  .paste-area:focus{ outline:none; border-color:var(--amber-dim); }

  .status-box .box-title{ color:var(--amber); }
  .status-line{
    display:flex; align-items:center; justify-content:space-between;
    background:#0a0a0a; border-radius:8px; padding:9px 12px; margin-bottom:6px;
  }
  .status-line:last-child{ margin-bottom:0; }
  .status-label{ font-size:11px; color:#ccc; }
  .status-state{ font-size:10.5px; font-weight:700; letter-spacing:0.5px; }
  .status-state.waiting{ color:#777; }
  .status-state.ready{ color:var(--amber); }

  .analyze-box{ text-align:center; }
  .analyze-box .box-title{ color:var(--amber); }
  .analyze-btn{
    width:100%; padding:11px; border-radius:9px; margin-top:3px;
    background:transparent; border:1.5px solid #444; color:#666;
    font-size:12.5px; font-weight:800; letter-spacing:1.5px;
    cursor:not-allowed; transition:all .25s ease;
  }
  .analyze-btn.enabled{
    border-color:var(--amber); color:var(--amber); cursor:pointer;
    box-shadow:0 0 14px rgba(255,157,46,0.3);
  }
  .analyze-hint{ font-size:10px; color:#777; margin-top:7px; }

  .bottom-nav{
    position:fixed; bottom:0; left:0; right:0;
    background:#000; border-top:1px solid #1c1c1c;
    display:flex; justify-content:center;
  }
  .bottom-nav-inner{
    width:100%; max-width:420px; display:flex; justify-content:space-around;
    padding:8px 0 10px;
  }
  .nav-item{ display:flex; flex-direction:column; align-items:center; gap:3px; font-size:9px; color:#666; letter-spacing:0.8px; cursor:pointer; background:none; border:none; font-family:inherit; }
  .nav-item.active{ color:var(--amber); }
  .nav-icon{ font-size:14px; }
</style>
</head>
<body>
<div class="screen">

  <div class="tiger-header"><img src="tiger.png" alt="BABAYAGA tiger mark" onerror="this.style.display='none'"></div>
  <div class="brand">BABAYAGA</div>
  <div class="brand-sub">FOOTBALL INTELLIGENCE FRAMEWORK</div>

  <!-- Statarea webpage document only. No bookmaker/odds section, no images,
       no thumbnails anywhere in this file. accept is intentionally "*/*" —
       a restrictive accept list (.mhtml,.html,etc) can grey out or hide the
       real file in Android's system picker when the saved-webpage file
       doesn't carry a matching MIME type, which is common. -->
  <div id="uploadSection" style="width:100%;"></div>

  <div class="box status-box">
    <div class="box-title">SYSTEM STATUS</div>
    <div id="statusSection"></div>
  </div>

  <div class="box analyze-box">
    <div class="box-title">ANALYZE</div>
    <button class="analyze-btn" id="analyzeBtn" disabled>ANALYZE</button>
    <div class="analyze-hint" id="analyzeHint">Upload a document to enable analysis</div>
  </div>

</div>

<div class="bottom-nav">
  <div class="bottom-nav-inner">
    <button class="nav-item active" onclick="goTo('page1.html')"><span class="nav-icon">&#8962;</span>HOME</button>
    <button class="nav-item" onclick="goTo('page2.html')"><span class="nav-icon">&#8982;</span>RANGE</button>
    <button class="nav-item" onclick="goTo('page3.html')"><span class="nav-icon">&#9881;</span>PROCESSING</button>
    <button class="nav-item" onclick="goTo('page4.html')"><span class="nav-icon">&#128202;</span>RESULTS</button>
  </div>
</div>

<script>
  function goTo(page){
    window.location.href = page;
  }
</script>

<script>
  // Single upload: Statarea webpage document. No odds/bookmaker input at all.
  const uploads = [
    { key:'statarea', label:'UPLOAD STATAREA WEBPAGE', statusLabel:'Statarea Webpage', multiple:false }
  ];

  const docState = {};
  const fileState = {};
  uploads.forEach(u => { docState[u.key] = []; fileState[u.key] = false; });

  function renderUploadBoxes(){
    const container = document.getElementById('uploadSection');
    container.innerHTML = uploads.map(u => `
      <div class="box upload-box">
        <div class="box-title">${u.label}</div>
        <div class="box-sub">Open the Statarea compare page → menu (⋮) → "View page source" (or Share → Save as webpage, then open that file in a text app) → select all, copy.</div>
        <div class="file-row">
          <button class="file-btn" onclick="document.getElementById('input_${u.key}').click()">Choose File</button>
          <span class="file-name" id="pickname_${u.key}">Choose a saved webpage file...</span>
        </div>
        <input type="file" id="input_${u.key}" accept="*/*" ${u.multiple ? 'multiple' : ''} onchange="onDocFilesChosen('${u.key}', this)">
        <div style="text-align:center;font-size:9px;color:#555;margin:6px 0;">— or —</div>
        <textarea id="paste_${u.key}" class="paste-area" placeholder="...paste the page source/text here instead" oninput="onDocPasted('${u.key}', this)"></textarea>
        <div class="doc-list" id="doclist_${u.key}"></div>
      </div>
    `).join('');
  }

  function renderStatusLines(){
    const container = document.getElementById('statusSection');
    container.innerHTML = uploads.map(u => `
      <div class="status-line">
        <span class="status-label">${u.statusLabel}</span>
        <span class="status-state waiting" id="status_${u.key}">WAITING</span>
      </div>
    `).join('');
  }

  function renderDocList(key){
    const el = document.getElementById(`doclist_${key}`);
    if(!el) return;
    el.innerHTML = docState[key].map((d, i) => `
      <div class="doc-item">
        <span class="doc-name">${d.name} (${d.text.length.toLocaleString()} chars)</span>
        <button class="doc-remove" onclick="removeDoc('${key}', ${i})">&times; remove</button>
      </div>
    `).join('');
  }

  function removeDoc(key, index){
    docState[key].splice(index, 1);
    renderDocList(key);
    persistDocs(key);
    refreshStateFor(key);
  }
  window.removeDoc = removeDoc;

  function refreshStateFor(key){
    const ready = docState[key].length > 0;
    fileState[key] = ready;
    const statusEl = document.getElementById(`status_${key}`);
    statusEl.textContent = ready ? 'READY' : 'WAITING';
    statusEl.classList.toggle('ready', ready);
    statusEl.classList.toggle('waiting', !ready);
    updateAnalyzeState();
  }

  const IDB_NAME = 'babayaga_db';
  const IDB_STORE = 'kv';
  function idbOpen(){
    return new Promise((resolve, reject) => {
      const req = indexedDB.open(IDB_NAME, 1);
      req.onupgradeneeded = () => { req.result.createObjectStore(IDB_STORE); };
      req.onsuccess = () => resolve(req.result);
      req.onerror = () => reject(req.error);
    });
  }
  async function idbSet(key, value){
    const db = await idbOpen();
    return new Promise((resolve, reject) => {
      const tx = db.transaction(IDB_STORE, 'readwrite');
      tx.objectStore(IDB_STORE).put(value, key);
      tx.oncomplete = () => resolve(true);
      tx.onerror = () => reject(tx.error);
    });
  }
  function persistDocs(key){
    idbSet(`docs_${key}`, docState[key]).catch(err => {
      console.error('Failed to persist documents to IndexedDB:', err);
      alert('Warning: document loaded but could not be saved for the next page. Try reloading and try again.');
    });
  }

  function onDocFilesChosen(key, input){
    const files = Array.from(input.files || []);
    if(!files.length) return;
    const uploadDef = uploads.find(u => u.key === key);

    const readOne = (file) => new Promise((resolve) => {
      const reader = new FileReader();
      reader.onload = e => resolve({ name:file.name, text:e.target.result });
      reader.onerror = () => { alert('Could not read file: ' + file.name); resolve(null); };
      reader.readAsText(file);
    });

    Promise.all(files.map(readOne)).then(results => {
      const good = results.filter(Boolean);
      if(!uploadDef.multiple) docState[key] = [];
      docState[key].push(...good);
      renderDocList(key);
      persistDocs(key);
      refreshStateFor(key);
      document.getElementById(`pickname_${key}`).textContent =
        `${docState[key].length} document${docState[key].length === 1 ? '' : 's'} loaded`;
    });

    input.value = '';
  }
  window.onDocFilesChosen = onDocFilesChosen;

  let pasteTimers = {};
  function onDocPasted(key, textarea){
    clearTimeout(pasteTimers[key]);
    pasteTimers[key] = setTimeout(() => {
      const text = textarea.value;
      const uploadDef = uploads.find(u => u.key === key);
      const MIN_LEN = 200;

      if(text.trim().length < MIN_LEN){
        return;
      }

      const doc = { name:'pasted.html', text };
      if(!uploadDef.multiple){
        docState[key] = [doc];
      } else {
        docState[key].push(doc);
        textarea.value = '';
      }
      renderDocList(key);
      persistDocs(key);
      refreshStateFor(key);
    }, 250);
  }
  window.onDocPasted = onDocPasted;

  function updateAnalyzeState(){
    const allReady = uploads.every(u => fileState[u.key]);
    const btn = document.getElementById('analyzeBtn');
    const hint = document.getElementById('analyzeHint');
    if(allReady){
      btn.disabled = false;
      btn.classList.add('enabled');
      hint.textContent = 'Ready to proceed to Range Analysis';
    } else {
      btn.disabled = true;
      btn.classList.remove('enabled');
      hint.textContent = 'Upload a document to enable analysis';
    }
  }

  document.getElementById('analyzeBtn').addEventListener('click', function(){
    if(this.disabled) return;
    window.location.href = 'page2.html';
  });

  renderUploadBoxes();
  renderStatusLines();
</script>
</body>
</html>
