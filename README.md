# MoodiCare — Product Design Case Study

Static HTML/CSS page presenting a Product Design case study for **MoodiCare**, a
mobile app that integrates medication adherence and mood tracking for
mental-health care.

> This repository is the **case-study website**, not the MoodiCare app. It
> contains no application code — only a single static page, its stylesheet
> system, design documentation, and exported design assets.

## Project overview

MoodiCare is an academic Product Design / Information Systems project: a mobile
app concept and high-fidelity prototype that brings medication-routine management
and emotional self-monitoring into one experience, with a shared calendar,
weekly and monthly indicators, and an exportable clinical report. The app was
implemented and run on a real device as part of the project.

This repository presents that work as a self-contained case-study page. It walks
through the project's origin, the problem, exploratory research, personas,
product and UX decisions, flows, visual identity, validation, and reflections.
The page is built from a Figma visual reference — each block carries a
`data-figma` attribute linking it to its Figma node — and from the project's
written source of truth, `project documentation`.

Two things are kept distinct throughout this README:

- **MoodiCare (the product / academic project)** — the app, its documented
  capabilities, and its implementation. Context only; none of it lives in this
  repository.
- **This repository (the case-study page)** — a static HTML/CSS document *about*
  that project.

## Current status

Work in progress. `index.html` is an explicitly labelled structural scaffold:
the section structure and the visual system are in place, but 19 blocks are
marked `data-provisional` — copy that is not final, still in Portuguese, or
dependent on an asset flagged for cleanup. The design-system consolidation is
complete and documented in `design-system.md`; a short list of open
visual-review items is kept in its section 11.

Regarding the product itself, as documented in `project documentation`: the app was
implemented and executed on a real device, but has **not** been published to app
stores and has **not** been used by anyone outside the project team.

## Documented product capabilities (MoodiCare app)

Described in the project sources; **not implemented in this repository**:

- Medication registration with dosage form, posology, schedule, treatment
  duration and stock control
- Dose states: confirm, postpone, skip, extra dose, suspend and resume — with
  history preserved
- Mood logging: 1–10 intensity scale, feeling selection, optional free-text notes
- Integrated calendar showing medication and mood entries by date
- Weekly and monthly indicators (adherence, mood average and distribution)
- Clinical report exported as PDF, with email/export
- Reminders and notifications
- Account, profile and notification settings

### What this web implementation actually contains

- One static page (`index.html`): a cover, a Project Overview metric strip,
  nineteen titled case sections (Context, Problem, Solution, My Role,
  Methodology, Requirements, Competitive Analysis, Target Audience, Empathy Map,
  Personas, User Journey, Sitemap, Card Sorting, Wireframes, Visual Identity,
  Validating the Proposal, The Flows, Outcomes &amp; Recognition, Reflection
  &amp; Next Steps) and a closing footer
- A four-file CSS design-token and component system
- Static images exported from the Figma reference (app screens, phone mockups,
  personas, illustrations, decorative SVGs)
- Responsive layout with three breakpoints, and horizontal-scroll containers for
  oversized diagrams
- No interactivity: there is no JavaScript in the project

## Tech stack

**This repository**

- HTML5 — a single semantic document, `index.html`
- CSS3 — custom properties (design tokens), Grid, Flexbox, fluid type via
  `clamp()`, and `@media` queries (breakpoints at 480 / 640 / 900)
- Poppins, loaded from Google Fonts via `<link>`, with a system-font fallback
  stack
- `tokens.json` — design tokens in DTCG format (a documentation and
  Figma-translation artifact; not consumed at runtime)
- No JavaScript, no framework, no build tool, no package manager, and no
  dependencies to install

**MoodiCare app** (context only, not in this repository) — per `project documentation`:
React Native for the mobile app, Laravel for the backend/API, PostgreSQL for
persistence, and Figma for the prototype.

## Project structure

