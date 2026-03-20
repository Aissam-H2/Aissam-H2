<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>DEV MODE — Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,300;0,400;0,500;0,700;1,400&display=swap" rel="stylesheet"/>
<style>
  :root {
    --base:    #1e1e2e;
    --mantle:  #181825;
    --crust:   #11111b;
    --surface0:#313244;
    --surface1:#45475a;
    --surface2:#585b70;
    --overlay0:#6c7086;
    --overlay1:#7f849c;
    --text:    #cdd6f4;
    --subtext1:#bac2de;
    --subtext0:#a6adc8;
    --lavender:#b4befe;
    --blue:    #89b4fa;
    --sapphire:#74c7ec;
    --sky:     #89dceb;
    --teal:    #94e2d5;
    --green:   #a6e3a1;
    --yellow:  #f9e2af;
    --peach:   #fab387;
    --maroon:  #eba0ac;
    --red:     #f38ba8;
    --mauve:   #cba6f7;
    --pink:    #f5c2e7;
    --flamingo:#f2cdcd;
    --rosewater:#f5e0dc;
    --mono: 'JetBrains Mono', monospace;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--crust);
    color: var(--text);
    font-family: var(--mono);
    font-size: 14px;
    line-height: 1.6;
    cursor: none;
    overflow-x: hidden;
  }

  /* ─── CUSTOM CURSOR ─── */
  #cursor {
    position: fixed; top: 0; left: 0; z-index: 9999;
    width: 2px; height: 18px;
    background: var(--green);
    pointer-events: none;
    animation: blink 1.1s step-end infinite;
    transform: translate(-1px, -2px);
    transition: top 0.05s, left 0.05s;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* ─── SCANLINES ─── */
  body::before {
    content:''; position:fixed; inset:0; z-index:1000;
    background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.03) 2px, rgba(0,0,0,0.03) 4px);
    pointer-events:none;
  }

  /* ─── STATUS BAR (top) ─── */
  #statusbar-top {
    position: fixed; top: 0; left: 0; right: 0; z-index: 500;
    background: var(--mauve);
    color: var(--crust);
    display: flex; align-items: center;
    height: 26px; padding: 0 16px;
    font-size: 12px; font-weight: 700;
    gap: 0;
  }
  .sb-mode  { background: var(--green); color: var(--crust); padding: 0 12px; height: 100%; display:flex;align-items:center; font-weight:700; letter-spacing:.05em; }
  .sb-file  { background: var(--blue);  color: var(--crust); padding: 0 12px; height: 100%; display:flex;align-items:center; }
  .sb-branch{ background: var(--surface0); color: var(--mauve); padding: 0 12px; height: 100%; display:flex;align-items:center; gap:4px; }
  .sb-mid   { flex:1; background: var(--surface1); height:100%; display:flex;align-items:center; padding:0 12px; color:var(--subtext0); font-weight:400; }
  .sb-right { background: var(--surface0); color: var(--subtext1); padding: 0 12px; height: 100%; display:flex;align-items:center; gap:8px; }
  .sb-ln    { background: var(--mauve); color: var(--crust); padding: 0 12px; height: 100%; display:flex;align-items:center; font-weight:700; }

  /* ─── STATUS BAR (bottom) ─── */
  #statusbar-bot {
    position: fixed; bottom: 0; left: 0; right: 0; z-index: 500;
    background: var(--mantle);
    border-top: 1px solid var(--surface0);
    display: flex; align-items: center;
    height: 22px; padding: 0 16px;
    font-size: 11px; color: var(--overlay0);
    gap: 16px;
  }
  .sb-hint { color: var(--subtext0); }
  .sb-hint span { color: var(--yellow); }

  /* ─── SIDEBAR (nvim-tree) ─── */
  #sidebar {
    position: fixed; left: 0; top: 26px; bottom: 22px;
    width: 220px; z-index: 400;
    background: var(--mantle);
    border-right: 1px solid var(--surface0);
    padding: 12px 0;
    overflow-y: auto;
  }
  .tree-title {
    padding: 4px 14px 10px;
    font-size: 11px;
    color: var(--overlay0);
    letter-spacing: .08em;
    text-transform: uppercase;
  }
  .tree-item {
    display: flex; align-items: center; gap: 8px;
    padding: 3px 14px;
    font-size: 12.5px;
    color: var(--subtext1);
    cursor: pointer;
    transition: background .1s, color .1s;
    text-decoration: none;
  }
  .tree-item:hover, .tree-item.active {
    background: var(--surface0);
    color: var(--text);
  }
  .tree-item.active { border-left: 2px solid var(--mauve); padding-left: 12px; }
  .tree-icon { font-style: normal; width: 16px; text-align: center; }
  .tree-dir  { color: var(--blue); font-size: 11px; padding: 8px 14px 2px; letter-spacing:.06em; text-transform:uppercase; }

  /* ─── MAIN CONTENT ─── */
  #main {
    margin-left: 220px;
    padding-top: 26px;
    padding-bottom: 22px;
    min-height: 100vh;
  }

  /* ─── TABS ─── */
  #tabs {
    display: flex; align-items: stretch;
    background: var(--mantle);
    border-bottom: 1px solid var(--surface0);
    height: 34px;
    overflow-x: auto;
  }
  #tabs::-webkit-scrollbar { height: 0; }
  .tab {
    display: flex; align-items: center; gap: 6px;
    padding: 0 16px;
    font-size: 12px;
    color: var(--overlay1);
    cursor: pointer;
    border-right: 1px solid var(--surface0);
    white-space: nowrap;
    transition: color .15s, background .15s;
    text-decoration: none;
  }
  .tab:hover { color: var(--subtext1); background: var(--surface0); }
  .tab.active { color: var(--text); background: var(--base); border-top: 2px solid var(--mauve); }
  .tab .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--mauve); opacity: 0; }
  .tab.modified .dot { opacity: 1; }

  /* ─── SECTIONS ─── */
  .section {
    padding: 48px 56px;
    border-bottom: 1px solid var(--surface0);
    animation: fadein .4s ease both;
  }
  @keyframes fadein { from{opacity:0;transform:translateY(10px)} to{opacity:1;transform:none} }

  /* ─── LINE NUMBERS (fake gutter) ─── */
  .with-gutter {
    display: flex;
    gap: 0;
  }
  .gutter {
    min-width: 48px;
    color: var(--surface2);
    font-size: 13px;
    text-align: right;
    padding-right: 16px;
    padding-top: 2px;
    line-height: 1.9;
    user-select: none;
    flex-shrink: 0;
    border-right: 1px solid var(--surface0);
    margin-right: 20px;
  }
  .code-area { flex: 1; }

  /* ─── HERO SECTION ─── */
  #hero {
    padding: 64px 56px 48px;
    border-bottom: 1px solid var(--surface0);
    position: relative;
  }
  .hero-comment { color: var(--overlay0); font-size: 13px; margin-bottom: 8px; }
  .hero-name {
    font-size: clamp(2.4rem, 5vw, 4rem);
    font-weight: 700;
    letter-spacing: -.02em;
    line-height: 1.1;
    margin-bottom: 4px;
  }
  .hero-name .kw  { color: var(--mauve); }
  .hero-name .fn  { color: var(--blue); }
  .hero-name .str { color: var(--green); }
  .hero-name .paren { color: var(--overlay1); }
  .hero-role {
    color: var(--subtext0);
    font-size: 15px;
    margin-bottom: 32px;
    padding-left: 2px;
  }
  .hero-role .hl { color: var(--yellow); }

  .hero-badges { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 36px; }
  .badge {
    display: inline-flex; align-items: center; gap: 6px;
    padding: 4px 10px;
    border-radius: 4px;
    font-size: 11px; font-weight: 600;
    letter-spacing: .04em;
  }
  .badge-green  { background: rgba(166,227,161,.12); color: var(--green);   border: 1px solid rgba(166,227,161,.25); }
  .badge-blue   { background: rgba(137,180,250,.12); color: var(--blue);    border: 1px solid rgba(137,180,250,.25); }
  .badge-mauve  { background: rgba(203,166,247,.12); color: var(--mauve);   border: 1px solid rgba(203,166,247,.25); }
  .badge-yellow { background: rgba(249,226,175,.12); color: var(--yellow);  border: 1px solid rgba(249,226,175,.25); }
  .badge-peach  { background: rgba(250,179,135,.12); color: var(--peach);   border: 1px solid rgba(250,179,135,.25); }

  .hero-btns { display: flex; gap: 12px; flex-wrap: wrap; }
  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 9px 20px;
    border-radius: 6px;
    font-family: var(--mono);
    font-size: 12.5px; font-weight: 600;
    cursor: pointer; transition: all .15s;
    text-decoration: none; border: none;
    letter-spacing: .03em;
  }
  .btn-primary { background: var(--mauve); color: var(--crust); }
  .btn-primary:hover { background: var(--lavender); transform: translateY(-1px); }
  .btn-ghost { background: transparent; color: var(--subtext1); border: 1px solid var(--surface1); }
  .btn-ghost:hover { border-color: var(--mauve); color: var(--mauve); transform: translateY(-1px); }

  /* ─── SECTION HEADERS ─── */
  .sec-header {
    display: flex; align-items: center; gap: 12px;
    margin-bottom: 28px;
  }
  .sec-kw   { color: var(--mauve); font-size: 13px; }
  .sec-name { color: var(--blue); font-size: 22px; font-weight: 700; }
  .sec-line { flex: 1; height: 1px; background: var(--surface0); max-width: 200px; }
  .sec-num  { color: var(--overlay0); font-size: 12px; }

  /* ─── ABOUT ─── */
  .about-block {
    background: var(--mantle);
    border: 1px solid var(--surface0);
    border-radius: 8px;
    padding: 24px 28px;
    font-size: 13.5px;
    color: var(--subtext1);
    line-height: 1.9;
    max-width: 720px;
  }
  .about-block .comment { color: var(--overlay0); }
  .about-block .key { color: var(--mauve); }
  .about-block .val { color: var(--green); }
  .about-block .str { color: var(--yellow); }
  .about-block .num { color: var(--peach); }
  .about-block .bool { color: var(--red); }

  /* ─── SKILLS ─── */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 16px;
  }
  .skill-group {
    background: var(--mantle);
    border: 1px solid var(--surface0);
    border-radius: 8px;
    padding: 18px 20px;
    transition: border-color .2s;
  }
  .skill-group:hover { border-color: var(--surface2); }
  .skill-group-title {
    font-size: 11px; font-weight: 700;
    letter-spacing: .1em; text-transform: uppercase;
    margin-bottom: 12px;
    display: flex; align-items: center; gap: 8px;
  }
  .skill-group-title::before { content:''; display:inline-block; width:3px; height:12px; border-radius:2px; }
  .sg-lang::before   { background: var(--mauve); }
  .sg-lang   .skill-group-title { color: var(--mauve); }
  .sg-front::before  { background: var(--blue); }
  .sg-front  .skill-group-title { color: var(--blue); }
  .sg-back::before   { background: var(--green); }
  .sg-back   .skill-group-title { color: var(--green); }
  .sg-tools::before  { background: var(--yellow); }
  .sg-tools  .skill-group-title { color: var(--yellow); }
  .skill-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .skill-tag {
    font-size: 11.5px; padding: 3px 9px;
    border-radius: 4px;
    background: var(--surface0);
    color: var(--subtext1);
    border: 1px solid var(--surface1);
    transition: all .15s;
  }
  .skill-tag:hover { background: var(--surface1); color: var(--text); }

  /* ─── PROJECTS ─── */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 16px;
  }
  .project-card {
    background: var(--mantle);
    border: 1px solid var(--surface0);
    border-radius: 8px;
    padding: 22px 24px;
    display: flex; flex-direction: column; gap: 14px;
    transition: border-color .2s, transform .2s;
    cursor: pointer; text-decoration: none; color: inherit;
  }
  .project-card:hover { border-color: var(--mauve); transform: translateY(-2px); }
  .project-top { display: flex; align-items: flex-start; justify-content: space-between; gap: 12px; }
  .project-name { color: var(--blue); font-weight: 700; font-size: 15px; }
  .project-status {
    font-size: 10px; font-weight: 700; letter-spacing: .08em;
    padding: 2px 8px; border-radius: 3px;
    flex-shrink: 0;
  }
  .ps-live   { background: rgba(166,227,161,.15); color: var(--green);  border: 1px solid rgba(166,227,161,.3); }
  .ps-wip    { background: rgba(249,226,175,.15); color: var(--yellow); border: 1px solid rgba(249,226,175,.3); }
  .ps-stable { background: rgba(137,180,250,.15); color: var(--blue);   border: 1px solid rgba(137,180,250,.3); }
  .project-desc { color: var(--subtext0); font-size: 13px; line-height: 1.7; }
  .project-stack { display: flex; flex-wrap: wrap; gap: 6px; }
  .project-lang {
    font-size: 11px; padding: 2px 8px;
    border-radius: 3px;
    background: var(--surface0);
    color: var(--mauve);
  }
  .project-links { display: flex; gap: 10px; margin-top: auto; }
  .project-link {
    font-size: 11.5px; color: var(--subtext0);
    text-decoration: none;
    display: flex; align-items: center; gap: 5px;
    transition: color .15s;
  }
  .project-link:hover { color: var(--mauve); }

  /* ─── CONTACT ─── */
  .contact-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 12px; }
  .contact-card {
    background: var(--mantle);
    border: 1px solid var(--surface0);
    border-radius: 8px;
    padding: 16px 20px;
    display: flex; align-items: center; gap: 14px;
    text-decoration: none; color: inherit;
    transition: border-color .2s, transform .2s;
  }
  .contact-card:hover { border-color: var(--mauve); transform: translateY(-1px); }
  .contact-icon { font-size: 20px; width: 24px; text-align: center; }
  .contact-label { font-size: 11px; color: var(--overlay1); }
  .contact-value { font-size: 13px; color: var(--subtext1); margin-top: 2px; }
  .contact-card:hover .contact-value { color: var(--mauve); }

  /* ─── SCROLLBAR ─── */
  ::-webkit-scrollbar { width: 6px; height: 6px; }
  ::-webkit-scrollbar-track { background: var(--mantle); }
  ::-webkit-scrollbar-thumb { background: var(--surface1); border-radius: 3px; }
  ::-webkit-scrollbar-thumb:hover { background: var(--surface2); }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 768px) {
    #sidebar { display: none; }
    #main { margin-left: 0; }
    .section, #hero { padding: 32px 20px; }
    .gutter { display: none; }
    .with-gutter { display: block; }
  }
