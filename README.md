<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ConstitutionIQ — UPSC Polity</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,500;0,700;1,500&family=Geist:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;}
:root{
  --bg:#F6F3EE;
  --sidebar:#100E0B;
  --accent:#C8310A;
  --accent2:#E8522A;
  --card:#FFFFFF;
  --text:#18140F;
  --text2:#7B7368;
  --text3:#C0B9B0;
  --border:#EBE5DC;
  --border2:#D8D0C4;
  --green:#1A6B42;
  --green-bg:#E8F5EE;
  --amber:#8A5C00;
  --amber-bg:#FDF3DC;
  --blue:#1455A0;
  --font:'Geist',sans-serif;
  --serif:'Playfair Display',serif;
  --sh:0 1px 2px rgba(0,0,0,.04),0 4px 12px rgba(0,0,0,.05);
  --sh-lg:0 8px 30px rgba(0,0,0,.10);
  --r:13px;
  --r-sm:9px;
  --sw:224px;
  --ease:cubic-bezier(.4,0,.2,1);
}
[data-dark]{
  --bg:#0C0A07;--card:#141008;--text:#EDE8E0;--text2:#8A8278;
  --text3:#3A3428;--border:#201C14;--border2:#302A1C;
  --green-bg:#0A1A10;--amber-bg:#1A1204;
}

::-webkit-scrollbar{width:3px;height:3px;}
::-webkit-scrollbar-thumb{background:var(–border2);border-radius:3px;}
::-webkit-scrollbar-track{background:transparent;}

body{font-family:var(–font);background:var(–bg);color:var(–text);display:flex;min-height:100vh;font-size:13.5px;line-height:1.5;transition:background .3s,color .3s;}

/* ── SIDEBAR ── */
.sidebar{
width:var(–sw);min-height:100vh;background:var(–sidebar);
position:fixed;left:0;top:0;bottom:0;z-index:100;
display:flex;flex-direction:column;
transition:transform .28s var(–ease);
}
.sidebar.off{transform:translateX(-100%);}

