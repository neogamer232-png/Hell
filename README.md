<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ConstitutionIQ — UPSC Polity Dashboard</title>
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@300;400;500;600;700&family=Lora:ital,wght@0,500;0,600;1,400&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;}
:root{
  --bg:#F0EDE8;
  --sidebar:#151210;
  --sidebar-text:#A09890;
  --sidebar-active:#fff;
  --accent:#E8380D;
  --accent2:#FF6B3D;
  --card:#FFFFFF;
  --text:#1A1410;
  --text2:#7A746E;
  --text3:#B0AAA4;
  --border:#E8E3DC;
  --green:#1A7A4A;
  --green-bg:#E8F5EE;
  --blue-bg:#EBF2FB;
  --amber-bg:#FDF3E3;
  --font:'Sora',sans-serif;
  --font-serif:'Lora',serif;
}
[data-dark]{
  --bg:#0F0D0B;
  --card:#1C1916;
  --text:#F5F0EA;
  --text2:#A09890;
  --text3:#5A5450;
  --border:#2A2520;
  --green-bg:#0A2A1A;
  --blue-bg:#0A1525;
  --amber-bg:#1A1205;
}
body{font-family:var(--font);background:var(--bg);color:var(--text);display:flex;min-height:100vh;transition:background .3s,color .3s;}
/* SIDEBAR */
.sidebar{width:220px;min-height:100vh;background:var(--sidebar);display:flex;flex-direction:column;position:fixed;left:0;top:0;bottom:0;z-index:100;transition:transform .3s;}
.sidebar.collapsed{transform:translateX(-220px);}
.sidebar-logo{padding:20px 20px 16px;display:flex;align-items:center;gap:10px;border-bottom:1px solid #252220;}
.logo-icon{width:30px;height:30px;background:var(--accent);border-radius:8px;display:flex;align-items:center;justify-content:center;}
.logo-icon svg{width:18px;height:18px;fill:#fff;}
.logo-text{font-size:15px;font-weight:700;color:#fff;letter-spacing:-.3px;}
.sidebar-section{padding:14px 12px 8px;font-size:10px;font-weight:600;color:#4A4440;letter-spacing:1.2px;text-transform:uppercase;}
.nav-item{display:flex;align-items:center;gap:10px;padding:9px 14px;margin:1px 8px;border-radius:8px;cursor:pointer;color:var(--sidebar-text);font-size:13px;font-weight:500;transition:all .15s;text-decoration:none;}
.nav-item:hover{background:#252220;color:#D0C8C0;}
.nav-item.active{background:#252220;color:#fff;}
.nav-item .nav-icon{width:18px;height:18px;opacity:.7;flex-shrink:0;}
.nav-item.active .nav-icon{opacity:1;}
.nav-badge{margin-left:auto;background:var(--accent);color:#fff;font-size:10px;font-weight:600;padding:2px 6px;border-radius:20px;}
.sidebar-bottom{margin-top:auto;border-top:1px solid #252220;padding:10px 8px;}
.main{margin-left:220px;flex:1;padding:28px 32px;transition:margin .3s;min-height:100vh;}
.main.expanded{margin-left:0;}
/* TOP BAR */
.topbar{display:flex;align-items:center;justify-content:space-between;margin-bottom:28px;}
.topbar-left{display:flex;align-items:center;gap:12px;}
.breadcrumb{display:flex;align-items:center;gap:6px;font-size:13px;color:var(--text2);}
.breadcrumb-home{width:28px;height:28px;background:var(--card);border:1px solid var(--border);border-radius:8px;display:flex;align-items:center;justify-content:center;cursor:pointer;}
.mode-badge{display:flex;align-items:center;gap:7px;background:var(--card);border:1px solid var(--border);border-radius:20px;padding:6px 14px;font-size:13px;font-weight:500;cursor:pointer;transition:all .15s;}
.mode-badge:hover{border-color:#ccc;}
.mode-dot{width:7px;height:7px;border-radius:50%;background:var(--accent);animation:pulse 1.5s infinite;}
@keyframes pulse{0%,100%{opacity:1;}50%{opacity:.4;}}
.topbar-right{display:flex;align-items:center;gap:10px;}
.topbar-avatar{width:36px;height:36px;border-radius:50%;background:linear-gradient(135deg,var(--accent),var(--accent2));display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:700;color:#fff;cursor:pointer;}
/* HERO */
.hero-greeting{font-family:var(--font-serif);font-size:42px;font-weight:600;color:var(--text);letter-spacing:-.5px;margin-bottom:24px;line-height:1.1;}
.hero-greeting span{color:var(--accent);}
/* GRID */
.grid-2{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:16px;}
.grid-4{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;margin-bottom:16px;}
.grid-2b{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:24px;}
/* CARDS */
.card{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:20px 22px;transition:border-color .15s;}
.card:hover{border-color:#D0C8C0;}
.card-label{display:flex;align-items:center;gap:7px;font-size:12px;font-weight:600;color:var(--text2);margin-bottom:14px;}
.card-label-dot{width:8px;height:8px;border-radius:50%;}
.dot-red{background:var(--accent);}
.dot-blue{background:#378ADD;}
/* FOCUS CARD */
.focus-card{position:relative;overflow:hidden;}
.focus-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:6px;}
.focus-pct{display:flex;align-items:center;gap:6px;font-size:13px;font-weight:600;}
.focus-pct-num{font-size:22px;font-weight:700;color:var(--text);}
.waveform{display:flex;align-items:center;gap:2px;height:28px;}
.waveform span{display:block;width:3px;border-radius:2px;background:var(--green);animation:wave 1s ease-in-out infinite;}
.waveform span:nth-child(1){height:8px;animation-delay:0s;}
.waveform span:nth-child(2){height:18px;animation-delay:.1s;}
.waveform span:nth-child(3){height:24px;animation-delay:.2s;}
.waveform span:nth-child(4){height:14px;animation-delay:.3s;}
.waveform span:nth-child(5){height:20px;animation-delay:.4s;}
.waveform span:nth-child(6){height:10px;animation-delay:.5s;}
.waveform span:nth-child(7){height:22px;animation-delay:.6s;}
.waveform span:nth-child(8){height:16px;animation-delay:.7s;}
.waveform span:nth-child(9){height:8px;animation-delay:.3s;background:#D0D0D0;}
.waveform span:nth-child(10){height:12px;animation-delay:.1s;background:#D0D0D0;}
.waveform span:nth-child(11){height:18px;animation-delay:.5s;background:#D0D0D0;}
.waveform span:nth-child(12){height:6px;animation-delay:.2s;background:#D0D0D0;}
@keyframes wave{0%,100%{transform:scaleY(1);}50%{transform:scaleY(.6);}}
.focus-title{font-size:20px;font-weight:700;color:var(--text);margin:14px 0 6px;}
.focus-sub{font-size:13px;color:var(--text2);line-height:1.5;margin-bottom:18px;}
.btn-primary{background:var(--accent);color:#fff;border:none;border-radius:10px;padding:11px 22px;font-family:var(--font);font-size:13px;font-weight:600;cursor:pointer;transition:all .15s;}
.btn-primary:hover{background:#C42F08;transform:translateY(-1px);}
/* PROGRESS CARD */
.progress-stats{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-top:10px;}
.pstat{background:var(--bg);border-radius:12px;padding:14px 16px;text-align:center;transition:background .3s;}
.pstat-label{font-size:11px;color:var(--text3);margin-bottom:8px;font-weight:500;}
.pstat-val{font-size:28px;font-weight:700;color:var(--text);}
.pstat-val.green{background:var(--green-bg);border-radius:8px;padding:4px 8px;color:var(--green);}
.pstat-val.blue{background:var(--blue-bg);border-radius:8px;padding:4px 8px;color:#185FA5;}
.pstat-val.amber{background:var(--amber-bg);border-radius:8px;padding:4px 8px;color:#BA7517;}
/* MINI CARDS */
.mini-card{background:var(--card);border:1px solid var(--border);border-radius:14px;padding:16px 18px;}
.mini-label{display:flex;align-items:center;gap:6px;font-size:12px;font-weight:600;color:var(--text2);margin-bottom:12px;}
.mini-val{font-size:26px;font-weight:700;color:var(--text);}
.mini-sub{font-size:11px;color:var(--text3);margin-top:4px;}
/* PRACTICE MODE CARD */
.practice-card{background:linear-gradient(135deg,var(--accent) 0%,#FF8050 100%);border-radius:16px;padding:22px 22px;display:flex;flex-direction:column;justify-content:space-between;min-height:110px;}
.practice-title{font-size:18px;font-weight:700;color:#fff;margin-bottom:8px;}
.practice-sub{font-size:12px;color:rgba(255,255,255,.75);line-height:1.5;}
.btn-white{background:#fff;color:var(--accent);border:none;border-radius:10px;padding:9px 18px;font-family:var(--font);font-size:12px;font-weight:700;cursor:pointer;margin-top:14px;width:fit-content;transition:all .15s;}
.btn-white:hover{background:#FFF0EC;}
/* SECTION DIVIDER */
.section-head{display:flex;align-items:center;justify-content:space-between;margin:32px 0 18px;}
.section-title{font-family:var(--font-serif);font-size:24px;font-weight:600;color:var(--text);}
.section-badge{background:var(--accent);color:#fff;font-size:11px;font-weight:700;padding:3px 10px;border-radius:20px;margin-left:10px;}
.section-actions{display:flex;gap:8px;}
.filter-chip{background:var(--card);border:1px solid var(--border);border-radius:20px;padding:6px 14px;font-size:12px;font-weight:500;cursor:pointer;color:var(--text2);transition:all .15s;}
.filter-chip.on,.filter-chip:hover{background:var(--sidebar);color:#fff;border-color:var(--sidebar);}
/* PARTS */
.part-block{margin-bottom:28px;}
.part-label{font-size:11px;font-weight:700;color:var(--text3);text-transform:uppercase;letter-spacing:1.2px;margin-bottom:10px;display:flex;align-items:center;gap:8px;}
.part-label::after{content:'';flex:1;height:1px;background:var(--border);}
.part-num{background:var(--sidebar);color:#fff;font-size:10px;font-weight:700;padding:2px 8px;border-radius:20px;}
/* ARTICLE CARDS */
.articles-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:10px;}
.art-card{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:14px 16px;cursor:pointer;transition:all .2s;position:relative;overflow:hidden;}
.art-card::before{content:'';position:absolute;left:0;top:0;bottom:0;width:3px;background:transparent;border-radius:0 2px 2px 0;transition:background .15s;}
.art-card:hover{border-color:#C8C0B8;transform:translateY(-1px);box-shadow:0 4px 16px rgba(0,0,0,.06);}
.art-card:hover::before{background:var(--accent);}
.art-card.mem::before{background:var(--green);}
.art-card.bk::before{background:#E8B200;}
.art-num-badge{font-size:10px;font-weight:700;color:var(--accent);letter-spacing:.5px;margin-bottom:5px;}
.art-title{font-size:13px;font-weight:600;color:var(--text);line-height:1.4;margin-bottom:8px;}
.art-desc{font-size:11px;color:var(--text2);line-height:1.55;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden;}
.art-desc.expanded{-webkit-line-clamp:unset;}
.art-tags{display:flex;gap:4px;flex-wrap:wrap;margin:8px 0 10px;}
.a-tag{font-size:10px;padding:2px 7px;border-radius:20px;background:var(--bg);color:var(--text3);font-weight:500;border:1px solid var(--border);}
.a-tag.imp{background:#FFF0EC;color:#C42F08;border-color:#FFCAB8;}
.art-btns{display:flex;gap:6px;}
.a-btn{font-size:10px;padding:4px 9px;border-radius:7px;border:1px solid var(--border);cursor:pointer;background:transparent;color:var(--text2);font-family:var(--font);font-weight:500;transition:all .15s;}
.a-btn:hover{background:var(--bg);}
.a-btn.g{background:#E8F5EE;color:#1A7A4A;border-color:#C0DFC8;}
.a-btn.y{background:#FFF8E0;color:#A07A00;border-color:#FFE080;}
/* SEARCH */
.search-wrap{position:relative;margin-bottom:16px;}
.search-wrap input{width:100%;height:40px;border:1px solid var(--border);border-radius:10px;padding:0 16px 0 38px;font-family:var(--font);font-size:13px;background:var(--card);color:var(--text);outline:none;transition:border .15s;}
.search-wrap input:focus{border-color:#B0A8A0;}
.search-icon{position:absolute;left:12px;top:50%;transform:translateY(-50%);opacity:.4;pointer-events:none;}
/* STATS STRIP */
.stats-strip{display:flex;gap:8px;margin-bottom:20px;flex-wrap:wrap;}
.strip-stat{background:var(--card);border:1px solid var(--border);border-radius:10px;padding:8px 14px;font-size:12px;font-weight:600;display:flex;align-items:center;gap:6px;color:var(--text);}
.strip-dot{width:7px;height:7px;border-radius:50%;}
/* MODAL */
.modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,.5);z-index:500;display:flex;align-items:center;justify-content:center;opacity:0;pointer-events:none;transition:opacity .2s;}
.modal-overlay.open{opacity:1;pointer-events:auto;}
.modal{background:var(--card);border-radius:20px;padding:28px 30px;max-width:520px;width:90%;max-height:80vh;overflow-y:auto;transform:translateY(20px);transition:transform .2s;}
.modal-overlay.open .modal{transform:translateY(0);}
.modal-artnum{font-size:12px;font-weight:700;color:var(--accent);margin-bottom:4px;letter-spacing:.5px;}
.modal-title{font-family:var(--font-serif);font-size:22px;font-weight:600;color:var(--text);margin-bottom:14px;line-height:1.3;}
.modal-desc{font-size:14px;color:var(--text2);line-height:1.7;margin-bottom:18px;}
.modal-btns{display:flex;gap:8px;flex-wrap:wrap;}
.close-btn{position:absolute;top:20px;right:22px;background:var(--bg);border:1px solid var(--border);border-radius:8px;width:32px;height:32px;cursor:pointer;font-size:18px;color:var(--text2);display:flex;align-items:center;justify-content:center;}
.modal{position:relative;}
/* TOOLTIP */
.tooltip{position:relative;}
.tooltip:hover .ttip{opacity:1;}
.ttip{position:absolute;bottom:110%;left:50%;transform:translateX(-50%);background:#1A1410;color:#fff;font-size:11px;white-space:nowrap;padding:4px 8px;border-radius:6px;opacity:0;pointer-events:none;transition:opacity .15s;z-index:200;}
/* RESPONSIVE */
@media(max-width:900px){
  .sidebar{transform:translateX(-220px);}
  .main{margin-left:0;}
  .grid-2,.grid-4,.grid-2b{grid-template-columns:1fr;}
  .progress-stats{grid-template-columns:1fr 1fr 1fr;}
}
/* SCROLLBAR */
::-webkit-scrollbar{width:5px;height:5px;}
::-webkit-scrollbar-track{background:transparent;}
::-webkit-scrollbar-thumb{background:#C8C0B8;border-radius:10px;}
/* TOGGLE */
.sidebar-toggle{position:fixed;left:228px;top:20px;z-index:200;background:var(--card);border:1px solid var(--border);border-radius:8px;width:28px;height:28px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:left .3s;box-shadow:0 2px 8px rgba(0,0,0,.1);}
.sidebar-toggle.out{left:8px;}
/* EXAM COUNTDOWN */
.countdown-ring{display:flex;align-items:center;gap:12px;margin-top:4px;}
.ring-svg{transform:rotate(-90deg);}
</style>
</head>
<body>
<!-- SIDEBAR -->
<aside class="sidebar" id="sidebar">
  <div class="sidebar-logo">
    <div class="logo-icon"><svg viewBox="0 0 24 24"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg></div>
    <span class="logo-text">ConstitutionIQ</span>
  </div>
  <div style="padding:8px 0;overflow-y:auto;flex:1;">
    <div class="sidebar-section">Main</div>
    <a class="nav-item active" onclick="showPage('dashboard')">
      <svg class="nav-icon" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/></svg>
      Dashboard
    </a>
    <a class="nav-item" onclick="showPage('polity')">
      <svg class="nav-icon" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M12 3L3 9v12h6v-6h6v6h6V9z"/></svg>
      Polity
      <span class="nav-badge">NEW</span>
    </a>
    <a class="nav-item" onclick="showPage('exams')">
      <svg class="nav-icon" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M9 11l3 3L22 4"/><path d="M21 12v7a2 2 0 01-2 2H5a2 2 0 01-2-2V5a2 2 0 012-2h11"/></svg>
      Exams
    </a>
    <a class="nav-item">
      <svg class="nav-icon" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>
      Practice Mode
    </a>
    <a class="nav-item">
      <svg class="nav-icon" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M4 19.5A2.5 2.5 0 016.5 17H20"/><path d="M6.5 2H20v20H6.5A2.5 2.5 0 014 19.5v-15A2.5 2.5 0 016.5 2z"/></svg>
      Textbooks
    </a>
    <a class="nav-item">
      <svg class="nav-icon" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 00-4-4H5a4 4 0 00-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 00-3-3.87M16 3.13a4 4 0 010 7.75"/></svg>
      All Courses
    </a>
    <a class="nav-item">
      <svg class="nav-icon" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M21 15a2 2 0 01-2 2H7l-4 4V5a2 2 0 012-2h14a2 2 0 012 2z"/></svg>
      Message Center
    </a>
    <div class="sidebar-section">Settings</div>
    <a class="nav-item" id="dark-toggle" onclick="toggleDark()">
      <svg class="nav-icon" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M21 12.79A9 9 0 1111.21 3 7 7 0 0021 12.79z"/></svg>
      Dark Mode
    </a>
    <a class="nav-item">
      <svg class="nav-icon" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="3"/><path d="M19.07 4.93L4.93 19.07M19.07 19.07L4.93 4.93"/></svg>
      Help
    </a>
  </div>
  <div class="sidebar-bottom">
    <a class="nav-item" onclick="toggleSidebar()">
      <svg class="nav-icon" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M3 12h18M3 6h18M3 18h18"/></svg>
      Hide Sidebar
    </a>
  </div>
</aside>

<!-- SIDEBAR TOGGLE -->
<button class="sidebar-toggle" id="sb-toggle" onclick="toggleSidebar()">
  <svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path d="M9 18l6-6-6-6"/></svg>
</button>

<!-- MAIN -->
<main class="main" id="main">
  <!-- TOP BAR -->
  <div class="topbar">
    <div class="topbar-left">
      <div class="breadcrumb">
        <div class="breadcrumb-home">
          <svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/></svg>
        </div>
        <span id="breadcrumb-text">Dashboard</span>
      </div>
    </div>
    <div class="topbar-right">
      <div class="mode-badge">
        <span class="mode-dot"></span>
        <span style="font-size:13px;font-weight:600;">UPSC Mode</span>
        <svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>
      </div>
      <div class="topbar-avatar">AK</div>
    </div>
  </div>

  <!-- DASHBOARD PAGE -->
  <div id="page-dashboard">
    <div class="hero-greeting">Good morning, <span>Aspirant!</span></div>

    <!-- TOP 2 CARDS -->
    <div class="grid-2">
      <!-- FOCUS CARD -->
      <div class="card focus-card">
        <div class="focus-header">
          <div class="card-label"><span class="card-label-dot dot-red"></span>Today's Focus</div>
          <div style="display:flex;align-items:center;gap:8px;">
            <span class="focus-pct-num">56%</span>
            <div style="background:#DCF5E8;color:#1A7A4A;font-size:11px;font-weight:700;padding:2px 7px;border-radius:20px;">41</div>
            <div class="waveform">
              <span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span>
            </div>
          </div>
        </div>
        <div class="focus-title">Fundamental Rights & DPSP</div>
        <div class="focus-sub">Solve 10 questions on Articles 12–51 today. Focus on the relationship between FR and DPSP for Prelims 2025.</div>
        <button class="btn-primary" onclick="showPage('polity')">Practice Now →</button>
      </div>
      <!-- PROGRESS CARD -->
      <div class="card">
        <div class="card-label"><span style="color:#378ADD;font-size:14px;">▐▌</span>&nbsp;Today's Progress</div>
        <div class="progress-stats">
          <div class="pstat"><div class="pstat-label">Total Questions</div><div class="pstat-val">50</div></div>
          <div class="pstat"><div class="pstat-label">Correct Answers</div><div class="pstat-val green">40</div></div>
          <div class="pstat"><div class="pstat-label">Accuracy Rate</div><div class="pstat-val amber">80%</div></div>
        </div>
      </div>
    </div>

    <!-- MINI CARDS ROW -->
    <div class="grid-4">
      <div class="mini-card">
        <div class="mini-label">
          <svg width="15" height="15" fill="none" stroke="#E8380D" stroke-width="2" viewBox="0 0 24 24"><rect x="3" y="4" width="18" height="18" rx="2"/><path d="M16 2v4M8 2v4M3 10h18"/></svg>
          Daily Activity
        </div>
        <div class="mini-val">8</div>
        <div class="mini-sub">Articles reviewed today</div>
      </div>
      <div class="mini-card">
        <div class="mini-label">
          <svg width="15" height="15" fill="none" stroke="#E8380D" stroke-width="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 6v6l4 2"/></svg>
          Accuracy (7 days)
        </div>
        <div class="mini-val">72%</div>
        <div class="mini-sub">this week</div>
      </div>
      <div class="mini-card">
        <div class="mini-label">
          <svg width="15" height="15" fill="none" stroke="#E8380D" stroke-width="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>
          Exam Countdown
        </div>
        <div class="mini-val" id="countdown-days">—</div>
        <div class="mini-sub">Days until UPSC Prelims</div>
      </div>
      <div class="mini-card">
        <div class="mini-label">
          <svg width="15" height="15" fill="none" stroke="#E8380D" stroke-width="2" viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
          Consistency
        </div>
        <div class="mini-val">6 🔥</div>
        <div class="mini-sub">Practice streak</div>
      </div>
    </div>

    <!-- BOTTOM 2 -->
    <div class="grid-2b">
      <div style="display:flex;flex-direction:column;gap:10px;">
        <div class="card" style="cursor:pointer;display:flex;align-items:center;justify-content:space-between;" onclick="showPage('polity')">
          <div>
            <div style="font-size:15px;font-weight:700;color:var(--text);">Articles Quick Revision</div>
            <div style="font-size:12px;color:var(--text2);margin-top:3px;">Browse all 395+ constitutional articles</div>
          </div>
          <div style="width:36px;height:36px;background:var(--sidebar);border-radius:10px;display:flex;align-items:center;justify-content:center;color:#fff;font-size:18px;cursor:pointer;">▶</div>
        </div>
        <div class="card" style="cursor:pointer;display:flex;align-items:center;justify-content:space-between;">
          <div>
            <div style="font-size:15px;font-weight:700;color:var(--text);">Mock Test — Polity</div>
            <div style="font-size:12px;color:var(--text2);margin-top:3px;">25 MCQs · UPSC Prelims pattern</div>
          </div>
          <div style="width:36px;height:36px;background:var(--sidebar);border-radius:10px;display:flex;align-items:center;justify-content:center;color:#fff;font-size:18px;">▶</div>
        </div>
        <div class="card" style="cursor:pointer;display:flex;align-items:center;justify-content:space-between;">
          <div>
            <div style="font-size:15px;font-weight:700;color:var(--text);">Schedules & Amendments</div>
            <div style="font-size:12px;color:var(--text2);margin-top:3px;">12 Schedules · Key Amendments</div>
          </div>
          <div style="width:36px;height:36px;background:var(--sidebar);border-radius:10px;display:flex;align-items:center;justify-content:center;color:#fff;font-size:18px;">▶</div>
        </div>
      </div>
      <div class="practice-card">
        <div>
          <div class="practice-title">Polity Practice Mode</div>
          <div class="practice-sub">Test yourself on the most frequently asked constitutional articles in UPSC Prelims. Adaptive difficulty based on your performance.</div>
        </div>
        <button class="btn-white" onclick="showPage('polity')">Start Practice →</button>
      </div>
    </div>
  </div>

  <!-- POLITY PAGE -->
  <div id="page-polity" style="display:none;">
    <div class="hero-greeting" style="font-size:32px;margin-bottom:8px;">Indian <span>Constitution</span></div>
    <div style="font-size:14px;color:var(--text2);margin-bottom:24px;">All Articles · Organised by Parts · Interactive Study Tool</div>

    <div class="stats-strip">
      <div class="strip-stat"><span class="strip-dot" style="background:var(--accent);"></span><span id="s-total">448 Articles</span></div>
      <div class="strip-stat"><span class="strip-dot" style="background:#1A7A4A;"></span><span id="s-mem">0 Memorised</span></div>
      <div class="strip-stat"><span class="strip-dot" style="background:#E8B200;"></span><span id="s-bk">0 Bookmarked</span></div>
      <div class="strip-stat"><span class="strip-dot" style="background:#378ADD;"></span>22 Parts</div>
      <div class="strip-stat"><span class="strip-dot" style="background:#8B5CF6;"></span>12 Schedules</div>
    </div>

    <!-- SEARCH + FILTERS -->
    <div class="search-wrap">
      <svg class="search-icon" width="16" height="16" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg>
      <input type="text" id="polity-search" placeholder="Search by Article number, keyword, or Part name…" oninput="renderPolity()">
    </div>

    <div style="display:flex;gap:6px;flex-wrap:wrap;margin-bottom:20px;" id="polity-filters">
      <button class="filter-chip on" data-f="all" onclick="setFilter(this,'all')">All</button>
      <button class="filter-chip" data-f="imp" onclick="setFilter(this,'imp')">Important</button>
      <button class="filter-chip" data-f="FR" onclick="setFilter(this,'FR')">Fundamental Rights</button>
      <button class="filter-chip" data-f="DPSP" onclick="setFilter(this,'DPSP')">DPSP</button>
      <button class="filter-chip" data-f="FD" onclick="setFilter(this,'FD')">Fundamental Duties</button>
      <button class="filter-chip" data-f="Parliament" onclick="setFilter(this,'Parliament')">Parliament</button>
      <button class="filter-chip" data-f="President" onclick="setFilter(this,'President')">President</button>
      <button class="filter-chip" data-f="judiciary" onclick="setFilter(this,'judiciary')">Judiciary</button>
      <button class="filter-chip" data-f="Emergency" onclick="setFilter(this,'Emergency')">Emergency</button>
      <button class="filter-chip" data-f="Election" onclick="setFilter(this,'Election')">Elections</button>
      <button class="filter-chip" data-f="Panchayat" onclick="setFilter(this,'Panchayat')">Panchayat</button>
    </div>

    <div id="polity-content"></div>
  </div>

  <!-- EXAMS PAGE -->
  <div id="page-exams" style="display:none;">
    <div class="hero-greeting" style="font-size:32px;">Exams & <span>Tests</span></div>
    <div style="font-size:14px;color:var(--text2);margin:8px 0 24px;">Mock tests, previous year papers, and practice sets</div>
    <div class="grid-2">
      <div class="card" style="cursor:pointer;">
        <div class="focus-title">UPSC Prelims 2024</div>
        <div class="focus-sub">100 questions · General Studies Paper I · 2 hours</div>
        <button class="btn-primary" style="margin-top:12px;">Start Exam</button>
      </div>
      <div class="practice-card">
        <div class="practice-title">Polity Mock Test</div>
        <div class="practice-sub">25 questions focused on the Constitution of India</div>
        <button class="btn-white">Attempt Now →</button>
      </div>
    </div>
    <div style="margin-top:20px;background:var(--card);border:1px solid var(--border);border-radius:16px;padding:24px;text-align:center;color:var(--text2);font-size:14px;">
      More exams coming soon. Visit the Polity section to practise articles.
    </div>
  </div>
</main>

<!-- MODAL -->
<div class="modal-overlay" id="modal" onclick="closeModal(event)">
  <div class="modal">
    <button class="close-btn" onclick="document.getElementById('modal').classList.remove('open')">×</button>
    <div class="modal-artnum" id="m-num"></div>
    <div class="modal-title" id="m-title"></div>
    <div class="modal-desc" id="m-desc"></div>
    <div class="art-tags" id="m-tags"></div>
    <div class="modal-btns" id="m-btns"></div>
  </div>
</div>

<script>
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
    {n:"20",t:"Protection for conviction of offences",d:"No ex-post-facto law; no double jeopardy (not tried for same offence twice); no self-incrimination. These cannot be suspended even during national emergency.",tags:["imp","FR","criminal"]},
    {n:"21",t:"Protection of life and personal liberty",d:"No person shall be deprived of his life or personal liberty except according to procedure established by law. Judicial interpretation has expanded this to include right to privacy, right to livelihood, and more.",tags:["imp","FR","life"]},
    {n:"21A",t:"Right to education (86th Amendment)",d:"The State shall provide free and compulsory education to all children of the age of six to fourteen years in such manner as the State may, by law, determine.",tags:["imp","FR","education"]},
    {n:"22",t:"Protection against arrest and detention",d:"Right to be informed of grounds of arrest; right to consult a lawyer; produced before magistrate within 24 hours. No detention beyond 3 months without Advisory Board under preventive detention laws.",tags:["imp","FR","criminal"]},
    {n:"23",t:"Prohibition of forced labour",d:"Traffic in human beings, begar (forced labour) and similar forms of forced labour are prohibited. Any contravention shall be an offence punishable by law.",tags:["imp","FR","exploitation"]},
    {n:"24",t:"Prohibition of child labour",d:"No child below fourteen years of age shall be employed in any factory, mine, or other hazardous employment.",tags:["imp","FR","exploitation"]},
    {n:"25",t:"Freedom of religion",d:"All persons are equally entitled to freedom of conscience and the right to freely profess, practise and propagate religion. Subject to public order, morality and health.",tags:["imp","FR","religion"]},
    {n:"26",t:"Freedom to manage religious affairs",d:"Every religious denomination has the right to establish and maintain institutions for religious and charitable purposes and to manage its own affairs in matters of religion.",tags:["FR","religion"]},
    {n:"27",t:"Freedom from religious tax",d:"No person shall be compelled to pay taxes for promotion or maintenance of any particular religion or religious denomination.",tags:["FR","religion"]},
    {n:"28",t:"Freedom from religious instruction in State institutions",d:"No religious instruction shall be imparted in educational institutions wholly maintained out of State funds.",tags:["FR","religion"]},
    {n:"29",t:"Protection of minority interests",d:"Any section of citizens having a distinct language, script or culture shall have the right to conserve the same. No citizen shall be denied admission to any State-aided educational institution on grounds only of religion, race, caste, language.",tags:["imp","FR","minority"]},
    {n:"30",t:"Right of minorities to establish educational institutions",d:"All minorities, whether based on religion or language, have the right to establish and administer educational institutions of their choice. The State shall not discriminate against minority institutions in granting aid.",tags:["imp","FR","minority"]},
    {n:"32",t:"Right to Constitutional Remedies",d:"The right to move the Supreme Court by appropriate proceedings for enforcement of Fundamental Rights. The Supreme Court shall have power to issue writs — habeas corpus, mandamus, prohibition, quo warranto, certiorari. Dr Ambedkar called this the 'heart and soul' of the Constitution.",tags:["imp","FR","remedies"]},
    {n:"33",t:"Modification of FR for armed forces",d:"Parliament may by law determine to what extent any Fundamental Rights shall be restricted or abrogated in their application to members of the armed forces or police.",tags:["FR"]},
    {n:"34",t:"FR during martial law",d:"Parliament may indemnify any person in the service of the Union or of a State for any act done in connection with maintenance of order where martial law was in force.",tags:["FR"]},
    {n:"35",t:"Legislation to give effect to FR",d:"Parliament alone has the power to make laws prescribing punishment for offences mentioned under Articles 17 and 23, and to enforce Fundamental Rights under certain articles.",tags:["FR"]},
  ]},
  {part:"Part IV",partFull:"Part IV — Directive Principles of State Policy (Articles 36–51)",arts:[
    {n:"36",t:"Definition of State for DPSP",d:"In this Part, 'the State' has the same meaning as in Part III.",tags:["DPSP","definition"]},
    {n:"37",t:"DPSP are fundamental in governance",d:"The provisions of this Part shall not be enforceable by any court, but the principles are fundamental in the governance of the country and it shall be the duty of the State to apply these principles in making laws.",tags:["imp","DPSP"]},
    {n:"38",t:"Promote welfare of people",d:"The State shall strive to promote the welfare of the people by securing and protecting as effectively as it may a social order in which justice — social, economic and political — shall inform all institutions.",tags:["imp","DPSP"]},
    {n:"39",t:"Certain principles of policy",d:"Adequate means of livelihood; equitable distribution of material resources of community; no concentration of wealth; equal pay for equal work for men and women; protection of childhood and youth against exploitation.",tags:["imp","DPSP"]},
    {n:"39A",t:"Equal justice and free legal aid",d:"The State shall secure that the operation of the legal system promotes justice on a basis of equal opportunity, and shall provide free legal aid to those who cannot afford it.",tags:["imp","DPSP"]},
    {n:"40",t:"Organisation of village panchayats",d:"The State shall take steps to organise village panchayats and endow them with such powers and authority as may be necessary to enable them to function as units of self-government.",tags:["imp","DPSP","panchayat"]},
    {n:"41",t:"Right to work and education",d:"The State shall make effective provision for securing the right to work, to education and to public assistance in cases of unemployment, old age, sickness and disablement.",tags:["DPSP"]},
    {n:"42",t:"Just and humane work conditions",d:"The State shall make provision for securing just and humane conditions of work and for maternity relief.",tags:["DPSP"]},
    {n:"43",t:"Living wage for workers",d:"The State shall endeavour to secure a living wage, a decent standard of life and full enjoyment of leisure and social and cultural opportunities for all workers — industrial or agricultural.",tags:["DPSP"]},
    {n:"43A",t:"Participation of workers in management",d:"The State shall take steps to secure the participation of workers in the management of undertakings, establishments or other organisations engaged in any industry.",tags:["DPSP"]},
    {n:"44",t:"Uniform Civil Code",d:"The State shall endeavour to secure for the citizens a uniform civil code throughout the territory of India. One of the most debated directives.",tags:["imp","DPSP"]},
    {n:"45",t:"Early childhood care and education",d:"The State shall endeavour to provide early childhood care and education for all children until they complete the age of six years.",tags:["DPSP"]},
    {n:"46",t:"Promotion of SC/ST interests",d:"The State shall promote with special care the educational and economic interests of the weaker sections of the people, and in particular, of the Scheduled Castes and Scheduled Tribes.",tags:["imp","DPSP"]},
    {n:"47",t:"Raise level of nutrition and public health",d:"The State shall regard raising the level of nutrition and standard of living and improvement of public health as among its primary duties. Prohibition of intoxicating drinks and drugs.",tags:["DPSP"]},
    {n:"48",t:"Cattle and agriculture",d:"The State shall endeavour to organise agriculture on modern and scientific lines and take steps for preserving and improving the breeds of cattle and prohibit slaughter of cows, calves and other milch and draught cattle.",tags:["DPSP"]},
    {n:"48A",t:"Protection of environment",d:"The State shall endeavour to protect and improve the environment and to safeguard the forests and wildlife of the country. Added by 42nd Amendment 1976.",tags:["imp","DPSP","environment"]},
    {n:"49",t:"Protection of monuments",d:"It shall be the obligation of the State to protect every monument, place or object of artistic or historic interest, declared by Parliament as of national importance.",tags:["DPSP"]},
    {n:"50",t:"Separation of judiciary from executive",d:"The State shall take steps to separate the judiciary from the executive in the public services of the State.",tags:["imp","DPSP","judiciary"]},
    {n:"51",t:"Promotion of international peace",d:"The State shall endeavour to promote international peace and security; maintain just and honourable relations between nations; foster respect for international law and treaty obligations.",tags:["DPSP","international"]},
  ]},
  {part:"Part IVA",partFull:"Part IV-A — Fundamental Duties (Article 51A)",arts:[
    {n:"51A",t:"Fundamental Duties (11 duties)",d:"Citizens' duties: abide by the Constitution and respect the national flag/anthem; cherish noble ideals of freedom struggle; uphold sovereignty, unity and integrity; defend the country; promote harmony; value composite culture; preserve natural environment; develop scientific temper; safeguard public property; strive for excellence; parents to provide educational opportunities to children aged 6–14.",tags:["imp","FD"]},
  ]},
  {part:"Part V",partFull:"Part V — The Union Government (Articles 52–151)",arts:[
    {n:"52",t:"The President of India",d:"There shall be a President of India, who is the constitutional head of the executive of the Union.",tags:["imp","President"]},
    {n:"53",t:"Executive power vested in President",d:"The executive power of the Union shall be vested in the President and shall be exercised by him either directly or through officers subordinate to him in accordance with the Constitution.",tags:["imp","President"]},
    {n:"54",t:"Election of President",d:"The President shall be elected by an Electoral College consisting of elected members of both Houses of Parliament and elected members of the Legislative Assemblies of all States.",tags:["imp","President"]},
    {n:"55",t:"Manner of election",d:"The election of President shall be by the system of proportional representation by means of single transferable vote and voting shall be by secret ballot with uniformity of scale among States.",tags:["President"]},
    {n:"56",t:"Term of office — President",d:"The President shall hold office for a term of five years from the date on which he enters upon his office. Eligible for re-election.",tags:["imp","President"]},
    {n:"57",t:"Eligibility for re-election",d:"A person who holds, or has held, office as President shall be eligible for re-election.",tags:["President"]},
    {n:"58",t:"Qualifications to be President",d:"Must be a citizen of India, completed 35 years of age, and qualified for election as a member of the Lok Sabha.",tags:["imp","President"]},
    {n:"61",t:"Impeachment of President",d:"The President may be removed by impeachment for violation of the Constitution. A charge must be preferred by either House, passed by a majority of the total membership with at least two-thirds majority of members present and voting.",tags:["imp","President"]},
    {n:"63",t:"The Vice-President of India",d:"There shall be a Vice-President of India.",tags:["imp","VP"]},
    {n:"64",t:"VP as Chairman of Rajya Sabha",d:"The Vice-President shall be ex officio Chairman of the Council of States (Rajya Sabha) and shall not hold any other office of profit.",tags:["imp","VP","Parliament","Rajya Sabha"]},
    {n:"66",t:"Election of Vice-President",d:"VP is elected by members of an electoral college consisting of members of both Houses of Parliament by proportional representation — single transferable vote by secret ballot.",tags:["imp","VP"]},
    {n:"72",t:"President's power to grant pardon",d:"The President may grant pardons, reprieves, respites or remissions of punishment or suspend, remit or commute sentence in all cases — involving a Union law, a death sentence, or court-martial.",tags:["imp","President","pardon"]},
    {n:"74",t:"Council of Ministers to aid President",d:"There shall be a Council of Ministers with the Prime Minister at the head to aid and advise the President, who shall act in accordance with such advice. The President may return advice for reconsideration once.",tags:["imp","PM","cabinet"]},
    {n:"75",t:"Other provisions as to Ministers",d:"The Prime Minister shall be appointed by the President; other Ministers shall be appointed by the President on the advice of the PM. Ministers shall hold office during the pleasure of the President and shall be collectively responsible to Lok Sabha.",tags:["imp","PM","cabinet"]},
    {n:"76",t:"Attorney-General of India",d:"The President shall appoint a person qualified to be a Judge of the Supreme Court to be the Attorney-General for India. The AG shall have audience in all courts in India.",tags:["imp","AG"]},
    {n:"79",t:"Constitution of Parliament",d:"There shall be a Parliament of the Union which shall consist of the President and two Houses — the Council of States (Rajya Sabha) and the House of the People (Lok Sabha).",tags:["imp","Parliament"]},
    {n:"80",t:"Composition of Rajya Sabha",d:"Maximum 250 members: 12 nominated by President for distinguished service in literature, science, art, and social service + 238 representatives of States and UTs. Members are not directly elected by the people; elected by State Legislative Assemblies.",tags:["imp","Parliament","Rajya Sabha"]},
    {n:"81",t:"Composition of Lok Sabha",d:"Maximum 552 members: up to 530 from States + up to 20 from UTs + 2 nominated Anglo-Indians (provision abolished by 104th Amendment 2019). All directly elected by adult suffrage.",tags:["imp","Parliament","Lok Sabha"]},
    {n:"83",t:"Duration of Houses of Parliament",d:"Rajya Sabha shall not be subject to dissolution — it is a permanent body with 1/3 members retiring every 2 years. Lok Sabha's normal term is 5 years but may be extended during National Emergency.",tags:["imp","Parliament"]},
    {n:"85",t:"Sessions of Parliament",d:"The President shall from time to time summon each House of Parliament. The gap between two sessions shall not exceed 6 months. The President may prorogue or dissolve the Lok Sabha.",tags:["imp","Parliament"]},
    {n:"93",t:"Speaker and Deputy Speaker of Lok Sabha",d:"The House of the People shall elect from among its members a Speaker and a Deputy Speaker. The Speaker may be removed by a resolution of the House passed by a majority of all then members.",tags:["imp","Parliament","Speaker"]},
    {n:"100",t:"Voting in Houses",d:"All questions in each House shall be determined by a majority of votes of the members present and voting. The Chairman/Speaker has an ordinary vote and also a casting vote in case of a tie.",tags:["Parliament"]},
    {n:"108",t:"Joint sitting of both Houses",d:"In case of a deadlock on a bill (other than Money Bills or Constitution Amendment Bills), the President may summon a joint sitting of both Houses. Only 3 joint sittings held so far.",tags:["imp","Parliament"]},
    {n:"109",t:"Special procedure for Money Bills",d:"A Money Bill shall not be introduced in the Rajya Sabha. After it is passed by Lok Sabha, Rajya Sabha has 14 days to return it with recommendations. If Rajya Sabha does not return it in 14 days, it is deemed passed. Lok Sabha may accept or reject RS recommendations.",tags:["imp","Parliament","money bill"]},
    {n:"110",t:"Definition of Money Bill",d:"A Bill is a Money Bill if it deals solely with: imposition or abolition of taxes; regulation of borrowing; custody of Consolidated Fund; appropriation of money from Consolidated Fund; declaration of expenditure charged on Consolidated Fund. Speaker's certificate is final.",tags:["imp","Parliament","money bill"]},
    {n:"112",t:"Annual Financial Statement",d:"The President shall cause to be laid before both Houses of Parliament a statement of the estimated receipts and expenditure of the Government for each financial year — this is the Union Budget.",tags:["imp","Parliament","budget"]},
    {n:"114",t:"Appropriation Bills",d:"No money shall be withdrawn from the Consolidated Fund of India except under appropriation made by law. An Appropriation Bill must be passed for all grants voted by Lok Sabha.",tags:["Parliament","budget"]},
    {n:"123",t:"President's Ordinance-making power",d:"When both Houses of Parliament are not in session and the President is satisfied that circumstances exist which render immediate action necessary, he may promulgate Ordinances. Must be laid before Parliament and ceases to operate after 6 weeks of reassembly.",tags:["imp","President","ordinance"]},
    {n:"124",t:"Establishment of Supreme Court",d:"There shall be a Supreme Court of India consisting of a Chief Justice of India and not more than 33 other Judges (as per latest amendments).",tags:["imp","SC","judiciary"]},
    {n:"125",t:"Salaries of Judges",d:"The salaries and other conditions of service of Judges of the Supreme Court shall be as determined by Parliament by law and shall be charged on the Consolidated Fund of India.",tags:["SC","judiciary"]},
    {n:"129",t:"Supreme Court as court of record",d:"The Supreme Court shall be a court of record and shall have all the powers of such a court including the power to punish for contempt of itself.",tags:["imp","SC","judiciary"]},
    {n:"131",t:"Original jurisdiction of SC",d:"The Supreme Court has exclusive original jurisdiction in disputes between: (a) Government of India and one or more States; (b) Government of India and any State(s) on one side and one or more States on the other; (c) Two or more States.",tags:["imp","SC","jurisdiction"]},
    {n:"136",t:"Special Leave Petition",d:"The Supreme Court may, in its discretion, grant special leave to appeal from any judgment, decree, determination, sentence or order in any cause or matter passed by any court or tribunal in India (except courts/tribunals constituted by or under any law relating to the Armed Forces).",tags:["imp","SC","jurisdiction"]},
    {n:"137",t:"Review of SC judgments",d:"The Supreme Court shall have power to review any judgment pronounced or order made by it. Review petitions are allowed under strict grounds.",tags:["SC","jurisdiction"]},
    {n:"141",t:"Law declared by SC is binding",d:"The law declared by the Supreme Court shall be binding on all courts within the territory of India.",tags:["imp","SC"]},
    {n:"143",t:"Advisory jurisdiction of SC",d:"If at any time it appears to the President that a question of law or fact of public importance has arisen or is likely to arise, he may refer it to the Supreme Court for its opinion (Advisory/Consultative Jurisdiction).",tags:["imp","SC","President"]},
    {n:"148",t:"Comptroller and Auditor-General",d:"There shall be a Comptroller and Auditor-General of India appointed by the President by warrant under his hand and seal. Salary charged to Consolidated Fund. Can be removed only in the same manner as a Supreme Court judge.",tags:["imp","CAG"]},
  ]},
  {part:"Part VI",partFull:"Part VI — The States (Articles 152–237)",arts:[
    {n:"153",t:"Governors of States",d:"There shall be a Governor for each State. One person can be Governor of two or more States.",tags:["imp","Governor","State"]},
    {n:"154",t:"Executive power of State",d:"The executive power of the State shall be vested in the Governor and shall be exercised by him either directly or through officers subordinate to him.",tags:["Governor","State"]},
    {n:"155",t:"Appointment of Governor",d:"The Governor of a State shall be appointed by the President by warrant under his hand and seal. Not elected — nominated by the Central Government.",tags:["imp","Governor"]},
    {n:"156",t:"Term of Governor",d:"The Governor shall hold office during the pleasure of the President. Normal term is 5 years. Can be removed any time before the term.",tags:["imp","Governor"]},
    {n:"161",t:"Governor's pardon power",d:"The Governor may grant pardons, reprieves, etc., in all cases where punishment is for an offence against any law relating to a matter to which the executive power of the State extends — except in cases of death sentence (which is President's power) and court-martial.",tags:["imp","Governor","pardon"]},
    {n:"163",t:"Council of Ministers to aid Governor",d:"There shall be a Council of Ministers with the Chief Minister as the head to aid and advise the Governor, who shall act in accordance with such advice, except in matters in which he is required by or under the Constitution to act in his discretion.",tags:["imp","CM","State"]},
    {n:"164",t:"Other provisions as to Ministers",d:"The Chief Minister shall be appointed by the Governor; other Ministers shall be appointed by the Governor on the advice of the Chief Minister. Ministers shall hold office during the pleasure of the Governor and shall be collectively responsible to the Legislative Assembly.",tags:["imp","CM","State"]},
    {n:"165",t:"Advocate-General of the State",d:"The Governor of each State shall appoint a person qualified to be appointed as a judge of the High Court to be the Advocate-General for the State.",tags:["State","AG"]},
    {n:"168",t:"Constitution of State Legislatures",d:"For every State there shall be a Legislature which shall consist of the Governor and one or two Houses. States with bicameral legislature: Andhra Pradesh, Telangana, Karnataka, Maharashtra, Bihar, Uttar Pradesh, J&K.",tags:["imp","State Legislature"]},
    {n:"200",t:"Assent to Bills",d:"When a Bill is presented to the Governor, he may: (a) give assent; (b) withhold assent; (c) return the Bill for reconsideration (except Money Bills); (d) reserve the Bill for the President's consideration.",tags:["imp","Governor","State Legislature"]},
    {n:"213",t:"Governor's Ordinance power",d:"When the State Legislature is not in session, the Governor may promulgate such Ordinances as circumstances require. Ordinance must be approved by the State Legislature within 6 weeks of reassembly.",tags:["imp","Governor","ordinance"]},
    {n:"214",t:"High Courts for States",d:"There shall be a High Court for each State. Parliament may establish a common High Court for two or more States.",tags:["imp","HC","judiciary"]},
    {n:"215",t:"HC as court of record",d:"Every High Court shall be a court of record and shall have all the powers of such a court including the power to punish for contempt of itself.",tags:["HC","judiciary"]},
    {n:"226",t:"Power of HC to issue writs",d:"The High Court may issue writs — habeas corpus, mandamus, prohibition, quo warranto and certiorari — for enforcement of Fundamental Rights and for any other purpose. Broader than SC's Article 32 writ jurisdiction.",tags:["imp","HC","writs","judiciary"]},
    {n:"227",t:"HC superintendence over lower courts",d:"Every High Court shall have superintendence over all courts and tribunals throughout the territories in relation to which it exercises jurisdiction, including the right to call for returns and issue general rules.",tags:["imp","HC","judiciary"]},
    {n:"233",t:"Appointment of District Judges",d:"Appointments of persons to be and the posting and promotion of district judges shall be made by the Governor of the State in consultation with the High Court.",tags:["judiciary","State"]},
  ]},
  {part:"Part VIII",partFull:"Part VIII — Union Territories (Articles 239–242)",arts:[
    {n:"239",t:"Administration of Union Territories",d:"Every Union territory shall be administered by the President acting to such extent as he thinks fit through an administrator appointed by him.",tags:["imp","UT"]},
    {n:"239AA",t:"Special provisions for Delhi",d:"Delhi is administered as a Union Territory with its own Legislature (State Legislative Assembly) and Council of Ministers. However, matters relating to public order, police and land are subject to the Lieutenant Governor acting on behalf of the President.",tags:["imp","UT","Delhi"]},
    {n:"240",t:"Power to make regulations for UTs",d:"The President may make regulations for the peace, progress and good government of certain Union territories — Andaman & Nicobar, Lakshadweep, Dadra & Nagar Haveli, Daman & Diu, Puducherry, Ladakh.",tags:["UT"]},
  ]},
  {part:"Part IX",partFull:"Part IX — Panchayats (Articles 243–243O)",arts:[
    {n:"243",t:"Definitions under Panchayats",d:"Defines district, Gram Sabha, intermediate level, municipality, panchayat, panchayat area, population, village.",tags:["Panchayat"]},
    {n:"243A",t:"Gram Sabha",d:"A Gram Sabha may exercise such powers and perform such functions at the village level as the Legislature of a State may by law provide.",tags:["imp","Panchayat"]},
    {n:"243B",t:"Constitution of Panchayats",d:"There shall be constituted in every State Panchayats at the village, intermediate and district levels. Added by 73rd Constitutional Amendment 1992.",tags:["imp","Panchayat"]},
    {n:"243D",t:"Reservation of seats in Panchayats",d:"Seats shall be reserved for SC/ST in proportion to their population. Not less than 1/3rd seats shall be reserved for women. State may also provide reservation for OBC.",tags:["imp","Panchayat","reservation"]},
    {n:"243E",t:"Duration of Panchayats",d:"Every Panchayat shall continue for five years. Elections must be completed before the expiry of the current term. If dissolved, elections must be held within 6 months.",tags:["Panchayat"]},
    {n:"243G",t:"Powers of Panchayats",d:"Legislature of a State may endow Panchayats with powers and authority to prepare plans and implement schemes for economic development and social justice with respect to 29 subjects listed in the Eleventh Schedule.",tags:["imp","Panchayat"]},
    {n:"243I",t:"Finance Commission for Panchayats",d:"The Governor shall constitute a Finance Commission every 5 years to review the financial position of Panchayats and make recommendations.",tags:["Panchayat","Finance"]},
  ]},
  {part:"Part IXA",partFull:"Part IX-A — Municipalities (Articles 243P–243ZG)",arts:[
    {n:"243P",t:"Definitions under Municipalities",d:"Defines metropolitan area (population 10 lakh or more), municipal area, municipality, panchayat, and ward.",tags:["Municipalities"]},
    {n:"243Q",t:"Constitution of Municipalities",d:"There shall be constituted in every State a Nagar Panchayat for transitional area, a Municipal Council for smaller urban areas, and a Municipal Corporation for larger urban areas. Added by 74th Amendment 1992.",tags:["imp","Municipalities"]},
    {n:"243T",t:"Reservation in Municipalities",d:"Seats shall be reserved for SC/ST in proportion to population. Not less than 1/3rd seats shall be reserved for women.",tags:["imp","Municipalities","reservation"]},
    {n:"243W",t:"Powers of Municipalities",d:"Legislature may endow Municipalities with powers for preparation and implementation of plans with respect to 18 subjects in the Twelfth Schedule.",tags:["imp","Municipalities"]},
  ]},
  {part:"Part X",partFull:"Part X — Scheduled and Tribal Areas (Article 244)",arts:[
    {n:"244",t:"Administration of Scheduled Areas",d:"The provisions of the Fifth Schedule shall apply to the administration and control of Scheduled Areas and Scheduled Tribes in States other than Assam, Meghalaya, Tripura and Mizoram. The Sixth Schedule applies to tribal areas in those four northeastern states.",tags:["imp","Tribes","Schedule"]},
  ]},
  {part:"Part XI",partFull:"Part XI — Relations between Union and States (Articles 245–263)",arts:[
    {n:"245",t:"Extent of laws by Parliament and States",d:"Parliament may make laws for the whole or any part of India; a State Legislature may make laws for the whole or any part of the State only. Parliament can also make extra-territorial legislation.",tags:["imp","Centre-State"]},
    {n:"246",t:"Subject matter of legislation — three lists",d:"Parliament has exclusive power over Union List (List I — 97 subjects); Parliament and State Legislatures both can legislate on Concurrent List (List III — 47 subjects); States have exclusive power over State List (List II — 66 subjects). Residuary power with Parliament.",tags:["imp","Centre-State","lists"]},
    {n:"248",t:"Residuary powers",d:"Parliament has exclusive power to make any law with respect to any matter not enumerated in the Concurrent List or State List — residuary power.",tags:["imp","Centre-State"]},
    {n:"249",t:"Parliament to legislate on State List in national interest",d:"If Rajya Sabha passes a resolution supported by at least 2/3 majority that it is necessary in national interest, Parliament may legislate on any matter in the State List for a period of 1 year (extendable).",tags:["imp","Centre-State"]},
    {n:"250",t:"Parliament to legislate during national emergency",d:"While a Proclamation of National Emergency is in operation, Parliament shall have power to make laws for the whole or any part of India on any subject in the State List.",tags:["imp","Centre-State","Emergency"]},
    {n:"256",t:"Obligation of States",d:"The executive power of every State shall be exercised so as to ensure compliance with laws made by Parliament. The Union may give directions to a State in this regard.",tags:["Centre-State"]},
    {n:"262",t:"Adjudication of water disputes",d:"Parliament may by law provide for adjudication of any dispute or complaint with respect to use, distribution or control of waters of any inter-State river or river valley.",tags:["imp","Centre-State","water"]},
    {n:"263",t:"Inter-State Council",d:"If it appears to the President that the public interests would be served by the establishment of a Council for enquiring into disputes between States, the President may establish an inter-State Council.",tags:["imp","Centre-State"]},
  ]},
  {part:"Part XII",partFull:"Part XII — Finance, Property and Contracts (Articles 264–300A)",arts:[
    {n:"265",t:"Taxes only by authority of law",d:"No tax shall be levied or collected except by authority of law. This is a fundamental guarantee against arbitrary taxation.",tags:["imp","Finance"]},
    {n:"266",t:"Consolidated Funds",d:"All revenues received by the Government of India, all loans raised by that Government, and all money received in repayment of loans shall form the Consolidated Fund of India. Similarly for States.",tags:["imp","Finance"]},
    {n:"267",t:"Contingency Fund",d:"Parliament/State Legislature may establish a Contingency Fund in the nature of an imprest account placed at the disposal of the President/Governor for meeting unforeseen expenditure.",tags:["Finance"]},
    {n:"280",t:"Finance Commission",d:"The President shall constitute a Finance Commission within 2 years of commencement of the Constitution and thereafter at the end of every 5th year. Recommends distribution of taxes between Centre and States.",tags:["imp","Finance","FC"]},
    {n:"300A",t:"Right to property",d:"No person shall be deprived of his property save by authority of law. Moved from Fundamental Rights to a mere constitutional right by the 44th Amendment 1978.",tags:["imp","Property"]},
  ]},
  {part:"Part XIII",partFull:"Part XIII — Trade, Commerce and Intercourse (Articles 301–307)",arts:[
    {n:"301",t:"Freedom of trade throughout India",d:"Subject to the other provisions of this Part, trade, commerce and intercourse throughout the territory of India shall be free.",tags:["imp","Trade"]},
    {n:"302",t:"Parliament to restrict trade",d:"Parliament may by law impose such restrictions on the freedom of trade, commerce or intercourse between one State and another or within any part of the territory of India as may be required in the public interest.",tags:["Trade"]},
    {n:"304",t:"Restrictions on inter-State trade by States",d:"The Legislature of a State may impose reasonable restrictions on the freedom of trade in the public interest, with the previous sanction of the President.",tags:["Trade"]},
  ]},
  {part:"Part XIV",partFull:"Part XIV — Services under the Union and States (Articles 308–323)",arts:[
    {n:"312",t:"All India Services",d:"If Rajya Sabha passes a resolution by not less than 2/3 majority of members present and voting declaring it necessary in national interest, Parliament may create new All-India Services common to Union and States (like IAS, IPS, IFS).",tags:["imp","Services"]},
    {n:"315",t:"Public Service Commissions",d:"There shall be a Public Service Commission for the Union (UPSC) and a Public Service Commission for each State (SPSC). A Joint PSC may be created for two or more States.",tags:["imp","UPSC"]},
    {n:"320",t:"Functions of UPSC",d:"It is the duty of UPSC to conduct examinations for appointments to services of the Union. The UPSC shall be consulted on all matters relating to methods of recruitment, promotions, and disciplinary matters.",tags:["imp","UPSC"]},
    {n:"323A",t:"Administrative Tribunals",d:"Parliament may provide for adjudication of disputes and complaints with respect to recruitment and conditions of service of persons appointed to public services — through Administrative Tribunals (CAT, SAT etc.).",tags:["imp","Tribunals"]},
    {n:"323B",t:"Tribunals for other matters",d:"Appropriate Legislature may provide for the adjudication of disputes relating to taxation, foreign exchange, industrial and labour disputes, land reforms, elections to Parliament and State Legislatures, etc., by tribunals.",tags:["Tribunals"]},
  ]},
  {part:"Part XV",partFull:"Part XV — Elections (Articles 324–329)",arts:[
    {n:"324",t:"Superintendence vested in Election Commission",d:"The superintendence, direction and control of preparation of electoral rolls and the conduct of all elections to Parliament and to the Legislature of every State and of elections to the offices of President and Vice-President shall be vested in the Election Commission.",tags:["imp","Election","EC"]},
    {n:"325",t:"No discrimination in electoral rolls",d:"There shall be one general electoral roll for every territorial constituency. No person shall be ineligible for inclusion in any electoral roll on grounds of religion, race, caste or sex.",tags:["imp","Election"]},
    {n:"326",t:"Adult suffrage",d:"The elections to the House of the People and to the Legislative Assembly of every State shall be on the basis of adult suffrage; every citizen who is not less than 18 years of age shall be entitled to vote.",tags:["imp","Election"]},
    {n:"327",t:"Parliament to provide for elections",d:"Parliament may from time to time by law make provision with respect to elections to Parliament and State Legislatures.",tags:["Election"]},
    {n:"329",t:"Bar to court interference in elections",d:"No election to Parliament or State Legislature shall be called in question except by an election petition presented to such authority and in such manner as may be provided for by or under any law made by the appropriate Legislature.",tags:["imp","Election"]},
  ]},
  {part:"Part XVI",partFull:"Part XVI — Special Provisions (Articles 330–342A)",arts:[
    {n:"330",t:"Reservation for SC/ST in Lok Sabha",d:"Seats shall be reserved in the House of the People for Scheduled Castes and Scheduled Tribes. Reservation was initially for 10 years, extended repeatedly by amendments.",tags:["imp","Reservation","SC/ST"]},
    {n:"332",t:"Reservation in State Legislatures",d:"Seats shall be reserved in the Legislative Assembly of every State for Scheduled Castes and Scheduled Tribes.",tags:["imp","Reservation","SC/ST"]},
    {n:"335",t:"Claims of SC/ST in services",d:"The claims of the members of the Scheduled Castes and Scheduled Tribes shall be taken into consideration, consistently with the maintenance of efficiency of administration, in the making of appointments to services and posts.",tags:["SC/ST","Services"]},
    {n:"338",t:"National Commission for SC",d:"There shall be a National Commission for Scheduled Castes to investigate and monitor all matters relating to safeguards provided for Scheduled Castes.",tags:["imp","SC/ST","Commission"]},
    {n:"338A",t:"National Commission for ST",d:"There shall be a National Commission for Scheduled Tribes to investigate and monitor all matters relating to safeguards provided for Scheduled Tribes.",tags:["imp","SC/ST","Commission"]},
    {n:"340",t:"OBC Commission",d:"The President may appoint a Commission to investigate the conditions of socially and educationally backward classes within Indian territory and difficulties under which they labour.",tags:["OBC","Commission"]},
    {n:"341",t:"Scheduled Castes",d:"The President may with respect to any State or UT and where it is a State, after consultation with the Governor thereof, by public notification specify the castes, races, tribes or parts of or groups within castes, races or tribes which shall for the purposes of this Constitution be deemed to be Scheduled Castes.",tags:["imp","SC/ST"]},
    {n:"342",t:"Scheduled Tribes",d:"The President may with respect to any State or UT, after consultation with the Governor thereof, by public notification specify the tribes or tribal communities or parts of or groups within tribes or tribal communities which shall be deemed to be Scheduled Tribes.",tags:["imp","SC/ST"]},
    {n:"342A",t:"Socially and educationally backward classes",d:"The President may by public notification specify the socially and educationally backward classes. Added by 102nd Amendment 2018, which also created the National Commission for Backward Classes (NCBC) under Article 338B.",tags:["imp","OBC"]},
  ]},
  {part:"Part XVII",partFull:"Part XVII — Official Language (Articles 343–351)",arts:[
    {n:"343",t:"Official language of the Union",d:"The official language of the Union shall be Hindi in Devanagari script. International form of Indian numerals shall be used. English was permitted for official purposes for 15 years (until 1965); Parliament extended its use indefinitely.",tags:["imp","Language"]},
    {n:"344",t:"Official Language Commission",d:"The President shall, after 5 years from commencement and thereafter at the expiry of 10 years, constitute a Commission to report on progressive use of Hindi for official purposes of the Union.",tags:["Language"]},
    {n:"345",t:"Official language of a State",d:"Subject to Article 346, the Legislature of a State may by law adopt any one or more of the languages in use in the State or Hindi as the official language.",tags:["Language"]},
    {n:"348",t:"Language of Supreme Court and HCs",d:"All proceedings in the Supreme Court and in every High Court shall be in English until Parliament by law otherwise provides.",tags:["Language","judiciary"]},
    {n:"351",t:"Directive for development of Hindi",d:"It shall be the duty of the Union to promote the spread of the Hindi language so that it may serve as a medium of expression for all the elements of the composite culture of India.",tags:["imp","Language"]},
  ]},
  {part:"Part XVIII",partFull:"Part XVIII — Emergency Provisions (Articles 352–360)",arts:[
    {n:"352",t:"National Emergency",d:"The President may proclaim a National Emergency if he is satisfied that the security of India or any part thereof is threatened by war, external aggression, or armed rebellion. The Cabinet must recommend in writing. Approved by special majority of Parliament within one month.",tags:["imp","Emergency"]},
    {n:"353",t:"Effect of National Emergency",d:"During National Emergency, Parliament may legislate on State List subjects; Executive power of the Union extends to giving directions to States on any matter; Centre-State financial relations may be modified.",tags:["imp","Emergency","Centre-State"]},
    {n:"354",t:"Application of provisions relating to distribution of revenues",d:"The President may, while a Proclamation of Emergency is in operation, direct that all or any of the provisions for distribution of revenues between Centre and States shall not apply or shall apply with modifications.",tags:["Emergency","Finance"]},
    {n:"355",t:"Duty of Union to protect States",d:"It shall be the duty of the Union to protect every State against external aggression and internal disturbance and to ensure that the government of every State is carried on in accordance with the Constitution.",tags:["imp","Emergency","Centre-State"]},
    {n:"356",t:"President's Rule — failure of constitutional machinery",d:"If the President is satisfied on receipt of a report from the Governor or otherwise that the Government of a State cannot be carried on in accordance with the Constitution, he may proclaim President's Rule. Must be approved by Parliament within 2 months.",tags:["imp","Emergency","President's Rule"]},
    {n:"360",t:"Financial Emergency",d:"The President may proclaim a Financial Emergency if the financial stability or credit of India or of any part thereof is threatened. Never been proclaimed in India so far.",tags:["imp","Emergency","Finance"]},
  ]},
  {part:"Part XIX",partFull:"Part XIX — Miscellaneous (Articles 361–367)",arts:[
    {n:"361",t:"Protection of President and Governors",d:"The President and the Governors shall not be answerable to any court for the exercise and performance of the powers and duties of their office. No criminal proceedings shall be instituted against them during their term of office.",tags:["President","Governor"]},
    {n:"365",t:"Effect of failure to comply with Union directions",d:"Where any State fails to comply with any provision of the Constitution or any provision of any law made by Parliament, it shall be lawful for the President to hold that a situation has arisen in which the Government of the State cannot be carried on in accordance with the Constitution.",tags:["Centre-State","Emergency"]},
  ]},
  {part:"Part XX",partFull:"Part XX — Amendment of the Constitution (Article 368)",arts:[
    {n:"368",t:"Power to amend the Constitution",d:"Parliament may, in the exercise of its constituent power, amend by way of addition, variation or repeal any provision of this Constitution. Types of amendment: (1) Simple majority; (2) Special majority of Parliament — 2/3 of members present and voting + majority of total membership; (3) Special majority + ratification by not less than one-half of the State Legislatures.",tags:["imp","Amendment"]},
  ]},
  {part:"Part XXI",partFull:"Part XXI — Temporary, Transitional and Special Provisions (Articles 369–392)",arts:[
    {n:"370",t:"Special status of J&K (now abrogated)",d:"Provided special autonomous status to Jammu & Kashmir — only Articles 1 and 370 of the Constitution applied to J&K, and other provisions applied with modifications. Abrogated by Presidential Order on August 5, 2019. J&K was bifurcated into two UTs: J&K (with Legislature) and Ladakh (without Legislature).",tags:["imp","J&K","Special"]},
    {n:"371",t:"Special provisions — Maharashtra and Gujarat",d:"The President may, by order, provide for the establishment of separate development boards for Vidarbha, Marathwada, rest of Maharashtra and for Saurashtra, Kutch, rest of Gujarat.",tags:["Special"]},
    {n:"371A",t:"Special provisions for Nagaland",d:"No Act of Parliament in respect of religious or social practices of the Nagas, Naga customary law and procedure, administration of civil and criminal justice involving decisions according to Naga customary law shall apply to Nagaland unless the Legislative Assembly of Nagaland by a resolution so decides.",tags:["imp","Special","Northeast"]},
    {n:"371B",t:"Special provisions for Assam",d:"Parliament may provide for the constitution and functions of a committee of the Legislative Assembly of Assam consisting of members elected from tribal areas.",tags:["Special","Northeast"]},
    {n:"371C",t:"Special provisions for Manipur",d:"Parliament may provide for a Committee of members elected to the Legislative Assembly of Manipur from Hill areas of that State.",tags:["Special","Northeast"]},
    {n:"371D",t:"Special provisions for Andhra Pradesh",d:"Special provisions regarding educational and employment opportunities in Andhra Pradesh — different zones for different regions.",tags:["Special"]},
    {n:"371F",t:"Special provisions for Sikkim",d:"Provisions made applicable to Sikkim when it was admitted to the Union in 1975 (36th Amendment).",tags:["Special"]},
    {n:"371G",t:"Special provisions for Mizoram",d:"No Act of Parliament with respect to religious or social practices of Mizo, Mizo customary law and procedure, etc., shall apply to Mizoram unless the Legislative Assembly so decides.",tags:["imp","Special","Northeast"]},
    {n:"371H",t:"Special provisions for Arunachal Pradesh",d:"The Governor of Arunachal Pradesh shall have special responsibility with respect to law and order in that State.",tags:["Special","Northeast"]},
  ]},
  {part:"Part XXII",partFull:"Part XXII — Short Title, Commencement, Authoritative Text (Articles 393–395)",arts:[
    {n:"393",t:"Short title",d:"This Constitution may be called the Constitution of India.",tags:["basics"]},
    {n:"394",t:"Commencement",d:"This Article and Articles 5, 6, 7, 8, 9, 60, 324, 366, 367, 379, 380, 388, 391, 392 and 393 shall come into force at once (November 26, 1949). The remaining provisions of this Constitution shall come into force on January 26, 1950 — celebrated as Republic Day.",tags:["imp","basics"]},
    {n:"395",t:"Repeals",d:"The Indian Independence Act 1947 and the Government of India Act 1935 together with all Schedules and amendments thereto are hereby repealed.",tags:["basics"]},
  ]},
];

let mem=JSON.parse(localStorage.getItem('pm_mem')||'{}');
let bks=JSON.parse(localStorage.getItem('pm_bk')||'{}');
let activeFilter='all';
let sidebarOpen=true;
let isDark=false;
let currentPage='dashboard';

function updateStats(){
  const tm=Object.values(mem).filter(Boolean).length;
  const tb=Object.values(bks).filter(Boolean).length;
  document.getElementById('s-mem').textContent=tm+' Memorised';
  document.getElementById('s-bk').textContent=tb+' Bookmarked';
}
function save(){localStorage.setItem('pm_mem',JSON.stringify(mem));localStorage.setItem('pm_bk',JSON.stringify(bks));updateStats();}

function toggleSidebar(){
  sidebarOpen=!sidebarOpen;
  document.getElementById('sidebar').classList.toggle('collapsed',!sidebarOpen);
  document.getElementById('main').classList.toggle('expanded',!sidebarOpen);
  const t=document.getElementById('sb-toggle');
  t.classList.toggle('out',!sidebarOpen);
  t.style.left=sidebarOpen?'228px':'8px';
  t.querySelector('svg').style.transform=sidebarOpen?'':'rotate(180deg)';
}
function toggleDark(){
  isDark=!isDark;
  document.body.setAttribute('data-dark',isDark?'1':'');
  if(!isDark)document.body.removeAttribute('data-dark');
}

function showPage(p){
  currentPage=p;
  ['dashboard','polity','exams'].forEach(x=>{
    document.getElementById('page-'+x).style.display=x===p?'block':'none';
  });
  document.querySelectorAll('.nav-item').forEach(el=>el.classList.remove('active'));
  const navMap={dashboard:0,polity:1,exams:2};
  document.querySelectorAll('.nav-item')[navMap[p]]?.classList.add('active');
  document.getElementById('breadcrumb-text').textContent=p.charAt(0).toUpperCase()+p.slice(1);
  if(p==='polity')renderPolity();
}

function setFilter(el,f){
  activeFilter=f;
  document.querySelectorAll('.filter-chip').forEach(c=>c.classList.remove('on'));
  el.classList.add('on');
  renderPolity();
}

function renderPolity(){
  const q=(document.getElementById('polity-search')?.value||'').toLowerCase().trim();
  const f=activeFilter;
  let html='';
  let totalShown=0;
  for(const part of ARTICLES){
    const filtered=part.arts.filter(a=>{
      const mq=!q||a.n.toLowerCase().includes(q)||a.t.toLowerCase().includes(q)||a.d.toLowerCase().includes(q)||part.partFull.toLowerCase().includes(q);
      const mf=f==='all'||a.tags.includes(f);
      return mq&&mf;
    });
    if(!filtered.length)continue;
    totalShown+=filtered.length;
    html+=`<div class="part-block">
      <div class="part-label"><span class="part-num">${part.part}</span>${part.partFull.replace(part.part+' — ','').replace(part.part+' — ','')}</div>
      <div class="articles-grid">
        ${filtered.map(a=>artCard(a)).join('')}
      </div>
    </div>`;
  }
  if(!totalShown)html='<div style="text-align:center;padding:3rem;color:var(--text2);font-size:15px;">No articles found for your search.</div>';
  document.getElementById('polity-content').innerHTML=html;
}

function artCard(a){
  const im=!!mem[a.n];const ib=!!bks[a.n];
  return`<div class="art-card ${im?'mem':ib?'bk':''}" id="ac-${a.n}">
    <div class="art-num-badge">ART. ${a.n}</div>
    <div class="art-title">${a.t}</div>
    <div class="art-desc" id="desc-${a.n}">${a.d}</div>
    <div class="art-tags">${a.tags.map(t=>`<span class="a-tag ${t==='imp'?'imp':''}">${t}</span>`).join('')}</div>
    <div class="art-btns">
      <button class="a-btn ${im?'g':''}" onclick="toggleMem('${a.n}',event)">${im?'✓ Memorised':'Memorise'}</button>
      <button class="a-btn ${ib?'y':''}" onclick="toggleBk('${a.n}',event)">${ib?'★ Saved':'Bookmark'}</button>
      <button class="a-btn" onclick="openModal('${a.n}')">Details</button>
    </div>
  </div>`;
}

function toggleMem(n,e){e.stopPropagation();mem[n]=!mem[n];save();renderPolity();}
function toggleBk(n,e){e.stopPropagation();bks[n]=!bks[n];save();renderPolity();}

function openModal(n){
  const a=ARTICLES.flatMap(p=>p.arts).find(x=>x.n===n);
  if(!a)return;
  document.getElementById('m-num').textContent='Article '+a.n;
  document.getElementById('m-title').textContent=a.t;
  document.getElementById('m-desc').textContent=a.d;
  document.getElementById('m-tags').innerHTML=a.tags.map(t=>`<span class="a-tag ${t==='imp'?'imp':''}">${t}</span>`).join('');
  const im=!!mem[a.n];const ib=!!bks[a.n];
  document.getElementById('m-btns').innerHTML=`
    <button class="a-btn ${im?'g':''}" onclick="toggleMem('${a.n}',{stopPropagation:()=>{}})">${im?'✓ Memorised':'Memorise'}</button>
    <button class="a-btn ${ib?'y':''}" onclick="toggleBk('${a.n}',{stopPropagation:()=>{}})">${ib?'★ Saved':'Bookmark'}</button>
  `;
  document.getElementById('modal').classList.add('open');
}
function closeModal(e){if(e.target.id==='modal')document.getElementById('modal').classList.remove('open');}

// Countdown to UPSC Prelims (typically last Sunday of May)
function computeCountdown(){
  const now=new Date();
  const prelims=new Date(2025,4,25); // May 25, 2025
  if(prelims<now){prelims.setFullYear(now.getFullYear()+1);}
  const days=Math.ceil((prelims-now)/(1000*60*60*24));
  document.getElementById('countdown-days').textContent=days+' days';
}
computeCountdown();
updateStats();
</script>
</body>
</html>
