# Your Path to REACH Forgiveness — interactive workbook

A free, private, interactive web edition of the evidence-based **REACH Forgiveness** workbook by **Everett L. Worthington, Jr.** (Virginia Commonwealth University), adapted by **Richard Cowden** and **Kate Jackson-Meyer** as part of the [Human Flourishing Program](https://hfh.fas.harvard.edu/) at Harvard's Global Forgiveness Movement.

The workbook was evaluated in a multisite randomized controlled trial with 4,500+ participants across five countries and found to increase forgiveness, hope, and flourishing while reducing anxiety and depression (Ho et al., 2024, *BMJ Public Health*).

## Privacy model

**Everything a user writes stays on their device.** This is a static site — no server, no accounts, no analytics, no cookies. Responses are stored in the browser's `localStorage` and persist until the user erases them (an "Erase everything" control and text/JSON export live on the in-app Privacy page). A strict Content-Security-Policy (`connect-src 'none'`) blocks any network transmission, and all fonts are self-hosted, so the app makes **zero third-party requests**.

## Structure

```
index.html        app shell (CSP, fonts, noscript fallback)
css/style.css     design system (palette & type sampled from the printed workbook)
css/fonts.css     self-hosted @font-face declarations
js/app.js         hash router + renderers for every step/block type
js/content.js     the entire workbook as structured data (12 lessons)
js/storage.js     localStorage wrapper (save, resume, export, erase)
assets/fonts/     Poppins, Nunito Sans, Sacramento (woff2)
```

Lessons are pure data: each lesson is a list of steps, each step a list of typed blocks (`text`, `scale`, `choice`, `rank`, `timer`, `dialogue`, `certificate`, `blanks`, …) rendered by `js/app.js`. Editing content never requires touching the engine.

## Development

No build step. Serve the folder and open it:

```
python3 -m http.server 8000
```

## Deployment

Hosted on GitHub Pages from the `main` branch root. Hash-based routing (`#/lesson/4/2`) keeps deep links working on Pages without any 404 tricks.

## Attribution

- REACH Forgiveness model and workbook: Everett L. Worthington, Jr. — [EvWorthington-forgiveness.com](https://www.evworthington-forgiveness.com)
- Workbook adaptation: Richard Cowden, PhD & Kate Jackson-Meyer, PhD, Human Flourishing Program, Harvard University, with funding from Bancel Philanthropies and the Kern Family Foundation
- Original book design: [Wyndetryst](https://wyndetryst.com)

This self-guided workbook is not a substitute for professional mental-health care. See the in-app "Resources for Psychological Support" page.
