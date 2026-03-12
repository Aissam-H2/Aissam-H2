<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>:e ~/portfolio.md</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700;800&display=swap" rel="stylesheet"/>
<style>
:root{
  --bg:#0d0e16;--bg2:#12131f;--bg3:#1a1b2e;--surface:#1e1f33;--border:#2a2d4a;
  --green:#57c7a0;--blue:#7aa2f7;--purple:#bb9af7;--cyan:#2ac3de;
  --yellow:#e0af68;--orange:#ff9e64;--red:#f7768e;
  --text:#c0caf5;--dim:#565f89;--muted:#414868;
}
*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{background:var(--bg);color:var(--text);font-family:'JetBrains Mono',monospace;min-height:100vh;overflow-x:hidden;}
body::before{content:'';position:fixed;inset:0;background:repeating-linear-gradient(0deg,transparent,transparent 3px,rgba(0,0,0,.1) 3px,rgba(0,0,0,.1) 4px);pointer-events:none;z-index:9000;}
body::after{content:'';position:fixed;inset:0;background:radial-gradient(ellipse at center,transparent 55%,rgba(0,0,0,.7) 100%);pointer-events:none;z-index:8999;}
#particles{position:fixed;inset:0;pointer-events:none;z-index:1;overflow:hidden;}
.pt{position:absolute;border-radius:50%;animation:pfloat linear infinite;opacity:0;}
@keyframes pfloat{0%{transform:translateY(100vh) translateX(0);opacity:0;}10%{opacity:.5;}90%{opacity:.15;}100%{transform:translateY(-5vh) translateX(var(--dx));opacity:0;}}
#tabbar{position:sticky;top:0;z-index:500;background:var(--bg2);border-bottom:1px solid var(--border);display:flex;align-items:stretch;}
.tab{padding:9px 16px;font-size:11px;color:var(--dim);border-right:1px solid var(--border);cursor:pointer;display:flex;align-items:center;gap:7px;transition:all .2s;white-space:nowrap;}
.tab:hover{color:var(--text);background:var(--bg3);}
.tab.active{color:var(--text);background:var(--bg);border-bottom:2px solid var(--green);margin-bottom:-1px;}
.tdot{width:7px;height:7px;border-radius:50%;flex-shrink:0;}
.sbar{margin-left:auto;padding:0 12px;font-size:11px;color:var(--dim);display:flex;align-items:center;gap:12px;}
.mode{background:var(--green);color:var(--bg);padding:4px 10px;font-weight:800;font-size:11px;letter-spacing:.1em;}
#hero{min-height:100vh;display:flex;flex-direction:column;justify-content:center;max-width:920px;margin:0 auto;padding:60px 28px;position:relative;z-index:10;}
.lnum{color:var(--muted);margin-right:16px;font-size:12px;user-select:none;display:inline-block;min-width:20px;text-align:right;}
.hero-name{font-size:clamp(38px,7vw,76px);font-weight:800;line-height:1;letter-spacing:-.03em;background:linear-gradient(135deg,var(--blue),var(--purple),var(--cyan));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;animation:nameGlow 3s ease-in-out infinite alternate;}
@keyframes nameGlow{from{filter:drop-shadow(0 0 6px rgba(122,162,247,.3));}to{filter:drop-shadow(0 0 28px rgba(187,154,247,.7));}}
.hero-role{font-size:15px;color:var(--green);font-weight:600;margin:10px 0 6px;letter-spacing:.05em;}
.hero-sub{font-size:12px;color:var(--dim);}
.cblink{display:inline-block;width:10px;height:18px;background:var(--cyan);animation:blink .9s step-end infinite;vertical-align:middle;margin-left:2px;}
@keyframes blink{0%,100%{opacity:1;}50%{opacity:0;}}
.hero-pills{display:flex;flex-wrap:wrap;gap:8px;margin-top:28px;}
.pill{padding:5px 14px;border:1px solid var(--border);font-size:11px;color:var(--dim);letter-spacing:.05em;transition:all .2s;cursor:default;}
.pill:hover{border-color:var(--green);color:var(--green);background:rgba(87,199,160,.06);}
.sec{max-width:920px;margin:0 auto;padding:44px 28px;position:relative;z-index:10;}
.sec-head{display:flex;align-items:center;gap:12px;margin-bottom:26px;padding-bottom:10px;border-bottom:1px solid var(--border);}
.sec-title{font-size:12px;font-weight:700;letter-spacing:.12em;color:var(--yellow);}
.sec-title::before{content:'## ';color:var(--muted);}
.sec-rule{flex:1;height:1px;background:linear-gradient(to right,var(--border),transparent);}
#pixel-sec{background:var(--bg2);border:1px solid var(--border);padding:28px 20px;margin-bottom:36px;position:relative;overflow:hidden;}
#pixel-sec::after{content:'neovim.shrine';position:absolute;top:0;right:0;background:var(--green);color:var(--bg);font-size:10px;font-weight:800;padding:3px 12px;letter-spacing:.1em;}
.canvas-row{display:flex;justify-content:center;align-items:flex-end;gap:28px;flex-wrap:wrap;padding:12px 0;}
.pxwrap{text-align:center;}
.pxwrap canvas{image-rendering:pixelated;display:block;margin:0 auto;animation:bob 2.2s ease-in-out infinite;}
.pxwrap:nth-child(2) canvas{animation-delay:.5s;}
.pxwrap:nth-child(3) canvas{animation-delay:1s;}
.pxwrap:nth-child(4) canvas{animation-delay:1.5s;}
@keyframes bob{0%,100%{transform:translateY(0);}50%{transform:translateY(-10px);}}
.pxlabel{font-size:10px;color:var(--dim);margin-top:8px;letter-spacing:.07em;}
.term{background:#080910;border:1px solid var(--border);overflow:hidden;margin-bottom:32px;}
.term-top{display:flex;align-items:center;gap:7px;padding:9px 14px;background:#0d0e16;border-bottom:1px solid var(--border);}
.tdd{width:12px;height:12px;border-radius:50%;}
.term-name{margin-left:auto;font-size:11px;color:var(--dim);}
.term-body{padding:18px 22px;}
.tl{font-size:12.5px;line-height:2.1;opacity:0;animation:lin .2s ease forwards;}
@keyframes lin{to{opacity:1;}}
.g{color:var(--green);}.b{color:var(--blue);}.pu{color:var(--purple);}
.c{color:var(--cyan);}.y{color:var(--yellow);}.o{color:var(--orange);}
.r{color:var(--red);}.d{color:var(--dim);}
.lang-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(105px,1fr));gap:10px;margin-bottom:36px;}
.lcard{background:var(--bg2);border:1px solid var(--border);padding:16px 10px;text-align:center;transition:all .25s;cursor:default;position:relative;overflow:hidden;}
.lcard::before{content:'';position:absolute;inset:0;background:var(--lc,var(--blue));opacity:0;transition:opacity .25s;}
.lcard:hover{border-color:var(--lc,var(--blue));transform:translateY(-5px);box-shadow:0 10px 30px rgba(0,0,0,.5);}
.lcard:hover::before{opacity:.07;}
.lcard img{width:34px;height:34px;display:block;margin:0 auto 8px;position:relative;z-index:1;}
.lname{font-size:10px;color:var(--dim);letter-spacing:.07em;position:relative;z-index:1;}
.lbar{height:2px;background:var(--muted);margin-top:8px;overflow:hidden;}
.lbar-f{height:100%;background:var(--lc,var(--blue));transform:scaleX(0);transform-origin:left;animation:barIn 1.4s ease forwards;}
@keyframes barIn{to{transform:scaleX(1);}}
.proj-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(360px,1fr));gap:14px;margin-bottom:36px;}
.pcard{background:var(--bg2);border:1px solid var(--border);padding:22px;transition:all .25s;position:relative;overflow:hidden;}
.pcard::after{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(to right,var(--pc,var(--blue)),transparent);}
.pcard:hover{border-color:var(--pc,var(--blue));transform:translateY(-4px);box-shadow:0 14px 36px rgba(0,0,0,.5);}
.pname{font-size:14px;font-weight:700;color:var(--pc,var(--blue));margin-bottom:8px;}
.pdesc{font-size:12px;color:var(--dim);line-height:1.7;margin-bottom:12px;}
.ptags{display:flex;flex-wrap:wrap;gap:6px;}
.ptag{font-size:10px;padding:2px 8px;border:1px solid var(--muted);color:var(--dim);}
.stats-row{display:grid;grid-template-columns:repeat(auto-fill,minmax(165px,1fr));gap:10px;margin-bottom:28px;}
.scard{background:var(--bg2);border:1px solid var(--border);padding:22px;text-align:center;}
.snum{font-size:36px;font-weight:800;}
.slabel{font-size:10px;color:var(--dim);letter-spacing:.1em;margin-top:4px;}
#footer{border-top:1px solid var(--border);background:var(--bg2);padding:22px;text-align:center;font-size:11px;color:var(--dim);position:relative;z-index:10;}
.reveal{opacity:0;transform:translateY(24px);transition:opacity .6s ease,transform .6s ease;}
.reveal.vis{opacity:1;transform:translateY(0);}
::-webkit-scrollbar{width:3px;}
::-webkit-scrollbar-track{background:var(--bg);}
::-webkit-scrollbar-thumb{background:var(--muted);}
</style>
</head>
<body>
<div id="particles"></div>