</style>
</head>
<body>

<!-- Custom cursor -->
<div id="cursor"></div>

<!-- Status bar top -->
<div id="statusbar-top">
  <span class="sb-mode">NORMAL</span>
  <span class="sb-file">󰌞 portfolio/index.lua</span>
  <span class="sb-branch"> main</span>
  <span class="sb-mid">DEV MODE</span>
  <span class="sb-right">
    <span style="color:var(--green)">✓ 0</span>
    <span style="color:var(--yellow)">⚠ 0</span>
    <span>lua</span>
    <span>utf-8</span>
  </span>
  <span class="sb-ln"> ln 1  col 1</span>
</div>

<!-- Sidebar -->
<nav id="sidebar">
  <div class="tree-title"> nvim-tree</div>
  <div class="tree-dir">portfolio/</div>
  <a class="tree-item active" href="#hero">
    <i class="tree-icon">󰌞</i> init.lua
  </a>
  <a class="tree-item" href="#about">
    <i class="tree-icon">󰆼</i> about.lua
  </a>
  <a class="tree-item" href="#skills">
    <i class="tree-icon"></i> stack.toml
  </a>
  <a class="tree-item" href="#projects">
    <i class="tree-icon">󰙀</i> projects.lua
  </a>
  <a class="tree-item" href="#contact">
    <i class="tree-icon">󰇮</i> contact.lua
  </a>
  <div class="tree-dir" style="margin-top:16px">recent</div>
  <a class="tree-item" href="#projects">
    <i class="tree-icon" style="color:var(--yellow)">󰈙</i> project_alpha
  </a>
  <a class="tree-item" href="#projects">
    <i class="tree-icon" style="color:var(--mauve)">󰈙</i> project_beta
  </a>
  <a class="tree-item" href="#projects">
    <i class="tree-icon" style="color:var(--blue)">󰈙</i> project_gamma
  </a>
