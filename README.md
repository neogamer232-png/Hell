<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ConstitutionIQ — UPSC Polity</title>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,500;0,9..144,600;1,9..144,400&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;}
:root{
  --bg:#F4F1EC;
  --sidebar:#0E0B09;
  --sidebar-text:#6A6460;
  --accent:#D4320A;
  --accent-soft:#FDEEE9;
  --accent2:#FF6B3D;
  --card:#FFFFFF;
  --text:#171210;
  --text2:#7A746E;
  --text3:#B8B0A8;
  --border:#E6E0D8;
  --border-strong:#CFC7BC;
  --green:#1A6B42;
  --green-bg:#E6F4ED;
  --blue:#1A5FA0;
  --blue-bg:#E8F0FB;
  --amber:#9A6600;
  --amber-bg:#FDF3E0;
  --font:'DM Sans',sans-serif;
  --font-serif:'Fraunces',serif;
  --shadow:0 1px 3px rgba(0,0,0,.06),0 4px 16px rgba(0,0,0,.04);
  --shadow-lg:0 8px 32px rgba(0,0,0,.10);
  --radius:14px;
  --radius-sm:9px;
  --sidebar-w:230px;
  --ease:cubic-bezier(.4,0,.2,1);
}
[data-dark]{
  --bg:#0C0A08;
  --card:#181410;
  --text:#F0EBE4;
  --text2:#9A928A;
  --text3:#504840;
  --border:#262018;
  --border-strong:#362E24;
  --green-bg:#0A1E12;
  --blue-bg:#08101E;
  --amber-bg:#1A1205;
  --accent-soft:#2A1008;
}

/* ─── SCROLLBAR ─── */
::-webkit-scrollbar{width:4px;height:4px;}
::-webkit-scrollbar-thumb{background:var(--border-strong);border-radius:4px;}
::-webkit-scrollbar-track{background:transparent;}

body{
  font-family:var(--font);
  background:var(--bg);
  color:var(--text);
  display:flex;
  min-height:100vh;
  transition:background .35s var(--ease),color .35s var(--ease);
  font-size:14px;
  line-height:1.5;
}

/* ─── SIDEBAR ─── */
.sidebar{
  width:var(--sidebar-w);
  min-height:100vh;
  background:var(--sidebar);
  display:flex;
  flex-direction:column;
  position:fixed;
  left:0;top:0;bottom:0;
  z-index:100;
  transition:transform .3s var(--ease);
}
.sidebar.hidden{transform:translateX(-100%);}