.s-logo{
padding:20px 16px 16px;border-bottom:1px solid #1C1810;
display:flex;align-items:center;gap:10px;
}
.s-mark{
width:30px;height:30px;background:var(–accent);border-radius:9px;
display:flex;align-items:center;justify-content:center;flex-shrink:0;
}
.s-mark svg{width:15px;height:15px;stroke:#fff;fill:none;stroke-width:2.2;}
.s-name{font-family:var(–serif);font-size:14px;font-weight:500;color:#fff;line-height:1.2;}
.s-name small{font-family:var(–font);font-size:9px;color:#3A3628;font-weight:400;letter-spacing:.8px;text-transform:uppercase;display:block;margin-top:1px;}

.s-group{padding:16px 8px 4px;}
.s-glabel{font-size:9px;font-weight:600;color:#2E2A22;letter-spacing:1.4px;text-transform:uppercase;padding:0 8px;margin-bottom:3px;}

.s-item{
display:flex;align-items:center;gap:9px;
padding:7px 10px;border-radius:8px;
font-size:12.5px;font-weight:500;color:#5A5448;
cursor:pointer;transition:all .12s;margin-bottom:1px;
position:relative;text-decoration:none;
}
.s-item svg{width:15px;height:15px;flex-shrink:0;opacity:.55;transition:opacity .12s;}
.s-item:hover{background:#181410;color:#B8B0A4;}
.s-item:hover svg{opacity:.75;}
.s-item.on{background:#1C1810;color:#fff;}
.s-item.on svg{opacity:1;}
.s-item.on::before{content:’’;position:absolute;left:0;top:50%;transform:translateY(-50%);width:2.5px;height:16px;background:var(–accent);border-radius:0 2px 2px 0;}
.s-badge{margin-left:auto;background:var(–accent);color:#fff;font-size:8.5px;font-weight:700;padding:1.5px 5px;border-radius:20px;}

.s-footer{margin-top:auto;border-top:1px solid #1C1810;padding:8px;}

/* ── TOGGLE ── */
.s-toggle{
position:fixed;left:calc(var(–sw) + 10px);top:16px;z-index:200;
background:var(–card);border:1px solid var(–border);border-radius:8px;
width:28px;height:28px;cursor:pointer;display:flex;align-items:center;justify-content:center;
transition:left .28s var(–ease),background .15s;box-shadow:var(–sh);
}
.s-toggle:hover{background:var(–bg);}
.s-toggle.off{left:10px;}
.s-toggle svg{transition:transform .28s var(–ease);}
.s-toggle.off svg{transform:rotate(180deg);}

/* ── MAIN ── */
.main{margin-left:var(–sw);flex:1;padding:26px 32px 60px;transition:margin .28s var(–ease);min-height:100vh;}
.main.wide{margin-left:0;}

/* ── TOPBAR ── */
.topbar{display:flex;align-items:center;justify-content:space-between;margin-bottom:28px;}
.bc{display:flex;align-items:center;gap:7px;font-size:12.5px;color:var(–text2);}
.bc-home{width:28px;height:28px;background:var(–card);border:1px solid var(–border);border-radius:8px;display:flex;align-items:center;justify-content:center;cursor:pointer;transition:border-color .15s;}
.bc-home:hover{border-color:var(–border2);}
.bc-sep{color:var(–text3);}
.bc-now{font-weight:600;color:var(–text);}
.topbar-r{display:flex;align-items:center;gap:7px;}

.live-pill{
display:flex;align-items:center;gap:6px;
background:var(–card);border:1px solid var(–border);border-radius:20px;
padding:5px 12px 5px 9px;font-size:11.5px;font-weight:600;
box-shadow:var(–sh);cursor:default;
}
.ldot{width:6px;height:6px;border-radius:50%;background:var(–accent);animation:blink 1.8s ease-in-out infinite;}
@keyframes blink{0%,100%{opacity:1;}50%{opacity:.2;}}

.icon-btn{
width:32px;height:32px;background:var(–card);border:1px solid var(–border);
border-radius:8px;cursor:pointer;display:flex;align-items:center;justify-content:center;
transition:border-color .15s;box-shadow:var(–sh);
}
.icon-btn:hover{border-color:var(–border2);}
.avatar{width:32px;height:32px;border-radius:50%;background:linear-gradient(135deg,var(–accent),#E8724A);display:flex;align-items:center;justify-content:center;font-size:11.5px;font-weight:700;color:#fff;cursor:pointer;flex-shrink:0;}

/* ── GREETING ── */
.greeting{font-family:var(–serif);font-size:36px;font-weight:500;letter-spacing:-.3px;line-height:1.1;margin-bottom:26px;}
.greeting em{color:var(–accent);font-style:italic;}

/* ── GRIDS ── */
.g2{display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-bottom:14px;}
.g4{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-bottom:14px;}
.g2b{display:grid;grid-template-columns:5fr 4fr;gap:14px;margin-bottom:28px;}

/* ── CARD ── */
.card{background:var(–card);border:1px solid var(–border);border-radius:var(–r);padding:20px 22px;box-shadow:var(–sh);transition:border-color .2s;}
.card:hover{border-color:var(–border2);}
.clabel{display:flex;align-items:center;gap:6px;font-size:10.5px;font-weight:600;color:var(–text2);text-transform:uppercase;letter-spacing:.8px;margin-bottom:14px;}
.clabel svg{width:12px;height:12px;}

/* ── FOCUS CARD ── */
.focus-card{
background:linear-gradient(150deg,#0E0B08 0%,#1C1610 100%);
border:1px solid #241E14;color:#EDE8E0;
position:relative;overflow:hidden;
}
.focus-card::after{content:’’;position:absolute;top:-50px;right:-50px;width:170px;height:170px;background:radial-gradient(circle,rgba(200,49,10,.2) 0%,transparent 70%);pointer-events:none;}
.focus-card .clabel{color:#3A3628;}
.f-meta{display:flex;align-items:center;gap:8px;margin-bottom:4px;}
.f-pct{font-size:12px;font-weight:700;color:#fff;background:rgba(200,49,10,.18);border:1px solid rgba(200,49,10,.35);border-radius:6px;padding:3px 8px;}
.f-cnt{background:rgba(26,107,66,.2);color:#5AD090;font-size:10.5px;font-weight:700;padding:3px 7px;border-radius:5px;border:1px solid rgba(26,107,66,.3);}
.f-title{font-family:var(–serif);font-size:20px;font-weight:500;color:#EDE8E0;margin:10px 0 5px;line-height:1.3;}
.f-sub{font-size:12.5px;color:#6A6358;line-height:1.65;margin-bottom:16px;}

/* ── WAVE ── */
.wave{display:flex;align-items:center;gap:2px;height:22px;}
.wave span{display:block;width:2.5px;border-radius:2px;animation:wp 1.2s ease-in-out infinite;}
@keyframes wp{0%,100%{transform:scaleY(1);}50%{transform:scaleY(.45);}}

/* ── STATS ── */
.prow{display:grid;grid-template-columns:1fr 1fr 1fr;gap:9px;margin-top:4px;}
.pstat{background:var(–bg);border:1px solid var(–border);border-radius:10px;padding:13px 14px;text-align:center;}
.pstat-l{font-size:10px;color:var(–text3);margin-bottom:7px;font-weight:500;text-transform:uppercase;letter-spacing:.5px;}
.pstat-n{font-size:25px;font-weight:700;color:var(–text);line-height:1;}
.pstat-n.g{color:var(–green);}
.pstat-n.a{color:var(–amber);}

/* ── MINI CARDS ── */
.mini{background:var(–card);border:1px solid var(–border);border-radius:11px;padding:15px 16px;box-shadow:var(–sh);transition:border-color .2s,transform .2s;}
.mini:hover{border-color:var(–border2);transform:translateY(-1px);}
.mini-l{display:flex;align-items:center;gap:5px;font-size:10px;font-weight:600;color:var(–text2);margin-bottom:9px;text-transform:uppercase;letter-spacing:.6px;}
.mini-l svg{width:13px;height:13px;}
.mini-v{font-size:23px;font-weight:700;color:var(–text);line-height:1.1;}
.mini-s{font-size:10.5px;color:var(–text3);margin-top:3px;}

/* ── ACTION LIST ── */
.alist{display:flex;flex-direction:column;gap:7px;}
.arow{
background:var(–card);border:1px solid var(–border);border-radius:var(–r-sm);
padding:13px 16px;display:flex;align-items:center;justify-content:space-between;
cursor:pointer;box-shadow:var(–sh);transition:border-color .15s,transform .15s,box-shadow .15s;
}
.arow:hover{border-color:var(–border2);transform:translateX(2px);box-shadow:var(–sh-lg);}
.arow-t{font-size:13.5px;font-weight:600;color:var(–text);margin-bottom:2px;}
.arow-s{font-size:11px;color:var(–text2);}
.arrow{width:32px;height:32px;background:var(–sidebar);border-radius:8px;display:flex;align-items:center;justify-content:center;color:#fff;font-size:15px;flex-shrink:0;transition:background .15s;}
.arow:hover .arrow{background:var(–accent);}

/* ── CTA ── */
.cta{
background:linear-gradient(140deg,var(–accent) 0%,#E86030 100%);
border:none;border-radius:var(–r);padding:26px 22px;
display:flex;flex-direction:column;justify-content:space-between;
min-height:210px;position:relative;overflow:hidden;
box-shadow:0 6px 22px rgba(200,49,10,.28);
}
.cta::before{content:’’;position:absolute;bottom:-30px;right:-30px;width:130px;height:130px;background:rgba(255,255,255,.07);border-radius:50%;}
.cta::after{content:’’;position:absolute;top:-18px;right:55px;width:70px;height:70px;background:rgba(255,255,255,.05);border-radius:50%;}
.cta-t{font-family:var(–serif);font-size:20px;font-weight:500;color:#fff;line-height:1.3;margin-bottom:7px;}
.cta-s{font-size:12px;color:rgba(255,255,255,.72);line-height:1.65;}
.btn-ghost{background:rgba(255,255,255,.14);backdrop-filter:blur(8px);border:1px solid rgba(255,255,255,.28);color:#fff;border-radius:9px;padding:9px 18px;font-family:var(–font);font-size:12.5px;font-weight:600;cursor:pointer;width:fit-content;transition:background .15s;margin-top:14px;}
.btn-ghost:hover{background:rgba(255,255,255,.24);}
.btn-primary{background:var(–accent);color:#fff;border:none;border-radius:9px;padding:10px 20px;font-family:var(–font);font-size:12.5px;font-weight:600;cursor:pointer;transition:background .15s,transform .15s;box-shadow:0 2px 8px rgba(200,49,10,.3);}
.btn-primary:hover{background:#B02A08;transform:translateY(-1px);}

/* ── POLITY PAGE ── */
.stats-row{display:flex;gap:7px;flex-wrap:wrap;margin-bottom:18px;}
.spill{background:var(–card);border:1px solid var(–border);border-radius:8px;padding:6px 12px;font-size:11.5px;font-weight:600;display:flex;align-items:center;gap:6px;box-shadow:var(–sh);}
.sdot{width:6px;height:6px;border-radius:50%;flex-shrink:0;}

.search-wrap{position:relative;margin-bottom:14px;}
.search-wrap input{
width:100%;height:40px;border:1px solid var(–border);border-radius:10px;
padding:0 14px 0 38px;font-family:var(–font);font-size:13px;
background:var(–card);color:var(–text);outline:none;
transition:border-color .2s,box-shadow .2s;box-shadow:var(–sh);
}
.search-wrap input:focus{border-color:var(–accent);box-shadow:0 0 0 3px rgba(200,49,10,.07);}
.search-wrap input::placeholder{color:var(–text3);}
.sicon{position:absolute;left:12px;top:50%;transform:translateY(-50%);opacity:.3;pointer-events:none;}

.filters{display:flex;gap:5px;flex-wrap:wrap;margin-bottom:20px;}
.chip{background:var(–card);border:1px solid var(–border);border-radius:20px;padding:5px 12px;font-size:11.5px;font-weight:500;cursor:pointer;color:var(–text2);transition:all .13s;white-space:nowrap;}
.chip:hover{border-color:var(–border2);color:var(–text);}
.chip.on{background:var(–sidebar);color:#fff;border-color:var(–sidebar);}

/* ── PART BLOCK ── */
.part-block{margin-bottom:26px;}
.part-label{display:flex;align-items:center;gap:7px;font-size:10px;font-weight:700;color:var(–text3);text-transform:uppercase;letter-spacing:1.2px;margin-bottom:8px;}
.part-label::after{content:’’;flex:1;height:1px;background:var(–border);}
.ptag{background:var(–sidebar);color:#fff;font-size:8.5px;font-weight:700;padding:2px 8px;border-radius:20px;flex-shrink:0;}

/* ── ARTICLE CARDS ── */
.agrid{display:grid;grid-template-columns:repeat(auto-fill,minmax(262px,1fr));gap:9px;}
.ac{
background:var(–card);border:1px solid var(–border);border-radius:11px;
padding:14px 15px;cursor:pointer;transition:border-color .2s,box-shadow .2s,transform .2s;
position:relative;overflow:hidden;
}
.ac::before{content:’’;position:absolute;left:0;top:0;bottom:0;width:2.5px;background:transparent;transition:background .2s;}
.ac:hover{border-color:var(–border2);box-shadow:var(–sh-lg);transform:translateY(-2px);}
.ac:hover::before{background:var(–accent);}
.ac.mem::before{background:var(–green);}
.ac.bk::before{background:#C89A00;}

.an{font-size:9px;font-weight:700;color:var(–accent);letter-spacing:.8px;text-transform:uppercase;margin-bottom:4px;}
.at{font-size:13px;font-weight:600;color:var(–text);line-height:1.35;margin-bottom:6px;}
.ad{font-size:11px;color:var(–text2);line-height:1.65;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden;margin-bottom:9px;}
.atags{display:flex;gap:3px;flex-wrap:wrap;margin-bottom:9px;}
.atag{font-size:9px;padding:2px 6px;border-radius:20px;background:var(–bg);color:var(–text3);font-weight:500;border:1px solid var(–border);}
.atag.imp{background:#FEF0EC;color:var(–accent);border-color:#F4C4B4;}
.abtns{display:flex;gap:4px;}
.abtn{font-size:10px;padding:4px 8px;border-radius:7px;border:1px solid var(–border);cursor:pointer;background:transparent;color:var(–text2);font-family:var(–font);font-weight:500;transition:all .13s;}
.abtn:hover{background:var(–bg);border-color:var(–border2);}
.abtn.mem-on{background:var(–green-bg);color:var(–green);border-color:#9FD4B4;}
.abtn.bk-on{background:var(–amber-bg);color:var(–amber);border-color:#E8C860;}

/* ── MODAL ── */
.overlay{position:fixed;inset:0;background:rgba(0,0,0,.4);backdrop-filter:blur(5px);z-index:500;display:flex;align-items:center;justify-content:center;opacity:0;pointer-events:none;transition:opacity .22s var(–ease);}
.overlay.open{opacity:1;pointer-events:auto;}
.modal{background:var(–card);border:1px solid var(–border);border-radius:18px;padding:28px 30px;max-width:500px;width:90%;max-height:80vh;overflow-y:auto;position:relative;transform:translateY(14px) scale(.97);transition:transform .22s var(–ease);box-shadow:var(–sh-lg);}
.overlay.open .modal{transform:none;}
.m-num{font-size:10.5px;font-weight:700;color:var(–accent);letter-spacing:.8px;text-transform:uppercase;margin-bottom:4px;}
.m-title{font-family:var(–serif);font-size:20px;font-weight:500;color:var(–text);margin-bottom:13px;line-height:1.3;}
.m-desc{font-size:13.5px;color:var(–text2);line-height:1.8;margin-bottom:16px;}
.m-close{position:absolute;top:16px;right:16px;background:var(–bg);border:1px solid var(–border);border-radius:7px;width:28px;height:28px;cursor:pointer;font-size:15px;color:var(–text2);display:flex;align-items:center;justify-content:center;transition:background .13s;}
.m-close:hover{background:var(–border);}
.m-btns{display:flex;gap:7px;flex-wrap:wrap;margin-top:6px;}

/* ── EXAMS ── */
.empty-coming{background:var(–card);border:1px solid var(–border);border-radius:var(–r);padding:44px 30px;text-align:center;color:var(–text2);font-size:13.5px;box-shadow:var(–sh);margin-top:14px;}

/* ── EMPTY ── */
.empty-state{text-align:center;padding:56px 30px;color:var(–text2);font-size:13.5px;}
.empty-state svg{opacity:.18;margin-bottom:12px;}

.page{animation:pagein .22s var(–ease);}
@keyframes pagein{from{opacity:0;transform:translateY(7px);}to{opacity:1;transform:none;}}

@media(max-width:960px){
.sidebar{transform:translateX(-100%);}
.sidebar.vis{transform:none;}
.main{margin-left:0;padding:20px 18px 60px;}
.g2,.g4,.g2b{grid-template-columns:1fr;}
.s-toggle{left:10px;}
.s-toggle.off{left:calc(var(–sw) + 10px);}
}
@media(max-width:540px){
.greeting{font-size:27px;}
.prow{grid-template-columns:1fr 1fr;}
.agrid{grid-template-columns:1fr;}
}
</style>

</head>
<body>

<aside class="sidebar" id="sidebar">
  <div class="s-logo">
    <div class="s-mark"><svg viewBox="0 0 24 24"><path d="M12 3L3 8.5v7L12 21l9-5.5v-7z"/><path d="M12 3v18M3 8.5l9 5.5 9-5.5"/></svg></div>
    <div class="s-name">ConstitutionIQ<small>UPSC Polity</small></div>
  </div>

  <div class="s-group">
    <div class="s-glabel">Main</div>
    <a class="s-item on" id="nav-dashboard" onclick="goto('dashboard')">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7" rx="1.5"/><rect x="14" y="3" width="7" height="7" rx="1.5"/><rect x="3" y="14" width="7" height="7" rx="1.5"/><rect x="14" y="14" width="7" height="7" rx="1.5"/></svg>
      Dashboard
    </a>
    <a class="s-item" id="nav-polity" onclick="goto('polity')">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M12 3L3 9v12h6v-6h6v6h6V9z"/></svg>
      Polity
      <span class="s-badge">NEW</span>
    </a>
    <a class="s-item" id="nav-exams" onclick="goto('exams')">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M9 11l3 3L22 4"/><path d="M21 12v7a2 2 0 01-2 2H5a2 2 0 01-2-2V5a2 2 0 012-2h11"/></svg>
      Exams
    </a>
    <a class="s-item">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>
      Practice Mode
    </a>
    <a class="s-item">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M4 19.5A2.5 2.5 0 016.5 17H20"/><path d="M6.5 2H20v20H6.5A2.5 2.5 0 014 19.5v-15A2.5 2.5 0 016.5 2z"/></svg>
      Textbooks
    </a>
  </div>

  <div class="s-group">
    <div class="s-glabel">Settings</div>
    <a class="s-item" onclick="toggleDark()">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M21 12.79A9 9 0 1111.21 3 7 7 0 0021 12.79z"/></svg>
      <span id="dlabel">Dark Mode</span>
    </a>
    <a class="s-item">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 00.33 1.82l.06.06a2 2 0 010 2.83 2 2 0 01-2.83 0l-.06-.06a1.65 1.65 0 00-1.82-.33 1.65 1.65 0 00-1 1.51V21a2 2 0 01-4 0v-.09A1.65 1.65 0 009 19.4a1.65 1.65 0 00-1.82.33l-.06.06a2 2 0 01-2.83-2.83l.06-.06A1.65 1.65 0 004.68 15a1.65 1.65 0 00-1.51-1H3a2 2 0 010-4h.09A1.65 1.65 0 004.6 9a1.65 1.65 0 00-.33-1.82l-.06-.06a2 2 0 012.83-2.83l.06.06A1.65 1.65 0 009 4.68a1.65 1.65 0 001-1.51V3a2 2 0 014 0v.09a1.65 1.65 0 001 1.51 1.65 1.65 0 001.82-.33l.06-.06a2 2 0 012.83 2.83l-.06.06A1.65 1.65 0 0019.4 9a1.65 1.65 0 001.51 1H21a2 2 0 010 4h-.09a1.65 1.65 0 00-1.51 1z"/></svg>
      Preferences
    </a>
  </div>

  <div class="s-footer">
    <a class="s-item" onclick="toggleSidebar()">
      <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M11 19l-7-7 7-7M4 12h16"/></svg>
      Collapse
    </a>
  </div>
</aside>

<button class="s-toggle" id="stoggle" onclick="toggleSidebar()">
  <svg width="12" height="12" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path d="M9 18l6-6-6-6"/></svg>
</button>

<main class="main" id="main">
  <div class="topbar">
    <div class="bc">
      <div class="bc-home" onclick="goto('dashboard')">
        <svg width="12" height="12" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/></svg>
      </div>
      <span class="bc-sep">›</span>
      <span class="bc-now" id="bctext">Dashboard</span>
    </div>
    <div class="topbar-r">
      <div class="live-pill">
        <span class="ldot"></span>
        UPSC Mode
        <svg width="12" height="12" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>
      </div>
      <button class="icon-btn" onclick="toggleDark()">
        <svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M21 12.79A9 9 0 1111.21 3 7 7 0 0021 12.79z"/></svg>
      </button>
      <div class="avatar">N</div>
    </div>
  </div>

  <!-- DASHBOARD -->

  <div id="pg-dashboard" class="page">
    <div class="greeting">Good morning, <em>Aspirant!</em></div>

```
<div class="g2">
  <div class="card focus-card">
    <div class="clabel">
      <svg fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg>
      Today's Focus
    </div>
    <div class="f-meta">
      <span class="f-pct">56% complete</span>
      <span class="f-cnt">41 done</span>
      <div class="wave" style="margin-left:4px;">
        <span style="height:7px;background:#1A6B42;animation-delay:0s;"></span>
        <span style="height:14px;background:#1A6B42;animation-delay:.1s;"></span>
        <span style="height:20px;background:#1A6B42;animation-delay:.2s;"></span>
        <span style="height:11px;background:#1A6B42;animation-delay:.3s;"></span>
        <span style="height:17px;background:#1A6B42;animation-delay:.4s;"></span>
        <span style="height:7px;background:#302820;animation-delay:.1s;"></span>
        <span style="height:13px;background:#302820;animation-delay:.2s;"></span>
        <span style="height:19px;background:#302820;animation-delay:.3s;"></span>
        <span style="height:9px;background:#302820;animation-delay:.4s;"></span>
      </div>
    </div>
    <div class="f-title">Fundamental Rights &amp; DPSP</div>
    <div class="f-sub">Solve 10 questions on Articles 12–51. Focus on the FR–DPSP relationship — a recurring Prelims theme.</div>
    <button class="btn-primary" onclick="goto('polity')">Practice Now →</button>
  </div>

  <div class="card">
    <div class="clabel">
      <svg fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
      Today's Progress
    </div>
    <div class="prow">
      <div class="pstat"><div class="pstat-l">Attempted</div><div class="pstat-n">50</div></div>
      <div class="pstat"><div class="pstat-l">Correct</div><div class="pstat-n g">40</div></div>
      <div class="pstat"><div class="pstat-l">Accuracy</div><div class="pstat-n a">80%</div></div>
    </div>
  </div>
</div>

<div class="g4">
  <div class="mini">
    <div class="mini-l"><svg fill="none" stroke="var(--accent)" stroke-width="2" viewBox="0 0 24 24"><rect x="3" y="4" width="18" height="18" rx="2"/><path d="M16 2v4M8 2v4M3 10h18"/></svg>Daily Activity</div>
    <div class="mini-v">8</div><div class="mini-s">Articles reviewed today</div>
  </div>
  <div class="mini">
    <div class="mini-l"><svg fill="none" stroke="var(--accent)" stroke-width="2" viewBox="0 0 24 24"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"/><polyline points="17 6 23 6 23 12"/></svg>7-Day Accuracy</div>
    <div class="mini-v">72%</div><div class="mini-s">Up 4% this week</div>
  </div>
  <div class="mini">
    <div class="mini-l"><svg fill="none" stroke="var(--accent)" stroke-width="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>Prelims Countdown</div>
    <div class="mini-v" id="cdown">—</div><div class="mini-s">Days until UPSC Prelims</div>
  </div>
  <div class="mini">
    <div class="mini-l"><svg fill="none" stroke="var(--accent)" stroke-width="2" viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>Streak</div>
    <div class="mini-v">6 🔥</div><div class="mini-s">Days in a row</div>
  </div>
</div>

<div class="g2b">
  <div class="alist">
    <div class="arow" onclick="goto('polity')">
      <div><div class="arow-t">Articles Quick Revision</div><div class="arow-s">Browse all 395+ constitutional articles</div></div>
      <div class="arrow">›</div>
    </div>
    <div class="arow">
      <div><div class="arow-t">Mock Test — Polity</div><div class="arow-s">25 MCQs · UPSC Prelims pattern</div></div>
      <div class="arrow">›</div>
    </div>
    <div class="arow">
      <div><div class="arow-t">Schedules &amp; Amendments</div><div class="arow-s">12 Schedules · Key Amendments explained</div></div>
      <div class="arrow">›</div>
    </div>
    <div class="arow">
      <div><div class="arow-t">Previous Year Questions</div><div class="arow-s">Polity PYQs from 2013–2024</div></div>
      <div class="arrow">›</div>
    </div>
  </div>
  <div class="cta">
    <div>
      <div class="cta-t">Adaptive Practice Mode</div>
      <div class="cta-s">Test yourself on the most-asked constitutional articles. Difficulty adjusts based on your performance.</div>
    </div>
    <button class="btn-ghost" onclick="goto('polity')">Start Practice →</button>
  </div>
</div>
```

  </div>

  <!-- POLITY -->

  <div id="pg-polity" style="display:none;">
    <div class="greeting" style="font-size:28px;margin-bottom:4px;">Indian <em>Constitution</em></div>
    <p style="font-size:13px;color:var(--text2);margin-bottom:20px;">All Articles · Organised by Parts · Interactive Study Tool</p>

```
<div class="stats-row">
  <div class="spill"><span class="sdot" style="background:var(--accent);"></span><span id="s-total">448 Articles</span></div>
  <div class="spill"><span class="sdot" style="background:var(--green);"></span><span id="s-mem">0 Memorised</span></div>
  <div class="spill"><span class="sdot" style="background:#C89A00;"></span><span id="s-bk">0 Bookmarked</span></div>
  <div class="spill"><span class="sdot" style="background:var(--blue);"></span>22 Parts</div>
  <div class="spill"><span class="sdot" style="background:#8B5CF6;"></span>12 Schedules</div>
</div>

<div class="search-wrap">
  <svg class="sicon" width="14" height="14" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg>
  <input type="text" id="psearch" placeholder="Search by Article number, keyword, or Part name…" oninput="renderPolity()">
</div>

<div class="filters" id="pfilters">
  <button class="chip on" onclick="setFilter(this,'all')">All</button>
  <button class="chip" onclick="setFilter(this,'imp')">⭐ Important</button>
  <button class="chip" onclick="setFilter(this,'FR')">Fundamental Rights</button>
  <button class="chip" onclick="setFilter(this,'DPSP')">DPSP</button>
  <button class="chip" onclick="setFilter(this,'FD')">Fundamental Duties</button>
  <button class="chip" onclick="setFilter(this,'Parliament')">Parliament</button>
  <button class="chip" onclick="setFilter(this,'President')">President</button>
  <button class="chip" onclick="setFilter(this,'judiciary')">Judiciary</button>
  <button class="chip" onclick="setFilter(this,'Emergency')">Emergency</button>
  <button class="chip" onclick="setFilter(this,'Election')">Elections</button>
  <button class="chip" onclick="setFilter(this,'Panchayat')">Panchayat</button>
</div>

<div id="polity-content"></div>
```

  </div>

  <!-- EXAMS -->

  <div id="pg-exams" style="display:none;">
    <div class="greeting" style="font-size:28px;margin-bottom:4px;">Exams &amp; <em>Tests</em></div>
    <p style="font-size:13px;color:var(--text2);margin-bottom:22px;">Mock tests, previous year papers, and practice sets</p>
    <div class="g2">
      <div class="card">
        <div class="clabel">
          <svg fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
          Full Mock
        </div>
        <div style="font-family:var(--serif);font-size:19px;font-weight:500;margin-bottom:5px;">UPSC Prelims 2024</div>
        <div style="font-size:12.5px;color:var(--text2);margin-bottom:14px;">100 questions · General Studies Paper I · 2 hours</div>
        <button class="btn-primary">Start Exam</button>
      </div>
      <div class="cta">
        <div>
          <div class="cta-t">Polity Mock Test</div>
          <div class="cta-s">25 focused questions on the Constitution — Prelims pattern with negative marking.</div>
        </div>
        <button class="btn-ghost">Attempt Now →</button>
      </div>
    </div>
    <div class="empty-coming">
      <div style="font-size:36px;margin-bottom:10px;">📋</div>
      More exams coming soon. Visit the <strong>Polity</strong> section to practise articles in the meantime.
    </div>
  </div>
</main>

<!-- MODAL -->

<div class="overlay" id="modal" onclick="maybeClose(event)">
  <div class="modal" role="dialog" aria-modal="true">
    <button class="m-close" onclick="closeModal()">×</button>
    <div class="m-num" id="m-num"></div>
    <div class="m-title" id="m-title"></div>
    <div class="m-desc" id="m-desc"></div>
    <div class="atags" id="m-tags"></div>
    <div class="m-btns" id="m-btns"></div>
  </div>
</div>

<script>
const DATA=[
  {p:"Part I",pf:"Part I — The Union and its Territory",arts:[
    {n:"1",t:"Name and territory of the Union",d:"India, that is Bharat, shall be a Union of States. The territory includes territories of States, Union territories in the First Schedule, and other territories acquired.",tags:["imp","basics"]},
    {n:"2",t:"Admission of new States",d:"Parliament may by law admit into the Union, or establish, new States on such terms and conditions as it thinks fit.",tags:["basics"]},
    {n:"3",t:"Formation of new States",d:"Parliament may form a new State by separation, union, or addition of territories. Requires prior recommendation of the President.",tags:["imp","basics"]},
    {n:"4",t:"Laws under Articles 2 and 3",d:"Laws admitting or altering States shall contain supplemental provisions and amend the First and Fourth Schedules.",tags:["basics"]},
  ]},
  {p:"Part II",pf:"Part II — Citizenship",arts:[
    {n:"5",t:"Citizenship at commencement",d:"A person is a citizen if domiciled in India and (a) born in India, (b) either parent born in India, or (c) ordinarily resident for 5 years before commencement.",tags:["imp","citizenship"]},
    {n:"6",t:"Migrants from Pakistan",d:"Persons migrating from Pakistan before July 19, 1948 or registered as citizens under prescribed procedure are deemed citizens.",tags:["citizenship"]},
    {n:"7",t:"Migrants to Pakistan — exclusion",d:"Persons who migrated to Pakistan after March 1, 1947 are not citizens, even on return with resettlement permit.",tags:["citizenship"]},
    {n:"8",t:"Persons of Indian origin abroad",d:"Persons of Indian origin residing outside India may be registered as citizens by a diplomatic or consular representative.",tags:["citizenship"]},
    {n:"9",t:"Voluntary foreign citizenship",d:"A person who voluntarily acquires citizenship of a foreign state shall not be a citizen of India.",tags:["citizenship"]},
    {n:"11",t:"Parliament to regulate citizenship",d:"Nothing in Articles 5–10 derogates from Parliament's power to make provisions on acquisition and termination of citizenship.",tags:["citizenship"]},
  ]},
  {p:"Part III",pf:"Part III — Fundamental Rights (Articles 12–35)",arts:[
    {n:"12",t:"Definition of State",d:"State includes the Government and Parliament of India, Government and Legislature of each State, and all local or other authorities within India or under the control of the Government.",tags:["imp","FR","definition"]},
    {n:"13",t:"Laws inconsistent with FR are void",d:"Pre-constitutional laws inconsistent with Fundamental Rights are void to the extent of inconsistency. The State shall not make any law that takes away or abridges Fundamental Rights.",tags:["imp","FR"]},
    {n:"14",t:"Equality before law",d:"The State shall not deny to any person equality before the law or the equal protection of the laws within the territory of India.",tags:["imp","FR","equality"]},
    {n:"15",t:"Prohibition of discrimination",d:"No discrimination on grounds of religion, race, caste, sex or place of birth. Special provisions for women, children, and backward classes are permitted.",tags:["imp","FR","equality"]},
    {n:"16",t:"Equality in public employment",d:"Equal opportunity for all citizens in matters of employment or appointment under the State. Reservation for backward classes is permitted.",tags:["imp","FR","equality"]},
    {n:"17",t:"Abolition of Untouchability",d:"Untouchability is abolished and its practice in any form is forbidden. Enforcement of any disability arising from it is an offence.",tags:["imp","FR","equality"]},
    {n:"18",t:"Abolition of Titles",d:"No title except military or academic distinction shall be conferred by the State. No citizen shall accept a title from a foreign State.",tags:["FR","equality"]},
    {n:"19",t:"Protection of six freedoms",d:"Citizens have: (a) freedom of speech and expression; (b) to assemble peaceably; (c) to form associations; (d) to move freely; (e) to reside and settle; (g) to practise any profession. Subject to reasonable restrictions in the interest of sovereignty, security, public order, decency or morality.",tags:["imp","FR","freedom"]},
    {n:"20",t:"Protection for conviction of offences",d:"No ex-post-facto law; no double jeopardy; no self-incrimination. Cannot be suspended even during national emergency.",tags:["imp","FR","criminal"]},
    {n:"21",t:"Protection of life and personal liberty",d:"No person shall be deprived of his life or personal liberty except according to procedure established by law. Judicially expanded to include right to privacy, livelihood, and more.",tags:["imp","FR","life"]},
    {n:"21A",t:"Right to education (86th Amendment)",d:"The State shall provide free and compulsory education to all children of six to fourteen years in such manner as the State may by law determine.",tags:["imp","FR","education"]},
    {n:"22",t:"Protection against arrest and detention",d:"Right to be informed of grounds of arrest; right to consult a lawyer; produced before magistrate within 24 hours. No detention beyond 3 months without Advisory Board.",tags:["imp","FR","criminal"]},
    {n:"23",t:"Prohibition of forced labour",d:"Traffic in human beings, begar (forced labour) and similar forms are prohibited. Any contravention shall be a punishable offence.",tags:["imp","FR","exploitation"]},
    {n:"24",t:"Prohibition of child labour",d:"No child below fourteen years of age shall be employed in any factory, mine, or other hazardous employment.",tags:["imp","FR","exploitation"]},
    {n:"25",t:"Freedom of religion",d:"All persons are equally entitled to freedom of conscience and the right to freely profess, practise and propagate religion. Subject to public order, morality and health.",tags:["imp","FR","religion"]},
    {n:"26",t:"Freedom to manage religious affairs",d:"Every religious denomination has the right to establish institutions for religious and charitable purposes and to manage its own affairs in matters of religion.",tags:["FR","religion"]},
    {n:"27",t:"Freedom from religious tax",d:"No person shall be compelled to pay taxes for promotion of any particular religion or denomination.",tags:["FR","religion"]},
    {n:"28",t:"Freedom from religious instruction",d:"No religious instruction shall be imparted in educational institutions wholly maintained out of State funds.",tags:["FR","religion"]},
    {n:"29",t:"Protection of minority interests",d:"Citizens having a distinct language, script or culture shall have the right to conserve them. No citizen shall be denied admission to State-aided institutions on grounds of religion, race, caste, or language.",tags:["imp","FR","minority"]},
    {n:"30",t:"Right of minorities to establish institutions",d:"All minorities, whether religious or linguistic, may establish and administer educational institutions. The State shall not discriminate against minority institutions in granting aid.",tags:["imp","FR","minority"]},
    {n:"32",t:"Right to Constitutional Remedies",d:"The right to move the Supreme Court for enforcement of Fundamental Rights. The SC may issue writs — habeas corpus, mandamus, prohibition, quo warranto, certiorari. Dr Ambedkar called this the 'heart and soul' of the Constitution.",tags:["imp","FR","remedies"]},
    {n:"35",t:"Legislation to give effect to FR",d:"Parliament alone has the power to make laws prescribing punishment for offences under Articles 17 and 23 and to enforce certain Fundamental Rights.",tags:["FR"]},
  ]},
  {p:"Part IV",pf:"Part IV — Directive Principles of State Policy (Articles 36–51)",arts:[
    {n:"37",t:"DPSP are fundamental in governance",d:"DPSP shall not be enforceable by any court but are fundamental in the governance of the country and it shall be the State's duty to apply these principles in making laws.",tags:["imp","DPSP"]},
    {n:"38",t:"Promote welfare of people",d:"The State shall strive to promote the welfare of the people by securing a social order in which justice — social, economic and political — shall inform all institutions.",tags:["imp","DPSP"]},
    {n:"39",t:"Certain principles of policy",d:"Adequate means of livelihood; equitable distribution of material resources; no concentration of wealth; equal pay for equal work for men and women; protection of childhood and youth against exploitation.",tags:["imp","DPSP"]},
    {n:"39A",t:"Equal justice and free legal aid",d:"The State shall secure that the legal system promotes justice on a basis of equal opportunity and shall provide free legal aid to those who cannot afford it.",tags:["imp","DPSP"]},
    {n:"40",t:"Organisation of village panchayats",d:"The State shall take steps to organise village panchayats and endow them with powers to function as units of self-government.",tags:["imp","DPSP","Panchayat"]},
    {n:"44",t:"Uniform Civil Code",d:"The State shall endeavour to secure for the citizens a uniform civil code throughout the territory of India. One of the most debated directives.",tags:["imp","DPSP"]},
    {n:"45",t:"Early childhood care and education",d:"The State shall endeavour to provide early childhood care and education for all children until they complete the age of six years.",tags:["DPSP"]},
    {n:"46",t:"Promotion of SC/ST interests",d:"The State shall promote with special care the educational and economic interests of the weaker sections, particularly Scheduled Castes and Scheduled Tribes.",tags:["imp","DPSP"]},
    {n:"48A",t:"Protection of environment",d:"The State shall endeavour to protect and improve the environment and safeguard forests and wildlife. Added by 42nd Amendment 1976.",tags:["imp","DPSP","environment"]},
    {n:"50",t:"Separation of judiciary from executive",d:"The State shall take steps to separate the judiciary from the executive in the public services of the State.",tags:["imp","DPSP","judiciary"]},
    {n:"51",t:"Promotion of international peace",d:"The State shall endeavour to promote international peace; maintain just and honourable relations between nations; foster respect for international law and treaty obligations.",tags:["DPSP","international"]},
  ]},
  {p:"Part IVA",pf:"Part IV-A — Fundamental Duties (Article 51A)",arts:[
    {n:"51A",t:"Fundamental Duties (11 duties)",d:"Citizens must: abide by the Constitution; cherish ideals of the freedom struggle; uphold sovereignty and integrity; defend the country; promote harmony; value composite culture; preserve the natural environment; develop scientific temper; safeguard public property; strive for excellence; parents to provide educational opportunities to children aged 6–14.",tags:["imp","FD"]},
  ]},
  {p:"Part V",pf:"Part V — The Union Government (Articles 52–151)",arts:[
    {n:"52",t:"The President of India",d:"There shall be a President of India, who is the constitutional head of the executive of the Union.",tags:["imp","President"]},
    {n:"53",t:"Executive power vested in President",d:"The executive power of the Union shall be vested in the President and shall be exercised by him directly or through officers subordinate to him.",tags:["imp","President"]},
    {n:"54",t:"Election of President",d:"The President is elected by an Electoral College consisting of elected members of both Houses of Parliament and elected members of the State Legislative Assemblies.",tags:["imp","President"]},
    {n:"56",t:"Term of office — President",d:"The President shall hold office for five years from the date of entering office. Eligible for re-election.",tags:["imp","President"]},
    {n:"58",t:"Qualifications to be President",d:"Must be a citizen of India, completed 35 years of age, and qualified for election as a member of Lok Sabha.",tags:["imp","President"]},
    {n:"61",t:"Impeachment of President",d:"The President may be removed for violation of the Constitution. A charge must be passed by a two-thirds majority of total membership of either House.",tags:["imp","President"]},
    {n:"63",t:"The Vice-President of India",d:"There shall be a Vice-President of India.",tags:["imp","VP"]},
    {n:"64",t:"VP as Chairman of Rajya Sabha",d:"The Vice-President shall be ex officio Chairman of the Rajya Sabha and shall not hold any other office of profit.",tags:["imp","VP","Parliament"]},
    {n:"72",t:"President's power to grant pardon",d:"The President may grant pardons, reprieves, respites or remissions of punishment in all cases involving a Union law, a death sentence, or court-martial.",tags:["imp","President","pardon"]},
    {n:"74",t:"Council of Ministers to aid President",d:"There shall be a Council of Ministers with the Prime Minister at the head to aid and advise the President, who shall act in accordance with such advice. The President may return advice for reconsideration once.",tags:["imp","PM","cabinet"]},
    {n:"75",t:"Other provisions as to Ministers",d:"The PM shall be appointed by the President; other Ministers appointed on PM's advice. Ministers hold office during the pleasure of the President and are collectively responsible to Lok Sabha.",tags:["imp","PM","cabinet"]},
    {n:"76",t:"Attorney-General of India",d:"The President shall appoint a person qualified to be a Judge of the Supreme Court as Attorney-General. The AG shall have audience in all courts in India.",tags:["imp","AG"]},
    {n:"79",t:"Constitution of Parliament",d:"There shall be a Parliament consisting of the President and two Houses — the Council of States (Rajya Sabha) and the House of the People (Lok Sabha).",tags:["imp","Parliament"]},
    {n:"80",t:"Composition of Rajya Sabha",d:"Maximum 250 members: 12 nominated by President for distinguished service in literature, science, art, and social service + 238 representatives of States and UTs.",tags:["imp","Parliament"]},
    {n:"81",t:"Composition of Lok Sabha",d:"Maximum 552 members: up to 530 from States + up to 20 from UTs + 2 nominated Anglo-Indians (provision abolished by 104th Amendment 2019). All directly elected by adult suffrage.",tags:["imp","Parliament"]},
    {n:"83",t:"Duration of Houses of Parliament",d:"Rajya Sabha is a permanent body with 1/3 members retiring every 2 years. Lok Sabha's normal term is 5 years, extendable during National Emergency.",tags:["imp","Parliament"]},
    {n:"108",t:"Joint sitting of both Houses",d:"In case of a deadlock on a bill (not Money Bills or Constitution Amendment Bills), the President may summon a joint sitting. Only 3 joint sittings held so far.",tags:["imp","Parliament"]},
    {n:"109",t:"Special procedure for Money Bills",d:"A Money Bill shall not be introduced in Rajya Sabha. Rajya Sabha has 14 days to return it with recommendations. If not returned in 14 days, deemed passed.",tags:["imp","Parliament"]},
    {n:"110",t:"Definition of Money Bill",d:"A Bill is a Money Bill if it deals solely with imposition or abolition of taxes, regulation of borrowing, custody of Consolidated Fund, appropriation of money, or expenditure charged on Consolidated Fund. Speaker's certificate is final.",tags:["imp","Parliament"]},
    {n:"112",t:"Annual Financial Statement (Budget)",d:"The President shall cause to be laid before both Houses a statement of estimated receipts and expenditure for each financial year — the Union Budget.",tags:["imp","Parliament"]},
    {n:"123",t:"President's Ordinance-making power",d:"When Parliament is not in session, the President may promulgate Ordinances if immediate action is necessary. Must be laid before Parliament and ceases after 6 weeks of reassembly.",tags:["imp","President","ordinance"]},
    {n:"124",t:"Establishment of Supreme Court",d:"There shall be a Supreme Court of India consisting of a Chief Justice and not more than 33 other Judges.",tags:["imp","SC","judiciary"]},
    {n:"131",t:"Original jurisdiction of SC",d:"The Supreme Court has exclusive original jurisdiction in disputes between: (a) Government of India and one or more States; (b) two or more States.",tags:["imp","SC","jurisdiction"]},
    {n:"136",t:"Special Leave Petition",d:"The Supreme Court may grant special leave to appeal from any judgment, decree, or order passed by any court or tribunal in India (except Armed Forces courts).",tags:["imp","SC","jurisdiction"]},
    {n:"141",t:"Law declared by SC is binding",d:"The law declared by the Supreme Court shall be binding on all courts within the territory of India.",tags:["imp","SC"]},
    {n:"143",t:"Advisory jurisdiction of SC",d:"If any question of law or fact of public importance has arisen, the President may refer it to the Supreme Court for its opinion.",tags:["imp","SC","President"]},
    {n:"148",t:"Comptroller and Auditor-General",d:"There shall be a CAG appointed by the President. Can be removed only in the same manner as a Supreme Court judge.",tags:["imp","CAG"]},
  ]},
  {p:"Part VI",pf:"Part VI — The States (Articles 152–237)",arts:[
    {n:"153",t:"Governors of States",d:"There shall be a Governor for each State. One person can be Governor of two or more States.",tags:["imp","Governor","State"]},
    {n:"155",t:"Appointment of Governor",d:"The Governor shall be appointed by the President by warrant. Not elected — nominated by the Central Government.",tags:["imp","Governor"]},
    {n:"156",t:"Term of Governor",d:"The Governor holds office during the pleasure of the President. Normal term is 5 years. Can be removed any time.",tags:["imp","Governor"]},
    {n:"161",t:"Governor's pardon power",d:"The Governor may grant pardons in all cases where punishment is for a State law offence — except death sentence (President's power) and court-martial.",tags:["imp","Governor","pardon"]},
    {n:"163",t:"Council of Ministers to aid Governor",d:"There shall be a Council of Ministers with the Chief Minister as head to aid and advise the Governor, who acts in accordance with such advice except in matters requiring his discretion.",tags:["imp","CM","State"]},
    {n:"168",t:"Constitution of State Legislatures",d:"For every State there shall be a Legislature consisting of the Governor and one or two Houses. States with bicameral legislature: Andhra Pradesh, Telangana, Karnataka, Maharashtra, Bihar, Uttar Pradesh, J&K.",tags:["imp","State Legislature"]},
    {n:"200",t:"Assent to Bills",d:"When a Bill is presented to the Governor, he may: (a) give assent; (b) withhold assent; (c) return the Bill (except Money Bills); (d) reserve it for the President's consideration.",tags:["imp","Governor"]},
    {n:"213",t:"Governor's Ordinance power",d:"When the State Legislature is not in session, the Governor may promulgate Ordinances as required. Must be approved by the Legislature within 6 weeks of reassembly.",tags:["imp","Governor","ordinance"]},
    {n:"214",t:"High Courts for States",d:"There shall be a High Court for each State. Parliament may establish a common High Court for two or more States.",tags:["imp","HC","judiciary"]},
    {n:"226",t:"Power of HC to issue writs",d:"The High Court may issue writs — habeas corpus, mandamus, prohibition, quo warranto and certiorari — for enforcement of Fundamental Rights and for any other purpose.",tags:["imp","HC","writs","judiciary"]},
    {n:"227",t:"HC superintendence over lower courts",d:"Every High Court shall have superintendence over all courts and tribunals throughout the territories in relation to which it exercises jurisdiction.",tags:["imp","HC","judiciary"]},
  ]},
  {p:"Part VIII",pf:"Part VIII — Union Territories (Articles 239–242)",arts:[
    {n:"239",t:"Administration of Union Territories",d:"Every Union territory shall be administered by the President acting through an administrator appointed by him.",tags:["imp","UT"]},
    {n:"239AA",t:"Special provisions for Delhi",d:"Delhi is administered as a UT with its own Legislature and Council of Ministers. However, matters relating to public order, police and land are subject to the Lieutenant Governor.",tags:["imp","UT","Delhi"]},
  ]},
  {p:"Part IX",pf:"Part IX — Panchayats (Articles 243–243O)",arts:[
    {n:"243A",t:"Gram Sabha",d:"A Gram Sabha may exercise such powers and perform such functions at the village level as the State Legislature may by law provide.",tags:["imp","Panchayat"]},
    {n:"243B",t:"Constitution of Panchayats",d:"There shall be Panchayats at the village, intermediate and district levels. Added by 73rd Constitutional Amendment 1992.",tags:["imp","Panchayat"]},
    {n:"243D",t:"Reservation of seats in Panchayats",d:"Seats shall be reserved for SC/ST in proportion to their population. Not less than 1/3rd seats shall be reserved for women.",tags:["imp","Panchayat","reservation"]},
  ]},
  {p:"Part IXA",pf:"Part IX-A — Municipalities (Articles 243P–243ZG)",arts:[
    {n:"243Q",t:"Constitution of Municipalities",d:"There shall be a Nagar Panchayat for transitional areas, a Municipal Council for smaller urban areas, and a Municipal Corporation for larger urban areas. Added by 74th Amendment 1992.",tags:["imp","Municipalities"]},
    {n:"243T",t:"Reservation in Municipalities",d:"Seats shall be reserved for SC/ST in proportion to population. Not less than 1/3rd seats shall be reserved for women.",tags:["imp","Municipalities","reservation"]},
  ]},
  {p:"Part XI",pf:"Part XI — Relations between Union and States (Articles 245–263)",arts:[
    {n:"245",t:"Extent of laws — Parliament and States",d:"Parliament may make laws for the whole or any part of India; a State Legislature may make laws for the whole or any part of the State only.",tags:["imp","Centre-State"]},
    {n:"246",t:"Subject matter of legislation — three lists",d:"Parliament has exclusive power over Union List (97 subjects); Parliament and States can both legislate on Concurrent List (47 subjects); States have exclusive power over State List (66 subjects). Residuary power with Parliament.",tags:["imp","Centre-State"]},
    {n:"249",t:"Parliament to legislate on State List",d:"If Rajya Sabha passes a resolution by 2/3 majority that it is necessary in the national interest, Parliament may legislate on any State List matter for 1 year (extendable).",tags:["imp","Centre-State"]},
    {n:"250",t:"Parliament to legislate during emergency",d:"While a National Emergency is in operation, Parliament shall have power to make laws for any part of India on any subject in the State List.",tags:["imp","Centre-State","Emergency"]},
  ]},
  {p:"Part XII",pf:"Part XII — Finance, Property and Contracts (Articles 264–300A)",arts:[
    {n:"265",t:"Taxes only by authority of law",d:"No tax shall be levied or collected except by authority of law. A fundamental guarantee against arbitrary taxation.",tags:["imp","Finance"]},
    {n:"266",t:"Consolidated Funds",d:"All revenues received by the Government of India, all loans raised, and all money received in repayment of loans shall form the Consolidated Fund of India.",tags:["imp","Finance"]},
    {n:"280",t:"Finance Commission",d:"The President shall constitute a Finance Commission within 2 years of commencement and thereafter every 5 years. Recommends distribution of taxes between Centre and States.",tags:["imp","Finance"]},
    {n:"300A",t:"Right to property",d:"No person shall be deprived of his property save by authority of law. Moved from Fundamental Rights to a mere constitutional right by the 44th Amendment 1978.",tags:["imp","Property"]},
  ]},
  {p:"Part XV",pf:"Part XV — Elections (Articles 324–329)",arts:[
    {n:"324",t:"Superintendence vested in Election Commission",d:"The superintendence, direction and control of elections to Parliament, State Legislatures, and offices of President and Vice-President shall be vested in the Election Commission.",tags:["imp","Election","EC"]},
    {n:"325",t:"No discrimination in electoral rolls",d:"There shall be one general electoral roll for every territorial constituency. No person shall be ineligible on grounds of religion, race, caste or sex.",tags:["imp","Election"]},
    {n:"326",t:"Adult suffrage",d:"Elections to Lok Sabha and State Legislative Assemblies shall be on the basis of adult suffrage; every citizen not less than 18 years of age shall be entitled to vote.",tags:["imp","Election"]},
  ]},
  {p:"Part XVI",pf:"Part XVI — Special Provisions (Articles 330–342A)",arts:[
    {n:"330",t:"Reservation for SC/ST in Lok Sabha",d:"Seats shall be reserved in the House of the People for Scheduled Castes and Scheduled Tribes. Reservation was initially for 10 years, extended repeatedly.",tags:["imp","Reservation","SC/ST"]},
    {n:"338",t:"National Commission for SC",d:"There shall be a National Commission for Scheduled Castes to investigate and monitor all matters relating to safeguards provided for Scheduled Castes.",tags:["imp","SC/ST"]},
    {n:"338A",t:"National Commission for ST",d:"There shall be a National Commission for Scheduled Tribes to investigate and monitor all matters relating to safeguards for Scheduled Tribes.",tags:["imp","SC/ST"]},
  ]},
  {p:"Part XVII",pf:"Part XVII — Official Language (Articles 343–351)",arts:[
    {n:"343",t:"Official language of the Union",d:"The official language of the Union shall be Hindi in Devanagari script. English was permitted for 15 years (until 1965); Parliament extended its use indefinitely.",tags:["imp","Language"]},
    {n:"351",t:"Directive for development of Hindi",d:"It shall be the duty of the Union to promote the spread of Hindi so that it may serve as a medium of expression for all elements of the composite culture of India.",tags:["imp","Language"]},
  ]},
  {p:"Part XVIII",pf:"Part XVIII — Emergency Provisions (Articles 352–360)",arts:[
    {n:"352",t:"National Emergency",d:"The President may proclaim a National Emergency if security of India is threatened by war, external aggression, or armed rebellion. Cabinet must recommend in writing. Approved by special majority of Parliament within one month.",tags:["imp","Emergency"]},
    {n:"355",t:"Duty of Union to protect States",d:"It shall be the duty of the Union to protect every State against external aggression and internal disturbance and to ensure every State government is carried on in accordance with the Constitution.",tags:["imp","Emergency"]},
    {n:"356",t:"President's Rule",d:"If the President is satisfied that the government of a State cannot be carried on in accordance with the Constitution, he may proclaim President's Rule. Must be approved by Parliament within 2 months.",tags:["imp","Emergency"]},
    {n:"360",t:"Financial Emergency",d:"The President may proclaim a Financial Emergency if the financial stability or credit of India or any part thereof is threatened. Never proclaimed in India.",tags:["imp","Emergency"]},
  ]},
  {p:"Part XX",pf:"Part XX — Amendment of the Constitution (Article 368)",arts:[
    {n:"368",t:"Power to amend the Constitution",d:"Parliament may amend by addition, variation or repeal any provision of the Constitution. Types: (1) Simple majority; (2) Special majority — 2/3 present and voting + majority of total membership; (3) Special majority + ratification by at least half the State Legislatures.",tags:["imp","Amendment"]},
  ]},
  {p:"Part XXI",pf:"Part XXI — Temporary, Transitional and Special Provisions",arts:[
    {n:"370",t:"Special status of J&K (now abrogated)",d:"Provided special autonomous status to Jammu & Kashmir. Abrogated on August 5, 2019. J&K was bifurcated into two UTs: J&K (with Legislature) and Ladakh (without Legislature).",tags:["imp","J&K","Special"]},
    {n:"371A",t:"Special provisions for Nagaland",d:"No Act of Parliament on religious or social practices of the Nagas, Naga customary law and procedure, etc., shall apply to Nagaland unless its Legislative Assembly so decides.",tags:["imp","Special","Northeast"]},
    {n:"371G",t:"Special provisions for Mizoram",d:"No Act of Parliament on religious or social practices of Mizo, Mizo customary law and procedure, etc., shall apply to Mizoram unless its Legislative Assembly so decides.",tags:["imp","Special","Northeast"]},
  ]},
  {p:"Part XXII",pf:"Part XXII — Short Title and Commencement (Articles 393–395)",arts:[
    {n:"394",t:"Commencement",d:"Most provisions came into force on January 26, 1950 — celebrated as Republic Day. Some provisions came into force on November 26, 1949.",tags:["imp","basics"]},
    {n:"395",t:"Repeals",d:"The Indian Independence Act 1947 and the Government of India Act 1935, together with all Schedules and amendments, are hereby repealed.",tags:["basics"]},
  ]},
];

// ── STATE ──────────────────────────────────────────────────────────────────
let mem={},bks={},filt='all',sideOn=true,dark=false;
try{mem=JSON.parse(localStorage.getItem('iq_mem')||'{}');}catch(e){}
try{bks=JSON.parse(localStorage.getItem('iq_bk')||'{}');}catch(e){}

function save(){
  localStorage.setItem('iq_mem',JSON.stringify(mem));
  localStorage.setItem('iq_bk',JSON.stringify(bks));
  syncStrip();
}

function syncStrip(){
  const tm=Object.values(mem).filter(Boolean).length;
  const tb=Object.values(bks).filter(Boolean).length;
  const em=document.getElementById('s-mem'),eb=document.getElementById('s-bk');
  if(em)em.textContent=tm+' Memorised';
  if(eb)eb.textContent=tb+' Bookmarked';
}

function countdown(){
  const now=new Date();
  let d=new Date(now.getFullYear(),4,25);
  if(d<now)d.setFullYear(now.getFullYear()+1);
  const el=document.getElementById('cdown');
  if(el)el.textContent=Math.ceil((d-now)/86400000);
}

// ── NAV ────────────────────────────────────────────────────────────────────
function goto(p){
  ['dashboard','polity','exams'].forEach(x=>{
    const el=document.getElementById('pg-'+x);
    if(el)el.style.display=x===p?'block':'none';
  });
  document.querySelectorAll('.s-item').forEach(e=>e.classList.remove('on'));
  const n=document.getElementById('nav-'+p);
  if(n)n.classList.add('on');
  document.getElementById('bctext').textContent=p[0].toUpperCase()+p.slice(1);
  if(p==='polity'){syncStrip();renderPolity();}
}

function toggleSidebar(){
  sideOn=!sideOn;
  const sb=document.getElementById('sidebar'),btn=document.getElementById('stoggle'),main=document.getElementById('main');
  const mob=window.innerWidth<=960;
  if(mob){sb.classList.toggle('vis',sideOn);}
  else{sb.classList.toggle('off',!sideOn);main.classList.toggle('wide',!sideOn);}
  btn.classList.toggle('off',!sideOn);
}

function toggleDark(){
  dark=!dark;
  dark?document.body.setAttribute('data-dark','1'):document.body.removeAttribute('data-dark');
  document.getElementById('dlabel').textContent=dark?'Light Mode':'Dark Mode';
}

// ── POLITY ─────────────────────────────────────────────────────────────────
function setFilter(el,f){
  filt=f;
  document.querySelectorAll('.chip').forEach(c=>c.classList.remove('on'));
  el.classList.add('on');
  renderPolity();
}

function renderPolity(){
  const q=(document.getElementById('psearch')?.value||'').toLowerCase().trim();
  let html='',tot=0;
  for(const part of DATA){
    const arts=part.arts.filter(a=>{
      const mq=!q||a.n.toLowerCase().includes(q)||a.t.toLowerCase().includes(q)||a.d.toLowerCase().includes(q)||part.pf.toLowerCase().includes(q);
      return mq&&(filt==='all'||a.tags.includes(filt));
    });
    if(!arts.length)continue;
    tot+=arts.length;
    const name=part.pf.replace(part.p+' — ','');
    html+=`<div class="part-block">
      <div class="part-label"><span class="ptag">${part.p}</span>${name}</div>
      <div class="agrid">${arts.map(buildCard).join('')}</div>
    </div>`;
  }
  if(!tot)html=`<div class="empty-state"><svg width="44" height="44" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg><div>No articles match your search.</div></div>`;
  document.getElementById('polity-content').innerHTML=html;
  document.getElementById('s-total').textContent=tot+' Articles';
}

function buildCard(a){
  const im=!!mem[a.n],ib=!!bks[a.n];
  return `<div class="ac ${im?'mem':ib?'bk':''}" id="ac-${a.n}">
    <div class="an">Art. ${a.n}</div>
    <div class="at">${a.t}</div>
    <div class="ad">${a.d}</div>
    <div class="atags">${a.tags.map(t=>`<span class="atag ${t==='imp'?'imp':''}">${t}</span>`).join('')}</div>
    <div class="abtns">
      <button class="abtn ${im?'mem-on':''}" onclick="toggleMem('${a.n}',event)">${im?'✓ Memorised':'Memorise'}</button>
      <button class="abtn ${ib?'bk-on':''}" onclick="toggleBk('${a.n}',event)">${ib?'★ Saved':'Bookmark'}</button>
      <button class="abtn" onclick="openModal('${a.n}')">Details</button>
    </div>
  </div>`;
}

function toggleMem(n,e){e.stopPropagation();mem[n]=!mem[n];if(!mem[n])delete mem[n];save();renderPolity();}
function toggleBk(n,e){e.stopPropagation();bks[n]=!bks[n];if(!bks[n])delete bks[n];save();renderPolity();}

// ── MODAL ──────────────────────────────────────────────────────────────────
function openModal(n){
  const a=DATA.flatMap(p=>p.arts).find(x=>x.n===n);
  if(!a)return;
  document.getElementById('m-num').textContent='Article '+a.n;
  document.getElementById('m-title').textContent=a.t;
  document.getElementById('m-desc').textContent=a.d;
  document.getElementById('m-tags').innerHTML=a.tags.map(t=>`<span class="atag ${t==='imp'?'imp':''}">${t}</span>`).join('');
  const im=!!mem[a.n],ib=!!bks[a.n];
  document.getElementById('m-btns').innerHTML=`
    <button class="abtn ${im?'mem-on':''}" onclick="toggleMem('${a.n}',{stopPropagation:()=>{}})">${im?'✓ Memorised':'Memorise'}</button>
    <button class="abtn ${ib?'bk-on':''}" onclick="toggleBk('${a.n}',{stopPropagation:()=>{}})">${ib?'★ Saved':'Bookmark'}</button>`;
  document.getElementById('modal').classList.add('open');
}
function closeModal(){document.getElementById('modal').classList.remove('open');}
function maybeClose(e){if(e.target===document.getElementById('modal'))closeModal();}
document.addEventListener('keydown',e=>{if(e.key==='Escape')closeModal();});

countdown();syncStrip();
</script>

</body>
</html>