<div id="tabbar">
  <div class="tab active"><span class="tdot" style="background:#57c7a0"></span>portfolio.md</div>
  <div class="tab"><span class="tdot" style="background:#e0af68"></span>init.lua</div>
  <div class="tab"><span class="tdot" style="background:#7aa2f7"></span>projects/</div>
  <div class="tab"><span class="tdot" style="background:#f7768e"></span>contact.sh</div>
  <div class="sbar">
    <span class="mode">NORMAL</span>
    <span style="color:var(--green)">⎇ main</span>
    <span id="ldisp" style="color:var(--dim)">ln 1</span>
    <span id="clk" style="color:var(--cyan)"></span>
  </div>
</div>

<div id="hero">
  <div style="margin-bottom:20px;line-height:2.2;font-size:12px;">
    <div><span class="lnum">1</span><span class="d">-- ╔══════════════════════════════════╗</span></div>
    <div><span class="lnum">2</span><span class="d">-- ║   welcome to my portfolio        ║</span></div>
    <div><span class="lnum">3</span><span class="d">-- ╚══════════════════════════════════╝</span></div>
  </div>
  <div style="font-size:13px;color:var(--dim);margin-bottom:4px;"><span class="lnum">4</span><span style="color:var(--blue)">local</span> <span style="color:var(--green)">me</span> <span style="color:var(--dim)">=</span> {</div>
  <div style="padding-left:28px;margin:8px 0;">
    <div class="hero-name">YourName<span class="cblink"></span></div>
    <div class="hero-role">Full-Stack Dev &amp; Neovim Monk</div>
    <div class="hero-sub">crafting software from the terminal, one keymap at a time</div>
  </div>
  <div style="font-size:13px;color:var(--dim);"><span class="lnum">5</span>}</div>
  <div class="hero-pills">
    <div class="pill">🏯 neovim btw</div>
    <div class="pill">☕ coffee → code</div>
    <div class="pill">🐧 arch btw</div>
    <div class="pill">⚡ wezterm</div>
    <div class="pill">🌙 tokyo-night</div>
    <div class="pill">🎵 lo-fi OST</div>
  </div>
