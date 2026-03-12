<!-- ================================================================
  ███╗   ██╗███████╗ ██████╗ ██╗   ██╗██╗███╗   ███╗
  ████╗  ██║██╔════╝██╔═══██╗██║   ██║██║████╗ ████║
  ██╔██╗ ██║█████╗  ██║   ██║██║   ██║██║██╔████╔██║
  ██║╚██╗██║██╔══╝  ██║   ██║╚██╗ ██╔╝██║██║╚██╔╝██║
  ██║ ╚████║███████╗╚██████╔╝ ╚████╔╝ ██║██║ ╚═╝ ██║
  ╚═╝  ╚═══╝╚══════╝ ╚═════╝   ╚═══╝  ╚═╝╚═╝     ╚═╝
  github.com/yourusername — init.md loaded successfully ✓
================================================================ -->

<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=rect&color=0:0d0d0d,50:0a1a0a,100:0d0d0d&height=3&section=header"/>

```
 ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
 ░  nvim ~/.github/README.md                                  ░
 ░  [No Name]  ·  ft=markdown  ·  utf-8  ·  unix  ·  100%   ░
 ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
```

<!-- Pixel art boy coding GIF - right aligned -->
<img align="right" width="220" src="https://media.giphy.com/media/ZVik7pIoRHB7o/giphy.gif" title="pixel coding"/>

