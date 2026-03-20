<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>MediMap Dhaka — Hospital Navigator</title>

<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500;9..40,600&display=swap" rel="stylesheet"/>

<!--
  CDN: jsDelivr — chosen over unpkg because it has proper
  Asia/Bangladesh edge nodes. unpkg has no Asian PoP,
  causing 3-8s latency or outright timeouts which produce
  "L is not defined". jsDelivr resolves in <80ms from BD.
  Scripts are SYNCHRONOUS (no defer/async) so they fully
  execute before any inline JS runs — guaranteed.
-->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/leaflet@1.9.4/dist/leaflet.css"/>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/leaflet-routing-machine@3.2.12/dist/leaflet-routing-machine.css"/>
<script src="https://cdn.jsdelivr.net/npm/leaflet@1.9.4/dist/leaflet.js"></script>
<script src="https://cdn.jsdelivr.net/npm/leaflet-routing-machine@3.2.12/dist/leaflet-routing-machine.js"></script>

<style>
:root{
  --teal:#0a8f8f; --teal-d:#055858; --teal-l:#12b5b5;
  --red:#e53e3e; --green:#22c55e; --gold:#f6ad55;
  --bg:#f0f4f8; --surface:#fff; --text:#1a202c; --muted:#718096;
  --border:#e2e8f0; --sh:0 4px 24px rgba(10,143,143,.14);
  --sh-lg:0 8px 40px rgba(10,143,143,.22); --r:14px; --sw:380px;
}
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--text);height:100vh;overflow:hidden;display:flex;flex-direction:column}
a{text-decoration:none} button{cursor:pointer;font-family:inherit}