</div>

<!-- PIXEL NEOVIM -->
<div class="sec">
  <div class="sec-head reveal">
    <span class="sec-title">Neovim Shrine</span>
    <div class="sec-rule"></div>
  </div>
  <div id="pixel-sec" class="reveal">
    <div class="canvas-row" id="canvas-row"></div>
    <div style="text-align:center;margin-top:14px;font-size:12px;color:var(--dim);">
      <span style="color:var(--green)">:help neovim</span> — my editor, my religion, my entire personality
    </div>
  </div>
</div>

<!-- TERMINAL -->
<div class="sec">
  <div class="sec-head reveal"><span class="sec-title">About Me</span><div class="sec-rule"></div></div>
  <div class="term reveal">
    <div class="term-top">
      <div class="tdd" style="background:#f7768e"></div>
      <div class="tdd" style="background:#e0af68"></div>
      <div class="tdd" style="background:#57c7a0"></div>
      <div class="term-name">~  zsh  ──  nvim  ──  tmux</div>
    </div>
    <div class="term-body" id="term-body"></div>
  </div>
</div>

<!-- LANGUAGES -->
<div class="sec">
  <div class="sec-head reveal"><span class="sec-title">Languages &amp; Tools</span><div class="sec-rule"></div></div>
  <div class="lang-grid reveal" id="lang-grid"></div>
</div>

