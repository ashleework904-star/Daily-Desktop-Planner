# 🌧 Daily — A Liquid Glass Daily Planner

A self-contained, single-file daily productivity planner with a focus on aesthetic calm, built entirely in HTML/CSS/JavaScript. No frameworks, no installation, no accounts required. Just open the file in any browser.

**Live demo:** *(https://ashleework904-star.github.io/Daily-Desktop-Planner/)*

---

![Daily Planner Preview](preview.png)

---

## ✨ Features

### Today View
| Widget | What it does |
|---|---|
| **Tasks** | Add tasks with priority levels (High/Med/Low), check off, delete, set a task as the focus for the timer. Tracks completion rate. |
| **Focus Timer** | Circular countdown with colour-coded ring (green → amber → red). Presets: 5m / 15m / 25m / 50m. Stick-slip ring animation, session counter, and browser notification on completion. |
| **Schedule** | Timed events with colour tags (Blue/Sage/Sand/Clay). Hover to edit or delete inline. Sorted automatically by time. |
| **Mood Check-in** | 5-point emoji scale. Logged per day in the browser. |
| **Daily Quote** | Rotating curated quotes. One click cycles to the next. |
| **Habit Tracker** | 7-day dot grid per habit. Streak counter with 🔥. Fully customisable habits. |
| **Hydration** | 8-glass tracker. Resets daily. |
| **Quick Note** | Auto-saves as you type. |

### Insights View
| Panel | What it shows |
|---|---|
| **Mood Calendar** | Full monthly calendar with your logged emoji per day, plus tiny indicators for water and task tracking. Navigate months with ‹ ›. |
| **Personalized Insights** | Auto-generated analysis of your last 7 days across hydration, task completion, mood, and habit streaks. Colour-coded by tone (good / warning / alert). |
| **Hydration Chart** | 14-day bar chart — avg/day, best day, goal % reached. |
| **Task Completion Chart** | 14-day bar chart — avg rate, current streak, total done. |
| **Habit Heatmap** | 30-day GitHub-style heatmap per habit. |

### Settings Panel
| Control | What it does |
|---|---|
| **AI Background** | Generates a photorealistic rainy-window background via the [Krea-2 LoRA](https://huggingface.co/krea/Krea-2-LoRA-rainywindow) model on fal.ai. Paste your fal.ai API key, type a prompt, click generate. Or upload a locally generated image. |
| **Glass & Atmosphere** | Sliders for transparency (1–20%), blur intensity (0–60px), and noise texture (0–15%). All applied live. |
| **Theme** | 5 themes: Fog (blue-grey), Moss (dark green), Storm (deep slate), Porcelain (white light), Linen (warm light). Instantly switches all surfaces, text, and blobs. |
| **Widgets** | Toggle any of the 6 panels on or off. Grid repacks automatically. Preferences saved. |
| **Rain Effect** | Toggle rain visual on/off. Adjust drop size, count, and speed live. |
| **Rain Sound** | Three intensities: **Drizzle** (soft sibilant hiss, delicate pattering), **Steady** (consistent murmuring drone), **Downpour** (pounding, roaring, chaotic percussion). All three layer randomised glass-tap impacts on top. |
| **Thunder** | Distant rolling thunder at random intervals (18–60s). Pure Web Audio API — no audio files. |
| **Accent Color** | 8 muted earthy swatches. Affects timer ring, progress bars, selected states, schedule tags, and more. |

---

## 🌧 Rain Physics

The rain effect is a two-layer simulation:

**Layer A — Rain falling behind the glass**
Soft translucent streaks falling at varying speeds, matching the reference-repo technique from [ayushkumar15070/CSS-Raindrop-Effect-on-a-Window](https://github.com/ayushkumar15070/CSS-Raindrop-Effect-on-a-Window).

**Layer B — Drops on the glass (refraction-based)**
Each bead is rendered as a true lens — it clips out a miniature inverted copy of the scene behind it. This is the technique used in [rainyday.js](https://github.com/mubaidr/rainyday.js) and is what makes water look real to the eye (a water drop is a fisheye that flips and compresses the world behind it).

Physics modelled per drop:
- **Condensation** — drops appear small, cling via surface tension
- **Growth** — merges with neighbours it touches
- **Impact splat** — new drops scatter 2–4 micro-satellites
- **Sliding** — once heavy enough, gravity overcomes surface tension
- **Stick-slip motion** — drops lurch rather than glide (real surface tension behaviour)
- **Teardrop stretch** — sliding drops elongate under velocity
- **Wet runnels** — trails rendered as a dark channel + light catchline
- **Shed mass** — sliding drops lose radius into the trail, may re-stick
- **Evaporation** — all drops slowly shrink and vanish; small drops disappear first (higher surface-area-to-volume ratio, matching real physics)

---

## 🎨 Tech Stack

- **Zero dependencies** — pure HTML, CSS, JavaScript
- **Web Audio API** — all rain/thunder sound synthesised live, no audio files
- **Canvas API** — rain physics simulation at 60fps
- **CSS custom properties** — entire theme system built on swappable variables
- **localStorage** — all user data (tasks, habits, moods, water, notes, settings) persists locally

---

## 🚀 Usage

### Option 1 — Just open it
Download `index.html` and open it in any modern browser. Nothing else needed.

### Option 2 — GitHub Pages (host it live)
1. Fork this repo
2. Go to **Settings → Pages → Source → main branch → / (root)**
3. Your planner is live at `https://yourusername.github.io/daily-planner/`

### Option 3 — Self-host
Drop `index.html` on any static hosting service (Netlify, Vercel, Cloudflare Pages, etc.).

---

## 🤖 AI Background (optional)

To use the Krea-2 rainy window background generator:

1. Create a free account at [fal.ai](https://fal.ai)
2. Go to Dashboard → API Keys → Create key
3. Open the planner → Settings → AI Background → paste your key
4. Type a scene prompt (must include `rainy window style`) → Generate

Cost: ~$0.003 per image. The key is stored in your browser only.

**Alternatively**, generate images locally for free using the included [Colab notebook](krea_rainywindow_colab.ipynb) (requires a free Google account and Hugging Face account).

---

## 💾 Data & Privacy

All data lives in your browser's `localStorage`. Nothing is sent to any server unless you use the optional AI background feature (which calls fal.ai directly from your browser).

To export your data: open the browser console → `JSON.stringify(localStorage)` → copy and save.

---

## 🗂 File Structure

```
daily-planner/
├── index.html              # The entire application (self-contained)
├── krea_rainywindow_colab.ipynb  # Optional: Colab notebook to generate AI backgrounds
└── README.md
```

---

## 🛤 Roadmap / Ideas

- [ ] Export tasks to CSV
- [ ] Weekly summary email (requires backend)
- [ ] PWA (Progressive Web App) — install on home screen
- [ ] Cross-device sync via a lightweight backend
- [ ] More themes (Dusk, Ocean, Sand)
- [ ] Pomodoro mode with automatic break scheduling

---

## 👩‍💻 Built by

**Ashlee (LEE Pui Shuen)**
BA (Hons) Fashion — Contour Fashion & Activewear
School of Fashion and Textiles, The Hong Kong Polytechnic University

Built during the Mitacs Globalink Research Internship 2026 at the University of Regina.

---

## 📄 Licence

MIT — free to use, modify, and share. Attribution appreciated.