```
.
├── index.html              Single-page case study (semantic sections, data-figma refs)
├── assets/
│   ├── css/
│   │   ├── tokens.css      Design tokens — primitive + semantic tiers, plus exceptions
│   │   ├── base.css        Reset, element defaults, focus styles, container helpers
│   │   ├── layout.css      Page shell, section-band rhythm, tinted/dark bands, rings
│   │   └── components.css  Nine reusable components + section composition patterns
│   └── img/
│       ├── README.md       Log of exported Figma assets and their source nodes
│       ├── flows/          Flow screen exports (flow-28 … flow-51)
│       └── *.png / *.svg / *.jpg   Screens, mockups, personas, illustrations, decor
├── tokens.json             Design tokens in DTCG JSON (mirrors tokens.css)
├── design-system.md        Design-system reference
├── project documentation            Operational source of truth (PT) — context, evidence, decisions
├── project guidelines               Project brief and working guidelines (PT)
└── README.md               This file
```

CSS load order is `tokens → base → layout → components`.

## How to run locally

There is no build step and no dependencies. Clone the repository:

```
git clone https://github.com/sahmanuela/moodicare-case-study.git
cd moodicare-case-study
```

Then open `index.html` in a browser (double-click it, or drag it into a browser
window). Everything works from the local file system. The Poppins webfont
requires an internet connection; a system font is used as a fallback when
offline.

Optionally, if you have Python installed, you can serve the folder over HTTP:

```
python -m http.server 8000
```

and visit `http://localhost:8000`.

## Design system overview

Documented in full in `design-system.md`. In brief:

- **Two token tiers** — `primitive` (raw values), then `semantic` (intent-named
  aliases). Components reference semantic tokens only. A small `exceptions` block
  covers three identity elements: the phone-mockup geometry, the decorative
  rings, and the organic blob-swatch radius.
- **Nine reusable components** — section heading, eyebrow/kicker, card (with
  surface and scale modifiers), badge, marker list, quote, media frame, data
  table, stat number. Section-specific classes handle composition (grid, order,
  position) only.
- **Ten typographic roles** — display, section title, h2, h3, lead, body,
  body-small, caption, label/kicker, metric.
- **Three breakpoints** — `max-width` 480 / 640 / 900.
- **`tokens.json`** mirrors the token layer in DTCG JSON, grouped for later
  translation into Figma variables and styles. Fluid type, gradients and layered
  shadows stay in the web layer and are noted rather than exported as variables.

## Visual direction

Off-white ground; teal (verde-água) paired with deep navy (azul-marinho);
Poppins throughout; rounded, organic geometry — concentric decorative rings,
blob-shaped swatches, a highlighter swipe behind section titles, pill shapes;
overlapping tilted phone mockups on the cover; a calm, plain-spoken, editorial
tone. Sections are composed differently but built from the same small kit.

## Documentation and source files

| File | Contents |
|--|--|
| `project documentation` | Operational source of truth (Portuguese) — project context, evidence, decisions, flows, requirements, and the recalculated survey figures. |
| `design-system.md` | Design-system reference (English) — tokens, components, rhythm, responsive rules, accessibility notes, and open items. |
| `tokens.json` | Design tokens in DTCG format. |
| `project guidelines` | Project brief and working guidelines (Portuguese). |
| `assets/img/README.md` | Export log mapping each asset to its Figma source node. |

## Credits

- **Author:** Samantha Manuela Ferri Tavares — end-to-end UX/UI.
- **Advisor:** André Fabiano de Moraes.
- **Academic context:** undergraduate project in Information Systems, Instituto
  Federal Catarinense — Campus Camboriú, 2026.
- **Documented recognition** (from `project documentation`): presented at the XV FICE
  (2024), recognised as *Trabalho Destaque* in the Research category; full paper
  accepted and presented at DiTTEt 2025 (Salamanca); presented at Latinoware
  2025 (Foz do Iguaçu).
- **Assets:** UI reference and prototype in Figma; illustrations from the
  *Lifesavers* collection on Blush; typeface Poppins via Google Fonts.

## License

No license file is currently included in this repository, and no license has
been defined in the project sources. Until one is added, all rights are reserved
by the author.