<!-- PROJECTS -->
<div class="sec">
  <div class="sec-head reveal"><span class="sec-title">Featured Projects</span><div class="sec-rule"></div></div>
  <div class="proj-grid reveal" id="proj-grid"></div>
</div>

<!-- STATS -->
<div class="sec">
  <div class="sec-head reveal"><span class="sec-title">GitHub Stats</span><div class="sec-rule"></div></div>
  <div class="stats-row reveal" id="stats-row"></div>
  <div class="reveal" style="text-align:center;">
    <img src="https://github-readme-streak-stats.herokuapp.com/?user=yourusername&theme=tokyonight&hide_border=true&background=12131f&ring=57c7a0&fire=ff9e64&currStreakLabel=57c7a0&border_radius=0" style="max-width:100%;border:1px solid var(--border);" alt="streak stats"/>
  </div>
</div>

<div id="footer">
  <span style="color:var(--green)">:wq</span> &nbsp;·&nbsp; built inside neovim &nbsp;·&nbsp;
  <span style="color:var(--purple)">tokyo-night</span> &nbsp;·&nbsp;
  <span style="color:var(--cyan)">© 2025 YourName</span>
  <br/><br/>
  <span style="color:var(--muted)">-- INSERT mode: feel free to fork --</span>
</div>

<script>
// Clock
const clk=document.getElementById('clk');
const tick=()=>{const n=new Date();clk.textContent=n.toLocaleTimeString('en',{hour:'2-digit',minute:'2-digit'});};
tick();setInterval(tick,1000);

// Scroll line
window.addEventListener('scroll',()=>{
  const p=window.scrollY/(document.body.scrollHeight-window.innerHeight||1);
  document.getElementById('ldisp').textContent='ln '+(Math.floor(p*420)+1);
});

// Particles
const pc=document.getElementById('particles');
const cols=['#57c7a0','#7aa2f7','#bb9af7','#2ac3de','#e0af68'];
for(let i=0;i<50;i++){
  const el=document.createElement('div');el.className='pt';
  const sz=Math.random()*3+1;
  el.style.cssText=`left:${Math.random()*100}%;width:${sz}px;height:${sz}px;background:${cols[i%cols.length]};--dx:${(Math.random()-.5)*120}px;animation-duration:${7+Math.random()*12}s;animation-delay:${Math.random()*10}s;`;
  pc.appendChild(el);
}

// ── Pixel Neovim ──
function drawNvim(canvas,variant,scale){
  const ctx=canvas.getContext('2d');
  const P={
    green:['#57c7a0','#3d9e7a','#1e5e48'],
    blue: ['#7aa2f7','#4a72d0','#2a44a0'],
    purple:['#bb9af7','#8a6ad0','#5a3aaa'],
    fire: ['#ff9e64','#f7768e','#aa2244'],
  }[variant]||['#57c7a0','#3d9e7a','#1e5e48'];
  const S='#e0af68',T='transparent';

  // Two-frame pixel art: stylized N + vim lightning bolt
  const frames=[
    [
      T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,
      T,P[0],P[0],T,T,T,T,T,T,T,P[0],P[0],T,T,T,T,
      T,P[0],P[1],P[0],T,T,T,T,T,P[0],P[1],P[0],T,T,T,T,
      T,P[0],P[1],P[1],P[0],T,T,T,P[0],P[1],P[1],P[0],T,T,T,T,
      T,P[0],P[1],P[1],P[1],P[0],T,P[0],P[1],P[1],P[1],P[0],T,T,T,T,
      T,P[0],P[1],P[2],P[1],P[1],P[0],P[1],P[2],P[1],P[1],P[0],T,T,T,T,
      T,P[0],P[1],T,P[1],P[1],P[1],P[1],P[1],P[1],P[0],T,T,T,T,T,
      T,P[0],P[1],T,T,P[1],P[1],P[1],P[1],P[0],T,T,T,T,T,T,
      T,P[0],P[1],T,T,T,P[1],P[1],P[0],T,T,T,T,T,T,T,
      T,P[0],P[0],T,T,T,T,P[0],P[0],T,T,T,T,T,T,T,
      T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,
      T,T,T,S,S,S,T,T,T,T,T,T,T,T,T,T,
      T,T,S,S,S,S,S,T,T,T,T,T,T,T,T,T,
      T,T,T,T,S,S,T,T,T,T,T,T,T,T,T,T,
      T,T,T,T,S,T,T,T,T,T,T,T,T,T,T,T,
      T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,
    ],
    [
      T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,
      T,P[0],P[0],T,T,T,T,T,T,T,P[0],P[0],T,T,T,T,
      T,P[0],P[1],P[0],T,T,T,T,T,P[0],P[1],P[0],T,T,T,T,
      T,P[0],P[1],P[1],P[0],T,T,T,P[0],P[1],P[1],P[0],T,T,T,T,
      T,P[0],P[1],P[1],P[1],P[0],T,P[0],P[1],P[1],P[1],P[0],T,T,T,T,
      T,P[0],P[1],P[2],P[1],P[1],P[0],P[1],P[2],P[1],P[1],P[0],T,T,T,T,
      T,P[0],P[1],T,P[1],P[1],P[1],P[1],P[1],P[1],P[0],T,T,T,T,T,
      T,P[0],P[1],T,T,P[1],P[1],P[1],P[1],P[0],T,T,T,T,T,T,
      T,P[0],P[1],T,T,T,P[1],P[1],P[0],T,T,T,T,T,T,T,
      T,P[0],P[0],T,T,T,T,P[0],P[0],T,T,T,T,T,T,T,
      T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,
      T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,
      T,T,T,S,S,S,T,T,T,T,T,T,T,T,T,T,
      T,T,S,S,S,S,S,T,T,T,T,T,T,T,T,T,
      T,T,T,T,S,S,T,T,T,T,T,T,T,T,T,T,
      T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,T,
    ],
  ];
  canvas.width=16*scale;canvas.height=16*scale;
  let f=0;
  function draw(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    frames[f].forEach((col,i)=>{
      if(col===T)return;
      ctx.fillStyle=col;
      ctx.fillRect((i%16)*scale,Math.floor(i/16)*scale,scale,scale);
    });
    f=(f+1)%frames.length;
  }
  draw();setInterval(draw,550);
}

