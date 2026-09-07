<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>BABAYEGA — Load Matches</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@500;600;700&family=Chakra+Petch:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --black: #050705;
    --panel: #0a100a;
    --panel-edge: #16241a;
    --green: #39ff6b;
    --green-dim: #1f7a3f;
    --green-glow: rgba(57,255,107,0.35);
    --text: #d9ffe4;
    --text-dim: #6f9c7e;
    --amber: #ffb020;
    --red: #ff4d4d;
  }

  *{ box-sizing:border-box; -webkit-tap-highlight-color:transparent; }

  body{
    margin:0;
    min-height:100vh;
    background:
      radial-gradient(ellipse at 50% -10%, rgba(57,255,107,0.10), transparent 55%),
      var(--black);
    color:var(--text);
    font-family:'Chakra Petch', sans-serif;
    display:flex;
    flex-direction:column;
    align-items:center;
    padding:0 0 48px;
  }

  header{
    width:100%;
    display:flex;
    flex-direction:column;
    align-items:center;
    padding:28px 20px 10px;
  }

  .logo{
    width:min(58vw, 220px);
    filter: drop-shadow(0 0 18px var(--green-glow)) drop-shadow(0 0 3px rgba(57,255,107,0.6));
  }

  .page-tag{
    margin-top:10px;
    font-family:'Rajdhani', sans-serif;
    font-weight:600;
    letter-spacing:0.35em;
    font-size:11px;
    color:var(--green-dim);
  }

  main{
    width:100%;
    max-width:480px;
    padding:24px 18px 0;
  }

  .rule{
    height:1px;
    width:100%;
    margin:18px 0 22px;
    background:linear-gradient(90deg, transparent, var(--green-dim), transparent);
  }

  h1{
    font-family:'Rajdhani', sans-serif;
    font-weight:700;
    font-size:22px;
    letter-spacing:0.02em;
    margin:0 0 6px;
    color:#eafff0;
  }

  .sub{
    font-size:14px;
    color:var(--text-dim);
    line-height:1.5;
    margin:0 0 24px;
  }

  .dropzone{
    border:1.5px dashed var(--green-dim);
    border-radius:4px;
    background:var(--panel);
    padding:28px 18px;
    text-align:center;
    transition:border-color .15s ease, background .15s ease;
    cursor:pointer;
  }
  .dropzone.drag{
    border-color:var(--green);
    background:#0d1a10;
  }
  .dropzone .icon{
    font-size:30px;
    line-height:1;
    margin-bottom:10px;
    color:var(--green);
  }
  .dropzone .label{
    font-family:'Rajdhani', sans-serif;
    font-weight:600;
    font-size:16px;
    color:var(--text);
  }
  .dropzone .hint{
    font-size:12.5px;
    color:var(--text-dim);
    margin-top:4px;
  }
  input[type=file]{ display:none; }

  .or{
    text-align:center;
    font-size:11px;
    letter-spacing:0.3em;
    color:var(--text-dim);
    margin:18px 0;
  }

  textarea{
    width:100%;
    min-height:110px;
    background:var(--panel);
    border:1px solid var(--panel-edge);
    border-radius:4px;
    color:var(--text);
    font-family:'Chakra Petch', monospace;
    font-size:12.5px;
    padding:12px;
    resize:vertical;
  }
  textarea:focus{ outline:none; border-color:var(--green-dim); }
  textarea::placeholder{ color:#3a4f40; }

  button.primary{
    width:100%;
    margin-top:16px;
    background:var(--green);
    color:#04120a;
    border:none;
    border-radius:4px;
    font-family:'Rajdhani', sans-serif;
    font-weight:700;
    font-size:16px;
    letter-spacing:0.04em;
    padding:14px;
    cursor:pointer;
    box-shadow:0 0 20px var(--green-glow);
  }
  button.primary:active{ transform:translateY(1px); }
  button.primary:disabled{
    background:#1c2b20;
    color:#4c6b56;
    box-shadow:none;
    cursor:not-allowed;
  }

  .status{
    margin-top:22px;
    border:1px solid var(--panel-edge);
    border-radius:4px;
    background:var(--panel);
    padding:14px 16px;
    display:none;
  }
  .status.show{ display:block; }
  .status.ok{ border-color:var(--green-dim); }
  .status.err{ border-color:#5a1f1f; }

  .status .line{
    font-size:13px;
    display:flex;
    justify-content:space-between;
    padding:4px 0;
    border-bottom:1px solid rgba(255,255,255,0.04);
  }
  .status .line:last-child{ border-bottom:none; }
  .status .line b{ color:#eafff0; font-weight:600; }
  .status .err-msg{ color:var(--red); font-size:13px; }

  .tab-row{ display:flex; gap:8px; margin-top:2px; }
  .chip{
    font-size:11px;
    font-family:'Rajdhani', sans-serif;
    font-weight:600;
    letter-spacing:0.05em;
    padding:4px 9px;
    border-radius:100px;
    border:1px solid var(--green-dim);
    color:var(--green);
  }

  .continue{
    display:none;
    width:100%;
    margin-top:14px;
    background:transparent;
    color:var(--green);
    border:1.5px solid var(--green);
    border-radius:4px;
    font-family:'Rajdhani', sans-serif;
    font-weight:700;
    font-size:15px;
    letter-spacing:0.04em;
    padding:13px;
    cursor:pointer;
  }
  .continue.show{ display:block; }
  .continue:active{ background:rgba(57,255,107,0.08); }

  .prev-note{
    margin-top:26px;
    font-size:12px;
    color:var(--text-dim);
    text-align:center;
    line-height:1.6;
  }
  .prev-note button{
    background:none;
    border:none;
    color:var(--green-dim);
    text-decoration:underline;
    font-size:12px;
    cursor:pointer;
    padding:0;
  }
</style>
</head>
<body>

<header>
  <img class="logo" src="logo-babayega.png" alt="BABAYEGA">
  <div class="page-tag">PAGE 1 — LOAD MATCHES</div>
</header>

<main>
  <div class="rule"></div>

  <h1>Import scraped odds</h1>
  <p class="sub">Load the JSON file exported by the SportyBet Instant Basketball scraper. All markets and quarter/half ladders come in at once.</p>

  <div class="dropzone" id="dropzone">
    <div class="icon">&#9660;</div>
    <div class="label">Tap to choose file</div>
    <div class="hint">or drop a .json export here</div>
    <input type="file" id="fileInput" accept="application/json,.json">
  </div>

  <div class="or">— OR PASTE JSON —</div>

  <textarea id="pasteArea" placeholder='{"exportedAt": "...", "totalMatches": 24, "matches": [...] }'></textarea>

  <button class="primary" id="loadBtn" disabled>Load matches</button>

  <div class="status" id="status"></div>

  <button class="continue" id="continueBtn">Continue to Odds Range →</button>

  <div class="prev-note" id="prevNote"></div>
</main>

<script>
(function(){
  const dropzone   = document.getElementById('dropzone');
  const fileInput  = document.getElementById('fileInput');
  const pasteArea  = document.getElementById('pasteArea');
  const loadBtn    = document.getElementById('loadBtn');
  const statusBox  = document.getElementById('status');
  const continueBtn= document.getElementById('continueBtn');
  const prevNote   = document.getElementById('prevNote');

  const STORAGE_KEY = 'babayegaBasketballMatches';
  let pendingText = '';

  function setPending(text){
    pendingText = text;
    loadBtn.disabled = !text || !text.trim();
  }

  dropzone.addEventListener('click', () => fileInput.click());

  ['dragenter','dragover'].forEach(evt =>
    dropzone.addEventListener(evt, e => { e.preventDefault(); dropzone.classList.add('drag'); })
  );
  ['dragleave','drop'].forEach(evt =>
    dropzone.addEventListener(evt, e => { e.preventDefault(); dropzone.classList.remove('drag'); })
  );
  dropzone.addEventListener('drop', e => {
    const file = e.dataTransfer.files[0];
    if (file) readFile(file);
  });

  fileInput.addEventListener('change', () => {
    const file = fileInput.files[0];
    if (file) readFile(file);
  });

  function readFile(file){
    const reader = new FileReader();
    reader.onload = () => {
      pasteArea.value = reader.result;
      setPending(reader.result);
      dropzone.querySelector('.label').textContent = file.name;
    };
    reader.readAsText(file);
  }

  pasteArea.addEventListener('input', () => setPending(pasteArea.value));

  function showStatus(kind, html){
    statusBox.className = 'status show ' + kind;
    statusBox.innerHTML = html;
  }

  // Validates + summarizes the scraper export without assuming anything
  // about market meaning - just structural checks (per the never-guess rule).
  function validateAndSummarize(data){
    if (!data || typeof data !== 'object') throw new Error('Not a JSON object.');
    if (!Array.isArray(data.matches)) throw new Error('Missing "matches" array.');
    if (data.matches.length === 0) throw new Error('"matches" array is empty.');

    const tabCounts = {};
    let ladderMarketCount = 0, simpleMarketCount = 0, missingTeams = 0;
    const marketNameSet = new Set();

    data.matches.forEach(m => {
      const tab = m.tab || 'unknown';
      tabCounts[tab] = (tabCounts[tab] || 0) + 1;
      if (!m.homeTeam || !m.awayTeam) missingTeams++;
      (m.markets || []).forEach(mk => {
        marketNameSet.add(mk.marketName);
        if (mk.values && mk.values.type === 'ladder') ladderMarketCount++;
        else simpleMarketCount++;
      });
    });

    return {
      total: data.matches.length,
      exportedAt: data.exportedAt || null,
      tabCounts, missingTeams,
      marketCount: marketNameSet.size,
      ladderMarketCount, simpleMarketCount
    };
  }

  loadBtn.addEventListener('click', () => {
    let data;
    try{
      data = JSON.parse(pendingText);
    }catch(e){
      showStatus('err', `<div class="err-msg">Couldn't parse that as JSON — check the file wasn't cut off mid-export.</div>`);
      continueBtn.classList.remove('show');
      return;
    }

    try{
      validateAndSummarize(data); // structural check only, nothing shown
    }catch(e){
      showStatus('err', `<div class="err-msg">${e.message}</div>`);
      continueBtn.classList.remove('show');
      return;
    }

    localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
    localStorage.setItem(STORAGE_KEY + 'LoadedAt', new Date().toISOString());

    continueBtn.classList.add('show');
  });

  continueBtn.addEventListener('click', () => {
    window.location.href = 'page2.html';
  });

  // If matches were already loaded in a previous visit, surface that instead
  // of forcing a re-upload every time the page opens.
  const existing = localStorage.getItem(STORAGE_KEY);
  const existingAt = localStorage.getItem(STORAGE_KEY + 'LoadedAt');
  if (existing) {
    try{
      const parsed = JSON.parse(existing);
      const count = Array.isArray(parsed.matches) ? parsed.matches.length : '?';
      const when = existingAt ? new Date(existingAt).toLocaleString() : 'earlier';
      prevNote.innerHTML = `${count} matches already loaded from ${when}. <button id="useExisting">Use these →</button>`;
      document.getElementById('useExisting').addEventListener('click', () => {
        window.location.href = 'page2.html';
      });
    }catch(e){ /* ignore corrupt cache */ }
  }
})();
</script>

</body>
</html>
