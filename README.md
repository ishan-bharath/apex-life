# APEX LIFE

> **Personal daily tracker built for personal use. Not intended for public deployment.**
> A public, customizable version — **APEX-LIFE ELITE** — is currently in development.

---

## What is this?

APEX LIFE is a mobile-first PWA I built as a personal life management system — schedule tracking, workout logging, project milestone tracking, and an AI coach in a single self-contained file. There is no backend, no database, no server, no account system. Everything runs locally on the device.

---

## Tech Stack

| Layer | Tech |
|---|---|
| App | Vanilla HTML5 + CSS + JavaScript (no frameworks, no build tools) |
| PWA | `manifest.json` + Service Worker (`sw.js`) |
| Persistence | Browser `localStorage` — 100% local, zero cloud |
| AI Coach | OpenRouter API (`openrouter/free` model) — user-supplied key |
| Hosting | Static file host (GitHub Pages) |

No React. No Node. No npm. No backend. Single file: `apex-life.html`.

---

## Features

### TODAY Tab
- Day-of-week schedule view (Weekday / Saturday / Sunday routines)
- Colour-coded task types: `routine`, `mental`, `hygiene`, `workout`, `nutrition`, `academic`, `project`, `sleep`, `recovery`
- Tap to expand task detail; checkbox to mark done
- Add custom tasks to any day; delete existing tasks
- All completions persist in `localStorage` keyed by date

### WORKOUT Tab
- Day-mapped workout plans (7 unique sessions: Mon–Sun)
- Each session has name, duration, focus, coaching note, and full exercise list with sets/reps/cues
- Exercises individually checkable; state persists per-date

### PROJECTS Tab
- 8-week milestone tracker with colour-coded project tracks
- "Due This Week" section auto-filters by current week number
- Weekly progress bar and countdown to semester start
- Weekly workout plan overview with one-tap jump to any day's workout

### COACH AI Tab
- Chat interface powered by **OpenRouter** (user provides their own API key)
- Key is stored in `localStorage` on the device only — never transmitted anywhere except directly to OpenRouter
- System prompt context includes full profile, routine, injury notes, and project priority stack
- Structured command parsing: coach responses can embed `---COMMANDS--- [...] ---END---` blocks to **add or delete schedule tasks** in real time — changes apply to `localStorage` immediately
- Workout sessions can be discussed and adjusted conversationally; static workout blocks are not directly editable via command
- Chat history persists in `localStorage`; clear button available

### INFO Tab
- Reference cards: stats, non-negotiables, summer calendar, career tools, hygiene protocol, AI coach usage guide
- Reset controls: reset today's marks, reset week, or full wipe

---

## Privacy

**APEX LIFE is fully local-first. There is no backend of any kind.**

- All data (checkmarks, schedule edits, chat history, API key) is stored exclusively in the browser's `localStorage` on the user's own device
- No data is collected, transmitted, or stored on any server by this app
- The only external network call is the AI coach request, which goes **directly from the browser to OpenRouter's API** using the user's own key
- Removing the app or clearing site data deletes everything

---

## OpenRouter API — Third-Party Disclaimer

The COACH AI feature uses the [OpenRouter](https://openrouter.ai) API. Users must supply their own OpenRouter API key.

> **Any issues, errors, rate limits, model availability changes, or unexpected outputs from the AI are the responsibility of OpenRouter, not the developer of this app.** This app simply passes the user's key and messages directly to OpenRouter's endpoint. The developer has no control over model behaviour, uptime, or OpenRouter's terms of service enforcement.
>
> Review OpenRouter's Terms of Service and Privacy Policy at [openrouter.ai/terms](https://openrouter.ai/terms) before using the AI coach feature.

---

## Repo Structure

```
apex-life/
├── apex-life.html     # Entire application — single file
├── manifest.json      # PWA manifest (standalone display, portrait)
├── sw.js              # Service worker for offline caching
└── APEXLOGO.png       # PWA icon (192×192 and 512×512)
```

---

## Usage

1. Clone or download the repo
2. Serve `apex-life.html` over HTTPS (required for PWA install and service worker)
3. On mobile: use "Add to Home Screen" to install as a standalone PWA
4. Open the **COACH AI** tab and enter your OpenRouter API key when prompted — it is saved locally and never leaves your device except in requests to OpenRouter

For persistent PWA behaviour on Android, self-hosting on a service like **Netlify** is recommended over GitHub Pages due to service worker scope limitations.

---

## Coming Next — V2 / APEX-LIFE ELITE

| Feature | Status |
|---|---|
| Wearables integration | Planned — V2 |
| Working push notification / reminder system | Planned — V2 |
| Dynamic user customization (not hardcoded profile) | In development — APEX-LIFE ELITE |
| Multi-user support | APEX-LIFE ELITE |
| Public release | APEX-LIFE ELITE |

---

## License & Copyright

© 2024–2026 Ishan Bharath. All rights reserved.

This repository is **source-available but not open source**. The code is published publicly for transparency and portfolio purposes only.

**You may not:**
- Fork, copy, redistribute, or deploy this application (in whole or in part) for personal or commercial use without explicit written permission
- Claim authorship or derivative ownership of the codebase
- Use any part of this project in other products without permission

This project was built as a personal tracker for personal use. It is not intended for public deployment, redistribution, or use by third parties. If you are interested in a customizable version, please wait for **APEX-LIFE ELITE**.

---

## Privacy Policy

By using this application, you acknowledge and agree to the following terms and conditions:

1. **No data collection.** This app does not collect, store, or transmit any personal data to the developer or any third party other than OpenRouter (when the AI coach is used).
2. **Local storage only.** All app data lives in your browser's `localStorage`. It does not leave your device except through your own OpenRouter API key requests.
3. **API key responsibility.** You are solely responsible for your OpenRouter API key. Do not share it. The app stores it in `localStorage` and sends it only to `openrouter.ai`.
4. **OpenRouter.** AI coach requests are subject to [OpenRouter's Privacy Policy](https://openrouter.ai/privacy). The developer of this app has no liability for how OpenRouter processes or stores your prompts.
5. **No warranties.** This software is provided as-is for personal use. The developer is not liable for data loss, device issues, or any other damages arising from use.

---

*APEX LIFE — one person, one system to track everything.*