const cr=document.getElementById('canvas-row');
[
  {v:'green',label:'v0.10 stable',sc:11},
  {v:'blue',label:':Lazy sync',sc:9},
  {v:'purple',label:'lsp attached',sc:13},
  {v:'fire',label:'gg dd undo',sc:10},
].forEach(({v,label,sc})=>{
  const w=document.createElement('div');w.className='pxwrap';
  const c=document.createElement('canvas');
  const l=document.createElement('div');l.className='pxlabel';l.textContent=label;
  w.append(c,l);cr.appendChild(w);
  drawNvim(c,v,sc);
});

// Terminal
const lines=[
  {h:`<span class="g">❯</span> <span class="b">whoami</span>`,d:300},
  {h:`<span class="g">yourname</span> — full-stack dev, neovim monk`,d:700},
  {h:`<span class="g">❯</span> <span class="b">cat</span> about.txt`,d:1300},
  {h:`  <span class="y">name</span>     <span class="d">=</span> <span class="c">"Your Name"</span>`,d:1700},
  {h:`  <span class="y">location</span> <span class="d">=</span> <span class="c">"Earth / Remote"</span>`,d:2000},
  {h:`  <span class="y">editor</span>   <span class="d">=</span> <span class="g">"neovim"</span>  <span class="d">-- obviously</span>`,d:2300},
  {h:`  <span class="y">os</span>       <span class="d">=</span> <span class="pu">"Arch Linux"</span>  <span class="d">-- btw</span>`,d:2600},
  {h:`  <span class="y">theme</span>    <span class="d">=</span> <span class="pu">"tokyo-night"</span>`,d:2900},
  {h:`  <span class="y">music</span>    <span class="d">=</span> <span class="o">"Hiroyuki Sawano OSTs"</span>`,d:3200},
  {h:`<span class="g">❯</span> <span class="b">nvim</span> <span class="d">.</span>   <span class="d">  # entering vim, never leaving</span>`,d:3700},
];
const tb=document.getElementById('term-body');
lines.forEach(({h,d},i)=>{
  setTimeout(()=>{
    const el=document.createElement('div');
    el.className='tl';el.innerHTML=h;
    el.style.animationDelay='0s';
    tb.appendChild(el);
    tb.scrollTop=tb.scrollHeight;
  },d);
});