<!-- Typing animation — terminal green, monospace -->
[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=18&pause=900&color=57C94E&center=false&vCenter=true&width=520&lines=%3A+require('me').setup()+-+loading...+%E2%96%88;%3A+set+nolife+%7C+set+anime%3Dtrue+%7C+set+nvim;+hello+from+the+terminal+%F0%9F%9F%A2;+i+use+neovim+btw+%E2%9A%A1)](https://git.io/typing-svg)

<br/>

<!-- Badges — all terminal green on black -->
[![GitHub](https://img.shields.io/badge/github-yourusername-57C94E?style=flat-square&logo=github&logoColor=57C94E&labelColor=0d0d0d)](https://github.com/yourusername)
[![Twitter](https://img.shields.io/badge/twitter-@handle-57C94E?style=flat-square&logo=twitter&logoColor=57C94E&labelColor=0d0d0d)](https://twitter.com/yourhandle)
[![AniList](https://img.shields.io/badge/anilist-profile-02a9ff?style=flat-square&logo=anilist&logoColor=02a9ff&labelColor=0d0d0d)](https://anilist.co/user/yourprofile)
[![Discord](https://img.shields.io/badge/discord-server-57C94E?style=flat-square&logo=discord&logoColor=57C94E&labelColor=0d0d0d)](https://discord.gg/yourserver)

![](https://komarev.com/ghpvc/?username=yourusername&color=57c94e&style=flat-square&label=profile+views)

<br clear="right"/>

</div>

---

```lua
-- ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
--  ~/.config/nvim/lua/me/init.lua
-- ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

local M = {}

M.config = {
  name        = "Your Name",
  alias       = "yourhandle",
  pronouns    = "he/him",
  location    = "📍 somewhere with good wifi and bad sleep",

  editor      = "Neovim (obviously)",
  terminal    = "Kitty + tmux + zsh",
  theme       = "Catppuccin Mocha 🐱",
  font        = "JetBrainsMono Nerd Font",
  rice        = "Hyprland + Waybar + eww widgets 🍚",

  current_arc    = "Backend Architect Arc ⚔️",
  currently_watching = { "Dandadan", "Kaiju No. 8", "Solo Leveling" },
  coding_bgm     = "Yoko Kanno + City Pop + Sawano 🎵",

  fun_facts = {
    "My .dotfiles repo has more commits than any project",
    "I've configured Neovim 47 times this year",
    "My startup time is 23ms. I will optimize more.",
    "I learned Lua just for Neovim. No regrets.",
  },
}

return M
```

---

## 　🟢 plugins.lua — Tech Stack

```lua
-- Lazy.nvim style — because we only load what we need

return {

  -- 🌐 Frontend Spells
  { "react",        version = "^18",    lazy = false },
  { "next.js",      version = "^14",    lazy = false },
  { "typescript",   version = "^5",     lazy = false },
  { "tailwindcss",  version = "^3",     lazy = true  },
  { "framer-motion",version = "^11",    lazy = true  },

  -- ⚙️  Backend Jutsu
  { "node.js",      runtime = "lts",    lazy = false },
  { "python",       version = "3.12",   lazy = false },
  { "postgresql",   version = "16",     lazy = false },
  { "redis",        version = "7",      lazy = true  },
  { "graphql",      lazy = true                      },

  -- 🐋 DevOps no Jutsu
  { "docker",       lazy = false                     },
  { "kubernetes",   lazy = true                      },
  { "aws",          lazy = true                      },
  { "github-actions", lazy = false                   },
  { "terraform",    lazy = true                      },

  -- ⚡ Editor Setup (THE REAL STACK)
  { "neovim",       version = "0.10+",  lazy = false },
  { "tmux",         lazy = false                     },
  { "zsh + oh-my-zsh", lazy = false                  },
  { "fzf + ripgrep",lazy = false                     },
  { "lazygit",      lazy = false                     },

}
```

<div align="center">

<!-- Tech badges in terminal green style -->
![TypeScript](https://img.shields.io/badge/TS-0d0d0d?style=for-the-badge&logo=typescript&logoColor=57C94E)
![React](https://img.shields.io/badge/React-0d0d0d?style=for-the-badge&logo=react&logoColor=57C94E)
![Next.js](https://img.shields.io/badge/Next-0d0d0d?style=for-the-badge&logo=next.js&logoColor=white)
![Python](https://img.shields.io/badge/Python-0d0d0d?style=for-the-badge&logo=python&logoColor=57C94E)
![Go](https://img.shields.io/badge/Go-0d0d0d?style=for-the-badge&logo=go&logoColor=57C94E)
![Neovim](https://img.shields.io/badge/Neovim-0d0d0d?style=for-the-badge&logo=neovim&logoColor=57C94E)
![Docker](https://img.shields.io/badge/Docker-0d0d0d?style=for-the-badge&logo=docker&logoColor=57C94E)
![Linux](https://img.shields.io/badge/Linux-0d0d0d?style=for-the-badge&logo=linux&logoColor=57C94E)
![AWS](https://img.shields.io/badge/AWS-0d0d0d?style=for-the-badge&logo=amazonaws&logoColor=57C94E)
![PostgreSQL](https://img.shields.io/badge/Postgres-0d0d0d?style=for-the-badge&logo=postgresql&logoColor=57C94E)

</div>

---

## 　📊 :checkhealth stats

<div align="center">

<img height="175em" src="https://github-readme-stats.vercel.app/api?username=yourusername&show_icons=true&theme=tokyonight&include_all_commits=true&count_private=true&hide_border=true&bg_color=0d0d0d&title_color=57C94E&icon_color=57C94E&text_color=8b9ebf&ring_color=57C94E&border_radius=4"/>
<img height="175em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=yourusername&layout=compact&langs_count=8&theme=tokyonight&hide_border=true&bg_color=0d0d0d&title_color=57C94E&text_color=8b9ebf&border_radius=4"/>

<img src="https://github-readme-streak-stats.herokuapp.com/?user=yourusername&theme=tokyonight&hide_border=true&background=0d0d0d&ring=57C94E&fire=39d353&currStreakLabel=57C94E&sideLabels=8b9ebf&dates=444&border_radius=4"/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=yourusername&theme=tokyo-night&hide_border=true&bg_color=0d0d0d&color=57C94E&line=39d353&point=57C94E&area=true&area_color=0a1a0a" width="100%"/>

</div>

---

## 　⚔️ :Telescope projects — Featured Work

```bash
$ fd --type project | fzf --preview 'bat --color=always {}/README.md'
```

<div align="center">

| 🟢 | Project | Description | Stack | Stars |
|----|---------|-------------|-------|-------|
| ⚡ | [**nvim-anime**](https://github.com/you/nvim-anime) | Neovim plugin that shows anime quote on startup | Lua · Neovim API | ![](https://img.shields.io/github/stars/you/nvim-anime?style=flat-square&color=57C94E&labelColor=0d0d0d) |
| 🏯 | [**dotfiles**](https://github.com/you/dotfiles) | My entire rice — Hyprland, nvim, tmux, zsh configs | Shell · Lua · TOML | ![](https://img.shields.io/github/stars/you/dotfiles?style=flat-square&color=57C94E&labelColor=0d0d0d) |
| 🌐 | [**Project Shikigami**](https://github.com/you/project) | Full-stack app: [what it does in 1 line] | Next.js · Postgres · tRPC | ![](https://img.shields.io/github/stars/you/project?style=flat-square&color=57C94E&labelColor=0d0d0d) |
| 🐍 | [**AniShell**](https://github.com/you/anishell) | CLI that fetches anime recommendations from AniList | Go · AniList API | ![](https://img.shields.io/github/stars/you/anishell?style=flat-square&color=57C94E&labelColor=0d0d0d) |

</div>

<div align="center">

[![Repo 1](https://github-readme-stats.vercel.app/api/pin/?username=yourusername&repo=your-repo-1&theme=tokyonight&hide_border=true&bg_color=0d0d0d&title_color=57C94E&icon_color=57C94E&border_radius=4)](https://github.com/yourusername/your-repo-1)
[![Repo 2](https://github-readme-stats.vercel.app/api/pin/?username=yourusername&repo=your-repo-2&theme=tokyonight&hide_border=true&bg_color=0d0d0d&title_color=57C94E&icon_color=57C94E&border_radius=4)](https://github.com/yourusername/your-repo-2)

</div>

---

## 　🎌 anime_db.json — The Sacred List

<div align="center">

<img align="left" width="160" src="https://media.giphy.com/media/l3vR6aasAuKFbgRSo/giphy.gif" title="pixel anime"/>
<img align="right" width="160" src="https://media.giphy.com/media/xUPGcguWZHRC2HyBRS/giphy.gif" title="pixel run"/>

```json
{
  "tier_s": [
    "Fullmetal Alchemist: Brotherhood",
    "Steins;Gate",
    "Mushishi",
    "Vinland Saga",
    "Ping Pong The Animation"
  ],
  "tier_a": [
    "Mob Psycho 100",
    "Jujutsu Kaisen",
    "Chainsaw Man",
    "Frieren",
    "Made in Abyss"
  ],
  "currently_watching": [
    { "title": "Dandadan",     "ep": "current", "rating": "??/10 🔥" },
    { "title": "Kaiju No. 8", "ep": "s2 ep 4", "rating": "8/10"    },
    { "title": "YOUR SHOW",   "ep": "?/?",      "rating": "tbd"     }
  ],
  "coding_ost_picks": [
    "Hiroyuki Sawano — Re:Zero OST",
    "Kevin Penkin — Made in Abyss OST",
    "Yoko Kanno — Cowboy Bebop",
    "any city pop playlist at 2am"
  ]
}
```

<br clear="both"/>

</div>

---

## 　🐍 :Git log --graph — Contribution Snake

<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/yourusername/yourusername/output/github-contribution-grid-snake-dark.svg"/>
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/yourusername/yourusername/output/github-contribution-grid-snake.svg"/>
    <img alt="contribution snake" src="https://raw.githubusercontent.com/yourusername/yourusername/output/github-contribution-grid-snake-dark.svg"/>
  </picture>
</div>

---

## 　🏆 :Mason installed — Trophies

<div align="center">
  <img src="https://github-profile-trophy.vercel.app/?username=yourusername&theme=tokyonight&no-frame=true&no-bg=true&margin-w=6&column=7"/>
</div>

---

## 　🎵 now_playing.lua

<div align="center">

[![Spotify](https://novatorem.vercel.app/api/spotify?background_color=0d0d0d&border_color=57C94E)](https://open.spotify.com/user/yourid)

</div>

---

## 　📡 :help connect — Find Me

<div align="center">

```bash
$ curl -s https://api.yourname.dev/contact | jq

{
  "email":     "you@yoursite.com",
  "twitter":   "@yourhandle",
  "discord":   "yourname#0000",
  "portfolio": "https://yoursite.dev",
  "anilist":   "https://anilist.co/user/yourprofile",
  "open_to":   ["freelance", "collabs", "talking about anime"],
  "response_time": "fast if it's interesting, slow if it's boring"
}
```

</div>

---

<div align="center">

<img width="55" src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" title="pixel star"/>

```
  ┌─────────────────────────────────────────────────────────┐
  │                                                         │
  │    :wq  ← how i end every conversation too             │
  │                                                         │
  │    "The quieter you become,                             │
  │     the more you are able to hear."  — Rumi            │
  │     (also good for :set nohlsearch after a bug hunt)   │
  │                                                         │
  └─────────────────────────────────────────────────────────┘

  -- EOF --  line 1,  col 1  ·  0%  ·  [No Errors]  ✓
```

<img width="55" src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" title="pixel star"/>

<br/>

<img width="100%" src="https://capsule-render.vercel.app/api?type=rect&color=0:0d0d0d,50:0a1a0a,100:0d0d0d&height=3&section=footer"/>

</div>