.sidebar-logo{
  padding:22px 18px 18px;
  display:flex;align-items:center;gap:10px;
  border-bottom:1px solid #1E1A16;
}
.logo-mark{
  width:32px;height:32px;
  background:var(--accent);
  border-radius:10px;
  display:flex;align-items:center;justify-content:center;
  flex-shrink:0;
}
.logo-mark svg{width:17px;height:17px;fill:none;stroke:#fff;stroke-width:2.2;}
.logo-text{font-family:var(--font-serif);font-size:15px;font-weight:500;color:#fff;letter-spacing:-.2px;line-height:1.2;}
.logo-text small{display:block;font-family:var(--font);font-size:9.5px;font-weight:400;color:#5A5450;letter-spacing:.6px;text-transform:uppercase;margin-top:1px;}

.nav-group{padding:18px 10px 6px;}
.nav-group-label{font-size:9.5px;font-weight:600;color:#3A3430;letter-spacing:1.4px;text-transform:uppercase;padding:0 8px;margin-bottom:4px;}

.nav-item{
  display:flex;align-items:center;gap:10px;
  padding:8px 12px;
  border-radius:9px;
  cursor:pointer;color:var(--sidebar-text);
  font-size:13px;font-weight:500;
  transition:all .15s;
  text-decoration:none;
  margin-bottom:1px;
  position:relative;
}
.nav-item svg{width:16px;height:16px;flex-shrink:0;opacity:.6;transition:opacity .15s;}
.nav-item:hover{background:#1A1510;color:#C0B8B0;}
.nav-item:hover svg{opacity:.8;}
.nav-item.active{background:#1E1A14;color:#fff;}
.nav-item.active svg{opacity:1;}
.nav-item.active::before{
  content:'';position:absolute;left:0;top:50%;transform:translateY(-50%);
  width:3px;height:18px;background:var(--accent);border-radius:0 3px 3px 0;
}
.nav-badge{
  margin-left:auto;
  background:var(--accent);color:#fff;
  font-size:9px;font-weight:700;
  padding:2px 6px;border-radius:20px;
  letter-spacing:.3px;
}

.sidebar-footer{margin-top:auto;border-top:1px solid #1E1A16;padding:10px;}

/* ─── TOGGLE BUTTON ─── */
.sidebar-toggle{
  position:fixed;
  left:calc(var(--sidebar-w) + 12px);
  top:18px;
  z-index:200;
  background:var(--card);
  border:1px solid var(--border);
  border-radius:9px;
  width:30px;height:30px;
  cursor:pointer;
  display:flex;align-items:center;justify-content:center;
  transition:left .3s var(--ease),background .2s;
  box-shadow:var(--shadow);
}
.sidebar-toggle:hover{background:var(--bg);}
.sidebar-toggle.floated{left:12px;}
.sidebar-toggle svg{transition:transform .3s var(--ease);}
.sidebar-toggle.floated svg{transform:rotate(180deg);}

/* ─── MAIN ─── */
.main{
  margin-left:var(--sidebar-w);
  flex:1;
  padding:28px 36px 60px;
  transition:margin .3s var(--ease);
  min-height:100vh;
  max-width:1280px;
}
.main.expanded{margin-left:0;}

/* ─── TOPBAR ─── */
.topbar{
  display:flex;align-items:center;justify-content:space-between;
  margin-bottom:32px;
}
.breadcrumb{
  display:flex;align-items:center;gap:8px;
  font-size:13px;color:var(--text2);
}
.bc-home{
  width:30px;height:30px;
  background:var(--card);
  border:1px solid var(--border);
  border-radius:9px;
  display:flex;align-items:center;justify-content:center;
  cursor:pointer;
  transition:border-color .15s;
}
.bc-home:hover{border-color:var(--border-strong);}
.bc-sep{color:var(--text3);}
.bc-current{font-weight:600;color:var(--text);}

.topbar-right{display:flex;align-items:center;gap:8px;}
.upsc-pill{
  display:flex;align-items:center;gap:7px;
  background:var(--card);
  border:1px solid var(--border);
  border-radius:20px;
  padding:6px 14px 6px 10px;
  font-size:12px;font-weight:600;
  color:var(--text);
  cursor:default;
  box-shadow:var(--shadow);
}
.live-dot{
  width:7px;height:7px;
  border-radius:50%;background:var(--accent);
  animation:blink 1.8s ease-in-out infinite;
}
@keyframes blink{0%,100%{opacity:1;}50%{opacity:.25;}}

.icon-btn{
  width:34px;height:34px;
  background:var(--card);
  border:1px solid var(--border);
  border-radius:9px;
  cursor:pointer;
  display:flex;align-items:center;justify-content:center;
  transition:border-color .15s,background .15s;
  box-shadow:var(--shadow);
}
.icon-btn:hover{background:var(--bg);border-color:var(--border-strong);}
.avatar{
  width:34px;height:34px;
  border-radius:50%;
  background:linear-gradient(135deg,var(--accent),#FF8C5A);
  display:flex;align-items:center;justify-content:center;
  font-size:12px;font-weight:700;color:#fff;
  cursor:pointer;flex-shrink:0;
}

/* ─── GREETING ─── */
.greeting{
  font-family:var(--font-serif);
  font-size:38px;
  font-weight:500;
  letter-spacing:-.5px;
  line-height:1.1;
  margin-bottom:28px;
  color:var(--text);
}
.greeting em{color:var(--accent);font-style:italic;}

/* ─── GRID SYSTEMS ─── */
.g2{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:16px;}
.g4{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-bottom:16px;}
.g2b{display:grid;grid-template-columns:5fr 4fr;gap:16px;margin-bottom:32px;}

/* ─── BASE CARD ─── */
.card{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:var(--radius);
  padding:22px 24px;
  box-shadow:var(--shadow);
  transition:border-color .2s,box-shadow .2s;
}
.card:hover{border-color:var(--border-strong);}
.card-label{
  display:flex;align-items:center;gap:7px;
  font-size:11px;font-weight:600;color:var(--text2);
  text-transform:uppercase;letter-spacing:.7px;
  margin-bottom:16px;
}

/* ─── FOCUS CARD ─── */
.focus-card{
  background:linear-gradient(145deg,#0E0B09 0%,#1E1510 100%);
  border:1px solid #2A2018;
  color:#F0EBE4;
  position:relative;
  overflow:hidden;
}
.focus-card::after{
  content:'';
  position:absolute;
  top:-40px;right:-40px;
  width:160px;height:160px;
  background:radial-gradient(circle,rgba(212,50,10,.25) 0%,transparent 70%);
  pointer-events:none;
}
.focus-card .card-label{color:#5A5450;}
.focus-meta{display:flex;align-items:center;gap:10px;margin-bottom:4px;}
.focus-pct{
  font-size:13px;font-weight:700;
  color:#fff;
  background:rgba(212,50,10,.2);
  border:1px solid rgba(212,50,10,.4);
  border-radius:7px;padding:3px 9px;
}
.focus-count{
  background:rgba(26,107,66,.25);
  color:#5AD89C;
  font-size:11px;font-weight:700;
  padding:3px 8px;border-radius:6px;
  border:1px solid rgba(26,107,66,.35);
}
.focus-title{
  font-family:var(--font-serif);
  font-size:22px;font-weight:500;
  color:#F0EBE4;
  margin:12px 0 6px;
  line-height:1.3;
}
.focus-sub{font-size:13px;color:#7A7068;line-height:1.6;margin-bottom:18px;}

/* ─── WAVEFORM ─── */
.waveform{display:flex;align-items:center;gap:2px;height:24px;}
.waveform span{display:block;width:3px;border-radius:2px;animation:wavepulse 1.2s ease-in-out infinite;}
@keyframes wavepulse{0%,100%{transform:scaleY(1);}50%{transform:scaleY(.5);}}

/* ─── PROGRESS CARD ─── */
.pstat-row{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-top:4px;}
.pstat{
  background:var(--bg);
  border:1px solid var(--border);
  border-radius:11px;padding:14px 16px;
  text-align:center;
  transition:background .3s,border .3s;
}
.pstat-label{font-size:10.5px;color:var(--text3);margin-bottom:8px;font-weight:500;text-transform:uppercase;letter-spacing:.5px;}
.pstat-num{font-size:26px;font-weight:700;color:var(--text);line-height:1;}
.pstat-num.g{color:var(--green);}
.pstat-num.a{color:var(--amber);}

/* ─── MINI STATS ─── */
.mini-card{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:12px;
  padding:16px 18px;
  box-shadow:var(--shadow);
  transition:border-color .2s,transform .2s;
}
.mini-card:hover{border-color:var(--border-strong);transform:translateY(-1px);}
.mini-label{display:flex;align-items:center;gap:6px;font-size:10.5px;font-weight:600;color:var(--text2);margin-bottom:10px;text-transform:uppercase;letter-spacing:.6px;}
.mini-label svg{width:14px;height:14px;flex-shrink:0;}
.mini-val{font-size:24px;font-weight:700;color:var(--text);line-height:1.1;}
.mini-sub{font-size:11px;color:var(--text3);margin-top:4px;}

/* ─── ACTION LIST ─── */
.action-list{display:flex;flex-direction:column;gap:8px;}
.action-row{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:var(--radius-sm);
  padding:14px 18px;
  display:flex;align-items:center;justify-content:space-between;
  cursor:pointer;
  transition:border-color .15s,transform .15s,box-shadow .15s;
  box-shadow:var(--shadow);
}
.action-row:hover{border-color:var(--border-strong);transform:translateX(2px);box-shadow:var(--shadow-lg);}
.action-info{}
.action-title{font-size:14px;font-weight:600;color:var(--text);margin-bottom:2px;}
.action-sub{font-size:11.5px;color:var(--text2);}
.action-arrow{
  width:34px;height:34px;
  background:var(--sidebar);
  border-radius:9px;
  display:flex;align-items:center;justify-content:center;
  color:#fff;font-size:16px;flex-shrink:0;
  transition:background .15s;
}
.action-row:hover .action-arrow{background:var(--accent);}

/* ─── CTA CARD ─── */
.cta-card{
  background:linear-gradient(145deg,var(--accent) 0%,#FF7444 100%);
  border:none;
  border-radius:var(--radius);
  padding:28px 24px;
  display:flex;flex-direction:column;
  justify-content:space-between;
  min-height:220px;
  position:relative;overflow:hidden;
  box-shadow:0 6px 24px rgba(212,50,10,.3);
}
.cta-card::before{
  content:'';
  position:absolute;bottom:-30px;right:-30px;
  width:140px;height:140px;
  background:rgba(255,255,255,.08);
  border-radius:50%;
}
.cta-card::after{
  content:'';
  position:absolute;top:-20px;right:60px;
  width:80px;height:80px;
  background:rgba(255,255,255,.06);
  border-radius:50%;
}
.cta-title{font-family:var(--font-serif);font-size:22px;font-weight:500;color:#fff;line-height:1.3;margin-bottom:8px;}
.cta-sub{font-size:12.5px;color:rgba(255,255,255,.75);line-height:1.6;}
.btn-ghost{
  background:rgba(255,255,255,.15);
  backdrop-filter:blur(8px);
  border:1px solid rgba(255,255,255,.3);
  color:#fff;
  border-radius:10px;
  padding:10px 20px;
  font-family:var(--font);font-size:13px;font-weight:600;
  cursor:pointer;
  width:fit-content;
  transition:background .15s;
  margin-top:16px;
}
.btn-ghost:hover{background:rgba(255,255,255,.25);}
.btn-primary{
  background:var(--accent);color:#fff;
  border:none;border-radius:10px;
  padding:11px 22px;
  font-family:var(--font);font-size:13px;font-weight:600;
  cursor:pointer;
  transition:background .15s,transform .15s;
  box-shadow:0 2px 8px rgba(212,50,10,.35);
}
.btn-primary:hover{background:#BA2A08;transform:translateY(-1px);}

/* ─── SECTION HEADER ─── */
.section-head{
  display:flex;align-items:center;justify-content:space-between;
  margin:36px 0 18px;
}
.section-title{
  font-family:var(--font-serif);
  font-size:26px;font-weight:500;
  color:var(--text);
  display:flex;align-items:center;gap:10px;
}
.section-badge{
  font-family:var(--font);
  font-size:10px;font-weight:700;
  background:var(--accent);color:#fff;
  padding:3px 9px;border-radius:20px;
  letter-spacing:.4px;
}

/* ─── FILTERS ─── */
.filters{display:flex;gap:6px;flex-wrap:wrap;}
.chip{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:20px;
  padding:6px 14px;
  font-size:12px;font-weight:500;
  cursor:pointer;color:var(--text2);
  transition:all .15s;
  white-space:nowrap;
}
.chip:hover{border-color:var(--border-strong);color:var(--text);}
.chip.active{background:var(--sidebar);color:#fff;border-color:var(--sidebar);}

/* ─── STATS STRIP ─── */
.stats-strip{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:20px;}
.stat-pill{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:9px;
  padding:7px 14px;
  font-size:12px;font-weight:600;
  display:flex;align-items:center;gap:7px;
  color:var(--text);
  box-shadow:var(--shadow);
  transition:border-color .15s;
}
.stat-pill:hover{border-color:var(--border-strong);}
.sdot{width:7px;height:7px;border-radius:50%;flex-shrink:0;}

/* ─── SEARCH ─── */
.search-wrap{position:relative;margin-bottom:16px;}
.search-wrap input{
  width:100%;height:42px;
  border:1px solid var(--border);
  border-radius:11px;
  padding:0 16px 0 40px;
  font-family:var(--font);font-size:13.5px;
  background:var(--card);color:var(--text);
  outline:none;
  transition:border-color .2s,box-shadow .2s;
  box-shadow:var(--shadow);
}
.search-wrap input:focus{border-color:var(--accent);box-shadow:0 0 0 3px rgba(212,50,10,.08);}
.search-wrap input::placeholder{color:var(--text3);}
.search-icon{position:absolute;left:13px;top:50%;transform:translateY(-50%);opacity:.35;pointer-events:none;}

/* ─── PART BLOCK ─── */
.part-block{margin-bottom:30px;}
.part-label{
  display:flex;align-items:center;gap:8px;
  font-size:10.5px;font-weight:700;
  color:var(--text3);
  text-transform:uppercase;letter-spacing:1.2px;
  margin-bottom:10px;
}
.part-label::after{content:'';flex:1;height:1px;background:var(--border);}
.part-tag{
  background:var(--sidebar);color:#fff;
  font-size:9.5px;font-weight:700;
  padding:2px 9px;border-radius:20px;
  letter-spacing:.3px;flex-shrink:0;
}

/* ─── ARTICLE CARDS ─── */
.articles-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(268px,1fr));
  gap:10px;
}
.art-card{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:12px;
  padding:15px 16px;
  cursor:pointer;
  transition:border-color .2s,box-shadow .2s,transform .2s;
  position:relative;
  overflow:hidden;
}
.art-card::before{
  content:'';
  position:absolute;left:0;top:0;bottom:0;
  width:3px;border-radius:0 3px 3px 0;
  background:transparent;
  transition:background .2s;
}
.art-card:hover{
  border-color:var(--border-strong);
  box-shadow:var(--shadow-lg);
  transform:translateY(-2px);
}
.art-card:hover::before{background:var(--accent);}
.art-card.mem::before{background:var(--green);}
.art-card.bk::before{background:#D4A800;}

.art-num{
  font-size:9.5px;font-weight:700;
  color:var(--accent);letter-spacing:.8px;
  text-transform:uppercase;
  margin-bottom:5px;
}
.art-title{
  font-size:13.5px;font-weight:600;
  color:var(--text);
  line-height:1.35;margin-bottom:7px;
}
.art-desc{
  font-size:11.5px;color:var(--text2);
  line-height:1.6;
  display:-webkit-box;
  -webkit-line-clamp:2;
  -webkit-box-orient:vertical;
  overflow:hidden;
  margin-bottom:10px;
}
.art-tags{display:flex;gap:4px;flex-wrap:wrap;margin-bottom:10px;}
.a-tag{
  font-size:9.5px;padding:2px 7px;
  border-radius:20px;
  background:var(--bg);
  color:var(--text3);font-weight:500;
  border:1px solid var(--border);
}
.a-tag.imp{background:var(--accent-soft);color:var(--accent);border-color:#F4C0B0;}
.art-btns{display:flex;gap:5px;}
.a-btn{
  font-size:10.5px;padding:4px 9px;
  border-radius:7px;border:1px solid var(--border);
  cursor:pointer;background:transparent;
  color:var(--text2);font-family:var(--font);font-weight:500;
  transition:all .15s;
}
.a-btn:hover{background:var(--bg);border-color:var(--border-strong);}
.a-btn.mem-on{background:var(--green-bg);color:var(--green);border-color:#A8D8BC;}
.a-btn.bk-on{background:var(--amber-bg);color:var(--amber);border-color:#F0CC70;}

/* ─── MODAL ─── */
.overlay{
  position:fixed;inset:0;
  background:rgba(0,0,0,.45);
  backdrop-filter:blur(4px);
  z-index:500;
  display:flex;align-items:center;justify-content:center;
  opacity:0;pointer-events:none;
  transition:opacity .25s var(--ease);
}
.overlay.open{opacity:1;pointer-events:auto;}
.modal{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:20px;
  padding:30px 32px;
  max-width:520px;width:90%;
  max-height:82vh;overflow-y:auto;
  position:relative;
  transform:translateY(16px) scale(.98);
  transition:transform .25s var(--ease);
  box-shadow:var(--shadow-lg);
}
.overlay.open .modal{transform:translateY(0) scale(1);}
.modal-artnum{
  font-size:11px;font-weight:700;
  color:var(--accent);letter-spacing:.8px;
  text-transform:uppercase;margin-bottom:4px;
}
.modal-title{
  font-family:var(--font-serif);
  font-size:22px;font-weight:500;
  color:var(--text);margin-bottom:14px;line-height:1.3;
}
.modal-desc{font-size:14px;color:var(--text2);line-height:1.75;margin-bottom:18px;}
.modal-close{
  position:absolute;top:18px;right:18px;
  background:var(--bg);border:1px solid var(--border);
  border-radius:8px;width:30px;height:30px;
  cursor:pointer;font-size:16px;color:var(--text2);
  display:flex;align-items:center;justify-content:center;
  transition:background .15s;
}
.modal-close:hover{background:var(--border);}
.modal-btns{display:flex;gap:8px;flex-wrap:wrap;margin-top:6px;}

/* ─── EXAMS PAGE ─── */
.exam-coming{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:var(--radius);
  padding:48px 32px;
  text-align:center;
  color:var(--text2);
  font-size:14px;
  box-shadow:var(--shadow);
}
.exam-coming-icon{font-size:40px;margin-bottom:12px;}

/* ─── RESPONSIVE ─── */
@media(max-width:960px){
  .sidebar{transform:translateX(-100%);}
  .sidebar.visible{transform:none;}
  .main{margin-left:0;padding:22px 20px 60px;}
  .g2,.g4,.g2b{grid-template-columns:1fr;}
  .pstat-row{grid-template-columns:1fr 1fr 1fr;}
  .sidebar-toggle{left:12px;}
  .sidebar-toggle.floated{left:calc(var(--sidebar-w) + 12px);}
}
@media(max-width:540px){
  .greeting{font-size:28px;}
  .pstat-row{grid-template-columns:1fr 1fr;}
  .articles-grid{grid-template-columns:1fr;}
}

/* ─── TRANSITIONS ─── */
.page{animation:pagein .25s var(--ease);}
@keyframes pagein{from{opacity:0;transform:translateY(8px);}to{opacity:1;transform:none;}}

/* ─── EMPTY ─── */
.empty-state{
  text-align:center;padding:60px 32px;
  color:var(--text2);font-size:14px;
}
.empty-state svg{opacity:.2;margin-bottom:14px;}
</style>
</head>
<body>

<!-- SIDEBAR -->
<aside class="sidebar" id="sidebar">
  <div class="sidebar-logo">
    <div class="logo-mark">
      <svg viewBox="0 0 24 24"><path d="M12 3L3 8.5v7L12 21l9-5.5v-7z"/><path d="M12 3v18M3 8.5l9 5.5 9-5.5"/></svg>
    </div>
    <div class="logo-text">ConstitutionIQ<small>UPSC Polity</small></div>
  </div>

  <div class="nav-group">
    <div class="nav-group-label">Main</div>
    <a class="nav-item active" id="nav-dashboard" onclick="showPage('dashboard')">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7" rx="1.5"/><rect x="14" y="3" width="7" height="7" rx="1.5"/><rect x="3" y="14" width="7" height="7" rx="1.5"/><rect x="14" y="14" width="7" height="7" rx="1.5"/></svg>
      Dashboard
    </a>
    <a class="nav-item" id="nav-polity" onclick="showPage('polity')">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M12 3L3 9v12h6v-6h6v6h6V9z"/></svg>
      Polity
      <span class="nav-badge">NEW</span>
    </a>
    <a class="nav-item" id="nav-exams" onclick="showPage('exams')">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M9 11l3 3L22 4"/><path d="M21 12v7a2 2 0 01-2 2H5a2 2 0 01-2-2V5a2 2 0 012-2h11"/></svg>
      Exams
    </a>
    <a class="nav-item">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>
      Practice Mode
    </a>
    <a class="nav-item">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M4 19.5A2.5 2.5 0 016.5 17H20"/><path d="M6.5 2H20v20H6.5A2.5 2.5 0 014 19.5v-15A2.5 2.5 0 016.5 2z"/></svg>
      Textbooks
    </a>
    <a class="nav-item">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 00-4-4H5a4 4 0 00-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 00-3-3.87M16 3.13a4 4 0 010 7.75"/></svg>
      All Courses
    </a>
  </div>

  <div class="nav-group">
    <div class="nav-group-label">Settings</div>
    <a class="nav-item" onclick="toggleDark()">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M21 12.79A9 9 0 1111.21 3 7 7 0 0021 12.79z"/></svg>
      <span id="dark-label">Dark Mode</span>
    </a>
    <a class="nav-item">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 00.33 1.82l.06.06a2 2 0 010 2.83 2 2 0 01-2.83 0l-.06-.06a1.65 1.65 0 00-1.82-.33 1.65 1.65 0 00-1 1.51V21a2 2 0 01-2 2 2 2 0 01-2-2v-.09A1.65 1.65 0 009 19.4a1.65 1.65 0 00-1.82.33l-.06.06a2 2 0 01-2.83 0 2 2 0 010-2.83l.06-.06A1.65 1.65 0 004.68 15a1.65 1.65 0 00-1.51-1H3a2 2 0 01-2-2 2 2 0 012-2h.09A1.65 1.65 0 004.6 9a1.65 1.65 0 00-.33-1.82l-.06-.06a2 2 0 010-2.83 2 2 0 012.83 0l.06.06A1.65 1.65 0 009 4.68a1.65 1.65 0 001-1.51V3a2 2 0 012-2 2 2 0 012 2v.09a1.65 1.65 0 001 1.51 1.65 1.65 0 001.82-.33l.06-.06a2 2 0 012.83 0 2 2 0 010 2.83l-.06.06A1.65 1.65 0 0019.4 9a1.65 1.65 0 001.51 1H21a2 2 0 012 2 2 2 0 01-2 2h-.09a1.65 1.65 0 00-1.51 1z"/></svg>
      Preferences
    </a>
  </div>

  <div class="sidebar-footer">
    <a class="nav-item" onclick="toggleSidebar()">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M11 19l-7-7 7-7M4 12h16"/></svg>
      Collapse
    </a>
  </div>
</aside>

<!-- TOGGLE -->
<button class="sidebar-toggle" id="sb-toggle" onclick="toggleSidebar()" title="Toggle sidebar">
  <svg width="13" height="13" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path d="M9 18l6-6-6-6"/></svg>
</button>

<!-- MAIN -->
<main class="main" id="main">
  <!-- TOPBAR -->
  <div class="topbar">
    <div class="breadcrumb">
      <div class="bc-home" onclick="showPage('dashboard')" title="Home">
        <svg width="13" height="13" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/></svg>
      </div>
      <span class="bc-sep">›</span>
      <span class="bc-current" id="bc-text">Dashboard</span>
    </div>
    <div class="topbar-right">
      <div class="upsc-pill">
        <span class="live-dot"></span>
        UPSC Mode
        <svg width="13" height="13" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>
      </div>
      <button class="icon-btn" onclick="toggleDark()" title="Toggle theme">
        <svg width="15" height="15" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M21 12.79A9 9 0 1111.21 3 7 7 0 0021 12.79z"/></svg>
      </button>
      <div class="avatar">N</div>
    </div>
  </div>

  <!-- ══════════════ DASHBOARD ══════════════ -->
  <div id="page-dashboard" class="page">
    <div class="greeting">Good morning, <em>Aspirant!</em></div>

    <div class="g2">
      <!-- FOCUS CARD -->
      <div class="card focus-card">
        <div class="card-label">
          <svg width="13" height="13" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg>
          Today's Focus
        </div>
        <div class="focus-meta">
          <span class="focus-pct">56% complete</span>
          <span class="focus-count">41 done</span>
          <div class="waveform" style="margin-left:4px;">
            <span style="height:8px;background:#1A6B42;animation-delay:0s;"></span>
            <span style="height:16px;background:#1A6B42;animation-delay:.1s;"></span>
            <span style="height:22px;background:#1A6B42;animation-delay:.2s;"></span>
            <span style="height:12px;background:#1A6B42;animation-delay:.3s;"></span>
            <span style="height:18px;background:#1A6B42;animation-delay:.4s;"></span>
            <span style="height:8px;background:#444038;animation-delay:.1s;"></span>
            <span style="height:14px;background:#444038;animation-delay:.2s;"></span>
            <span style="height:20px;background:#444038;animation-delay:.3s;"></span>
            <span style="height:10px;background:#444038;animation-delay:.4s;"></span>
          </div>
        </div>
        <div class="focus-title">Fundamental Rights & DPSP</div>
        <div class="focus-sub">Solve 10 questions on Articles 12–51. Focus on the FR–DPSP relationship — a recurring Prelims theme.</div>
        <button class="btn-primary" onclick="showPage('polity')">Practice Now →</button>
      </div>

      <!-- PROGRESS CARD -->
      <div class="card">
        <div class="card-label">
          <svg width="13" height="13" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
          Today's Progress
        </div>
        <div class="pstat-row">
          <div class="pstat">
            <div class="pstat-label">Attempted</div>
            <div class="pstat-num">50</div>
          </div>
          <div class="pstat">
            <div class="pstat-label">Correct</div>
            <div class="pstat-num g">40</div>
          </div>
          <div class="pstat">
            <div class="pstat-label">Accuracy</div>
            <div class="pstat-num a">80%</div>
          </div>
        </div>
      </div>
    </div>

    <!-- MINI STATS -->
    <div class="g4">
      <div class="mini-card">
        <div class="mini-label">
          <svg fill="none" stroke="var(--accent)" stroke-width="2" viewBox="0 0 24 24"><rect x="3" y="4" width="18" height="18" rx="2"/><path d="M16 2v4M8 2v4M3 10h18"/></svg>
          Daily Activity
        </div>
        <div class="mini-val">8</div>
        <div class="mini-sub">Articles reviewed today</div>
      </div>
      <div class="mini-card">
        <div class="mini-label">
          <svg fill="none" stroke="var(--accent)" stroke-width="2" viewBox="0 0 24 24"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"/><polyline points="17 6 23 6 23 12"/></svg>
          7-Day Accuracy
        </div>
        <div class="mini-val">72%</div>
        <div class="mini-sub">Up 4% this week</div>
      </div>
      <div class="mini-card">
        <div class="mini-label">
          <svg fill="none" stroke="var(--accent)" stroke-width="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>
          Prelims Countdown
        </div>
        <div class="mini-val" id="countdown-val">—</div>
        <div class="mini-sub">Days until UPSC Prelims</div>
      </div>
      <div class="mini-card">
        <div class="mini-label">
          <svg fill="none" stroke="var(--accent)" stroke-width="2" viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
          Streak
        </div>
        <div class="mini-val">6 🔥</div>
        <div class="mini-sub">Days in a row</div>
      </div>
    </div>

    <!-- BOTTOM ROW -->
    <div class="g2b">
      <div class="action-list">
        <div class="action-row" onclick="showPage('polity')">
          <div class="action-info">
            <div class="action-title">Articles Quick Revision</div>
            <div class="action-sub">Browse all 395+ constitutional articles</div>
          </div>
          <div class="action-arrow">›</div>
        </div>
        <div class="action-row">
          <div class="action-info">
            <div class="action-title">Mock Test — Polity</div>
            <div class="action-sub">25 MCQs · UPSC Prelims pattern</div>
          </div>
          <div class="action-arrow">›</div>
        </div>
        <div class="action-row">
          <div class="action-info">
            <div class="action-title">Schedules & Amendments</div>
            <div class="action-sub">12 Schedules · Key Amendments explained</div>
          </div>
          <div class="action-arrow">›</div>
        </div>
        <div class="action-row">
          <div class="action-info">
            <div class="action-title">Previous Year Questions</div>
            <div class="action-sub">Polity PYQs from 2013–2024</div>
          </div>
          <div class="action-arrow">›</div>
        </div>
      </div>

      <div class="cta-card">
        <div>
          <div class="cta-title">Adaptive Practice Mode</div>
          <div class="cta-sub">Test yourself on the most-asked constitutional articles. Difficulty adjusts based on your performance history.</div>
        </div>
        <button class="btn-ghost" onclick="showPage('polity')">Start Practice →</button>
      </div>
    </div>
  </div>

  <!-- ══════════════ POLITY ══════════════ -->
  <div id="page-polity" style="display:none;">
    <div class="greeting" style="font-size:30px;margin-bottom:6px;">Indian <em>Constitution</em></div>
    <p style="font-size:13.5px;color:var(--text2);margin-bottom:22px;">All Articles · Organised by Parts · Interactive Study Tool</p>

    <div class="stats-strip">
      <div class="stat-pill"><span class="sdot" style="background:var(--accent);"></span><span id="s-total">448 Articles</span></div>
      <div class="stat-pill"><span class="sdot" style="background:var(--green);"></span><span id="s-mem">0 Memorised</span></div>
      <div class="stat-pill"><span class="sdot" style="background:#D4A800;"></span><span id="s-bk">0 Bookmarked</span></div>
      <div class="stat-pill"><span class="sdot" style="background:var(--blue);"></span>22 Parts</div>
      <div class="stat-pill"><span class="sdot" style="background:#8B5CF6;"></span>12 Schedules</div>
    </div>

    <div class="search-wrap">
      <svg class="search-icon" width="15" height="15" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg>
      <input type="text" id="polity-search" placeholder="Search by Article number, keyword, or Part name…" oninput="renderPolity()">
    </div>

    <div class="filters" id="polity-filters" style="margin-bottom:22px;">
      <button class="chip active" data-f="all" onclick="setFilter(this,'all')">All</button>
      <button class="chip" data-f="imp" onclick="setFilter(this,'imp')">⭐ Important</button>
      <button class="chip" data-f="FR" onclick="setFilter(this,'FR')">Fundamental Rights</button>
      <button class="chip" data-f="DPSP" onclick="setFilter(this,'DPSP')">DPSP</button>
      <button class="chip" data-f="FD" onclick="setFilter(this,'FD')">Fundamental Duties</button>
      <button class="chip" data-f="Parliament" onclick="setFilter(this,'Parliament')">Parliament</button>
      <button class="chip" data-f="President" onclick="setFilter(this,'President')">President</button>
      <button class="chip" data-f="judiciary" onclick="setFilter(this,'judiciary')">Judiciary</button>
      <button class="chip" data-f="Emergency" onclick="setFilter(this,'Emergency')">Emergency</button>
      <button class="chip" data-f="Election" onclick="setFilter(this,'Election')">Elections</button>
      <button class="chip" data-f="Panchayat" onclick="setFilter(this,'Panchayat')">Panchayat</button>
    </div>

    <div id="polity-content"></div>
  </div>

  <!-- ══════════════ EXAMS ══════════════ -->
  <div id="page-exams" style="display:none;">
    <div class="greeting" style="font-size:30px;margin-bottom:6px;">Exams & <em>Tests</em></div>
    <p style="font-size:13.5px;color:var(--text2);margin-bottom:24px;">Mock tests, previous year papers, and practice sets</p>
    <div class="g2">
      <div class="card">
        <div class="card-label">
          <svg width="13" height="13" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
          Full Mock
        </div>
        <div style="font-family:var(--font-serif);font-size:20px;font-weight:500;margin-bottom:6px;">UPSC Prelims 2024</div>
        <div style="font-size:13px;color:var(--text2);margin-bottom:16px;">100 questions · General Studies Paper I · 2 hours</div>
        <button class="btn-primary">Start Exam</button>
      </div>
      <div class="cta-card">
        <div>
          <div class="cta-title">Polity Mock Test</div>
          <div class="cta-sub">25 focused questions on the Constitution of India — Prelims pattern with negative marking.</div>
        </div>
        <button class="btn-ghost">Attempt Now →</button>
      </div>
    </div>
    <div class="exam-coming" style="margin-top:16px;">
      <div class="exam-coming-icon">📋</div>
      More exams coming soon. Visit the <strong>Polity</strong> section to practise articles in the meantime.
    </div>
  </div>
</main>

<!-- MODAL -->
<div class="overlay" id="modal" onclick="maybeCloseModal(event)">
  <div class="modal" role="dialog" aria-modal="true">
    <button class="modal-close" onclick="closeModal()">×</button>
    <div class="modal-artnum" id="m-num"></div>
    <div class="modal-title" id="m-title"></div>
    <div class="modal-desc" id="m-desc"></div>
    <div class="art-tags" id="m-tags"></div>
    <div class="modal-btns" id="m-btns"></div>
  </div>
</div>

<script>
// ── DATA ──────────────────────────────────────────────────────────────────
const ARTICLES=[
  {part:"Part I",partFull:"Part I — The Union and its Territory",arts:[
    {n:"1",t:"Name and territory of the Union",d:"India, that is Bharat, shall be a Union of States. The territory of India shall consist of the territories of the States, the Union territories specified in the First Schedule, and such other territories as may be acquired.",tags:["imp","basics"]},
    {n:"2",t:"Admission of new States",d:"Parliament may by law admit into the Union, or establish, new States on such terms and conditions as it thinks fit.",tags:["basics"]},
    {n:"3",t:"Formation of new States",d:"Parliament may by law form a new State by separation of territory from any State or by uniting two or more States or parts of States or by uniting any territory to a part of any State. Requires prior recommendation of the President.",tags:["imp","basics"]},
    {n:"4",t:"Laws under Articles 2 and 3",d:"Law admitting new States or altering areas shall contain necessary supplemental provisions and shall amend the First and Fourth Schedules.",tags:["basics"]},
  ]},
  {part:"Part II",partFull:"Part II — Citizenship",arts:[
    {n:"5",t:"Citizenship at commencement",d:"A person is a citizen if domiciled in India and (a) born in India, (b) either parent born in India, or (c) ordinarily resident for 5 years before commencement of Constitution.",tags:["imp","citizenship"]},
    {n:"6",t:"Migrants from Pakistan — citizenship",d:"Persons who migrated to India from Pakistan before July 19, 1948 or registered as citizens under prescribed procedure are deemed citizens.",tags:["citizenship"]},
    {n:"7",t:"Migrants to Pakistan — exclusion",d:"Persons who migrated to Pakistan after March 1, 1947 are not citizens, even if they return later with resettlement permit.",tags:["citizenship"]},
    {n:"8",t:"Persons of Indian origin abroad",d:"Persons of Indian origin residing outside India may be registered as citizens by diplomatic or consular representative of India.",tags:["citizenship"]},
    {n:"9",t:"Voluntary foreign citizenship",d:"A person who voluntarily acquires citizenship of a foreign state shall not be a citizen of India.",tags:["citizenship"]},
    {n:"10",t:"Continuance of citizenship",d:"Every person who is deemed to be a citizen shall continue to be such subject to any law made by Parliament.",tags:["citizenship"]},
    {n:"11",t:"Parliament to regulate citizenship",d:"Nothing in Articles 5–10 shall derogate from the power of Parliament to make any provision with respect to acquisition and termination of citizenship.",tags:["citizenship"]},
  ]},
  {part:"Part III",partFull:"Part III — Fundamental Rights (Articles 12–35)",arts:[
    {n:"12",t:"Definition of State",d:"State includes the Government and Parliament of India, Government and Legislature of each State, and all local or other authorities within India or under the control of the Government of India.",tags:["imp","FR","definition"]},
    {n:"13",t:"Laws inconsistent with FR are void",d:"Pre-constitutional laws inconsistent with Fundamental Rights are void to the extent of inconsistency. The State shall not make any law that takes away or abridges Fundamental Rights.",tags:["imp","FR"]},
    {n:"14",t:"Equality before law",d:"The State shall not deny to any person equality before the law or the equal protection of the laws within the territory of India.",tags:["imp","FR","equality"]},
    {n:"15",t:"Prohibition of discrimination",d:"No discrimination on grounds of religion, race, caste, sex or place of birth. Special provisions for women, children, and backward classes are allowed.",tags:["imp","FR","equality"]},
    {n:"16",t:"Equality in public employment",d:"Equal opportunity for all citizens in matters relating to employment or appointment to any office under the State. Reservation for backward classes is permitted.",tags:["imp","FR","equality"]},
    {n:"17",t:"Abolition of Untouchability",d:"Untouchability is abolished and its practice in any form is forbidden. Enforcement of any disability arising from untouchability is an offence.",tags:["imp","FR","equality"]},
    {n:"18",t:"Abolition of Titles",d:"No title except military or academic distinction shall be conferred by the State. No citizen shall accept title from any foreign State.",tags:["FR","equality"]},
    {n:"19",t:"Protection of six freedoms",d:"All citizens shall have: (a) freedom of speech and expression; (b) to assemble peaceably; (c) to form associations; (d) to move freely; (e) to reside and settle; (g) to practise any profession. Subject to reasonable restrictions in the interest of sovereignty, security, public order, decency or morality.",tags:["imp","FR","freedom"]},
    {n:"20",t:"Protection for conviction of offences",d:"No ex-post-facto law; no double jeopardy; no self-incrimination. These cannot be suspended even during national emergency.",tags:["imp","FR","criminal"]},
    {n:"21",t:"Protection of life and personal liberty",d:"No person shall be deprived of his life or personal liberty except according to procedure established by law. Judicial interpretation has expanded this to include right to privacy, right to livelihood, and more.",tags:["imp","FR","life"]},
    {n:"21A",t:"Right to education (86th Amendment)",d:"The State shall provide free and compulsory education to all children of the age of six to fourteen years in such manner as the State may, by law, determine.",tags:["imp","FR","education"]},
    {n:"22",t:"Protection against arrest and detention",d:"Right to be informed of grounds of arrest; right to consult a lawyer; produced before magistrate within 24 hours. No detention beyond 3 months without Advisory Board under preventive detention laws.",tags:["imp","FR","criminal"]},
    {n:"23",t:"Prohibition of forced labour",d:"Traffic in human beings, begar (forced labour) and similar forms of forced labour are prohibited. Any contravention shall be an offence punishable by law.",tags:["imp","FR","exploitation"]},
    {n:"24",t:"Prohibition of child labour",d:"No child below fourteen years of age shall be employed in any factory, mine, or other hazardous employment.",tags:["imp","FR","exploitation"]},
    {n:"25",t:"Freedom of religion",d:"All persons are equally entitled to freedom of conscience and the right to freely profess, practise and propagate religion. Subject to public order, morality and health.",tags:["imp","FR","religion"]},
    {n:"26",t:"Freedom to manage religious affairs",d:"Every religious denomination has the right to establish and maintain institutions for religious and charitable purposes and to manage its own affairs in matters of religion.",tags:["FR","religion"]},
    {n:"27",t:"Freedom from religious tax",d:"No person shall be compelled to pay taxes for promotion or maintenance of any particular religion or religious denomination.",tags:["FR","religion"]},
    {n:"28",t:"Freedom from religious instruction",d:"No religious instruction shall be imparted in educational institutions wholly maintained out of State funds.",tags:["FR","religion"]},
    {n:"29",t:"Protection of minority interests",d:"Any section of citizens having a distinct language, script or culture shall have the right to conserve the same. No citizen shall be denied admission to any State-aided educational institution on grounds only of religion, race, caste, language.",tags:["imp","FR","minority"]},
    {n:"30",t:"Right of minorities to establish institutions",d:"All minorities, whether based on religion or language, have the right to establish and administer educational institutions of their choice. The State shall not discriminate against minority institutions in granting aid.",tags:["imp","FR","minority"]},
    {n:"32",t:"Right to Constitutional Remedies",d:"The right to move the Supreme Court by appropriate proceedings for enforcement of Fundamental Rights. The SC shall have power to issue writs — habeas corpus, mandamus, prohibition, quo warranto, certiorari. Dr Ambedkar called this the 'heart and soul' of the Constitution.",tags:["imp","FR","remedies"]},
    {n:"33",t:"Modification of FR for armed forces",d:"Parliament may by law determine to what extent any Fundamental Rights shall be restricted or abrogated in their application to members of the armed forces or police.",tags:["FR"]},
    {n:"34",t:"FR during martial law",d:"Parliament may indemnify any person in the service of the Union or of a State for any act done in connection with maintenance of order where martial law was in force.",tags:["FR"]},
    {n:"35",t:"Legislation to give effect to FR",d:"Parliament alone has the power to make laws prescribing punishment for offences mentioned under Articles 17 and 23, and to enforce Fundamental Rights under certain articles.",tags:["FR"]},
  ]},
  {part:"Part IV",partFull:"Part IV — Directive Principles of State Policy (Articles 36–51)",arts:[
    {n:"36",t:"Definition of State for DPSP",d:"In this Part, 'the State' has the same meaning as in Part III.",tags:["DPSP","definition"]},
    {n:"37",t:"DPSP are fundamental in governance",d:"The provisions of this Part shall not be enforceable by any court, but the principles are fundamental in the governance of the country and it shall be the duty of the State to apply these principles in making laws.",tags:["imp","DPSP"]},
    {n:"38",t:"Promote welfare of people",d:"The State shall strive to promote the welfare of the people by securing and protecting a social order in which justice — social, economic and political — shall inform all institutions.",tags:["imp","DPSP"]},
    {n:"39",t:"Certain principles of policy",d:"Adequate means of livelihood; equitable distribution of material resources; no concentration of wealth; equal pay for equal work for men and women; protection of childhood and youth against exploitation.",tags:["imp","DPSP"]},
    {n:"39A",t:"Equal justice and free legal aid",d:"The State shall secure that the operation of the legal system promotes justice on a basis of equal opportunity, and shall provide free legal aid to those who cannot afford it.",tags:["imp","DPSP"]},
    {n:"40",t:"Organisation of village panchayats",d:"The State shall take steps to organise village panchayats and endow them with such powers and authority as may be necessary to enable them to function as units of self-government.",tags:["imp","DPSP","panchayat"]},
    {n:"41",t:"Right to work and education",d:"The State shall make effective provision for securing the right to work, to education and to public assistance in cases of unemployment, old age, sickness and disablement.",tags:["DPSP"]},
    {n:"42",t:"Just and humane work conditions",d:"The State shall make provision for securing just and humane conditions of work and for maternity relief.",tags:["DPSP"]},
    {n:"43",t:"Living wage for workers",d:"The State shall endeavour to secure a living wage, a decent standard of life and full enjoyment of leisure and social and cultural opportunities for all workers.",tags:["DPSP"]},
    {n:"43A",t:"Participation of workers in management",d:"The State shall take steps to secure the participation of workers in the management of undertakings, establishments or other organisations engaged in any industry.",tags:["DPSP"]},
    {n:"44",t:"Uniform Civil Code",d:"The State shall endeavour to secure for the citizens a uniform civil code throughout the territory of India. One of the most debated directives.",tags:["imp","DPSP"]},
    {n:"45",t:"Early childhood care and education",d:"The State shall endeavour to provide early childhood care and education for all children until they complete the age of six years.",tags:["DPSP"]},
    {n:"46",t:"Promotion of SC/ST interests",d:"The State shall promote with special care the educational and economic interests of the weaker sections, and in particular, of the Scheduled Castes and Scheduled Tribes.",tags:["imp","DPSP"]},
    {n:"47",t:"Raise level of nutrition and public health",d:"The State shall regard raising the level of nutrition and standard of living and improvement of public health as among its primary duties. Prohibition of intoxicating drinks and drugs.",tags:["DPSP"]},
    {n:"48",t:"Cattle and agriculture",d:"The State shall endeavour to organise agriculture on modern and scientific lines and take steps for preserving and improving the breeds of cattle and prohibit slaughter of cows, calves and other milch and draught cattle.",tags:["DPSP"]},
    {n:"48A",t:"Protection of environment",d:"The State shall endeavour to protect and improve the environment and to safeguard the forests and wildlife of the country. Added by 42nd Amendment 1976.",tags:["imp","DPSP","environment"]},
    {n:"49",t:"Protection of monuments",d:"It shall be the obligation of the State to protect every monument, place or object of artistic or historic interest, declared by Parliament as of national importance.",tags:["DPSP"]},
    {n:"50",t:"Separation of judiciary from executive",d:"The State shall take steps to separate the judiciary from the executive in the public services of the State.",tags:["imp","DPSP","judiciary"]},
    {n:"51",t:"Promotion of international peace",d:"The State shall endeavour to promote international peace and security; maintain just and honourable relations between nations; foster respect for international law and treaty obligations.",tags:["DPSP","international"]},
  ]},
  {part:"Part IVA",partFull:"Part IV-A — Fundamental Duties (Article 51A)",arts:[
    {n:"51A",t:"Fundamental Duties (11 duties)",d:"Citizens' duties: abide by the Constitution; cherish noble ideals of freedom struggle; uphold sovereignty, unity and integrity; defend the country; promote harmony; value composite culture; preserve natural environment; develop scientific temper; safeguard public property; strive for excellence; parents to provide educational opportunities to children aged 6–14.",tags:["imp","FD"]},
  ]},
  {part:"Part V",partFull:"Part V — The Union Government (Articles 52–151)",arts:[
    {n:"52",t:"The President of India",d:"There shall be a President of India, who is the constitutional head of the executive of the Union.",tags:["imp","President"]},
    {n:"53",t:"Executive power vested in President",d:"The executive power of the Union shall be vested in the President and shall be exercised by him either directly or through officers subordinate to him in accordance with the Constitution.",tags:["imp","President"]},
    {n:"54",t:"Election of President",d:"The President shall be elected by an Electoral College consisting of elected members of both Houses of Parliament and elected members of the Legislative Assemblies of all States.",tags:["imp","President"]},
    {n:"55",t:"Manner of election of President",d:"Election shall be by the system of proportional representation by means of single transferable vote, voting by secret ballot, with uniformity of scale among States.",tags:["President"]},
    {n:"56",t:"Term of office — President",d:"The President shall hold office for a term of five years from the date on which he enters upon his office. Eligible for re-election.",tags:["imp","President"]},
    {n:"58",t:"Qualifications to be President",d:"Must be a citizen of India, completed 35 years of age, and qualified for election as a member of the Lok Sabha.",tags:["imp","President"]},
    {n:"61",t:"Impeachment of President",d:"The President may be removed by impeachment for violation of the Constitution. A charge must be preferred by either House, passed by a majority of total membership with at least two-thirds majority of members present and voting.",tags:["imp","President"]},
    {n:"63",t:"The Vice-President of India",d:"There shall be a Vice-President of India.",tags:["imp","VP"]},
    {n:"64",t:"VP as Chairman of Rajya Sabha",d:"The Vice-President shall be ex officio Chairman of the Council of States (Rajya Sabha) and shall not hold any other office of profit.",tags:["imp","VP","Parliament"]},
    {n:"66",t:"Election of Vice-President",d:"VP is elected by members of both Houses of Parliament by proportional representation — single transferable vote by secret ballot.",tags:["imp","VP"]},
    {n:"72",t:"President's power to grant pardon",d:"The President may grant pardons, reprieves, respites or remissions of punishment or suspend, remit or commute sentence in all cases involving a Union law, a death sentence, or court-martial.",tags:["imp","President","pardon"]},
    {n:"74",t:"Council of Ministers to aid President",d:"There shall be a Council of Ministers with the Prime Minister at the head to aid and advise the President, who shall act in accordance with such advice. The President may return advice for reconsideration once.",tags:["imp","PM","cabinet"]},
    {n:"75",t:"Other provisions as to Ministers",d:"The Prime Minister shall be appointed by the President; other Ministers appointed on the advice of the PM. Ministers shall hold office during the pleasure of the President and shall be collectively responsible to Lok Sabha.",tags:["imp","PM","cabinet"]},
    {n:"76",t:"Attorney-General of India",d:"The President shall appoint a person qualified to be a Judge of the Supreme Court to be the Attorney-General for India. The AG shall have audience in all courts in India.",tags:["imp","AG"]},
    {n:"79",t:"Constitution of Parliament",d:"There shall be a Parliament of the Union which shall consist of the President and two Houses — the Council of States (Rajya Sabha) and the House of the People (Lok Sabha).",tags:["imp","Parliament"]},
    {n:"80",t:"Composition of Rajya Sabha",d:"Maximum 250 members: 12 nominated by President for distinguished service in literature, science, art, and social service + 238 representatives of States and UTs. Members elected by State Legislative Assemblies.",tags:["imp","Parliament"]},
    {n:"81",t:"Composition of Lok Sabha",d:"Maximum 552 members: up to 530 from States + up to 20 from UTs + 2 nominated Anglo-Indians (provision abolished by 104th Amendment 2019). All directly elected by adult suffrage.",tags:["imp","Parliament"]},
    {n:"83",t:"Duration of Houses of Parliament",d:"Rajya Sabha shall not be subject to dissolution — it is a permanent body with 1/3 members retiring every 2 years. Lok Sabha's normal term is 5 years but may be extended during National Emergency.",tags:["imp","Parliament"]},
    {n:"85",t:"Sessions of Parliament",d:"The President shall from time to time summon each House. The gap between two sessions shall not exceed 6 months. The President may prorogue or dissolve the Lok Sabha.",tags:["imp","Parliament"]},
    {n:"93",t:"Speaker and Deputy Speaker of Lok Sabha",d:"The House of the People shall elect from among its members a Speaker and a Deputy Speaker.",tags:["imp","Parliament"]},
    {n:"108",t:"Joint sitting of both Houses",d:"In case of a deadlock on a bill (other than Money Bills or Constitution Amendment Bills), the President may summon a joint sitting. Only 3 joint sittings held so far.",tags:["imp","Parliament"]},
    {n:"109",t:"Special procedure for Money Bills",d:"A Money Bill shall not be introduced in the Rajya Sabha. Rajya Sabha has 14 days to return it with recommendations after it passes Lok Sabha. If not returned in 14 days, deemed passed.",tags:["imp","Parliament"]},
    {n:"110",t:"Definition of Money Bill",d:"A Bill is a Money Bill if it deals solely with: imposition or abolition of taxes; regulation of borrowing; custody of Consolidated Fund; appropriation of money; declaration of expenditure charged on Consolidated Fund. Speaker's certificate is final.",tags:["imp","Parliament"]},
    {n:"112",t:"Annual Financial Statement (Budget)",d:"The President shall cause to be laid before both Houses a statement of the estimated receipts and expenditure of the Government for each financial year — the Union Budget.",tags:["imp","Parliament"]},
    {n:"123",t:"President's Ordinance-making power",d:"When both Houses are not in session, the President may promulgate Ordinances if satisfied that immediate action is necessary. Must be laid before Parliament and ceases to operate after 6 weeks of reassembly.",tags:["imp","President","ordinance"]},
    {n:"124",t:"Establishment of Supreme Court",d:"There shall be a Supreme Court of India consisting of a Chief Justice of India and not more than 33 other Judges (as per latest amendments).",tags:["imp","SC","judiciary"]},
    {n:"129",t:"Supreme Court as court of record",d:"The Supreme Court shall be a court of record and shall have all the powers of such a court including the power to punish for contempt of itself.",tags:["imp","SC","judiciary"]},
    {n:"131",t:"Original jurisdiction of SC",d:"The Supreme Court has exclusive original jurisdiction in disputes between: (a) Government of India and one or more States; (b) two or more States.",tags:["imp","SC","jurisdiction"]},
    {n:"136",t:"Special Leave Petition",d:"The Supreme Court may, in its discretion, grant special leave to appeal from any judgment, decree, determination, sentence or order in any cause or matter passed or made by any court or tribunal in India (except Armed Forces courts).",tags:["imp","SC","jurisdiction"]},
    {n:"141",t:"Law declared by SC is binding",d:"The law declared by the Supreme Court shall be binding on all courts within the territory of India.",tags:["imp","SC"]},
    {n:"143",t:"Advisory jurisdiction of SC",d:"If any question of law or fact of public importance has arisen, the President may refer it to the Supreme Court for its opinion (Advisory/Consultative Jurisdiction).",tags:["imp","SC","President"]},
    {n:"148",t:"Comptroller and Auditor-General",d:"There shall be a CAG appointed by the President. Salary charged to Consolidated Fund. Can be removed only in the same manner as a Supreme Court judge.",tags:["imp","CAG"]},
  ]},
  {part:"Part VI",partFull:"Part VI — The States (Articles 152–237)",arts:[
    {n:"153",t:"Governors of States",d:"There shall be a Governor for each State. One person can be Governor of two or more States.",tags:["imp","Governor","State"]},
    {n:"155",t:"Appointment of Governor",d:"The Governor of a State shall be appointed by the President by warrant under his hand and seal. Not elected — nominated by the Central Government.",tags:["imp","Governor"]},
    {n:"156",t:"Term of Governor",d:"The Governor shall hold office during the pleasure of the President. Normal term is 5 years. Can be removed any time before the term.",tags:["imp","Governor"]},
    {n:"161",t:"Governor's pardon power",d:"The Governor may grant pardons, reprieves, etc., in all cases where punishment is for an offence against any State law — except death sentence (President's power) and court-martial.",tags:["imp","Governor","pardon"]},
    {n:"163",t:"Council of Ministers to aid Governor",d:"There shall be a Council of Ministers with the Chief Minister as the head to aid and advise the Governor, who shall act in accordance with such advice, except in matters requiring his discretion.",tags:["imp","CM","State"]},
    {n:"164",t:"Other provisions as to Ministers",d:"The Chief Minister shall be appointed by the Governor; other Ministers appointed on the advice of the CM. Ministers collectively responsible to the Legislative Assembly.",tags:["imp","CM","State"]},
    {n:"168",t:"Constitution of State Legislatures",d:"For every State there shall be a Legislature consisting of the Governor and one or two Houses. States with bicameral legislature: Andhra Pradesh, Telangana, Karnataka, Maharashtra, Bihar, Uttar Pradesh, J&K.",tags:["imp","State Legislature"]},
    {n:"200",t:"Assent to Bills",d:"When a Bill is presented to the Governor, he may: (a) give assent; (b) withhold assent; (c) return the Bill for reconsideration (except Money Bills); (d) reserve the Bill for the President's consideration.",tags:["imp","Governor"]},
    {n:"213",t:"Governor's Ordinance power",d:"When the State Legislature is not in session, the Governor may promulgate Ordinances as circumstances require. Must be approved by the State Legislature within 6 weeks of reassembly.",tags:["imp","Governor","ordinance"]},
    {n:"214",t:"High Courts for States",d:"There shall be a High Court for each State. Parliament may establish a common High Court for two or more States.",tags:["imp","HC","judiciary"]},
    {n:"226",t:"Power of HC to issue writs",d:"The High Court may issue writs — habeas corpus, mandamus, prohibition, quo warranto and certiorari — for enforcement of Fundamental Rights and for any other purpose. Broader than SC's Article 32 writ jurisdiction.",tags:["imp","HC","writs","judiciary"]},
    {n:"227",t:"HC superintendence over lower courts",d:"Every High Court shall have superintendence over all courts and tribunals throughout the territories in relation to which it exercises jurisdiction.",tags:["imp","HC","judiciary"]},
  ]},
  {part:"Part VIII",partFull:"Part VIII — Union Territories (Articles 239–242)",arts:[
    {n:"239",t:"Administration of Union Territories",d:"Every Union territory shall be administered by the President acting through an administrator appointed by him.",tags:["imp","UT"]},
    {n:"239AA",t:"Special provisions for Delhi",d:"Delhi is administered as a UT with its own Legislature and Council of Ministers. However, matters relating to public order, police and land are subject to the Lieutenant Governor acting on behalf of the President.",tags:["imp","UT","Delhi"]},
  ]},
  {part:"Part IX",partFull:"Part IX — Panchayats (Articles 243–243O)",arts:[
    {n:"243A",t:"Gram Sabha",d:"A Gram Sabha may exercise such powers and perform such functions at the village level as the Legislature of a State may by law provide.",tags:["imp","Panchayat"]},
    {n:"243B",t:"Constitution of Panchayats",d:"There shall be constituted in every State Panchayats at the village, intermediate and district levels. Added by 73rd Constitutional Amendment 1992.",tags:["imp","Panchayat"]},
    {n:"243D",t:"Reservation of seats in Panchayats",d:"Seats shall be reserved for SC/ST in proportion to their population. Not less than 1/3rd seats shall be reserved for women. State may also provide reservation for OBC.",tags:["imp","Panchayat","reservation"]},
    {n:"243G",t:"Powers of Panchayats",d:"Legislature of a State may endow Panchayats with powers to prepare plans and implement schemes for economic development and social justice — 29 subjects listed in the Eleventh Schedule.",tags:["imp","Panchayat"]},
  ]},
  {part:"Part IXA",partFull:"Part IX-A — Municipalities (Articles 243P–243ZG)",arts:[
    {n:"243Q",t:"Constitution of Municipalities",d:"There shall be constituted in every State a Nagar Panchayat for transitional area, a Municipal Council for smaller urban areas, and a Municipal Corporation for larger urban areas. Added by 74th Amendment 1992.",tags:["imp","Municipalities"]},
    {n:"243T",t:"Reservation in Municipalities",d:"Seats shall be reserved for SC/ST in proportion to population. Not less than 1/3rd seats shall be reserved for women.",tags:["imp","Municipalities","reservation"]},
    {n:"243W",t:"Powers of Municipalities",d:"Legislature may endow Municipalities with powers for preparation and implementation of plans with respect to 18 subjects in the Twelfth Schedule.",tags:["imp","Municipalities"]},
  ]},
  {part:"Part XI",partFull:"Part XI — Relations between Union and States (Articles 245–263)",arts:[
    {n:"245",t:"Extent of laws by Parliament and States",d:"Parliament may make laws for the whole or any part of India; a State Legislature may make laws for the whole or any part of the State only. Parliament can also make extra-territorial legislation.",tags:["imp","Centre-State"]},
    {n:"246",t:"Subject matter of legislation — three lists",d:"Parliament has exclusive power over Union List (List I — 97 subjects); Parliament and States can both legislate on Concurrent List (List III — 47 subjects); States have exclusive power over State List (List II — 66 subjects). Residuary power with Parliament.",tags:["imp","Centre-State"]},
    {n:"248",t:"Residuary powers",d:"Parliament has exclusive power to make any law with respect to any matter not enumerated in the Concurrent List or State List.",tags:["imp","Centre-State"]},
    {n:"249",t:"Parliament to legislate on State List",d:"If Rajya Sabha passes a resolution supported by at least 2/3 majority that it is necessary in national interest, Parliament may legislate on any State List matter for a period of 1 year (extendable).",tags:["imp","Centre-State"]},
    {n:"250",t:"Parliament to legislate during national emergency",d:"While a Proclamation of National Emergency is in operation, Parliament shall have power to make laws for the whole or any part of India on any subject in the State List.",tags:["imp","Centre-State","Emergency"]},
    {n:"263",t:"Inter-State Council",d:"If it appears to the President that the public interests would be served by the establishment of a Council for enquiring into disputes between States, the President may establish an inter-State Council.",tags:["imp","Centre-State"]},
  ]},
  {part:"Part XII",partFull:"Part XII — Finance, Property and Contracts (Articles 264–300A)",arts:[
    {n:"265",t:"Taxes only by authority of law",d:"No tax shall be levied or collected except by authority of law. This is a fundamental guarantee against arbitrary taxation.",tags:["imp","Finance"]},
    {n:"266",t:"Consolidated Funds",d:"All revenues received by the Government of India, all loans raised by that Government, and all money received in repayment of loans shall form the Consolidated Fund of India.",tags:["imp","Finance"]},
    {n:"280",t:"Finance Commission",d:"The President shall constitute a Finance Commission within 2 years of commencement and thereafter at the end of every 5th year. Recommends distribution of taxes between Centre and States.",tags:["imp","Finance"]},
    {n:"300A",t:"Right to property",d:"No person shall be deprived of his property save by authority of law. Moved from Fundamental Rights to a mere constitutional right by the 44th Amendment 1978.",tags:["imp","Property"]},
  ]},
  {part:"Part XV",partFull:"Part XV — Elections (Articles 324–329)",arts:[
    {n:"324",t:"Superintendence vested in Election Commission",d:"The superintendence, direction and control of preparation of electoral rolls and the conduct of all elections to Parliament and State Legislatures and offices of President and Vice-President shall be vested in the Election Commission.",tags:["imp","Election","EC"]},
    {n:"325",t:"No discrimination in electoral rolls",d:"There shall be one general electoral roll for every territorial constituency. No person shall be ineligible for inclusion on grounds of religion, race, caste or sex.",tags:["imp","Election"]},
    {n:"326",t:"Adult suffrage",d:"Elections to the House of the People and to the Legislative Assembly of every State shall be on the basis of adult suffrage; every citizen not less than 18 years of age shall be entitled to vote.",tags:["imp","Election"]},
    {n:"329",t:"Bar to court interference in elections",d:"No election to Parliament or State Legislature shall be called in question except by an election petition presented to such authority as may be provided for by or under any law made by the appropriate Legislature.",tags:["imp","Election"]},
  ]},
  {part:"Part XVI",partFull:"Part XVI — Special Provisions (Articles 330–342A)",arts:[
    {n:"330",t:"Reservation for SC/ST in Lok Sabha",d:"Seats shall be reserved in the House of the People for Scheduled Castes and Scheduled Tribes. Reservation was initially for 10 years, extended repeatedly by amendments.",tags:["imp","Reservation","SC/ST"]},
    {n:"338",t:"National Commission for SC",d:"There shall be a National Commission for Scheduled Castes to investigate and monitor all matters relating to safeguards provided for Scheduled Castes.",tags:["imp","SC/ST"]},
    {n:"338A",t:"National Commission for ST",d:"There shall be a National Commission for Scheduled Tribes to investigate and monitor all matters relating to safeguards provided for Scheduled Tribes.",tags:["imp","SC/ST"]},
    {n:"342A",t:"Socially and educationally backward classes",d:"The President may by public notification specify the socially and educationally backward classes. Added by 102nd Amendment 2018, which also created the National Commission for Backward Classes (NCBC) under Article 338B.",tags:["imp","OBC"]},
  ]},
  {part:"Part XVII",partFull:"Part XVII — Official Language (Articles 343–351)",arts:[
    {n:"343",t:"Official language of the Union",d:"The official language of the Union shall be Hindi in Devanagari script. English was permitted for official purposes for 15 years (until 1965); Parliament extended its use indefinitely.",tags:["imp","Language"]},
    {n:"351",t:"Directive for development of Hindi",d:"It shall be the duty of the Union to promote the spread of the Hindi language so that it may serve as a medium of expression for all the elements of the composite culture of India.",tags:["imp","Language"]},
  ]},
  {part:"Part XVIII",partFull:"Part XVIII — Emergency Provisions (Articles 352–360)",arts:[
    {n:"352",t:"National Emergency",d:"The President may proclaim a National Emergency if the security of India or any part thereof is threatened by war, external aggression, or armed rebellion. The Cabinet must recommend in writing. Approved by special majority of Parliament within one month.",tags:["imp","Emergency"]},
    {n:"353",t:"Effect of National Emergency",d:"During National Emergency, Parliament may legislate on State List subjects; Executive power of the Union extends to giving directions to States on any matter.",tags:["imp","Emergency"]},
    {n:"355",t:"Duty of Union to protect States",d:"It shall be the duty of the Union to protect every State against external aggression and internal disturbance and to ensure that the government of every State is carried on in accordance with the Constitution.",tags:["imp","Emergency"]},
    {n:"356",t:"President's Rule",d:"If the President is satisfied that the Government of a State cannot be carried on in accordance with the Constitution, he may proclaim President's Rule. Must be approved by Parliament within 2 months.",tags:["imp","Emergency"]},
    {n:"360",t:"Financial Emergency",d:"The President may proclaim a Financial Emergency if the financial stability or credit of India or of any part thereof is threatened. Never been proclaimed in India so far.",tags:["imp","Emergency"]},
  ]},
  {part:"Part XX",partFull:"Part XX — Amendment of the Constitution (Article 368)",arts:[
    {n:"368",t:"Power to amend the Constitution",d:"Parliament may amend by way of addition, variation or repeal any provision of this Constitution. Types: (1) Simple majority; (2) Special majority — 2/3 of members present and voting + majority of total membership; (3) Special majority + ratification by not less than one-half of State Legislatures.",tags:["imp","Amendment"]},
  ]},
  {part:"Part XXI",partFull:"Part XXI — Temporary, Transitional and Special Provisions",arts:[
    {n:"370",t:"Special status of J&K (now abrogated)",d:"Provided special autonomous status to Jammu & Kashmir. Abrogated by Presidential Order on August 5, 2019. J&K was bifurcated into two UTs: J&K (with Legislature) and Ladakh (without Legislature).",tags:["imp","J&K","Special"]},
    {n:"371A",t:"Special provisions for Nagaland",d:"No Act of Parliament in respect of religious or social practices of the Nagas, Naga customary law and procedure, etc. shall apply to Nagaland unless the Legislative Assembly by a resolution so decides.",tags:["imp","Special","Northeast"]},
    {n:"371G",t:"Special provisions for Mizoram",d:"No Act of Parliament with respect to religious or social practices of Mizo, Mizo customary law and procedure, etc., shall apply to Mizoram unless the Legislative Assembly so decides.",tags:["imp","Special","Northeast"]},
  ]},
  {part:"Part XXII",partFull:"Part XXII — Short Title and Commencement (Articles 393–395)",arts:[
    {n:"394",t:"Commencement",d:"Most provisions came into force on January 26, 1950 — celebrated as Republic Day. Some provisions (Arts. 5, 6, 7, 8, 9, 60, 324, 366, 367, 379, 380, 388, 391, 392 and 393) came into force on November 26, 1949.",tags:["imp","basics"]},
    {n:"395",t:"Repeals",d:"The Indian Independence Act 1947 and the Government of India Act 1935, together with all Schedules and amendments, are hereby repealed.",tags:["basics"]},
  ]},
];

// ── STATE ──────────────────────────────────────────────────────────────────
let mem = JSON.parse(localStorage.getItem('iq_mem') || '{}');
let bks = JSON.parse(localStorage.getItem('iq_bk')  || '{}');
let activeFilter = 'all';
let sidebarVisible = true;
let isDark = false;

// ── HELPERS ───────────────────────────────────────────────────────────────
function save() {
  localStorage.setItem('iq_mem', JSON.stringify(mem));
  localStorage.setItem('iq_bk',  JSON.stringify(bks));
  updateStatsStrip();
}

function updateStatsStrip() {
  const tm = Object.values(mem).filter(Boolean).length;
  const tb = Object.values(bks).filter(Boolean).length;
  const el_m = document.getElementById('s-mem');
  const el_b = document.getElementById('s-bk');
  if (el_m) el_m.textContent = tm + ' Memorised';
  if (el_b) el_b.textContent = tb + ' Bookmarked';
}

function computeCountdown() {
  const now = new Date();
  // UPSC Prelims 2025: May 25
  let prelims = new Date(now.getFullYear(), 4, 25);
  if (prelims < now) prelims.setFullYear(now.getFullYear() + 1);
  const days = Math.ceil((prelims - now) / 86400000);
  const el = document.getElementById('countdown-val');
  if (el) el.textContent = days;
}

// ── NAVIGATION ────────────────────────────────────────────────────────────
function showPage(p) {
  ['dashboard','polity','exams'].forEach(x => {
    const pg = document.getElementById('page-' + x);
    if (pg) pg.style.display = x === p ? 'block' : 'none';
  });
  document.querySelectorAll('.nav-item').forEach(el => el.classList.remove('active'));
  const navEl = document.getElementById('nav-' + p);
  if (navEl) navEl.classList.add('active');
  document.getElementById('bc-text').textContent = p.charAt(0).toUpperCase() + p.slice(1);
  if (p === 'polity') { updateStatsStrip(); renderPolity(); }
}

function toggleSidebar() {
  sidebarVisible = !sidebarVisible;
  const sb = document.getElementById('sidebar');
  const btn = document.getElementById('sb-toggle');
  const main = document.getElementById('main');
  const isMobile = window.innerWidth <= 960;

  if (isMobile) {
    sb.classList.toggle('visible', sidebarVisible);
  } else {
    sb.classList.toggle('hidden', !sidebarVisible);
    main.classList.toggle('expanded', !sidebarVisible);
    btn.style.left = sidebarVisible ? 'calc(var(--sidebar-w) + 12px)' : '12px';
  }
  btn.classList.toggle('floated', !sidebarVisible);
}

function toggleDark() {
  isDark = !isDark;
  if (isDark) document.body.setAttribute('data-dark', '1');
  else document.body.removeAttribute('data-dark');
  document.getElementById('dark-label').textContent = isDark ? 'Light Mode' : 'Dark Mode';
}

// ── POLITY RENDER ─────────────────────────────────────────────────────────
function setFilter(el, f) {
  activeFilter = f;
  document.querySelectorAll('.chip').forEach(c => c.classList.remove('active'));
  el.classList.add('active');
  renderPolity();
}

function renderPolity() {
  const q = (document.getElementById('polity-search')?.value || '').toLowerCase().trim();
  const f = activeFilter;
  let html = '';
  let total = 0;

  for (const part of ARTICLES) {
    const filtered = part.arts.filter(a => {
      const mq = !q
        || a.n.toLowerCase().includes(q)
        || a.t.toLowerCase().includes(q)
        || a.d.toLowerCase().includes(q)
        || part.partFull.toLowerCase().includes(q);
      const mf = f === 'all' || a.tags.includes(f);
      return mq && mf;
    });
    if (!filtered.length) continue;
    total += filtered.length;

    const partName = part.partFull.replace(part.part + ' — ', '');
    html += `<div class="part-block">
      <div class="part-label">
        <span class="part-tag">${part.part}</span>
        ${partName}
      </div>
      <div class="articles-grid">
        ${filtered.map(a => buildArtCard(a)).join('')}
      </div>
    </div>`;
  }

  if (!total) {
    html = `<div class="empty-state">
      <svg width="48" height="48" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg>
      <div>No articles match your search.</div>
    </div>`;
  }

  document.getElementById('polity-content').innerHTML = html;
  // Update total count
  document.getElementById('s-total').textContent = total + ' Articles';
}

function buildArtCard(a) {
  const im = !!mem[a.n];
  const ib = !!bks[a.n];
  const cls = im ? 'mem' : ib ? 'bk' : '';
  return `<div class="art-card ${cls}" id="ac-${a.n}">
    <div class="art-num">Art. ${a.n}</div>
    <div class="art-title">${a.t}</div>
    <div class="art-desc">${a.d}</div>
    <div class="art-tags">${a.tags.map(t => `<span class="a-tag ${t==='imp'?'imp':''}">${t}</span>`).join('')}</div>
    <div class="art-btns">
      <button class="a-btn ${im?'mem-on':''}" onclick="toggleMem('${a.n}',event)">${im?'✓ Memorised':'Memorise'}</button>
      <button class="a-btn ${ib?'bk-on':''}"  onclick="toggleBk('${a.n}',event)">${ib?'★ Saved':'Bookmark'}</button>
      <button class="a-btn" onclick="openModal('${a.n}')">Details</button>
    </div>
  </div>`;
}

function toggleMem(n, e) {
  e.stopPropagation();
  mem[n] = !mem[n];
  if (!mem[n]) delete mem[n];
  save();
  renderPolity();
}

function toggleBk(n, e) {
  e.stopPropagation();
  bks[n] = !bks[n];
  if (!bks[n]) delete bks[n];
  save();
  renderPolity();
}

// ── MODAL ─────────────────────────────────────────────────────────────────
function openModal(n) {
  const a = ARTICLES.flatMap(p => p.arts).find(x => x.n === n);
  if (!a) return;
  document.getElementById('m-num').textContent   = 'Article ' + a.n;
  document.getElementById('m-title').textContent = a.t;
  document.getElementById('m-desc').textContent  = a.d;
  document.getElementById('m-tags').innerHTML    = a.tags.map(t => `<span class="a-tag ${t==='imp'?'imp':''}">${t}</span>`).join('');
  const im = !!mem[a.n]; const ib = !!bks[a.n];
  document.getElementById('m-btns').innerHTML = `
    <button class="a-btn ${im?'mem-on':''}" onclick="toggleMem('${a.n}',{stopPropagation:()=>{}})">${im?'✓ Memorised':'Memorise'}</button>
    <button class="a-btn ${ib?'bk-on':''}"  onclick="toggleBk('${a.n}',{stopPropagation:()=>{}})">${ib?'★ Saved':'Bookmark'}</button>
  `;
  document.getElementById('modal').classList.add('open');
}

function closeModal() {
  document.getElementById('modal').classList.remove('open');
}

function maybeCloseModal(e) {
  if (e.target === document.getElementById('modal')) closeModal();
}

// Keyboard support
document.addEventListener('keydown', e => {
  if (e.key === 'Escape') closeModal();
});

// ── INIT ──────────────────────────────────────────────────────────────────
computeCountdown();
updateStatsStrip();
</script>
</body>
</html>