// Languages
const langs=[
  {n:'TypeScript',i:'https://cdn.simpleicons.org/typescript/3178c6',lc:'#3178c6',p:.9},
  {n:'JavaScript',i:'https://cdn.simpleicons.org/javascript/f7df1e',lc:'#f7df1e',p:.92},
  {n:'Python',i:'https://cdn.simpleicons.org/python/3776ab',lc:'#3776ab',p:.8},
  {n:'Lua',i:'https://cdn.simpleicons.org/lua/2c2d72',lc:'#7aa2f7',p:.75},
  {n:'Rust',i:'https://cdn.simpleicons.org/rust/ce422b',lc:'#ff9e64',p:.6},
  {n:'Go',i:'https://cdn.simpleicons.org/go/00add8',lc:'#2ac3de',p:.65},
  {n:'React',i:'https://cdn.simpleicons.org/react/61dafb',lc:'#61dafb',p:.88},
  {n:'Node.js',i:'https://cdn.simpleicons.org/nodedotjs/339933',lc:'#57c7a0',p:.85},
  {n:'PostgreSQL',i:'https://cdn.simpleicons.org/postgresql/4169e1',lc:'#7aa2f7',p:.78},
  {n:'Docker',i:'https://cdn.simpleicons.org/docker/2496ed',lc:'#2496ed',p:.8},
  {n:'Linux',i:'https://cdn.simpleicons.org/linux/fcc624',lc:'#e0af68',p:.95},
  {n:'Neovim',i:'https://cdn.simpleicons.org/neovim/57a143',lc:'#57c7a0',p:1.0},
];
const lg=document.getElementById('lang-grid');
langs.forEach(({n,i,lc,p},idx)=>{
  lg.innerHTML+=`<div class="lcard" style="--lc:${lc}">
    <img src="${i}" alt="${n}" onerror="this.style.opacity='.3'"/>
    <div class="lname">${n}</div>
    <div class="lbar"><div class="lbar-f" style="background:${lc};width:${p*100}%;animation-delay:${.5+idx*.07}s"></div></div>
  </div>`;
});

// Projects
const projs=[
  {n:'⚡ project-alpha',d:'A blazing-fast full-stack app built in 72h hackathon. Handles 10k+ req/s without breaking a sweat.',t:['Next.js','tRPC','Postgres','Redis'],pc:'#57c7a0'},
  {n:'🏯 shadow-cli',d:'Terminal workflow automation. Deploy, lint, release — one keypress straight from inside nvim.',t:['Go','Docker','GitHub Actions'],pc:'#7aa2f7'},
  {n:'🌌 lua-conf',d:'My entire Neovim config — 80+ plugins, all lazy-loaded, under 60ms cold startup.',t:['Lua','Neovim','Tree-sitter','LSP'],pc:'#bb9af7'},
  {n:'🔥 void.ts',d:'Zero-dependency animation library inspired by anime transitions. 3kb gzip. No build needed.',t:['TypeScript','Canvas API','Rollup'],pc:'#ff9e64'},
];
const pg=document.getElementById('proj-grid');
projs.forEach(({n,d,t,pc})=>{
  pg.innerHTML+=`<div class="pcard" style="--pc:${pc}">
    <div class="pname">${n}</div>
    <div class="pdesc">${d}</div>
    <div class="ptags">${t.map(x=>`<span class="ptag">${x}</span>`).join('')}</div>
  </div>`;
});

// Stats
const stats=[
  {v:'1.2k',l:'COMMITS / YEAR',c:'linear-gradient(135deg,#57c7a0,#2ac3de)'},
  {v:'48',l:'PUBLIC REPOS',c:'linear-gradient(135deg,#7aa2f7,#bb9af7)'},
  {v:'312',l:'STARS EARNED',c:'linear-gradient(135deg,#e0af68,#ff9e64)'},
  {v:'∞',l:'HOURS IN NVIM',c:'linear-gradient(135deg,#57c7a0,#57c7a0)'},
];
const sr=document.getElementById('stats-row');
stats.forEach(({v,l,c})=>{
  sr.innerHTML+=`<div class="scard">
    <div class="snum" style="background:${c};-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;">${v}</div>
    <div class="slabel">${l}</div>
  </div>`;
});

// Reveal on scroll
const obs=new IntersectionObserver(es=>{es.forEach(e=>{if(e.isIntersecting)e.target.classList.add('vis');});},{threshold:.1});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));
</script>
</body>
</html>
