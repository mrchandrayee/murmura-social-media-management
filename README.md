# Murmura — Social Media Management

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blue?style=for-the-badge&logo=github)](https://mrchandrayee.github.io/murmura-social-media-management/)
[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org) [![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org) [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](./LICENSE)

Runnable HTML/CSS/JavaScript reconstruction of the supplied 5.37-second screen recording (720 × 1280, 30 fps).

## Run locally
1. Extract `murmura-social-media-management.zip`.
2. Open `index.html` in Chrome, Edge, Firefox or Safari.
3. No npm install, bundler or backend is required.

Optional local server:
```bash
python3 -m http.server 8000
```
Then open `http://localhost:8000`.

## What is visible in the source video

The recording is titled **Social Media Management**. The product logo reads **murmura**. The app navigation shows:
- Overview
- Compose
- Calendar
- Inbox
- Approvals
- Analytics
- Listening

The Overview is branded **Afternoon, Camila** and displays:
- Audience across accounts: **976.2K**
- Engagement rate: **10.3%**
- Posts going out this week: **19**
- Needs your attention: **3**
- A featured queued post for **Ember & Oak**, marked **Awaiting approval**, with a countdown of **19 h 34 min**
- A “Needs you” approval list with Approve and Review actions

The Calendar screen is titled **Publishing calendar**. It includes counters for scheduled this week, awaiting approval, published this month and drafts; channel filters; month navigation; an October 2026 calendar grid; and an Unscheduled drafts panel.

The Analytics screen displays:
- Audience across accounts: **772.1K**
- New followers, last 30 days: **60.2K**
- Impressions, last 30 days: **6.39M**
- Avg. engagement rate: **3.9%**
- Audience growth and Impressions & engagement charts
- Network filters for Instagram, Facebook, X, LinkedIn, TikTok, YouTube, Pinterest and Threads

## Readable source code transcribed from the video

The code preview at the bottom is labelled `src/ui.ts`. The readable `slidePill` function is:

```ts
export function slidePill(pill, box, target, animate = true) {
  const W = pill.offsetWidth, H = pill.offsetHeight;
  const L = target.offsetLeft, R = W - (L + target.offsetWidth);
  const T = target.offsetTop, B = H - (T + target.offsetHeight);
  const clip = (l, r) =>
    `inset(${T}px ${r}px ${B}px ${l}px round 999px)`;
  const prev = pill.__lr;
  pill.__lr = [L, R];
  if (!animate || !prev) return gsap.set(pill, { clipPath: clip(L, R) });
  const o = { l: prev[0], r: prev[1] }, right = L > prev[0];
  const draw = () => gsap.set(pill, { clipPath: clip(o.l, o.r) });
  gsap.to(o, { l: L, duration: right ? 0.55 : 0.36,
    ease: right ? 'power3.inOut' : 'power3.out', onUpdate: draw });
  gsap.to(o, { r: R, duration: right ? 0.36 : 0.55,
    ease: right ? 'power3.out' : 'power3.inOut', onUpdate: draw });
}
```

The snippet animates a pill-shaped active navigation background by changing its CSS `clip-path` inset. It stores the previous left/right inset, then uses two GSAP tweens with direction-dependent durations and easing.

## Implemented in this project
- Dashboard overview with KPI cards, featured post, approval queue and upcoming posts.
- Compose screen with caption preview, brand/channel selectors and draft saving.
- Calendar month view with month navigation, network filter and clickable post events.
- Inbox with selectable conversations and a demo reply action.
- Approvals with approve and request-edits actions.
- Analytics with audience growth, impressions/engagement charts, network breakdown and top content.
- Listening screen with mentions and tracked topics.
- Settings with channel connection status and toggle controls.
- Responsive layout and compact dark left navigation rail.

## Files
- `index.html` — app shell and modal
- `styles.css` — visual design and responsive layout
- `app.js` — local demo data, page rendering and interactions
- `README.md` — source notes and run instructions

## Accuracy and limitations
The video is a screen recording of the running UI, not a complete source repository. The `slidePill` TypeScript snippet above is transcribed from the visible code panel; the rest of the HTML/CSS/JavaScript is reconstructed to match the screens and demonstrated navigation. The project uses illustrative local data for sections not fully legible in the recording. GSAP is not required by this runnable version; the navigation is implemented with ordinary CSS/JavaScript. Social network APIs, publishing queues, OAuth, real inbox sync, real approval workflows, analytics ingestion, listening APIs and a backend are not connected. Drafts and actions are demo-only and are lost on refresh.

## 👨‍💻 Author

**mrchandrayee** · [GitHub](https://github.com/mrchandrayee)

## 📄 License

[MIT License](./LICENSE)
