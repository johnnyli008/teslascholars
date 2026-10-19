# ⚡ Tesla Scholars Program

> **A concept scholarship web app in Tesla's design language — red, white, and built for builders.**

A single-file web application for a fictional **Tesla Scholars Program**: a $50,000, four-discipline scholarship with zero strings attached. Features a live application deadline countdown, an instant eligibility checker, and a fully working multi-step application flow.

![Status](https://img.shields.io/badge/status-concept-E31937)
![Size](https://img.shields.io/badge/size-single%20file-171A20)
![Dependencies](https://img.shields.io/badge/dependencies-none-success)

---

## ✨ Features

| Feature | Description |
|---|---|
| 🎟️ **Award ticket** | Hero centerpiece styled like a physical scholarship ticket with perforation + barcode |
| ⏱️ **Live countdown** | Ticks down to the March 1 deadline, auto-rolls to the next cycle when it passes |
| ✅ **Eligibility checker** | Three questions → instant verdict, pre-fills your application track |
| 📝 **Multi-step application** | 4 steps (You → Education → Essay → Review) with validation, live essay counter, and confirmation |
| 🆔 **Application ID** | Generates a `TS-26-XXXXXX` ID on submit and persists it in `localStorage` |
| 🧭 **Track picker** | Click any of the 4 disciplines to pre-fill the application form |
| 📅 **Dynamic timeline** | The application cycle timeline fills itself based on today's real date |
| 🔢 **Animated stats** | Count-up numbers when scrolled into view |
| ❓ **FAQ accordion** | Smooth open/close, one item at a time |
| 🍞 **Toast notifications** | Feedback when tracks are selected or applications are submitted |

---

## 🎨 Design

- **Palette** — Tesla Red `#E31937`, White `#FFFFFF`, Ink `#171A20`, plus light red tints. No heavy imagery — every word sits on a solid surface.
- **Typography**
  - Display: [Archivo](https://fonts.google.com/specimen/Archivo) (variable width, expanded uppercase)
  - Body: [Instrument Sans](https://fonts.google.com/specimen/Instrument+Sans)
  - Data/labels: [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono)
- **Motion** — line-mask headline reveals, scramble-decode hero word, marquee ticker, staggered scroll reveals, sticky program column, pulsing timeline dot. All disabled under `prefers-reduced-motion`.

---

## 🚀 Getting Started

No build step. No dependencies. No server required.

```bash
# Option 1: just open it
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux

# Option 2: serve locally (optional)
npx serve .
# or
python3 -m http.server 8000
```

Then visit the file (or `http://localhost:8000`) in any modern browser.

> **Note:** The only network requests are to Google Fonts. Everything else is self-contained — the app even works fully offline once fonts are cached.

---

## 🗂️ Structure

```
tesla-scholars/
├── index.html     # The entire app: markup, styles, and logic
└── README.md      # You are here
```

### Key sections inside `index.html`

| Section | ID | Purpose |
|---|---|---|
| Hero | `#home` | Headline + award ticket + spec strip with countdown |
| Ticker | — | Red marquee of program facts |
| Program | `#program` | Sticky two-column overview (grant / mentorship / network) |
| Tracks | `#tracks` | 4 selectable disciplines |
| Timeline | `#timeline` | Auto-progressing application cycle |
| Eligibility | `#eligibility` | 3-question instant verdict |
| Stats | — | Count-up band on red |
| Alumni | `#scholars` | Typographic postcards with quotes |
| Apply | `#apply` | Multi-step form + mini countdown |
| FAQ | `#faq` | Accordion |

---

## ⚙️ How It Works

### Countdown
Targets **March 1, 23:59 local time**. If that date has passed, it automatically targets the following year. Rendered in both the hero spec strip and the application panel.

### Application flow
1. **You** — name + valid email
2. **Education** — school, track, GPA (0.00–4.00)
3. **Essay** — prompt + 200–2,000 characters with a live counter
4. **Review** — summary + consent checkbox → submit

On submit, an application record is saved to `localStorage` under the key
`teslaScholarsApp`. Revisiting the page shows an **“ON FILE — IN REVIEW”** pill.

> To reset for demo purposes, run in the browser console:
> ```js
> localStorage.removeItem('teslaScholarsApp')
> ```

### Timeline progress
Computes the current cycle (Aug 12 → May 20) from the real date and fills the red progress line via a CSS variable — correct on desktop (horizontal) and mobile (vertical).

---

## 📱 Responsiveness

Fully responsive from **320px phones** to **ultrawide laptops**:

- Nav collapses to wordmark + Apply button
- Grids stack to single columns; sticky column releases
- Scholarship ticket, postcards, and timeline reflow for touch
- Form inputs are 16px+ to prevent iOS focus zoom

---

## ♿ Accessibility

- Semantic landmarks, labeled form fields, `aria-expanded` accordions, `aria-live` submission state
- Visible focus rings in Tesla red
- Keyboard support: track rows and FAQ items are focusable and Enter/Space-activatable
- Honors `prefers-reduced-motion` (disables ticker, reveals, scramble, pulses)

---

## 🧪 Browser Support

| Browser | Status |
|---|---|
| Chrome / Edge (latest) | ✅ |
| Firefox (latest) | ✅ |
| Safari (latest) | ✅ (webkit backdrop + stroke fallbacks included) |
| Mobile Safari / Chrome Android | ✅ |

---

## ⚖️ Disclaimer

This is a **design concept** for portfolio/educational purposes. It is **not affiliated with, endorsed by, or connected to Tesla, Inc.** No real applications are collected; data never leaves the browser.

---

*Accelerate the world's transition.* 🏁
