<!-- ============================================================ -->
<!--         LAZYVIM PORTFOLIO — README.md                        -->
<!--   Replace all [PLACEHOLDERS] with your own info              -->
<!-- ============================================================ -->

<div align="center">

<!-- WAVE HEADER -->
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:1e1e2e,50:313244,100:cba6f7&height=120&section=header&animation=fadeIn"/>

```
 ██╗      █████╗ ███████╗██╗   ██╗    ██████╗ ███████╗
 ██║     ██╔══██╗╚════██║╚██╗ ██╔╝    ██╔══██╗██╔════╝
 ██║     ███████║    ██╔╝ ╚████╔╝     ██║  ██║███████╗
 ██║     ██╔══██║   ██╔╝   ╚██╔╝      ██║  ██║╚════██║
 ███████╗██║  ██║   ██║     ██║       ██████╔╝███████║
 ╚══════╝╚═╝  ╚═╝   ╚═╝     ╚═╝       ╚═════╝ ╚══════╝
```

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=800&size=18&pause=600&color=CBA6F7&center=true&vCenter=true&multiline=true&width=750&height=90&lines=%E2%96%88+NORMAL+%E2%94%80%E2%94%80+%7E%2Fdev%2Fme.lua+%E2%94%80%E2%94%80+main+%E2%94%80%E2%94%80+%E2%99%A5+0+err+%E2%9A%A0+0+warn;%3Aw+%22crafting+existence%22+...+%5B+written+%5D;%3ALazyHealth+%E2%86%92+All+plugins+healthy+%E2%9C%93)](https://git.io/typing-svg)

</div>

---

<!-- LAZYVIM DASHBOARD PANEL -->

```lua
╭──────────────────────────────────────────────────────────────╮
│                                                              │
│    ██╗      █████╗ ███████╗██╗   ██╗    ██████╗ ███████╗    │
│    ██║     ██╔══██╗╚════██║╚██╗ ██╔╝    ██╔══██╗██╔════╝    │
│    ██║     ███████║    ██╔╝ ╚████╔╝     ██║  ██║███████╗    │
│    ██║     ██╔══██║   ██╔╝   ╚██╔╝      ██║  ██║╚════██║    │
│    ███████╗██║  ██║   ██║     ██║       ██████╔╝███████║    │
│    ╚══════╝╚═╝  ╚═╝   ╚═╝     ╚═╝       ╚═════╝ ╚══════╝    │
│                                                              │
│   Find File        <leader> ff      ░░░░░░░░░░░░░░░░░░░░   │
│   Find Text        <leader> fg      ░  Powered by          │
│   Recent Files     <leader> fr      ░  LazyVim  v14.x  ░   │
│   Projects         <leader> fp      ░░░░░░░░░░░░░░░░░░░░   │
│                                                              │
│   [YOUR NAME] · Full Stack Dev · Open Source Contributor     │
╰──────────────────────────────────────────────────────────────╯
```

<!-- ANIME ANIMATIONS -->

<div align="center">
<img src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif" height="200"/>
&nbsp;
<img src="https://media.giphy.com/media/SWoSkN6DxTszqIKEqv/giphy.gif" height="200"/>
&nbsp;
<img src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" height="200"/>
</div>

---

<!-- NVIM-TREE FILE STRUCTURE -->

<details open>
<summary><b>nvim-tree: <code>~/portfolio</code></b></summary>

```
portfolio/
├──  init.lua             <- bootstrap
├──  about.lua            <- who i am
├──  stack.toml           <- weapons of choice
├──  projects/
│   ├──  alpha.md
│   ├──  beta.md
│   └──  gamma.md
├──  anime/
│   └──  vibes.sh
└──  stats/
    └──  contributions.lua
```

</details>

---

## `about.lua` — buffer [1]

```lua
-- ┌─────────────────────────────────────────────────────┐
-- │  :e ~/portfolio/about.lua                           │
-- └─────────────────────────────────────────────────────┘

---@class Developer
local M = {}

M.profile = {
  name      = "[YOUR NAME]",
  alias     = { "dev_mode", "0x[handle]", "keyboard_ghost" },
  role      = "Full Stack Engineer  ·  OSS Contributor  ·  Vim Absolutist",
  location  = "🌍 [Your City], [Country]",
  timezone  = "UTC+[X] — coding at all hours",
  status    = "⚡ Currently breaking prod at [company/project]",
  coffee    = math.huge,
  sleep     = nil, -- not found

  now = {
    learning  = { "Rust", "Zig", "WebAssembly", "Category Theory" },
    building  = "[current project name — be specific]",
    listening = "lo-fi + anime OSTs in terminal",
    reading   = "[a book] by [author]",
  },

  links = {
    site      = "https://[yoursite].dev",
    email     = "[you]@[domain].dev",
    twitter   = "@[handle]",
    linkedin  = "linkedin.com/in/[you]",
    discord   = "[user]#0000",
  },

  fun_fact  = [[
    I have remapped <Esc> to jk so many times
    that I now type 'jk' in physical notebooks.
  ]],
}

return M
```

<div align="center">
<img src="https://media.giphy.com/media/RbDKaczqWovIugyJmW/giphy.gif" height="180" alt="anime thinking at computer"/>
</div>

---

## `stack.toml` — buffer [2]

```toml
# ┌───────────────────────────────────────────────────────────┐
# │  :Lazy  -> all plugins healthy   |  :Mason  -> armed      │
# └───────────────────────────────────────────────────────────┘

[meta]
editor   = "neovim"
config   = "lazyvim"
dotfiles = "github.com/[you]/dotfiles"
shell    = "zsh + starship + tmux"
os       = "arch/ubuntu/macos — rotating"
```

### `[languages]`

<div align="center">

![JavaScript](https://img.shields.io/badge/JavaScript-1e1e2e?style=for-the-badge&logo=javascript&logoColor=f9e2af)
![TypeScript](https://img.shields.io/badge/TypeScript-1e1e2e?style=for-the-badge&logo=typescript&logoColor=89b4fa)
![Python](https://img.shields.io/badge/Python-1e1e2e?style=for-the-badge&logo=python&logoColor=cba6f7)
![Rust](https://img.shields.io/badge/Rust-1e1e2e?style=for-the-badge&logo=rust&logoColor=fab387)
![Go](https://img.shields.io/badge/Go-1e1e2e?style=for-the-badge&logo=go&logoColor=89dceb)
![Lua](https://img.shields.io/badge/Lua-1e1e2e?style=for-the-badge&logo=lua&logoColor=74c7ec)
![C++](https://img.shields.io/badge/C++-1e1e2e?style=for-the-badge&logo=cplusplus&logoColor=f38ba8)
![Shell](https://img.shields.io/badge/Shell-1e1e2e?style=for-the-badge&logo=gnubash&logoColor=a6e3a1)

</div>

### `[frontend]`

<div align="center">

![React](https://img.shields.io/badge/React-181825?style=for-the-badge&logo=react&logoColor=89dceb)
![Next.js](https://img.shields.io/badge/Next.js-181825?style=for-the-badge&logo=nextdotjs&logoColor=cdd6f4)
![Vue](https://img.shields.io/badge/Vue.js-181825?style=for-the-badge&logo=vuedotjs&logoColor=a6e3a1)
![Svelte](https://img.shields.io/badge/Svelte-181825?style=for-the-badge&logo=svelte&logoColor=fab387)
![TailwindCSS](https://img.shields.io/badge/Tailwind-181825?style=for-the-badge&logo=tailwindcss&logoColor=89b4fa)
![Three.js](https://img.shields.io/badge/Three.js-181825?style=for-the-badge&logo=threedotjs&logoColor=cba6f7)
![WebGL](https://img.shields.io/badge/WebGL-181825?style=for-the-badge&logo=webgl&logoColor=f9e2af)

</div>

### `[backend]`

<div align="center">

![Node.js](https://img.shields.io/badge/Node.js-11111b?style=for-the-badge&logo=nodedotjs&logoColor=a6e3a1)
![FastAPI](https://img.shields.io/badge/FastAPI-11111b?style=for-the-badge&logo=fastapi&logoColor=94e2d5)
![GraphQL](https://img.shields.io/badge/GraphQL-11111b?style=for-the-badge&logo=graphql&logoColor=cba6f7)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-11111b?style=for-the-badge&logo=postgresql&logoColor=89b4fa)
![Redis](https://img.shields.io/badge/Redis-11111b?style=for-the-badge&logo=redis&logoColor=f38ba8)
![Docker](https://img.shields.io/badge/Docker-11111b?style=for-the-badge&logo=docker&logoColor=89dceb)
![Kubernetes](https://img.shields.io/badge/K8s-11111b?style=for-the-badge&logo=kubernetes&logoColor=89b4fa)

</div>

### `[sacred_tools]`

<div align="center">

![Neovim](https://img.shields.io/badge/Neovim-1e1e2e?style=for-the-badge&logo=neovim&logoColor=a6e3a1)
![LazyVim](https://img.shields.io/badge/LazyVim-1e1e2e?style=for-the-badge&logo=lua&logoColor=cba6f7)
![Git](https://img.shields.io/badge/Git-1e1e2e?style=for-the-badge&logo=git&logoColor=fab387)
![Linux](https://img.shields.io/badge/Linux-1e1e2e?style=for-the-badge&logo=linux&logoColor=f9e2af)
![Tmux](https://img.shields.io/badge/Tmux-1e1e2e?style=for-the-badge&logo=tmux&logoColor=a6e3a1)
![AWS](https://img.shields.io/badge/AWS-1e1e2e?style=for-the-badge&logo=amazonaws&logoColor=f9e2af)
![Figma](https://img.shields.io/badge/Figma-1e1e2e?style=for-the-badge&logo=figma&logoColor=f38ba8)

</div>

---

## `projects/showcase.lua` — buffer [3]

```lua
-- :Telescope find_files -> projects/
-- Results ──────────────────────────────────────────────
--  alpha.md            * flagship
--  beta.md             ~ wip
--  gamma.md            + stable
```

<br/>

### `[Project Alpha]` &emsp; ![](https://img.shields.io/badge/FLAGSHIP-a6e3a1?style=flat-square&labelColor=1e1e2e) ![](https://img.shields.io/badge/LIVE-1e1e2e?style=flat-square&logo=vercel&logoColor=a6e3a1)

> *"The one that taught me what 'on-call' really means."*

```diff
+ Full-stack SaaS · Next.js 14  x  Rust (Axum) backend
+ Real-time collab via WebSockets + Redis PubSub
+ 12k+ users · 99.97% uptime · multi-region AWS ECS
- auth.ts line 347 still haunts my dreams
```

[![Repo](https://img.shields.io/badge/Repo-1e1e2e?style=for-the-badge&logo=github&logoColor=cba6f7)](https://github.com/[you]/[project-alpha])
[![Live](https://img.shields.io/badge/Live_Demo-1e1e2e?style=for-the-badge&logoColor=89b4fa)](https://[project].dev)

---

### `[Project Beta]` &emsp; ![](https://img.shields.io/badge/WIP-f9e2af?style=flat-square&labelColor=1e1e2e)

> *"WebAssembly + ML inference in the browser. Cursed. Beautiful."*

```diff
+ Zero-backend ML: ONNX runtime compiled to WASM
+ Runs inference at 60fps, zero telemetry, zero server
+ Progressive enhancement — degrades gracefully on weak CPUs
! Currently rewriting the scheduler for the 4th time
```

[![Repo](https://img.shields.io/badge/Repo-1e1e2e?style=for-the-badge&logo=github&logoColor=cba6f7)](https://github.com/[you]/[project-beta])

---

### `[Project Gamma]` &emsp; ![](https://img.shields.io/badge/STABLE-89b4fa?style=flat-square&labelColor=1e1e2e)

> *"My love letter to TUI interfaces."*

```diff
+ k8s cluster dashboard in the terminal
+ Go + Bubble Tea + Lip Gloss · handles 500+ events/sec
+ Ships as a single statically-linked binary
+ Vim keybindings throughout (obviously)
```

[![Repo](https://img.shields.io/badge/Repo-1e1e2e?style=for-the-badge&logo=github&logoColor=cba6f7)](https://github.com/[you]/[project-gamma])

---

## `anime/vibes.sh` — buffer [4]

<div align="center">

```sh
#!/usr/bin/env bash
# Current BGM ──────────────────────────────────────────
# ♪  "unravel" — TK from 凛として時雨  (Tokyo Ghoul OP)
# ♪  "Decisive Battle" — Evangelion OST
# ♪  "Hikaru nara" — Your Lie in April
# ──────────────────────────────────────────────────────
# Volume: MAX   |   Repeat: infinity   |   Focus: LOCKED
```

<br/>

<img src="https://media.giphy.com/media/f9RzoxHizH72k15FKS/giphy.gif" height="220" alt="anime power up"/>
&nbsp;&nbsp;
<img src="https://media.giphy.com/media/citxUMHyVCbHi/giphy.gif" height="220" alt="anime laptop coding"/>

<br/><br/>

### Developer Power Levels — Calibrated Against Anime Arcs

| Power Level | Anime Equivalent | Dev Translation |
|:-----------:|:----------------|:----------------|
| `1` | Naruto graduation | Centering a div with Google open |
| `25` | Sasuke retrieval arc | First app deployed to prod |
| `50` | Pain arc | Debugging a race condition at 2am |
| `75` | 4th Great Ninja War | Maintaining a monorepo with 12 teams |
| `99` | Sage of Six Paths | Wrote the framework everyone else uses |
| `∞` | Saitama | One punch — one `git push --force` |

<br/>

<img src="https://media.giphy.com/media/KM4Lj1HDoMIHb9AVAI/giphy.gif" height="200" alt="anime keyboard warrior"/>

> *"Vim is not a text editor — it is a way of life."*
> *"LazyVim is not configuration — it is enlightenment."*

</div>

---

## `stats/contributions.lua` — buffer [5]

```lua
-- :checkhealth contributions
-- + GitHub API reachable
-- + Streak active  (do NOT break the chain)
-- + Top Languages computed
-- + Activity graph rendered
```

<div align="center">

### GitHub Metrics

<img src="https://github-readme-stats.vercel.app/api?username=[yourusername]&show_icons=true&theme=catppuccin_mocha&hide_border=true&bg_color=1e1e2e&title_color=cba6f7&icon_color=89b4fa&text_color=cdd6f4&ring_color=cba6f7&border_radius=10" width="49%"/>
<img src="https://github-readme-streak-stats.herokuapp.com?user=[yourusername]&theme=catppuccin-mocha&hide_border=true&background=1e1e2e&ring=cba6f7&fire=fab387&currStreakLabel=a6e3a1&border_radius=10" width="49%"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=[yourusername]&layout=compact&theme=catppuccin_mocha&hide_border=true&bg_color=1e1e2e&title_color=cba6f7&text_color=cdd6f4&border_radius=10" width="49%"/>

<br/><br/>

### Activity Graph

<img src="https://github-readme-activity-graph.vercel.app/graph?username=[yourusername]&theme=tokyo-night&hide_border=true&bg_color=1e1e2e&color=cba6f7&line=89b4fa&point=fab387&area=true&area_color=cba6f760" width="100%"/>

<br/>

### Trophy Shelf

<img src="https://github-profile-trophy.vercel.app/?username=[yourusername]&theme=darkhub&no-frame=true&no-bg=true&margin-w=8&row=1&column=7"/>

<br/>

### Contribution Snake

<picture>
  <source media="(prefers-color-scheme: dark)"  srcset="https://raw.githubusercontent.com/[yourusername]/[yourusername]/output/github-contribution-grid-snake-dark.svg"/>
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/[yourusername]/[yourusername]/output/github-contribution-grid-snake.svg"/>
  <img alt="snake animation" src="https://raw.githubusercontent.com/[yourusername]/[yourusername]/output/github-contribution-grid-snake.svg"/>
</picture>

</div>

---

<div align="center">

```lua
-- ╔══════════════════════════════════════════════════════════╗
-- ║                                                          ║
-- ║  Thanks for reaching buffer [5] — you earned a cookie.  ║
-- ║                                                          ║
-- ║  If you want to collab, open a PR, an issue, or just     ║
-- ║  send a message. All methods accepted equally.           ║
-- ║                                                          ║
-- ║  :wqa   <- I mean it this time. Goodbye.                 ║
-- ╚══════════════════════════════════════════════════════════╝
```

<br/>

[![Portfolio](https://img.shields.io/badge/Portfolio-1e1e2e?style=for-the-badge&logo=firefox&logoColor=cba6f7)](https://[yoursite].dev)
[![Twitter](https://img.shields.io/badge/Twitter-1e1e2e?style=for-the-badge&logo=x&logoColor=cdd6f4)](https://twitter.com/[handle])
[![LinkedIn](https://img.shields.io/badge/LinkedIn-1e1e2e?style=for-the-badge&logo=linkedin&logoColor=89b4fa)](https://linkedin.com/in/[you])
[![Email](https://img.shields.io/badge/Email-1e1e2e?style=for-the-badge&logo=gmail&logoColor=f38ba8)](mailto:[you]@[domain].dev)

<br/>

<img src="https://komarev.com/ghpvc/?username=[yourusername]&style=flat-square&color=cba6f7&label=profile+views"/>

</div>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:cba6f7,50:313244,100:1e1e2e&height=100&section=footer&animation=fadeIn"/>

<!-- EOF  [ buf 5/5 ]  [ ln 337 / col 42 ]  [ lua ]  [ unix ]  -- NORMAL -- -->