</nav>

<!-- Main content -->
<div id="main">

  <!-- Tabs -->
  <div id="tabs">
    <a class="tab active" href="#hero">
      <span class="dot"></span>init.lua
    </a>
    <a class="tab modified" href="#about">
      <span class="dot"></span>about.lua
    </a>
    <a class="tab" href="#skills">
      <span class="dot"></span>stack.toml
    </a>
    <a class="tab modified" href="#projects">
      <span class="dot"></span>projects.lua
    </a>
    <a class="tab" href="#contact">
      <span class="dot"></span>contact.lua
    </a>
  </div>

  <!-- HERO -->
  <section id="hero">
    <div class="with-gutter">
      <div class="gutter">
        1<br/>2<br/>3<br/>4<br/>5<br/>6<br/>7<br/>8<br/>9<br/>10<br/>11<br/>12
      </div>
      <div class="code-area">
        <p class="hero-comment">-- ┌─────────────────────────────────────────┐</p>
        <p class="hero-comment">-- │  DEV MODE  ·  portfolio/init.lua        │</p>
        <p class="hero-comment">-- └─────────────────────────────────────────┘</p>
        <br/>
        <div class="hero-name">
          <span class="kw">local</span>&nbsp;
          <span class="fn">me</span>
          <span class="paren"> = {</span>
        </div>
        <div style="padding-left:24px;margin:8px 0 4px;font-size:clamp(1.6rem,3.5vw,2.8rem);font-weight:700;">
          <span style="color:var(--subtext0);font-size:14px;font-weight:400;">name</span>
          <span style="color:var(--overlay0)"> = </span>
          <span class="hero-name" style="font-size:clamp(1.6rem,3.5vw,2.8rem);">
            <span class="str">"Your Name Here"</span>
          </span>
        </div>
        <div class="hero-role" style="padding-left:24px;">
          <span style="color:var(--overlay0)">role </span>
          <span style="color:var(--overlay0)">= </span>
          <span class="hl">"Full Stack Developer"</span>
          <span style="color:var(--overlay0)"> .. </span>
          <span style="color:var(--sapphire)">" · Open Source · Vim Cultist"</span>
        </div>
        <br/>
        <div class="hero-badges">
          <span class="badge badge-green">⚡ Available for hire</span>
          <span class="badge badge-blue"> Remote</span>
          <span class="badge badge-mauve">󰌞 Neovim btw</span>
          <span class="badge badge-yellow"> 3+ yrs exp</span>
          <span class="badge badge-peach"> Open Source</span>
        </div>
        <div class="hero-btns">
          <a class="btn btn-primary" href="#projects">:view projects&lt;CR&gt;</a>
          <a class="btn btn-ghost" href="#contact">:open contact&lt;CR&gt;</a>
          <a class="btn btn-ghost" href="#">:get resume&lt;CR&gt;</a>
        </div>
      </div>
    </div>
  </section>

  <!-- ABOUT -->
  <section class="section" id="about">
    <div class="sec-header">
      <span class="sec-kw">--</span>
      <span class="sec-name">about.lua</span>
      <div class="sec-line"></div>
      <span class="sec-num">buf 2</span>
    </div>
    <div class="with-gutter">
      <div class="gutter">
        14<br/>15<br/>16<br/>17<br/>18<br/>19<br/>20<br/>21<br/>22<br/>23<br/>24<br/>25<br/>26
      </div>
      <div class="code-area">
        <div class="about-block">
          <p><span class="comment">---@type Developer</span></p>
          <p><span class="key">local</span> <span style="color:var(--blue)">profile</span> = {</p>
          <p style="padding-left:20px"><span class="key">location</span>   = <span class="str">"[Your City, Country]"</span>,</p>
          <p style="padding-left:20px"><span class="key">timezone</span>   = <span class="str">"UTC+[X]"</span>,</p>
          <p style="padding-left:20px"><span class="key">exp_years</span>  = <span class="num">3</span>,</p>
          <p style="padding-left:20px"><span class="key">open_source</span>= <span class="bool">true</span>,</p>
          <p style="padding-left:20px"><span class="key">for_hire</span>   = <span class="bool">true</span>,</p>
          <br/>
          <p style="padding-left:20px"><span class="key">currently</span> = {</p>
          <p style="padding-left:40px"><span class="key">building</span>  = <span class="str">"[your current project]"</span>,</p>
          <p style="padding-left:40px"><span class="key">learning</span>  = <span class="str">{ "Rust", "WebAssembly", "Zig" }</span>,</p>
          <p style="padding-left:40px"><span class="key">obsessing</span> = <span class="str">"making dotfiles prettier than my social life"</span>,</p>
          <p style="padding-left:20px">},</p>
          <p>}</p>
        </div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section class="section" id="skills">
    <div class="sec-header">
      <span class="sec-kw">--</span>
      <span class="sec-name">stack.toml</span>
      <div class="sec-line"></div>
      <span class="sec-num">buf 3</span>
    </div>
    <div class="skills-grid">
      <div class="skill-group sg-lang">
        <div class="skill-group-title">Languages</div>
        <div class="skill-tags">
          <span class="skill-tag">JavaScript</span>
          <span class="skill-tag">TypeScript</span>
          <span class="skill-tag">Python</span>
          <span class="skill-tag">Rust</span>
          <span class="skill-tag">Go</span>
          <span class="skill-tag">Lua</span>
          <span class="skill-tag">C++</span>
          <span class="skill-tag">Shell</span>
        </div>
      </div>
      <div class="skill-group sg-front">
        <div class="skill-group-title">Frontend</div>
        <div class="skill-tags">
          <span class="skill-tag">React</span>
          <span class="skill-tag">Next.js</span>
          <span class="skill-tag">Vue</span>
          <span class="skill-tag">Svelte</span>
          <span class="skill-tag">Tailwind</span>
          <span class="skill-tag">Three.js</span>
          <span class="skill-tag">WebGL</span>
        </div>
      </div>
      <div class="skill-group sg-back">
        <div class="skill-group-title">Backend</div>
        <div class="skill-tags">
          <span class="skill-tag">Node.js</span>
          <span class="skill-tag">FastAPI</span>
          <span class="skill-tag">GraphQL</span>
          <span class="skill-tag">PostgreSQL</span>
          <span class="skill-tag">Redis</span>
          <span class="skill-tag">Docker</span>
          <span class="skill-tag">Kubernetes</span>
        </div>
      </div>
      <div class="skill-group sg-tools">
        <div class="skill-group-title">Tools</div>
        <div class="skill-tags">
          <span class="skill-tag">Neovim</span>
          <span class="skill-tag">LazyVim</span>
          <span class="skill-tag">Git</span>
          <span class="skill-tag">Linux</span>
          <span class="skill-tag">Tmux</span>
          <span class="skill-tag">AWS</span>
          <span class="skill-tag">Figma</span>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section class="section" id="projects">
    <div class="sec-header">
      <span class="sec-kw">--</span>
      <span class="sec-name">projects.lua</span>
      <div class="sec-line"></div>
      <span class="sec-num">buf 4</span>
    </div>
    <div class="projects-grid">

      <a class="project-card" href="#">
        <div class="project-top">
          <span class="project-name">project_alpha</span>
          <span class="project-status ps-live">LIVE</span>
        </div>
        <p class="project-desc">Full-stack SaaS platform with real-time collaboration. Built for scale — 12k+ users, 99.9% uptime across multi-region AWS.</p>
        <div class="project-stack">
          <span class="project-lang">Next.js</span>
          <span class="project-lang">Rust</span>
          <span class="project-lang">Redis</span>
          <span class="project-lang">PostgreSQL</span>
        </div>
        <div class="project-links">
          <a class="project-link" href="#">⌥ GitHub →</a>
          <a class="project-link" href="#">⎋ Live →</a>
        </div>
      </a>

      <a class="project-card" href="#">
        <div class="project-top">
          <span class="project-name">project_beta</span>
          <span class="project-status ps-wip">WIP</span>
        </div>
        <p class="project-desc">Browser-native ML inference using WebAssembly + ONNX. Zero backend, zero tracking. Runs GPT-2 at 60fps in the browser.</p>
        <div class="project-stack">
          <span class="project-lang">Rust</span>
          <span class="project-lang">WASM</span>
          <span class="project-lang">TypeScript</span>
          <span class="project-lang">ONNX</span>
        </div>
        <div class="project-links">
          <a class="project-link" href="#">⌥ GitHub →</a>
        </div>
      </a>

      <a class="project-card" href="#">
        <div class="project-top">
          <span class="project-name">project_gamma</span>
          <span class="project-status ps-stable">STABLE</span>
        </div>
        <p class="project-desc">TUI dashboard for monitoring k8s clusters in real-time. Built with Go + Bubble Tea. Ships as a single static binary.</p>
        <div class="project-stack">
          <span class="project-lang">Go</span>
          <span class="project-lang">Bubble Tea</span>
          <span class="project-lang">Kubernetes</span>
        </div>
        <div class="project-links">
          <a class="project-link" href="#">⌥ GitHub →</a>
          <a class="project-link" href="#">⎋ Docs →</a>
        </div>
      </a>

      <a class="project-card" href="#">
        <div class="project-top">
          <span class="project-name">project_delta</span>
          <span class="project-status ps-stable">STABLE</span>
        </div>
        <p class="project-desc">Open source developer CLI toolkit. 2k+ GitHub stars, used in 400+ projects. Plugin architecture, fully extensible.</p>
        <div class="project-stack">
          <span class="project-lang">TypeScript</span>
          <span class="project-lang">Node.js</span>
          <span class="project-lang">Shell</span>
        </div>
        <div class="project-links">
          <a class="project-link" href="#">⌥ GitHub →</a>
          <a class="project-link" href="#">⎋ Docs →</a>
        </div>
      </a>

    </div>
  </section>

  <!-- CONTACT -->
  <section class="section" id="contact">
    <div class="sec-header">
      <span class="sec-kw">--</span>
      <span class="sec-name">contact.lua</span>
      <div class="sec-line"></div>
      <span class="sec-num">buf 5</span>
    </div>
    <p style="color:var(--subtext0);font-size:13px;margin-bottom:20px;max-width:500px;">
      <span style="color:var(--overlay0)">-- </span>Open to freelance, full-time, and OSS collaboration.<br/>
      <span style="color:var(--overlay0)">-- </span>Best reached via email or GitHub issues.
    </p>
    <div class="contact-grid">
      <a class="contact-card" href="mailto:you@domain.dev">
        <span class="contact-icon">✉</span>
        <div>
          <div class="contact-label">email</div>
          <div class="contact-value">you@domain.dev</div>
        </div>
      </a>
      <a class="contact-card" href="https://github.com/yourusername" target="_blank">
        <span class="contact-icon">⌥</span>
        <div>
          <div class="contact-label">github</div>
          <div class="contact-value">@yourusername</div>
        </div>
      </a>
      <a class="contact-card" href="https://twitter.com/yourhandle" target="_blank">
        <span class="contact-icon">𝕏</span>
        <div>
          <div class="contact-label">twitter / x</div>
          <div class="contact-value">@yourhandle</div>
        </div>
      </a>
      <a class="contact-card" href="https://linkedin.com/in/yourprofile" target="_blank">
        <span class="contact-icon">in</span>
        <div>
          <div class="contact-label">linkedin</div>
          <div class="contact-value">yourprofile</div>
        </div>
      </a>
    </div>

    <div style="margin-top:48px; padding-top:24px; border-top:1px solid var(--surface0); color:var(--overlay0); font-size:12px;">
      <span style="color:var(--overlay1)">-- EOF  </span>
      [ buf 5/5 ]  [ ln 337 / col 1 ]  [ lua ]  [ unix ]  ──
      <span style="color:var(--mauve)"> NORMAL</span>
    </div>
  </section>

</div><!-- /main -->

<!-- Status bar bottom -->
<div id="statusbar-bot">
  <span class="sb-hint"><span>gg</span> top · <span>G</span> bottom · <span>&lt;leader&gt;ff</span> find file</span>
  <span style="flex:1"></span>
  <span>spaces: 2</span>
  <span>lua</span>
  <span style="color:var(--green)">✓ no errors</span>
</div>

<script>
  // Cursor
  const cur = document.getElementById('cursor');
  document.addEventListener('mousemove', e => {
    cur.style.left = e.clientX + 'px';
    cur.style.top  = e.clientY + 'px';
  });

  // Active sidebar + tab on scroll
  const sections = document.querySelectorAll('section[id]');
  const treeItems = document.querySelectorAll('.tree-item');
  const tabs = document.querySelectorAll('.tab');
  const lnEl = document.querySelector('.sb-ln');
  let lineNum = 1;

  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(s => {
      if (window.scrollY >= s.offsetTop - 80) current = s.id;
    });
    treeItems.forEach(i => {
      i.classList.toggle('active', i.getAttribute('href') === '#' + current);
    });
    tabs.forEach(t => {
      const href = t.getAttribute('href');
      const active = href === '#' + current || (current === 'hero' && href === '#hero');
      t.classList.toggle('active', active);
    });
    lineNum = Math.floor(window.scrollY / 20) + 1;
    lnEl.textContent = ` ln ${lineNum}  col 1`;
  });

  // Hover title change
  document.querySelectorAll('.tree-item').forEach(item => {
    item.addEventListener('mouseenter', () => {
      document.querySelector('.sb-mid').textContent = item.textContent.trim();
    });
    item.addEventListener('mouseleave', () => {
      document.querySelector('.sb-mid').textContent = 'DEV MODE';
    });
  });
</script>
</body>
</html>
