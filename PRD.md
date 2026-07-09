# PRD — Your Path to REACH Forgiveness (Interactive Web App)

**Status:** Draft for review
**Author:** Claude (with Wyatt)
**Date:** 2026-07-09
**Source material:** *Your Path to REACH Forgiveness* workbook (PDF, 49 pages) — Everett L. Worthington, Jr. (VCU), adapted by Richard Cowden & Kate Jackson-Meyer, Harvard Human Flourishing Program / Global Forgiveness Movement.

---

## 1. Overview

Transform the printed REACH Forgiveness workbook into an interactive, self-paced web app. The workbook is an evidence-based intervention (validated in a 4,500-participant RCT across 5 countries) that walks a person through forgiving one specific hurt via 12 short lessons built around the REACH model: **R**ecall, **E**mpathize, **A**ltruistic gift, **C**ommit, **H**old on.

The app breaks every lesson into small, discrete steps (one exercise — sometimes one prompt — per screen), replaces paper checkboxes and writing boxes with interactive controls, and adds timers, progress tracking, and gentle animation. Everything a user writes stays on their own device. No accounts, no server, no analytics.

### Goals
- Make the workbook *easier to complete* than the PDF: no printing, works on phone, picks up where you left off.
- Preserve the therapeutic sequence exactly — the lessons build on each other and the app should not let content be skipped ahead thoughtlessly (though users can always navigate back).
- Match the workbook's warm, botanical visual identity so it feels like the same product.
- Absolute clarity that responses are private and never leave the device.

### Non-goals
- No user accounts, cloud sync, or backend of any kind.
- No modification of the therapeutic content or exercise order.
- No native mobile app — but the web app is **mobile-first**: it should be beautiful and comforting to complete in a mobile browser, with desktop as the responsive enhancement.
- Not a replacement for therapy; retain the workbook's framing as self-directed learning.

---

## 2. Users

A single persona: someone carrying a specific interpersonal hurt who wants to work on forgiving it. They may be emotionally raw, may be on a phone, may be interrupted mid-session, and may be privacy-anxious about writing down sensitive things (the hurt often involves people they live or work with). Every design decision follows from those four facts.

---

## 3. Information architecture

```
Home (welcome, privacy promise, start/resume)
├── About / the letter from Ev & Tyler ("Dear Friend")
├── What is REACH? (the 5-step model, animated)
├── Privacy explainer (dedicated page, linked everywhere)
└── Journey (the 12 lessons)
    ├── Lesson intro screen (full-bleed color, lesson title)
    ├── Step 1..N (one exercise or sub-prompt per step)
    └── Lesson complete screen (recap + quiz where the workbook has one)
```

- **Hash-based routing** (`#/lesson/3/step/2`) so it works as a static GitHub Pages site with deep links and browser back/forward.
- A persistent **progress bar / lesson map** ("path" metaphor — a branch that grows leaves as you complete lessons, matching the botanical art).
- **Resume**: returning users land on a "Welcome back — continue Lesson 4, Exercise 4.3" card.

## 4. Content inventory & step breakdown (from the PDF)

Each workbook exercise becomes one or more app steps. Interaction types are noted.

### Front matter
| Screen | Source | Interaction |
|---|---|---|
| Welcome | Cover | Title animation; privacy promise front and center; Start button |
| Dear Friend | p.2 letter | Scrollable letter, styled as the navy page with script heading |
| REACH overview | p.3 | Animated reveal of R-E-A-C-H letters with definitions |