/* HEADER */
header{background:linear-gradient(135deg,var(--teal-d) 0%,var(--teal) 55%,var(--teal-l) 100%);height:62px;padding:0 18px;display:flex;align-items:center;justify-content:space-between;flex-shrink:0;z-index:1000;box-shadow:0 2px 20px rgba(5,88,88,.45)}
.logo{display:flex;align-items:center;gap:10px}
.logo-icon{width:36px;height:36px;background:rgba(255,255,255,.18);border-radius:9px;display:flex;align-items:center;justify-content:center}
.logo-txt{font-family:'Syne',sans-serif;color:#fff;font-size:1.3rem;font-weight:800;letter-spacing:-.5px}
.logo-txt span{color:#7fecec}
.hdr-r{display:flex;align-items:center;gap:10px}
.live-badge{background:rgba(255,255,255,.14);border:1px solid rgba(255,255,255,.25);color:#fff;font-size:.7rem;font-weight:700;padding:4px 10px;border-radius:20px;display:flex;align-items:center;gap:5px}
.pulse{width:7px;height:7px;background:#7fecec;border-radius:50%;animation:pls 1.6s infinite}
@keyframes pls{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.5;transform:scale(1.5)}}
.btn-locate{background:rgba(255,255,255,.18);border:1px solid rgba(255,255,255,.4);color:#fff;padding:7px 13px;border-radius:8px;font-size:.79rem;font-weight:600;display:flex;align-items:center;gap:6px;transition:background .2s}
.btn-locate:hover{background:rgba(255,255,255,.3)}

/* EMERGENCY STRIP */
.emg{background:linear-gradient(90deg,#b91c1c,var(--red));color:#fff;text-align:center;padding:5px 12px;font-size:.7rem;font-weight:700;display:flex;align-items:center;justify-content:center;gap:10px;flex-shrink:0}
.emg a{color:#fff;font-weight:800;background:rgba(255,255,255,.22);padding:2px 9px;border-radius:8px}

/* LAYOUT */
.app{display:flex;flex:1;overflow:hidden}

/* SIDEBAR */
.sb{width:var(--sw);background:var(--surface);display:flex;flex-direction:column;border-right:1px solid var(--border);z-index:100;box-shadow:2px 0 18px rgba(0,0,0,.07);transition:transform .3s;flex-shrink:0}
.sb-top{padding:14px 15px 11px;border-bottom:1px solid var(--border)}
.sw{position:relative;margin-bottom:9px}
.sw input{width:100%;padding:10px 14px 10px 37px;border:1.5px solid var(--border);border-radius:10px;font-size:.86rem;font-family:'DM Sans',sans-serif;color:var(--text);background:var(--bg);outline:none;transition:border-color .2s,background .2s}
.sw input:focus{border-color:var(--teal);background:#fff}
.si{position:absolute;left:11px;top:50%;transform:translateY(-50%);color:var(--muted);pointer-events:none}
.chips{display:flex;gap:5px;flex-wrap:wrap}
.chip{padding:4px 10px;border-radius:20px;font-size:.7rem;font-weight:700;border:1.5px solid var(--border);color:var(--muted);background:var(--bg);transition:all .2s;cursor:pointer;user-select:none}
.chip:hover,.chip.on{background:var(--teal);border-color:var(--teal);color:#fff}
.chip.e.on{background:var(--red);border-color:var(--red)}

/* AREA ROW */
.areas{display:flex;gap:5px;flex-wrap:wrap;padding:7px 15px 9px;border-bottom:1px solid var(--border);background:#fafcff}
.ac{padding:3px 9px;border-radius:14px;font-size:.67rem;font-weight:700;border:1.5px solid var(--border);color:var(--muted);background:#fff;transition:all .2s;cursor:pointer;user-select:none}
.ac:hover,.ac.on{background:var(--teal);border-color:var(--teal);color:#fff}

/* STATS */
.stats{display:flex;padding:9px 15px;gap:8px;background:linear-gradient(135deg,#e6fafa,#f0faf5);border-bottom:1px solid var(--border)}
.stat{flex:1;text-align:center}
.sn{font-family:'Syne',sans-serif;font-size:1.22rem;font-weight:800;color:var(--teal)}
.sl{font-size:.63rem;color:var(--muted);font-weight:700;text-transform:uppercase;letter-spacing:.5px}
.rlbl{padding:6px 15px;font-size:.7rem;color:var(--muted);font-weight:600;border-bottom:1px solid var(--border)}

/* LIST */
.hlist{flex:1;overflow-y:auto;padding:8px}
.hlist::-webkit-scrollbar{width:4px}
.hlist::-webkit-scrollbar-thumb{background:var(--border);border-radius:2px}

/* CARD */
.hc{background:var(--surface);border:1.5px solid var(--border);border-radius:var(--r);padding:12px 13px;margin-bottom:7px;cursor:pointer;transition:all .22s;position:relative;overflow:hidden}
.hc::before{content:'';position:absolute;left:0;top:0;bottom:0;width:3px;background:var(--teal);opacity:0;transition:opacity .2s}
.hc:hover,.hc.sel{border-color:var(--teal);box-shadow:var(--sh);transform:translateY(-1px)}
.hc:hover::before,.hc.sel::before{opacity:1}
.ct{display:flex;justify-content:space-between;align-items:flex-start;gap:7px;margin-bottom:5px}
.cn{font-family:'Syne',sans-serif;font-size:.87rem;font-weight:700;line-height:1.3}
.cb{font-size:.62rem;font-weight:700;text-transform:uppercase;letter-spacing:.4px;padding:2px 7px;border-radius:9px;flex-shrink:0}
.tg{background:#ebf8ff;color:#2563eb} .tp{background:#f0fff4;color:#276749} .ts{background:#fff5f5;color:#b91c1c}
.ca{font-size:.74rem;color:var(--muted);display:flex;align-items:flex-start;gap:4px;margin-bottom:6px;line-height:1.4}
.cm{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:4px}
.stars{display:flex;align-items:center;gap:2px}
.rn{font-weight:700;color:var(--text);font-size:.75rem;margin-left:2px}
.ob{font-size:.65rem;font-weight:700;padding:2px 7px;border-radius:9px}
.oo{background:#dcfce7;color:#166534} .oc{background:#fee2e2;color:#b91c1c} .o24{background:#dbeafe;color:#1d4ed8}
.cbs{display:flex;gap:5px;margin-top:8px}
.cbtn{flex:1;padding:6px;border-radius:7px;font-size:.7rem;font-weight:700;border:none;display:flex;align-items:center;justify-content:center;gap:4px;transition:all .2s;font-family:'DM Sans',sans-serif}
.bi{background:var(--bg);color:var(--teal);border:1.5px solid var(--teal)} .bi:hover{background:var(--teal);color:#fff}
.bn{background:var(--teal);color:#fff} .bn:hover{background:var(--teal-d)}
.bc{background:var(--green);color:#fff;flex:0;padding:6px 9px} .bc:hover{opacity:.85}

/* MAP */
#map{flex:1;height:100%;position:relative}

/* NAV PANEL */
.navp{position:absolute;bottom:28px;left:50%;transform:translateX(-50%);background:var(--surface);border-radius:var(--r);padding:13px 18px;box-shadow:var(--sh-lg);z-index:500;display:none;align-items:center;gap:13px;min-width:300px;border:1.5px solid var(--border)}
.navp.vis{display:flex}
.ni{flex:1}
.nd{font-family:'Syne',sans-serif;font-size:.86rem;font-weight:700;margin-bottom:2px}
.nm{font-size:.73rem;color:var(--muted)}
.bsn{background:var(--red);color:#fff;border:none;padding:8px 13px;border-radius:8px;font-size:.76rem;font-weight:700;transition:opacity .2s}
.bsn:hover{opacity:.85}

/* POPUP */
.leaflet-popup-content-wrapper{border-radius:12px!important;box-shadow:var(--sh-lg)!important;padding:0!important;overflow:hidden}
.leaflet-popup-content{margin:0!important;width:285px!important}

/* MODAL */
.mbg{position:fixed;inset:0;background:rgba(0,0,0,.48);z-index:3000;display:none;align-items:center;justify-content:center;padding:16px}
.mbg.open{display:flex}
.modal{background:#fff;border-radius:18px;max-width:520px;width:100%;max-height:85vh;overflow-y:auto;box-shadow:0 20px 60px rgba(0,0,0,.28);animation:mIn .28s ease}
@keyframes mIn{from{transform:scale(.93) translateY(16px);opacity:0}to{transform:scale(1) translateY(0);opacity:1}}
.modal::-webkit-scrollbar{width:4px}
.modal::-webkit-scrollbar-thumb{background:var(--border);border-radius:2px}
.mh{background:linear-gradient(135deg,var(--teal-d),var(--teal-l));padding:20px 22px 16px;color:#fff;position:relative}
.mc{position:absolute;top:14px;right:14px;background:rgba(255,255,255,.2);border:none;color:#fff;width:28px;height:28px;border-radius:50%;font-size:.93rem;display:flex;align-items:center;justify-content:center;transition:background .2s}
.mc:hover{background:rgba(255,255,255,.35)}
.mn{font-family:'Syne',sans-serif;font-size:1.18rem;font-weight:800;margin-bottom:5px;padding-right:34px;line-height:1.3}
.mt{display:inline-block;background:rgba(255,255,255,.2);padding:2px 11px;border-radius:20px;font-size:.69rem;font-weight:700;text-transform:uppercase;letter-spacing:.4px}
.mb{padding:18px 22px}
.dg{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:15px}
.di{background:var(--bg);border-radius:9px;padding:11px}
.dl{font-size:.65rem;font-weight:700;text-transform:uppercase;letter-spacing:.5px;color:var(--muted);margin-bottom:3px}
.dv{font-size:.85rem;font-weight:600;color:var(--text)}
.svcs{display:flex;flex-wrap:wrap;gap:5px;margin-bottom:15px}
.svc{background:linear-gradient(135deg,#e6fafa,#eef4ff);border:1px solid rgba(10,143,143,.2);color:var(--teal-d);padding:3px 10px;border-radius:9px;font-size:.7rem;font-weight:600}
.mbtns{display:flex;gap:8px}
.mbtn{flex:1;padding:11px;border-radius:10px;border:none;font-size:.82rem;font-weight:700;font-family:'DM Sans',sans-serif;display:flex;align-items:center;justify-content:center;gap:6px;transition:all .2s}
.mb-n{background:var(--teal);color:#fff} .mb-n:hover{background:var(--teal-d)}
.mb-c{background:var(--green);color:#fff} .mb-c:hover{opacity:.85}
.mb-w{background:#25d366;color:#fff}     .mb-w:hover{opacity:.85}

/* LOADER */
.loader{position:fixed;inset:0;background:linear-gradient(135deg,var(--teal-d),var(--teal));z-index:9999;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:20px;transition:opacity .5s}
.loader.fade{opacity:0;pointer-events:none}
.lc{animation:lft 2s ease-in-out infinite}
@keyframes lft{0%,100%{transform:translateY(0)}50%{transform:translateY(-10px)}}
.lt{font-family:'Syne',sans-serif;color:#fff;font-size:1.52rem;font-weight:800}
.ls{color:rgba(255,255,255,.72);font-size:.85rem}
.lb{width:190px;height:3px;background:rgba(255,255,255,.2);border-radius:2px;overflow:hidden}
.lf{height:100%;background:#7fecec;animation:lbar 2.3s ease forwards}
@keyframes lbar{from{width:0}to{width:100%}}

/* TOAST */
.toast{position:fixed;bottom:76px;right:16px;background:#1a202c;color:#fff;padding:10px 16px;border-radius:10px;font-size:.79rem;font-weight:500;z-index:9999;opacity:0;transform:translateY(8px);transition:all .28s;max-width:290px;pointer-events:none}
.toast.show{opacity:1;transform:translateY(0)}

/* CREDIT */
.credit{position:fixed;bottom:0;right:0;background:rgba(255,255,255,.94);backdrop-filter:blur(8px);border-top-left-radius:12px;padding:7px 14px;font-size:.69rem;color:var(--muted);z-index:900;border:1px solid var(--border);display:flex;align-items:center;gap:7px}
.credit a{color:var(--teal);font-weight:700}
.credit a:hover{text-decoration:underline}
.wa{display:inline-flex;align-items:center;gap:4px;background:#25d366;color:#fff!important;padding:2px 8px;border-radius:10px;font-weight:700!important;font-size:.67rem}

/* MOBILE */
.mob{display:none;position:fixed;bottom:76px;left:14px;z-index:800;background:var(--teal);color:#fff;border:none;border-radius:50%;width:48px;height:48px;font-size:1.15rem;box-shadow:var(--sh);align-items:center;justify-content:center}
@media(max-width:768px){
  .sb{position:fixed;left:0;top:0;bottom:0;transform:translateX(-100%);z-index:500;padding-top:62px}
  .sb.open{transform:translateX(0)}
  .mob{display:flex}
  .live-badge,.areas{display:none}
}

/* LEAFLET */
.leaflet-control-attribution{display:none}
.leaflet-routing-container{background:var(--surface)!important;border-radius:var(--r)!important;box-shadow:var(--sh-lg)!important;border:1.5px solid var(--border)!important;max-height:210px!important;overflow-y:auto!important;font-family:'DM Sans',sans-serif!important;font-size:.77rem!important}
</style>
</head>
<body>

<!-- LOADER -->
<div class="loader" id="loader">
  <div class="lc">
    <svg width="66" height="66" viewBox="0 0 66 66" fill="none">
      <circle cx="33" cy="33" r="32" fill="rgba(255,255,255,.1)" stroke="rgba(255,255,255,.35)" stroke-width="2"/>
      <rect x="25" y="9" width="16" height="48" rx="5" fill="white"/>
      <rect x="9" y="25" width="48" height="16" rx="5" fill="white"/>
    </svg>
  </div>
  <div class="lt">MediMap Dhaka</div>
  <div class="ls">Loading 73 hospitals &amp; live map…</div>
  <div class="lb"><div class="lf"></div></div>
</div>

<!-- HEADER -->
<header>
  <div class="logo">
    <div class="logo-icon">
      <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
        <rect x="7" y="1" width="6" height="18" rx="2.5" fill="white"/>
        <rect x="1" y="7" width="18" height="6" rx="2.5" fill="white"/>
      </svg>
    </div>
    <div class="logo-txt">Medi<span>Map</span> Dhaka</div>
  </div>
  <div class="hdr-r">
    <div class="live-badge"><div class="pulse"></div> Live · 73 Hospitals</div>
    <button class="btn-locate" onclick="locateUser()">
      <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><circle cx="12" cy="12" r="3"/><path d="M12 2v3M12 19v3M2 12h3M19 12h3"/></svg>
      My Location
    </button>
  </div>
</header>

<!-- EMERGENCY STRIP -->
<div class="emg">
  🚨 Emergency: <a href="tel:999">999</a>
  Ambulance: <a href="tel:199">199</a>
  Fire: <a href="tel:102">102</a>
  Police: <a href="tel:100">100</a>
</div>

<!-- APP -->
<div class="app">
  <!-- SIDEBAR -->
  <div class="sb" id="sb">
    <div class="sb-top">
      <div class="sw">
        <svg class="si" width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
        <input type="search" id="q" placeholder="Hospital, area, or service…" oninput="applyFilters()"/>
      </div>
      <div class="chips">
        <div class="chip on" onclick="setType('all',this)">All</div>
        <div class="chip"    onclick="setType('govt',this)">Govt</div>
        <div class="chip"    onclick="setType('private',this)">Private</div>
        <div class="chip"    onclick="setType('special',this)">Specialist</div>
        <div class="chip e"  onclick="setType('24h',this)">24H</div>
        <div class="chip e"  onclick="setType('emg',this)">Emergency</div>
      </div>
    </div>
    <div class="areas">
      <div class="ac on"  onclick="setArea('all',this)">All Areas</div>
      <div class="ac"     onclick="setArea('mirpur',this)">Mirpur</div>
      <div class="ac"     onclick="setArea('dhanmondi',this)">Dhanmondi</div>
      <div class="ac"     onclick="setArea('uttara',this)">Uttara</div>
      <div class="ac"     onclick="setArea('farmgate',this)">Farmgate</div>
      <div class="ac"     onclick="setArea('kawran',this)">Kawran Bazar</div>
      <div class="ac"     onclick="setArea('motijheel',this)">Motijheel</div>
      <div class="ac"     onclick="setArea('sayedabad',this)">Sayedabad</div>
      <div class="ac"     onclick="setArea('gulistan',this)">Gulistan</div>
      <div class="ac"     onclick="setArea('shahbagh',this)">Shahbagh</div>
      <div class="ac"     onclick="setArea('gulshan',this)">Gulshan</div>
      <div class="ac"     onclick="setArea('bashundhara',this)">Bashundhara</div>
      <div class="ac"     onclick="setArea('panthapath',this)">Panthapath</div>
    </div>
    <div class="stats">
      <div class="stat"><div class="sn" id="sTot">0</div><div class="sl">Hospitals</div></div>
      <div class="stat"><div class="sn" id="sOpen">0</div><div class="sl">Open Now</div></div>
      <div class="stat"><div class="sn" id="sEmg">0</div><div class="sl">Emergency</div></div>
      <div class="stat"><div class="sn" id="s24">0</div><div class="sl">24H Open</div></div>
    </div>
    <div class="rlbl" id="rlbl">Loading…</div>
    <div class="hlist" id="hlist"></div>
  </div>

  <!-- MAP -->
  <div id="map">
    <div class="navp" id="navp">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#0a8f8f" stroke-width="2.5"><polygon points="3 11 22 2 13 21 11 13 3 11"/></svg>
      <div class="ni"><div class="nd" id="navd">Navigating…</div><div class="nm" id="navm">Calculating route…</div></div>
      <button class="bsn" onclick="stopNav()">✕ Stop</button>
    </div>
  </div>
</div>

<button class="mob" onclick="document.getElementById('sb').classList.toggle('open')">☰</button>

<!-- MODAL -->
<div class="mbg" id="mbg" onclick="if(event.target===this)closeModal()">
  <div class="modal">
    <div class="mh">
      <button class="mc" onclick="closeModal()">✕</button>
      <div class="mn" id="mN">—</div>
      <span class="mt" id="mT">—</span>
    </div>
    <div class="mb" id="mB"></div>
  </div>
</div>

<div class="toast" id="toast"></div>

<div class="credit">
  🏥 Built for public health by
  <a href="https://www.linkedin.com/in/iftekhar-mohammad-irab" target="_blank" rel="noopener">Iftekhar Mohammad Irab</a>
  <a href="https://wa.me/8801619804451" target="_blank" rel="noopener" class="wa">
    <svg width="10" height="10" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
    WhatsApp
  </a>
</div>

<script>
/* ── CDN FALLBACK: if jsDelivr fails, retry with unpkg ─ */
function _showErr(){document.body.innerHTML='<div style="display:flex;height:100vh;align-items:center;justify-content:center;flex-direction:column;gap:14px;font-family:sans-serif;padding:20px;text-align:center"><h2 style="color:#dc2626">⚠️ Map failed to load</h2><p style="color:#6b7280">No internet or CDN unreachable.</p><button onclick="location.reload()" style="padding:11px 28px;background:#0a8f8f;color:#fff;border:none;border-radius:9px;cursor:pointer;font-size:1rem;font-weight:700">↺ Reload</button></div>';}
function _boot(){
  if(typeof L==='undefined'||typeof L.Routing==='undefined'){_showErr();return;}
  _run();
}

/* ── HOSPITAL DATA ─────────────────────────────────── */
const DB=[
  /* === EXISTING CORE === */
  {id:1,name:"Square Hospital",type:"private",area:"panthapath",lat:23.7463,lng:90.3724,address:"18/F Bir Uttam Qazi Nuruzzaman Sarak, Panthapath, Dhaka 1205",phone:"10616",hours:"24 Hours",always:true,rating:4.7,reviews:2840,services:["Cardiology","Neurology","Oncology","Pediatrics","Orthopedics","ICU","Emergency","NICU"],beds:500,emergency:true,website:"squarehospital.com"},
  {id:2,name:"United Hospital Limited",type:"private",area:"gulshan",lat:23.7940,lng:90.4149,address:"Plot 15, Road 71, Gulshan, Dhaka 1212",phone:"+8809610002",hours:"24 Hours",always:true,rating:4.6,reviews:3120,services:["Cardiology","Orthopedics","Gastroenterology","Oncology","Neurology","Emergency"],beds:500,emergency:true,website:"uhlbd.com"},
  {id:3,name:"Evercare Hospital Dhaka",type:"private",area:"bashundhara",lat:23.8223,lng:90.4278,address:"Plot 81, Block E, Bashundhara R/A, Dhaka 1229",phone:"+8809617002273",hours:"24 Hours",always:true,rating:4.5,reviews:1987,services:["Cardiology","Cancer Care","Orthopedics","Neurosurgery","IVF","Emergency"],beds:450,emergency:true,website:"evercarebd.com"},
  {id:4,name:"BIRDEM General Hospital",type:"special",area:"shahbagh",lat:23.7396,lng:90.3958,address:"122 Kazi Nazrul Islam Avenue, Shahbagh, Dhaka 1000",phone:"58610642",hours:"8 AM – 8 PM",always:false,rating:4.4,reviews:2210,services:["Diabetology","Endocrinology","Nephrology","Cardiology","Ophthalmology"],beds:600,emergency:true,website:"birdembd.org"},
  {id:5,name:"Dhaka Medical College Hospital",type:"govt",area:"shahbagh",lat:23.7225,lng:90.3954,address:"Bakshibazar, Dhaka 1000",phone:"0255165001",hours:"24 Hours",always:true,rating:3.9,reviews:4530,services:["Emergency","General Surgery","Gynecology","Pediatrics","Orthopedics","Burns Unit"],beds:2600,emergency:true,website:"dmc.gov.bd"},
  {id:6,name:"Bangabandhu Sheikh Mujib Medical University",type:"govt",area:"shahbagh",lat:23.7390,lng:90.3970,address:"Shahbagh, Dhaka 1000",phone:"0255167500",hours:"24 Hours",always:true,rating:4.2,reviews:3680,services:["Oncology","Hematology","Pediatrics","Cardiology","Neurology","Transplant"],beds:1700,emergency:true,website:"bsmmu.edu.bd"},
  {id:7,name:"National Heart Foundation Hospital",type:"special",area:"mirpur",lat:23.7924,lng:90.3683,address:"Plot 7/2, Section 2, Mirpur, Dhaka 1216",phone:"09666750075",hours:"24 Hours",always:true,rating:4.5,reviews:1876,services:["Cardiology","Cardiac Surgery","CCU","Cath Lab","Pacemaker","Echo"],beds:400,emergency:true,website:"nhf.org.bd"},
  {id:8,name:"Green Life Medical College Hospital",type:"private",area:"panthapath",lat:23.7441,lng:90.3752,address:"32 Bir Uttam K.M. Shafiullah Sarak, Green Road, Dhaka 1205",phone:"+880258611229",hours:"24 Hours",always:true,rating:4.3,reviews:1543,services:["Cardiology","Neurology","Orthopedics","Oncology","Pediatrics","Emergency"],beds:500,emergency:true,website:"greenlifebd.com"},
  {id:9,name:"Labaid Specialized Hospital",type:"private",area:"dhanmondi",lat:23.7472,lng:90.3742,address:"Road 6 & 7, House 6/2, Dhanmondi, Dhaka 1209",phone:"+880255022021",hours:"24 Hours",always:true,rating:4.3,reviews:2089,services:["Cardiac","Orthopedics","Neurology","Urology","Oncology","ICU"],beds:350,emergency:true,website:"labaidhospital.com"},
  {id:10,name:"Holy Family Red Crescent Medical College Hospital",type:"private",area:"shahbagh",lat:23.7408,lng:90.4003,address:"1 Eskaton Garden Road, Dhaka 1000",phone:"+88028312550",hours:"24 Hours",always:true,rating:4.1,reviews:1782,services:["Gynecology","Pediatrics","Surgery","Medicine","Emergency","ICU"],beds:450,emergency:true,website:"hfrcmch.edu.bd"},
  {id:11,name:"Shahid Suhrawardy Medical College Hospital",type:"govt",area:"mirpur",lat:23.7721,lng:90.3666,address:"Sher-e-Bangla Nagar, Shyamoli, Dhaka",phone:"9122560",hours:"24 Hours",always:true,rating:3.8,reviews:2340,services:["Emergency","General Surgery","Gynecology","Pediatrics","Medicine"],beds:500,emergency:true},
  {id:12,name:"Ad-Din Women's Medical College Hospital",type:"private",area:"moghbazar",lat:23.7504,lng:90.4094,address:"2 Bara Moghbazar, Dhaka 1217",phone:"9353391",hours:"24 Hours",always:true,rating:4.2,reviews:1430,services:["Gynecology","Obstetrics","Pediatrics","Neonatal ICU","Emergency"],beds:300,emergency:true},
  {id:13,name:"Asgar Ali Hospital",type:"private",area:"gandaria",lat:23.7105,lng:90.4133,address:"111/1/A Distillery Road, Gandaria, Dhaka 1204",phone:"01715000098",hours:"24 Hours",always:true,rating:4.0,reviews:1210,services:["General Medicine","Surgery","Gynecology","Pediatrics","Emergency"],beds:250,emergency:true},
  {id:14,name:"Ibn Sina Hospital Dhanmondi",type:"private",area:"dhanmondi",lat:23.7394,lng:90.3694,address:"House 48, Road 9/A, Dhanmondi, Dhaka 1209",phone:"9118206",hours:"8 AM – 10 PM",always:false,rating:4.1,reviews:1654,services:["Cardiology","Gastroenterology","Neurology","Diagnostics","Pathology"],beds:150,emergency:false,website:"ibnsinahospital.com"},
  {id:15,name:"Mugda Medical College Hospital",type:"govt",area:"mugda",lat:23.7296,lng:90.4321,address:"Dr. Kudrat-e-Khuda Road, Mugda, Dhaka",phone:"0255167600",hours:"24 Hours",always:true,rating:3.7,reviews:1120,services:["Emergency","General Medicine","Surgery","Pediatrics","ICU"],beds:500,emergency:true},
  {id:16,name:"Kuwait Bangladesh Friendship Govt. Hospital",type:"govt",area:"uttara",lat:23.8734,lng:90.3992,address:"Uttara, Dhaka 1230",phone:"028920161",hours:"24 Hours",always:true,rating:3.8,reviews:980,services:["General Medicine","Surgery","Orthopedics","Gynecology","Emergency"],beds:250,emergency:true},
  {id:17,name:"Popular Medical College Hospital",type:"private",area:"dhanmondi",lat:23.7495,lng:90.3688,address:"House 14, Road 4, Dhanmondi, Dhaka",phone:"+8801766660001",hours:"24 Hours",always:true,rating:4.0,reviews:1340,services:["Cardiology","Neurology","Oncology","Orthopedics","Emergency"],beds:300,emergency:true,website:"popularmedical.net"},
  {id:18,name:"Medinova Medical Moghbazar",type:"private",area:"moghbazar",lat:23.7478,lng:90.4082,address:"House 66/1, Road 1, Block B, Moghbazar, Dhaka",phone:"9333445",hours:"8 AM – 9 PM",always:false,rating:4.1,reviews:1098,services:["Cardiology","Gastroenterology","Neurology","Diagnostics"],beds:120,emergency:false,website:"medinovabd.com"},
  {id:19,name:"Central Hospital Limited",type:"private",area:"dhanmondi",lat:23.7465,lng:90.3720,address:"House 2, Road 5, Dhanmondi, Dhaka 1205",phone:"+88028619200",hours:"24 Hours",always:true,rating:4.2,reviews:1567,services:["Gynecology","Pediatrics","Cardiology","Oncology","ICU","Emergency"],beds:200,emergency:true,website:"centralhospitalltd.com"},
  {id:20,name:"Anwer Khan Modern Medical College Hospital",type:"private",area:"dhanmondi",lat:23.7431,lng:90.3660,address:"House 20, Road 8, Dhanmondi, Dhaka 1205",phone:"+88029130025",hours:"24 Hours",always:true,rating:4.0,reviews:1120,services:["General Medicine","Surgery","Gynecology","Pediatrics","Emergency"],beds:250,emergency:true},
  {id:21,name:"Islami Bank Hospital Kakrail",type:"private",area:"kakrail",lat:23.7520,lng:90.3917,address:"29 Kakrail, Dhaka 1000",phone:"9341439",hours:"24 Hours",always:true,rating:4.0,reviews:1243,services:["General Medicine","Surgery","Cardiology","Emergency","ICU"],beds:300,emergency:true},
  {id:22,name:"Bangladesh Eye Hospital",type:"special",area:"panthapath",lat:23.7510,lng:90.3880,address:"Mirpur Road, Sher-e-Bangla Nagar, Dhaka",phone:"9112206",hours:"8 AM – 8 PM",always:false,rating:4.3,reviews:876,services:["Ophthalmology","Laser Surgery","Cataract","Glaucoma","Retina"],beds:150,emergency:false},
  {id:23,name:"Kurmitola General Hospital",type:"govt",area:"cantonment",lat:23.8143,lng:90.4051,address:"Cantonment, Dhaka 1206",phone:"8870361",hours:"24 Hours",always:true,rating:3.6,reviews:1432,services:["General Medicine","Emergency","Surgery","Pediatrics"],beds:250,emergency:true},
  {id:24,name:"MH Samorita Hospital",type:"private",area:"panthapath",lat:23.7511,lng:90.3734,address:"89/1 Panthapath, Tejgaon, Dhaka",phone:"+88028116603",hours:"24 Hours",always:true,rating:4.0,reviews:1034,services:["Cardiology","Neurology","Surgery","Gynecology","Emergency"],beds:250,emergency:true},
  {id:25,name:"National Institute of Cardiovascular Diseases",type:"govt",area:"farmgate",lat:23.7554,lng:90.3897,address:"Sher-e-Bangla Nagar, Farmgate, Dhaka 1207",phone:"9113557",hours:"24 Hours",always:true,rating:4.1,reviews:2120,services:["Cardiology","Cardiac Surgery","CCU","Cath Lab","Heart Failure","Echo"],beds:600,emergency:true},

  /* === MIRPUR (10) === */
  {id:26,name:"National Institute of Neurosciences & Hospital",type:"govt",area:"mirpur",lat:23.7880,lng:90.3640,address:"Agargaon, Sher-e-Bangla Nagar, Dhaka 1207",phone:"029123188",hours:"24 Hours",always:true,rating:4.2,reviews:1876,services:["Neurology","Neurosurgery","Stroke","Epilepsy","Spine Surgery","Emergency"],beds:500,emergency:true},
  {id:27,name:"Ibn Sina Medical College Hospital Mirpur",type:"private",area:"mirpur",lat:23.8034,lng:90.3556,address:"House 1, Road 5, Section 6, Mirpur, Dhaka 1216",phone:"01713374555",hours:"24 Hours",always:true,rating:4.0,reviews:1120,services:["General Medicine","Surgery","Gynecology","Pediatrics","Emergency","ICU"],beds:300,emergency:true},
  {id:28,name:"Popular Diagnostic Centre Mirpur",type:"private",area:"mirpur",lat:23.7969,lng:90.3598,address:"3/1B, Section 6, Mirpur, Dhaka 1216",phone:"01766660002",hours:"8 AM – 9 PM",always:false,rating:4.0,reviews:876,services:["Diagnostics","Pathology","Radiology","CT Scan","MRI","Ultrasound"],beds:80,emergency:false,website:"populardiagnostic.com"},
  {id:29,name:"Nightingale Hospital Mirpur",type:"private",area:"mirpur",lat:23.8095,lng:90.3620,address:"Block C, Section 11, Mirpur, Dhaka 1216",phone:"01847120000",hours:"24 Hours",always:true,rating:3.8,reviews:654,services:["General Medicine","Surgery","Gynecology","Emergency","Pediatrics"],beds:150,emergency:true},
  {id:30,name:"Dhaka Shishu (Children) Hospital",type:"govt",area:"mirpur",lat:23.7780,lng:90.3559,address:"Sher-e-Bangla Nagar, Mirpur Road, Dhaka 1207",phone:"9112443",hours:"24 Hours",always:true,rating:4.1,reviews:2340,services:["Pediatrics","Neonatology","Pediatric Surgery","PICU","NICU","Pediatric Cardiology"],beds:800,emergency:true,website:"dsh.gov.bd"},
  {id:31,name:"National Inst. of Traumatology & Orthopedic",type:"govt",area:"mirpur",lat:23.7812,lng:90.3623,address:"Sher-e-Bangla Nagar, Agargaon, Dhaka 1207",phone:"9121028",hours:"24 Hours",always:true,rating:4.0,reviews:1540,services:["Orthopedics","Trauma Surgery","Spine","Fracture","Physiotherapy","Rehabilitation"],beds:450,emergency:true},
  {id:32,name:"Mirpur General Hospital",type:"private",area:"mirpur",lat:23.8060,lng:90.3568,address:"Block B, Section 10, Mirpur, Dhaka 1216",phone:"01711993454",hours:"24 Hours",always:true,rating:3.7,reviews:678,services:["General Medicine","Surgery","Emergency","Gynecology"],beds:100,emergency:true},
  {id:33,name:"Medinova Medical Mirpur",type:"private",area:"mirpur",lat:23.7993,lng:90.3576,address:"House 5, Road 2, Section 6, Mirpur, Dhaka 1216",phone:"01715050550",hours:"8 AM – 9 PM",always:false,rating:4.0,reviews:765,services:["Cardiology","Gastroenterology","Neurology","Diagnostics","Radiology"],beds:100,emergency:false},
  {id:34,name:"Doctors Hospital Mirpur",type:"private",area:"mirpur",lat:23.8020,lng:90.3545,address:"Plot 9, Section 6, Mirpur, Dhaka 1216",phone:"01709443322",hours:"24 Hours",always:true,rating:3.8,reviews:543,services:["General Medicine","Surgery","Orthopedics","Emergency","ICU"],beds:120,emergency:true},
  {id:35,name:"Dr. Sirajul Islam Medical College Hospital",type:"private",area:"mirpur",lat:23.7842,lng:90.3695,address:"Mirpur 1, Dhaka 1216",phone:"01713013066",hours:"24 Hours",always:true,rating:3.9,reviews:876,services:["Medicine","Surgery","Gynecology","Pediatrics","Emergency"],beds:200,emergency:true},

  /* === DHANMONDI (10) === */
  {id:36,name:"Impulse Hospital",type:"private",area:"dhanmondi",lat:23.7524,lng:90.3751,address:"House 304, Road 6, Dhanmondi, Dhaka",phone:"01780668877",hours:"24 Hours",always:true,rating:4.1,reviews:987,services:["Cardiology","Orthopedics","ENT","Ophthalmology","Emergency","Dialysis"],beds:200,emergency:true,website:"impulsehospital.com"},
  {id:37,name:"Comfort Nursing Home",type:"private",area:"dhanmondi",lat:23.7482,lng:90.3728,address:"House 14/2, Road 2, Dhanmondi, Dhaka 1205",phone:"8613666",hours:"24 Hours",always:true,rating:3.9,reviews:654,services:["Gynecology","Obstetrics","General Surgery","Emergency","ICU"],beds:100,emergency:true},
  {id:38,name:"Shahabuddin Medical College Hospital",type:"private",area:"dhanmondi",lat:23.7543,lng:90.3703,address:"House 52, Road 8, Dhanmondi, Dhaka 1209",phone:"9114313",hours:"24 Hours",always:true,rating:3.9,reviews:721,services:["General Medicine","Surgery","Gynecology","Pediatrics","Emergency"],beds:200,emergency:true},
  {id:39,name:"Pain Management Centre",type:"special",area:"dhanmondi",lat:23.7419,lng:90.3681,address:"House 3, Road 27, Dhanmondi, Dhaka",phone:"01811456789",hours:"9 AM – 6 PM",always:false,rating:4.2,reviews:432,services:["Pain Management","Physiotherapy","Spine","Neurology","Rehabilitation"],beds:30,emergency:false},
  {id:40,name:"Dhanmondi Hospital Ltd",type:"private",area:"dhanmondi",lat:23.7503,lng:90.3712,address:"House 13/1, Road 3, Dhanmondi, Dhaka 1205",phone:"8618891",hours:"24 Hours",always:true,rating:3.8,reviews:543,services:["General Medicine","Surgery","Gynecology","Emergency"],beds:80,emergency:true},
  {id:41,name:"City Hospital Dhanmondi",type:"private",area:"dhanmondi",lat:23.7459,lng:90.3697,address:"House 33, Road 8/A, Dhanmondi, Dhaka 1209",phone:"9115277",hours:"24 Hours",always:true,rating:3.8,reviews:489,services:["Medicine","Surgery","ENT","Orthopedics","Emergency"],beds:100,emergency:true},
  {id:42,name:"Bangladesh Medical College Hospital",type:"private",area:"dhanmondi",lat:23.7508,lng:90.3748,address:"House 34, Road 14/A, Dhanmondi, Dhaka 1209",phone:"9120066",hours:"24 Hours",always:true,rating:4.0,reviews:1087,services:["Medicine","Surgery","Gynecology","Pediatrics","Emergency","ICU"],beds:300,emergency:true},
  {id:43,name:"Pragati Medical Services",type:"private",area:"dhanmondi",lat:23.7436,lng:90.3643,address:"House 23, Road 5, Dhanmondi, Dhaka 1209",phone:"9124501",hours:"8 AM – 9 PM",always:false,rating:3.9,reviews:376,services:["Cardiology","Diabetes","Endocrinology","Gastroenterology","Diagnostics"],beds:60,emergency:false},
  {id:44,name:"Galaxy Diagnostic & Hospital",type:"private",area:"dhanmondi",lat:23.7450,lng:90.3670,address:"Road 4, Dhanmondi, Dhaka 1205",phone:"01714998877",hours:"8 AM – 10 PM",always:false,rating:3.8,reviews:421,services:["Diagnostics","CT Scan","MRI","Pathology","Ultrasound"],beds:50,emergency:false},
  {id:45,name:"Breast Health & Cancer Centre Dhanmondi",type:"special",area:"dhanmondi",lat:23.7466,lng:90.3658,address:"House 20, Road 7, Dhanmondi, Dhaka 1205",phone:"01713243556",hours:"9 AM – 5 PM",always:false,rating:4.3,reviews:345,services:["Breast Oncology","Cancer Screening","Mammography","Surgical Oncology"],beds:30,emergency:false},

  /* === UTTARA (10) === */
  {id:46,name:"Uttara Adhunik Medical College Hospital",type:"private",area:"uttara",lat:23.8743,lng:90.4004,address:"House 8, Road 6, Sector 9, Uttara, Dhaka 1230",phone:"8992626",hours:"24 Hours",always:true,rating:4.0,reviews:987,services:["General Medicine","Surgery","Gynecology","Pediatrics","Emergency","ICU"],beds:300,emergency:true,website:"uamch.edu.bd"},
  {id:47,name:"Crescent Hospital Uttara",type:"private",area:"uttara",lat:23.8699,lng:90.3967,address:"House 48, Road 7, Sector 7, Uttara, Dhaka 1230",phone:"01811345678",hours:"24 Hours",always:true,rating:3.9,reviews:765,services:["Medicine","Surgery","Gynecology","Orthopedics","Emergency"],beds:150,emergency:true},
  {id:48,name:"Uttara Modern Hospital",type:"private",area:"uttara",lat:23.8750,lng:90.3980,address:"House 5, Road 4, Sector 6, Uttara, Dhaka 1230",phone:"01712334455",hours:"24 Hours",always:true,rating:3.9,reviews:654,services:["General Medicine","Surgery","Pediatrics","Emergency","ICU"],beds:120,emergency:true},
  {id:49,name:"National Hospital Uttara",type:"private",area:"uttara",lat:23.8664,lng:90.3940,address:"House 13, Road 3, Sector 4, Uttara, Dhaka 1230",phone:"8953412",hours:"24 Hours",always:true,rating:3.7,reviews:543,services:["Medicine","Surgery","Gynecology","Emergency"],beds:100,emergency:true},
  {id:50,name:"LABAID Hospital Uttara",type:"private",area:"uttara",lat:23.8680,lng:90.3975,address:"House 19, Road 12, Sector 10, Uttara, Dhaka 1230",phone:"01766660010",hours:"24 Hours",always:true,rating:4.1,reviews:876,services:["Cardiac","Orthopedics","Neurology","Dialysis","Emergency","ICU"],beds:200,emergency:true,website:"labaidhospital.com"},
  {id:51,name:"Hope Hospital Uttara",type:"private",area:"uttara",lat:23.8712,lng:90.3955,address:"House 7, Road 8, Sector 4, Uttara, Dhaka 1230",phone:"01714556677",hours:"24 Hours",always:true,rating:3.8,reviews:456,services:["Medicine","Surgery","Gynecology","Pediatrics","Emergency"],beds:100,emergency:true},
  {id:52,name:"Care Medical College Hospital Uttara",type:"private",area:"uttara",lat:23.8724,lng:90.4012,address:"House 22, Road 13, Sector 12, Uttara, Dhaka 1230",phone:"8952233",hours:"24 Hours",always:true,rating:3.8,reviews:654,services:["Medicine","Surgery","Gynecology","Orthopedics","Emergency","ICU"],beds:150,emergency:true},
  {id:53,name:"Diabetic Hospital Uttara",type:"special",area:"uttara",lat:23.8650,lng:90.3960,address:"Plot 10, Road 5, Sector 3, Uttara, Dhaka 1230",phone:"01713456789",hours:"8 AM – 8 PM",always:false,rating:4.0,reviews:543,services:["Diabetology","Endocrinology","Nephrology","Eye Care","Foot Care"],beds:100,emergency:false},
  {id:54,name:"Regent Hospital Uttara",type:"private",area:"uttara",lat:23.8693,lng:90.3992,address:"House 3, Road 1, Sector 3, Uttara, Dhaka 1230",phone:"8951100",hours:"24 Hours",always:true,rating:3.9,reviews:432,services:["Medicine","Surgery","Pediatrics","Gynecology","Emergency"],beds:120,emergency:true},
  {id:55,name:"Popular Hospital Uttara",type:"private",area:"uttara",lat:23.8706,lng:90.4025,address:"House 34, Road 7, Sector 7, Uttara, Dhaka 1230",phone:"01766660008",hours:"8 AM – 10 PM",always:false,rating:4.0,reviews:765,services:["Cardiology","Diagnostics","Pathology","Radiology","CT Scan"],beds:80,emergency:false},

  /* === FARMGATE (5) === */
  {id:56,name:"National Cancer Research Institute & Hospital",type:"govt",area:"farmgate",lat:23.7569,lng:90.3878,address:"Mohakhali, Dhaka 1212",phone:"8853056",hours:"24 Hours",always:true,rating:4.0,reviews:1560,services:["Oncology","Radiation Therapy","Chemotherapy","Surgical Oncology","Palliative Care"],beds:300,emergency:true},
  {id:57,name:"BNSB Eye Hospital Farmgate",type:"special",area:"farmgate",lat:23.7560,lng:90.3912,address:"Farmgate, Dhaka 1215",phone:"9135399",hours:"8 AM – 8 PM",always:false,rating:4.2,reviews:876,services:["Ophthalmology","Cataract","Glaucoma","Retina","Low Vision"],beds:100,emergency:false},
  {id:58,name:"Prime Hospital Farmgate",type:"private",area:"farmgate",lat:23.7546,lng:90.3918,address:"37/1 Tejgaon, Farmgate, Dhaka",phone:"9133445",hours:"24 Hours",always:true,rating:3.9,reviews:543,services:["Medicine","Surgery","Orthopedics","Emergency","ICU"],beds:100,emergency:true},
  {id:59,name:"Farmgate General Hospital",type:"private",area:"farmgate",lat:23.7573,lng:90.3930,address:"85 Kazi Nazrul Islam Avenue, Farmgate, Dhaka 1215",phone:"9135677",hours:"24 Hours",always:true,rating:3.8,reviews:432,services:["General Medicine","Surgery","Emergency","Gynecology","Pediatrics"],beds:80,emergency:true},
  {id:60,name:"Institute of Child & Mother Health (Dhaka)",type:"govt",area:"farmgate",lat:23.7602,lng:90.3867,address:"Sher-e-Bangla Nagar, Dhaka (Farmgate area)",phone:"01714000001",hours:"8 AM – 8 PM",always:false,rating:3.9,reviews:654,services:["Pediatrics","Neonatology","Obstetrics","Maternal Health"],beds:200,emergency:false},

  /* === KAWRAN BAZAR (2) === */
  {id:61,name:"Dhaka Community Hospital",type:"private",area:"kawran",lat:23.7502,lng:90.3945,address:"190/1 Tejgaon Industrial Area, Kawran Bazar, Dhaka 1215",phone:"9110768",hours:"24 Hours",always:true,rating:4.0,reviews:987,services:["Medicine","Surgery","Cardiology","Emergency","ICU","Dialysis"],beds:200,emergency:true,website:"dchbd.org"},
  {id:62,name:"Kawran Bazar Diagnostic & Hospital",type:"private",area:"kawran",lat:23.7523,lng:90.3972,address:"Kawran Bazar, Tejgaon, Dhaka 1215",phone:"9119991",hours:"8 AM – 10 PM",always:false,rating:3.8,reviews:543,services:["Diagnostics","Pathology","Ultrasound","CT Scan","Cardiology OPD"],beds:60,emergency:false},

  /* === MOTIJHEEL (4) === */
  {id:63,name:"Medical College for Women & Hospital",type:"private",area:"motijheel",lat:23.7325,lng:90.4152,address:"67/1 Purana Paltan, Motijheel, Dhaka",phone:"9341600",hours:"24 Hours",always:true,rating:4.1,reviews:876,services:["Gynecology","Obstetrics","Pediatrics","Surgery","Emergency","ICU"],beds:200,emergency:true},
  {id:64,name:"Binimoy Hospital Motijheel",type:"private",area:"motijheel",lat:23.7279,lng:90.4193,address:"67 Purana Paltan, Motijheel, Dhaka 1000",phone:"9554001",hours:"24 Hours",always:true,rating:3.8,reviews:654,services:["General Medicine","Surgery","Emergency","Orthopedics","ICU"],beds:150,emergency:true},
  {id:65,name:"Government Employees Hospital",type:"govt",area:"motijheel",lat:23.7340,lng:90.4213,address:"Secretariat Road, Motijheel, Dhaka 1000",phone:"9551024",hours:"8 AM – 8 PM",always:false,rating:3.7,reviews:876,services:["General Medicine","Surgery","Gynecology","Orthopedics"],beds:200,emergency:false},
  {id:66,name:"Dhaka National Medical College Hospital",type:"private",area:"motijheel",lat:23.7355,lng:90.4177,address:"31/32 Banagram, Lalbagh, Dhaka",phone:"7312440",hours:"24 Hours",always:true,rating:3.9,reviews:765,services:["Medicine","Surgery","Gynecology","Emergency","Pediatrics","ICU"],beds:250,emergency:true},

  /* === SAYEDABAD (3) === */
  {id:67,name:"Al-Helal Specialized Hospital",type:"private",area:"sayedabad",lat:23.7108,lng:90.4277,address:"Sayedabad, Dhaka 1214",phone:"7551340",hours:"24 Hours",always:true,rating:3.9,reviews:543,services:["General Medicine","Surgery","Emergency","Gynecology","ICU"],beds:150,emergency:true},
  {id:68,name:"Sayedabad General Hospital",type:"private",area:"sayedabad",lat:23.7083,lng:90.4298,address:"Sayedabad Bus Stand Road, Dhaka 1214",phone:"01711332211",hours:"24 Hours",always:true,rating:3.6,reviews:321,services:["Emergency","General Medicine","Surgery","Gynecology"],beds:80,emergency:true},
  {id:69,name:"South Dhaka Community Hospital",type:"private",area:"sayedabad",lat:23.7125,lng:90.4256,address:"Jurain, Sayedabad, Dhaka",phone:"01715887766",hours:"24 Hours",always:true,rating:3.7,reviews:287,services:["General Medicine","Surgery","Emergency","Pediatrics"],beds:80,emergency:true},

  /* === GULISTAN (4) === */
  {id:70,name:"Sadar Hospital Dhaka",type:"govt",area:"gulistan",lat:23.7239,lng:90.4098,address:"Azimpur, Lalbagh, Dhaka 1000",phone:"9665226",hours:"24 Hours",always:true,rating:3.5,reviews:1230,services:["Emergency","General Medicine","Surgery","Gynecology","Pediatrics"],beds:500,emergency:true},
  {id:71,name:"Central Police Hospital",type:"govt",area:"gulistan",lat:23.7269,lng:90.4124,address:"Rajarbagh, Dhaka 1000",phone:"9334880",hours:"24 Hours",always:true,rating:3.7,reviews:432,services:["General Medicine","Surgery","Emergency","Orthopedics"],beds:200,emergency:true},
  {id:72,name:"Gulistan Nursing Home & Hospital",type:"private",area:"gulistan",lat:23.7230,lng:90.4148,address:"Bangabandhu Avenue, Gulistan, Dhaka 1000",phone:"9550124",hours:"24 Hours",always:true,rating:3.6,reviews:345,services:["General Medicine","Surgery","Gynecology","Emergency"],beds:80,emergency:true},
  {id:73,name:"Popular Hospital Gulistan Branch",type:"private",area:"gulistan",lat:23.7255,lng:90.4169,address:"Nayapaltan, Gulistan, Dhaka 1000",phone:"01766660015",hours:"8 AM – 9 PM",always:false,rating:3.9,reviews:543,services:["Diagnostics","Pathology","CT Scan","Radiology","Medicine OPD"],beds:50,emergency:false}
];

/* ── STATE ─────────────────────────────────────────── */
const S={map:null,userLL:null,userMkr:null,route:null,mkrs:[],tf:'all',af:'all'};

/* ── UTILS ─────────────────────────────────────────── */
const ph=r=>r?r.split(/[\/,]/)[0].trim().replace(/\s+/g,''):'';
const tl=t=>t==='govt'?'Government':t==='private'?'Private':'Specialist';
function openNow(h){
  if(h.always)return true;
  try{
    const[a,b]=h.hours.split('–').map(s=>s.trim());
    const tm=s=>{const m=s.match(/(\d+)(?::(\d+))?\s*(AM|PM)/i);if(!m)return 0;let hr=+m[1];const mn=+(m[2]||0),mer=m[3].toUpperCase();if(mer==='PM'&&hr!==12)hr+=12;if(mer==='AM'&&hr===12)hr=0;return hr*60+mn;};
    const n=new Date(),c=n.getHours()*60+n.getMinutes();return c>=tm(a)&&c<tm(b);
  }catch{return false;}
}
function stars(r){
  let s='';for(let i=1;i<=5;i++){const f=i<=Math.floor(r)?'#f6ad55':i-r<1?'rgba(246,173,85,.4)':'none';const k=f==='none'?'#d1d5db':'#f6ad55';s+=`<svg width="11" height="11" viewBox="0 0 24 24" fill="${f}" stroke="${k}" stroke-width="1.5"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>`;}
  return s;
}
let _tt;
function toast(m){const el=document.getElementById('toast');el.textContent=m;el.classList.add('show');clearTimeout(_tt);_tt=setTimeout(()=>el.classList.remove('show'),3200);}

/* ── MAP ───────────────────────────────────────────── */
function initMap(){
  S.map=L.map('map',{center:[23.7780,90.3889],zoom:12,zoomControl:false});
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',{maxZoom:19,attribution:'© OpenStreetMap'}).addTo(S.map);
  L.control.zoom({position:'bottomright'}).addTo(S.map);
  DB.forEach(h=>mkr(h));
  updateStats();
  renderList(DB);
  setTimeout(()=>{const l=document.getElementById('loader');l.classList.add('fade');setTimeout(()=>l.style.display='none',520);},2200);
}

/* ── MARKERS ───────────────────────────────────────── */
function mkrColor(h){return h.type==='govt'?'#2563eb':h.type==='special'?'#dc2626':'#0a8f8f';}
function mkr(h){
  const c=mkrColor(h);
  const icon=L.divIcon({html:`<div style="width:32px;height:32px;background:${c};border-radius:50% 50% 50% 0;transform:rotate(-45deg);border:3px solid #fff;box-shadow:0 3px 10px rgba(0,0,0,.28);display:flex;align-items:center;justify-content:center"><svg style="transform:rotate(45deg)" width="14" height="14" viewBox="0 0 20 20" fill="none"><rect x="7" y="1" width="6" height="18" rx="2" fill="white"/><rect x="1" y="7" width="18" height="6" rx="2" fill="white"/></svg></div>`,className:'',iconSize:[32,32],iconAnchor:[16,32],popupAnchor:[0,-36]});
  const m=L.marker([h.lat,h.lng],{icon}).addTo(S.map);
  m.bindPopup(popup(h),{maxWidth:300});
  m.on('click',()=>hlCard(h.id));
  S.mkrs.push({id:h.id,m});
}

/* ── POPUP ─────────────────────────────────────────── */
function popup(h){
  const ob=h.always?`<span style="background:#dbeafe;color:#1d4ed8;padding:2px 7px;border-radius:8px;font-size:.64rem;font-weight:700">24H</span>`:openNow(h)?`<span style="background:#dcfce7;color:#166534;padding:2px 7px;border-radius:8px;font-size:.64rem;font-weight:700">OPEN</span>`:`<span style="background:#fee2e2;color:#b91c1c;padding:2px 7px;border-radius:8px;font-size:.64rem;font-weight:700">CLOSED</span>`;
  return`<div style="font-family:'DM Sans',sans-serif">
    <div style="background:linear-gradient(135deg,#055858,#0a8f8f);padding:12px 14px;border-radius:3px 3px 0 0;color:#fff">
      <div style="font-family:'Syne',sans-serif;font-size:.93rem;font-weight:800;line-height:1.3;margin-bottom:1px">${h.name}</div>
      <div style="font-size:.67rem;opacity:.85">${tl(h.type)} · ${h.area.charAt(0).toUpperCase()+h.area.slice(1)}</div>
    </div>
    <div style="padding:12px 14px">
      <div style="display:flex;align-items:center;gap:4px;margin-bottom:7px">${stars(h.rating)}<span style="font-weight:700;font-size:.79rem;margin-left:2px">${h.rating}</span><span style="font-size:.69rem;color:#6b7280">(${h.reviews.toLocaleString()})</span>&nbsp;${ob}</div>
      <div style="font-size:.74rem;color:#4b5563;margin-bottom:4px;display:flex;gap:4px"><svg width="11" height="11" viewBox="0 0 24 24" fill="none" stroke="#0a8f8f" stroke-width="2.5" style="flex-shrink:0;margin-top:2px"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg><span>${h.address}</span></div>
      <div style="font-size:.74rem;color:#4b5563;margin-bottom:4px;display:flex;gap:4px;align-items:center"><svg width="11" height="11" viewBox="0 0 24 24" fill="none" stroke="#0a8f8f" stroke-width="2.5"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12a19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 3.6 1.27h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L7.91 9a16 16 0 0 0 6 6l1.27-.79a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/></svg><span>${h.phone}</span></div>
      <div style="font-size:.74rem;color:#4b5563;margin-bottom:10px;display:flex;gap:4px;align-items:center"><svg width="11" height="11" viewBox="0 0 24 24" fill="none" stroke="#0a8f8f" stroke-width="2.5"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg><span>${h.hours}</span>&nbsp;<span style="background:${h.emergency?'#fee2e2':'#f3f4f6'};color:${h.emergency?'#b91c1c':'#6b7280'};padding:1px 6px;border-radius:6px;font-size:.61rem;font-weight:700">${h.emergency?'🚨ER':'No ER'}</span></div>
      <div style="display:flex;gap:6px">
        <button onclick="navigateTo(${h.id})" style="flex:1;padding:7px;background:#0a8f8f;color:#fff;border:none;border-radius:7px;font-size:.72rem;font-weight:700;cursor:pointer;font-family:'DM Sans',sans-serif;display:flex;align-items:center;justify-content:center;gap:4px"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polygon points="3 11 22 2 13 21 11 13 3 11"/></svg>Navigate</button>
        <a href="tel:${ph(h.phone)}" style="flex:1;padding:7px;background:#22c55e;color:#fff;border-radius:7px;font-size:.72rem;font-weight:700;font-family:'DM Sans',sans-serif;display:flex;align-items:center;justify-content:center;gap:4px"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12a19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 3.6 1.27h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L7.91 9a16 16 0 0 0 6 6l1.27-.79a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/></svg>Call</a>
        <button onclick="openModal(${h.id})" style="padding:7px 10px;background:#f1f5f9;border:none;border-radius:7px;font-size:.72rem;font-weight:700;cursor:pointer;color:#1a202c">⋯</button>
      </div>
    </div>
  </div>`;
}

/* ── LIST ──────────────────────────────────────────── */
function renderList(list){
  const el=document.getElementById('hlist'),lb=document.getElementById('rlbl');
  lb.textContent=`Showing ${list.length} of ${DB.length} hospitals`;
  el.innerHTML='';
  if(!list.length){el.innerHTML=`<div style="text-align:center;padding:34px 14px;color:#9ca3af"><svg width="36" height="36" viewBox="0 0 24 24" fill="none" stroke="#d1d5db" stroke-width="1.5" style="margin:0 auto 10px;display:block"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg><div style="font-weight:700;margin-bottom:3px">No hospitals found</div><div style="font-size:.77rem">Try different search or filter</div></div>`;return;}
  list.forEach(h=>{
    const d=document.createElement('div');d.className='hc';d.id=`c${h.id}`;d.onclick=()=>focusH(h);
    const sc=h.always?'o24':openNow(h)?'oo':'oc',st=h.always?'24H':openNow(h)?'Open':'Closed';
    const tc=h.type==='govt'?'tg':h.type==='private'?'tp':'ts';
    d.innerHTML=`<div class="ct"><div class="cn">${h.name}</div><div class="cb ${tc}">${tl(h.type)}</div></div>
    <div class="ca"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" style="flex-shrink:0;margin-top:2px"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>${h.address}</div>
    <div class="cm"><div class="stars">${stars(h.rating)}<span class="rn">${h.rating}</span><span style="font-size:.67rem;color:#9ca3af;margin-left:2px">(${h.reviews.toLocaleString()})</span></div><div class="ob ${sc}">${st}</div></div>
    <div class="cbs">
      <button class="cbtn bi" onclick="event.stopPropagation();openModal(${h.id})"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><circle cx="12" cy="12" r="3"/><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/></svg>Details</button>
      <button class="cbtn bn" onclick="event.stopPropagation();navigateTo(${h.id})"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polygon points="3 11 22 2 13 21 11 13 3 11"/></svg>Navigate</button>
      <a href="tel:${ph(h.phone)}" class="cbtn bc" onclick="event.stopPropagation()"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12a19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 3.6 1.27h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L7.91 9a16 16 0 0 0 6 6l1.27-.79a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/></svg>Call</a>
    </div>`;
    el.appendChild(d);
  });
}

/* ── STATS ─────────────────────────────────────────── */
function updateStats(){
  document.getElementById('sTot').textContent=DB.length;
  document.getElementById('sOpen').textContent=DB.filter(h=>openNow(h)).length;
  document.getElementById('sEmg').textContent=DB.filter(h=>h.emergency).length;
  document.getElementById('s24').textContent=DB.filter(h=>h.always).length;
}

/* ── FILTERS ───────────────────────────────────────── */
function setType(t,el){S.tf=t;document.querySelectorAll('.chip').forEach(c=>c.classList.remove('on'));el.classList.add('on');applyFilters();}
function setArea(a,el){S.af=a;document.querySelectorAll('.ac').forEach(c=>c.classList.remove('on'));el.classList.add('on');applyFilters();}
function applyFilters(){
  const q=document.getElementById('q').value.trim().toLowerCase(),t=S.tf,a=S.af;
  const list=DB.filter(h=>{
    const ms=!q||h.name.toLowerCase().includes(q)||h.address.toLowerCase().includes(q)||h.area.toLowerCase().includes(q)||h.services.some(s=>s.toLowerCase().includes(q));
    const mt=t==='all'||(t==='govt'&&h.type==='govt')||(t==='private'&&h.type==='private')||(t==='special'&&h.type==='special')||(t==='24h'&&h.always)||(t==='emg'&&h.emergency);
    const ma=a==='all'||h.area===a;
    return ms&&mt&&ma;
  });
  renderList(list);
}

/* ── FOCUS ─────────────────────────────────────────── */
function focusH(h){S.map.setView([h.lat,h.lng],16,{animate:true});const m=S.mkrs.find(x=>x.id===h.id);if(m)m.m.openPopup();hlCard(h.id);if(window.innerWidth<=768)document.getElementById('sb').classList.remove('open');}
function hlCard(id){document.querySelectorAll('.hc').forEach(c=>c.classList.remove('sel'));const c=document.getElementById(`c${id}`);if(c){c.classList.add('sel');c.scrollIntoView({behavior:'smooth',block:'nearest'});}}

/* ── GEOLOCATION ───────────────────────────────────── */
const UICON=L.divIcon({html:`<div style="width:16px;height:16px;background:#0a8f8f;border-radius:50%;border:3px solid #fff;box-shadow:0 0 0 5px rgba(10,143,143,.22)"></div>`,className:'',iconSize:[16,16],iconAnchor:[8,8]});
function locateUser(){
  if(!navigator.geolocation){toast('⚠️ Geolocation not supported');return;}
  toast('📍 Requesting location…');
  navigator.geolocation.getCurrentPosition(pos=>{
    S.userLL=L.latLng(pos.coords.latitude,pos.coords.longitude);
    if(S.userMkr)S.map.removeLayer(S.userMkr);
    S.userMkr=L.marker(S.userLL,{icon:UICON}).addTo(S.map);
    S.userMkr.bindPopup('<b>📍 You are here</b>').openPopup();
    S.map.setView(S.userLL,14,{animate:true});
    toast('✅ Location found! Tap Navigate on any hospital.');
  },e=>{toast('❌ '+(e.code===1?'Location access denied.':e.code===2?'Position unavailable.':'Request timed out.'));},{enableHighAccuracy:true,timeout:12000});
}

/* ── NAVIGATION ────────────────────────────────────── */
function navigateTo(id){
  const h=DB.find(x=>x.id===id);if(!h)return;
  if(!S.userLL){
    if(!navigator.geolocation){toast('⚠️ Geolocation not supported');return;}
    toast('📍 Getting your location first…');
    navigator.geolocation.getCurrentPosition(pos=>{S.userLL=L.latLng(pos.coords.latitude,pos.coords.longitude);if(S.userMkr)S.map.removeLayer(S.userMkr);S.userMkr=L.marker(S.userLL,{icon:UICON}).addTo(S.map);startRoute(h);},()=>toast('❌ Enable location to navigate.'),{enableHighAccuracy:true,timeout:12000});
    return;
  }
  startRoute(h);
}
function startRoute(h){
  if(S.route){S.map.removeControl(S.route);S.route=null;}
  S.route=L.Routing.control({
    waypoints:[S.userLL,L.latLng(h.lat,h.lng)],
    router:L.Routing.osrmv1({serviceUrl:'https://router.project-osrm.org/route/v1',profile:'driving'}),
    routeWhileDragging:false,showAlternatives:false,fitSelectedRoutes:true,collapsible:true,
    lineOptions:{styles:[{color:'#0a8f8f',weight:5,opacity:.9}]},createMarker:()=>null
  }).addTo(S.map);
  S.route.on('routesfound',e=>{
    const r=e.routes[0].summary;
    document.getElementById('navd').textContent=h.name;
    document.getElementById('navm').textContent=`${(r.totalDistance/1000).toFixed(1)} km · ~${Math.round(r.totalTime/60)} min`;
    document.getElementById('navp').classList.add('vis');
    toast(`🏥 Route to ${h.name}`);
  });
  S.route.on('routingerror',()=>{
    toast('⚠️ Route unavailable — showing straight-line direction.');
    stopNav();
    L.polyline([S.userLL,[h.lat,h.lng]],{color:'#0a8f8f',weight:3,opacity:.7,dashArray:'8,8'}).addTo(S.map);
    S.map.fitBounds([[S.userLL.lat,S.userLL.lng],[h.lat,h.lng]]);
  });
}
function stopNav(){if(S.route){S.map.removeControl(S.route);S.route=null;}document.getElementById('navp').classList.remove('vis');toast('Navigation stopped.');}

/* ── MODAL ─────────────────────────────────────────── */
function openModal(id){
  const h=DB.find(x=>x.id===id);if(!h)return;
  document.getElementById('mN').textContent=h.name;
  document.getElementById('mT').textContent=tl(h.type)+' Hospital';
  const sc=h.always?'o24':openNow(h)?'oo':'oc',st=h.always?'24H Open':openNow(h)?'Currently Open':'Currently Closed';
  document.getElementById('mB').innerHTML=`
    <div style="display:flex;align-items:center;gap:5px;margin-bottom:14px">${stars(h.rating)}<span style="font-weight:800;font-size:.96rem;margin-left:3px">${h.rating}</span><span style="font-size:.76rem;color:#6b7280">(${h.reviews.toLocaleString()} reviews)</span></div>
    <div class="dg">
      <div class="di"><div class="dl">📍 Area</div><div class="dv">${h.area.charAt(0).toUpperCase()+h.area.slice(1)}</div></div>
      <div class="di"><div class="dl">🏥 Type</div><div class="dv">${tl(h.type)}</div></div>
      <div class="di" style="grid-column:1/-1"><div class="dl">📌 Address</div><div class="dv" style="font-size:.8rem;font-weight:500">${h.address}</div></div>
      <div class="di"><div class="dl">📞 Phone</div><div class="dv" style="font-size:.81rem">${h.phone}</div></div>
      <div class="di"><div class="dl">🕐 Hours</div><div class="dv">${h.hours}</div></div>
      <div class="di"><div class="dl">🛏️ Beds</div><div class="dv">${h.beds.toLocaleString()}</div></div>
      <div class="di"><div class="dl">🚨 Emergency</div><div class="dv" style="color:${h.emergency?'#166534':'#b91c1c'}">${h.emergency?'✅ Available':'❌ Not Available'}</div></div>
      <div class="di"><div class="dl">📊 Status</div><div class="ob ${sc}" style="display:inline-block;margin-top:2px">${st}</div></div>
    </div>
    <div style="margin-bottom:15px"><div class="dl" style="margin-bottom:7px">🩺 Services</div><div class="svcs">${h.services.map(s=>`<span class="svc">${s}</span>`).join('')}</div></div>
    ${h.website?`<div style="margin-bottom:15px"><a href="https://${h.website}" target="_blank" rel="noopener" style="color:#0a8f8f;font-size:.81rem;font-weight:600">🌐 ${h.website}</a></div>`:''}
    <div class="mbtns">
      <button class="mbtn mb-n" onclick="closeModal();navigateTo(${h.id})"><svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polygon points="3 11 22 2 13 21 11 13 3 11"/></svg>Navigate</button>
      <a href="tel:${ph(h.phone)}" class="mbtn mb-c"><svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12a19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 3.6 1.27h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L7.91 9a16 16 0 0 0 6 6l1.27-.79a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/></svg>Call</a>
    </div>`;
  document.getElementById('mbg').classList.add('open');
}
function closeModal(){document.getElementById('mbg').classList.remove('open');}

/* ── BOOT — window.onload fires after ALL external scripts finish ── */
/* DOMContentLoaded fires too early (before CDN scripts resolve).   */
/* window.onload is the correct hook for CDN-dependent map apps.    */
window.onload=function(){
  _boot();
};
function _run(){
  initMap();
  if(navigator.geolocation){
    navigator.geolocation.getCurrentPosition(pos=>{
      S.userLL=L.latLng(pos.coords.latitude,pos.coords.longitude);
      S.userMkr=L.marker(S.userLL,{icon:UICON}).addTo(S.map);
      S.userMkr.bindPopup('<b>📍 You are here</b>');
      toast('📍 Location found. Tap Navigate on any hospital.');
    },()=>toast('ℹ️ Enable location for navigation.'),{enableHighAccuracy:true,timeout:10000});
  }
}
</script>
</body>
</html>