### Lesson 1 — What You Are About to Experience
| Step | Source | Interaction |
|---|---|---|
| Intro | Lesson 1 opener + "In a few hours…" | Read screen; sets expectation of 12 experiences, 10–20 min each |
| Ex 1.1 Rate your usual forgiveness | 1–10 checkboxes | Tappable 1–10 scale (leaf-shaped buttons), saved |
| Ex 1.2 Choose a specific hurt | Writing box | **First free-text box — privacy reassurance inline** ("This stays on your device. Nothing you type is ever sent anywhere."), autosave indicator |
| Ex 1.3 Rate decisional forgiveness | 1–10 | Tappable scale |
| Ex 1.4 Rate emotional forgiveness | 1–10 | Tappable scale (with the workbook's guidance text, progressively disclosed) |
| Ex 1.5 Quiz Yourself | Fill-in-the-blank D_____ and E_____ | Type-in blanks with letter hints, gentle validation (accepts "decision/decisional", "emotional"), confetti-free success state (leaves, not confetti) |

### Lesson 2 — Why Forgive?
| Step | Source | Interaction |
|---|---|---|
| Intro | Opener | Note that this lesson runs longer |
| Ex 2.1 Quotes (Angelou, McCourt) | Word input, YES/NO, rephrase box | Quote displayed with text animation; single-word input; yes/no toggle + reasons box; rephrase box |
| Ex 2.2 Benefits brainstorm | 4 quadrants | Four labeled text areas (Physical, Mental, Relationships, Spirituality) with the workbook icons |
| Ex 2.3 Benefits found by science | Read + pick one | Four expandable benefit cards; then "which most motivates you?" single-select |
| Ex 2.4 Reflection on something you once forgave | Writing box | Free-text with inline privacy note (second reassurance placement) |
| Ex 2.5 Forgiveness is good for you | 4 × 0–2 ratings | Four rating rows (0 = no better, 1 = somewhat, 2 = much better) |
| Ex 2.6 Decisional vs emotional linked | Writing box | Free-text |
| Ex 2.7 Different effects | Read | Two-column read screen, "Think About This" callout styled as the purple cloud |
| Ex 2.8 Quiz Yourself | Checklist recap | Animated checklist recap (auto-check items as user taps through) |

### Lesson 3 — Making a Decision to Forgive
| Step | Source | Interaction |
|---|---|---|
| Intro | Opener + "slide into decisions" page | Read |
| Ex 3.1 Injustice gaps | Rank A–D from 1–4 | Drag-to-rank (or tap-to-assign) with validation that each rank used once; then reveal the "most people rank A=4…" explanation |
| Ex 3.2 Forgiveness is a choice | 7 × GOOD/BAD | Tappable good/bad toggles per item |
| Ex 3.3 Release the burden | **Movement activity, "hold for 30 more seconds"** | Guided step-through with **30-second on-screen timer**, then re-rate decisional forgiveness 1–10 (app shows their Lesson 1 rating for comparison) |
| Ex 3.4 Decisional + emotional | Reflection prompt | Yes/no + read |
| Ex 3.5 Examine yourself | Pick 1 of 4 benefits | Single-select with icons |
| Ex 3.6 Practical suggestions | 5 suggestions, write your own, commit | Expandable suggestion cards; free-text for #5; multi-select "I commit to…" checkboxes |
| Ex 3.7 Quiz Yourself | 2 × yes/no + why | Toggles + free-text |

### Lesson 4 — R: Recall the Hurt
| Step | Source | Interaction |
|---|---|---|
| Ex 4.1 Change your mindset | Read + REACH preview | Read; REACH letters re-shown with lesson map |
| Ex 4.2 Importance of being a forgiver | Writing box | Free-text |
| Ex 4.3 Describe the hurt differently | Rewrite story + 3 differences | App shows their Ex 1.2 story alongside for reference; two text areas |
| Ex 4.4 Giving the hurt away | **Movement activity, ~1 min hold + release** | Guided sequence with **~60-second timer**, "open your hands" release animation |
| Ex 4.5 We do things for reasons | Writing box | Free-text + purple "Think About This" |
| Ex 4.6 Why did they hurt you? | 4 prompts + 4-option self-check | Four labeled text areas; then "Yes quite a lot / Yes some / Yes a little / Not yet" select |
| Ex 4.7 Quiz Yourself | Fill-in E______ F______ | Type-in blank with validation |

### Lesson 5 — E: Empathize With the One Who Hurt You
| Step | Source | Interaction |
|---|---|---|
| Intro | Opener + "most important exercise" page | Read |
| Ex 5.1 Role play — example | Example dialogue | Chat-bubble presentation of the ME/WRONGDOER example, messages animate in sequentially |
| Ex 5.1 Role play — your turn | 3+ exchanges | Chat-style composer: user writes alternating ME / WRONGDOER messages (min 3 exchanges) |
| Empty chair | **Movement activity, 5–10 min** | Instructions + their written dialogue displayed for reading aloud + **5-minute timer** (extendable) |
| Insights | 2 writing boxes + 5 questions | Free-text × 2; then five numbered empathy questions ("reasons to feel sorry for them?", "do they need forgiveness?", … "do you feel sorrow on their behalf?") as labeled text areas |
| Ex 5.2 Compassion | 4-option select + writing box | "None / A little / A moderate amount / A lot" select; "what could you do to feel more compassion" free-text |
| Ex 5.3 Taking it into daily life | 3 numbered boxes | Three text areas (next times you'll see the person) + imagination prompt |
| Ex 5.4 Other emotions | 2 numbered boxes | Two text areas |
| Ex 5.5 How much forgiveness is enough? | 3 scenarios × 3 options | Three single-select rows (stranger / no-longer-in-relationship / loved one) |
| Ex 5.6 Quiz Yourself | Fill-in E______ and C______ | Type-in blanks (empathy, compassion) with validation |

### Lesson 6 — A: Give an Altruistic Gift of Forgiveness
| Step | Source | Interaction |
|---|---|---|
| Ex 6.1 How might forgiveness be useful to you? | Writing box | Free-text + purple "Think About This" (altruistic forgiving brings greater benefits) |
| Ex 6.2 When did you do something altruistic? | 2 writing boxes | "What you did" and "what you felt" text areas |
| Ex 6.3 We are all capable of wrongdoing | Yehiel Dinur story + Q1 write, Q2 yes/no | Story presented with reveal animation; free-text; yes/no toggle |
| Ex 6.3b When did you need forgiving? | Writing box + 2 questions | Description text area + two numbered reflection boxes |
| Ex 6.4 Gratitude for our forgiveness | Writing box | "Letter of gratitude" style free-text |
| Ex 6.5 The gift of forgiving | Writing box | "Would you help them if in trouble?" free-text |
| Ex 6.6 A crucial question | Percent input + 1–10 rating | "I have forgiven ___ percent" number input; re-rate emotional forgiveness 1–10 **with Ex 1.4 comparison shown** |
| Ex 6.7 Quiz Yourself | Checklist + fill-in G______ | Animated checklist; type-in blank (grateful/gratitude) |

### Lesson 7 — C: Commit to the Forgiveness You Experienced
| Step | Source | Interaction |
|---|---|---|
| Ex 7.1 Commit by writing | Full-page writing box | Free-text |
| Ex 7.2 **Certificate of Emotional Forgiveness** | Fill-in certificate | Interactive on-screen certificate (date auto-filled, name of person, the hurt, percent forgiven, typed "signature" rendered in the script font); **downloadable/printable** — a signature app moment |
| Ex 7.3 What if it isn't complete? | Read + 3 steps | Read screen with the repeat-lessons guidance |
| Ex 7.4 Hand washing | **Movement activity** | Guided step-through (write "HURT" on hand, wash it off) with hand illustration + reflection check |
| Ex 7.5 Review of major concepts | R/E/A/C/H fill-ins + 2 definitions | Five type-in blanks validated against the REACH words; two definition text areas; "go back and check Ex 1.3/1.4" helper link |
| Ex 7.6 You can control your emotions | 5 numbered prompts | Five labeled text areas (Luskin "emotion channels" metaphor) |
| Ex 7.7 Quiz Yourself | Checklist + fill-ins | Recap; "Repeat Lessons ___ and ___" blanks (5, 6); S______ and L______ blanks (sympathy, love) |

### Lesson 8 — H: Hold on to Forgiveness When You Doubt
| Step | Source | Interaction |
|---|---|---|
| Ex 8.1 Things that make you doubt | Yes/no | Toggle + hot/cold reminders "Think About This" |
| Ex 8.2 Hold on during a "reminder" experience | Writing box + 3 columns | Free-text; three numbered text areas for future hot-reminder situations |
| Ex 8.3 Important example (hot stove) | Read | Read screen with the "pain ≠ unforgiveness" reframe callout |
| Ex 8.4 Control your worry (white bear) | **20-second timed activity** + 2 writing boxes | "Try NOT to think about white bears" with **20 s timer** and bear illustration; two reflection text areas |
| Ex 8.5 Summary of ways to hold on | Multi-select of 6 methods | Tappable method chips (select the ones you intend to use) |
| Ex 8.6 What demonstrates you got it? | 2 commitments | Read + two commitment checkboxes (teach one important person; teach five others) |
| Ex 8.7 Quiz Yourself | Writing box | "Write a sentence or two to convince yourself you have truly forgiven" free-text |

### Lessons 9 & 10 — Dedicate Yourself to Being a More Forgiving Person (12 steps across 2 lessons)
| Step | Source | Interaction |
|---|---|---|
| Intro | "2 lessons, 12 steps" page | Read; 12-step progress strip within these lessons |
| 9.1 Step 1: Why forgive? | Writing box | Free-text list |
| 9.2 Step 2: Five not-completely-forgiven hurts | 5 numbered boxes | Five text areas; **stored as a list reused in later steps** |
| 9.3 Step 3: Forgive one wound at a time | Pick one + R/E/A/C/H summaries | Select one of their five hurts (populated from Step 2); then five sequential screens — Recall / Empathize / Altruistic / Commit / Hold — each a leaf-badged writing box; ends with the "Can you now decide to forgive?" full-teal screen |
| 9.4 Step 4: Forgiveness heroes | 3 writing boxes | Three prompts (someone in your life / historical / present-day stranger) |
| 9.5 Step 5: Examine yourself | **Movement activity** | "Send yourself an email or text expressing your desire to be more forgiving" — app offers a compose-to-self helper (mailto:/copy button; nothing sent by the site itself) |
| 9.6 | Quiz deferred | Read screen: quiz comes at end of Lesson 10 |
| 10.1 Step 6: Become more forgiving | Writing box | Free-text |
| 10.2 Step 7: Change your experience with the past | Pick 1 of 5 + writing box | Select from stored Step 2 list; free-text |
| 10.3 Step 8: Plan your strategy | 3 writing boxes | Three prompts incl. dedication sentence |
| 10.4 Step 9: Forgiving under imagined conditions | Pick person + writing box | Select from Step 2 list; "imagine you are in a room with that person" free-text |
| 10.5 Step 10: Day to day | Pick person + writing box | Select from Step 2 list ("most negative feeling toward"); list their strengths |
| 10.6 Step 11: Consult someone you trust | Writing box | Free-text |
| 10.7 Step 12: Campaign of warmth | 2 columns | "Privately" and "Publicly" text areas |
| 10.8 Freeing yourself from the burden | **Movement activity, 30 s** | Final burden-release sequence with **30 s timer** (mirrors Ex 3.3 — closes the loop) |
| 10.9 What now? | Read | Read screen; link to EvWorthington-forgiveness.com longer workbook |
| 10.10 Quiz Yourself | Writing box | "Most important things you learned" free-text |

### Lesson 11 — Processing the Whole Workbook Experience
| Step | Source | Interaction |
|---|---|---|
| Intro: 4 lessons to remember | Pencil / mirror / bodybuilder / scientist | Icon-forward intro screen |
| Ex 11.1 Lessons of a pencil | Read, 4 points | Points reveal one-by-one alongside pencil illustration |
| Ex 11.2 Lessons of a mirror | **Movement activity** | Two-part guided mirror activity |
| Ex 11.3 Lessons of a bodybuilder | **Movement activity** | Flex-in-mirror moment with the strength metaphor |
| Ex 11.4 Lessons of a scientist | Read, 6 findings | Findings as revealed checklist |
| Ex 11.5 Evaluate your learning | 8 items × 1–5 scale | Eight rating rows (1 = not at all … 5 = tremendous amount), incl. the R/E/A/C/H self-naming item with type-in blanks |
| Ex 11.6 Quiz Yourself | 7-item checklist | "Could you explain this to a 13-year-old?" self-check checklist |

### Lesson 12 — Evaluating Just How Far You've Come
| Step | Source | Interaction |
|---|---|---|
| Ex 12.1 Rate (again) usual forgiveness | 1–10 | Scale **with Ex 1.1 answer shown side-by-side**; delta celebrated gently |
| Ex 12.2–12.3 Consider the hurt; rate (again) decision to forgive | 1–10 | Scale with Ex 1.3 comparison |
| Ex 12.4 Rate (again) emotional forgiveness | 1–10 | Scale with Ex 1.4 comparison; **journey summary chart** of all before/after ratings |
| Ex 12.5 Rate what you learned | Read | Encouraging read screen ("you can return to this workbook for new hurts") |
| Ex 12.6 How long did you spend? | Hours + minutes | Number inputs (app can offer its own tracked estimate) |
| Ex 12.7 Feedback | Writing box + 0–100% scale | Free-text (stays local like everything else) + likelihood slider |
| Ex 12.8 Conclusion | Closing message | Full navy closing screen with the completed tree illustration — every lesson's leaf now grown |

### Back matter
| Screen | Source | Interaction |
|---|---|---|
| Resources for Psychological Support | p.121 | Always-accessible page (footer link): "this is not a substitute for counseling" + the workbook's therapist directory links (Psychology Today, Headway, InnoPsych, GoodTherapy, Zencare, ABCT, NOCD) |
| Notes | p.120 | Optional free-notes page in the menu |

## 5. Interaction & motion design

- **One thing per screen.** Short read screens; a single rating, prompt, or activity per step. Continue button advances; progress within lesson shown as dots/leaves.
- **Timers** for the timed activities (30 s burden holds in Ex 3.3 and 10.8, ~60 s in Ex 4.4, 5 min empty chair in Lesson 5, 20 s white bear in Ex 8.4) — large, calm countdown with a growing-leaf animation rather than an anxious ring; skippable (the workbook never forces).
- **Text animations**: headline words fade/rise on lesson intros; quotes type in gently; REACH letters draw in with the script-font stroke effect. Subtle — this is a contemplative product, not a marketing site. Respect `prefers-reduced-motion`.
- **Autosave everything** on input (debounced), with a quiet "Saved on this device ✓" microcopy near text boxes.
- **Comparisons over time**: wherever the workbook asks to re-rate (Ex 3.3 vs 1.3), show the earlier answer for reflection.
- **Quizzes**: forgiving validation (case-insensitive, accepts near-matches), always allow "show me" — quizzes are for consolidation, not gatekeeping.
- **Lesson completion**: the path/branch on the journey map sprouts a new colored leaf; brief affirming copy from the workbook's tone.

## 6. Privacy & data model (core requirement)

- **All responses stored in `localStorage`** under a single versioned key (e.g. `reach-forgiveness.v1`). Nothing is ever transmitted — the site is static files with zero network calls after load (self-hosted fonts, no analytics, no CDNs at runtime).
- Why localStorage rather than a literal session cookie: cookies are sent to the server with every request, which contradicts "no data is sent anywhere"; localStorage never leaves the browser and survives accidental tab closes so users don't lose deeply personal writing mid-journey.
- **Privacy messaging appears:**
  1. On the welcome screen, prominently, before "Start" — plain-language: "Everything you write stays on this device. No account. No server. We couldn't read your answers even if we wanted to."
  2. Inline beside the **first three text inputs** (Ex 1.2, 2.1, 2.4).
  3. In the footer of every page ("Private by design — your writing never leaves this device").
  4. On a dedicated "How your privacy works" page explaining localStorage in plain language, including the honest caveats: answers are visible to anyone using this browser profile; clearing browser data erases them.
- **User data controls:** "Download my responses" (JSON and printable text export) and "Erase everything" (with confirm) in a settings/menu area.
- No third-party requests at all. CSP meta tag as belt-and-suspenders.

## 7. Visual design (from the PDF)

**Palette** (sampled from the workbook):
| Token | Hex (approx) | Use |
|---|---|---|
| Cream | `#F4EFE3` | Page background, writing boxes |
| Teal | `#1B7F72` | Primary headings, buttons, lesson accents |
| Deep teal | `#0F6659` | Hover/darker accents, full-bleed teal pages |
| Ink navy | `#123B53` | Dark pages (letters, quizzes), body text on light |
| Plum | `#7E3A67` | "Think About This" callouts, numerals, subtitle text |
| Mustard | `#E7B54A` | Leaf accents, highlights |
| Sage | `#8FBCAD` | Leaf accents, secondary chips |
| Lavender | `#C6A3C8` | Leaf accents |
| Slate blue | `#5B7E96` | Leaf accents |

**Typography:**
- Headings: geometric sans in the spirit of the workbook's (e.g. **Poppins** SemiBold) — teal on cream, white on navy.
- Script accents ("Exercise 1.1", "Quiz Yourself", "Dear Friend"): monoline script (e.g. **Sacramento**).
- Body: humanist sans (e.g. **Nunito Sans**).
- All fonts self-hosted (no Google Fonts requests at runtime — privacy).

**Illustration:** recreate the workbook's motifs as inline SVG — line-drawn branches with scattered colored leaves; overlapping translucent leaf-shape collages for lesson title screens; the purple thought-cloud "Think About This" badge; checkbox and leaf-shaped rating buttons on cream ovals. The quiz pages use the navy background with white script, as in the book.

## 8. Technical approach

- **Stack: zero-build static site** — semantic HTML, modern CSS (custom properties, grid), vanilla ES modules. No framework, no bundler, no dependencies. Rationale: GitHub Pages serves it directly; trivially auditable ("view source proves no data leaves"); nothing to maintain.
- **Structure:**
  ```
  /index.html          app shell
  /css/…               design tokens + components
  /js/app.js           hash router, step engine
  /js/content.js       all workbook content as structured data (lessons → steps → blocks)
  /js/storage.js       localStorage wrapper, export/erase
  /assets/…            SVGs, self-hosted fonts
  ```
- **Content as data**: every lesson/step defined declaratively (type: `read | scale | text | multitext | quiz-blank | rank | choice | timer-activity | dialogue | certificate | percent | checklist`), so content tweaks are data changes, not new code.
- **Responsive**: designed mobile-first (the workbook is likely to be done on a couch, on a phone); comfortable reading measure on desktop.
- **Accessibility**: WCAG AA contrast, full keyboard operability, visible focus, `aria-live` for timer/save states, `prefers-reduced-motion` honored, semantic headings.
- **Works offline after first load** (optional stretch: tiny service worker so the journey continues without connectivity — also reinforces the privacy story).

## 9. Deployment

- GitHub repository with the site at root (or `/docs`), **GitHub Pages** via Actions or branch deploy.
- No custom domain assumed (URL: `https://<user>.github.io/<repo>/`); hash routing avoids 404 issues on Pages.
- README covering the project, privacy stance, and how to add lessons.

**Decided:** repo `forgiveness`, created and pushed via `gh`, Pages enabled (URL: `https://<user>.github.io/forgiveness/`).

## 10. Milestones

1. **M1 — Skeleton**: shell, router, design tokens, storage layer, welcome + privacy pages.
2. **M2 — Lesson engine**: all step/block types incl. timers, scales, quizzes, dialogue composer.
3. **M3 — Content**: all 12 lessons fully authored from the PDF; journey map; resume flow.
4. **M4 — Polish**: animations, SVG illustration set, certificate, export/erase, a11y pass, mobile QA.
5. **M5 — Deploy**: repo, Pages workflow, README.

## 11. Success criteria

- A user can complete all 12 lessons end-to-end on a phone with no instructions.
- Refresh/close/reopen at any point resumes exactly where they left off with all writing intact.
- The network tab shows **zero requests** containing user data at any point (verifiable claim, stated on the site).
- Visual side-by-side with the PDF reads as the same brand.
- Lighthouse: 95+ accessibility, 95+ performance.

## 12. Decisions (resolved)

1. **Copyright/attribution**: Wyatt is doing this work with Harvard and is comfortable publishing it. The site carries full attribution and a link to EvWorthington-forgiveness.com.
2. **Storage**: **localStorage** confirmed — responses persist until the user deletes them (via the in-app "erase everything" control or clearing browser data). Never transmitted.
3. **Sensitive-context safety**: the workbook itself includes a "Resources for Psychological Support" page ("not a substitute for certified mental health counseling") — surfaced in the app footer and as its own always-reachable page.
4. **Deployment**: repo named **`forgiveness`**, created and pushed by Claude, with GitHub Pages enabled.
