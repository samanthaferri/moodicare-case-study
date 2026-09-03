# Exported Figma assets

Exported from the Figma reference (file `visual reference`, frame
`moodicare-en` 11600:31363) for the first visual pass. Re-export from Figma
if the design changes.

## In use — hero / overview / context

| File | Figma source | Used for |
|--|--|--|
| `logo-heart.svg` | cover · logo icon | logo tab mark |
| `deco-rings-union.svg` | cover · "Union" (11593:31222) | hero top-right decoration |
| `deco-rings-corner.svg` | "Shape" (concentric rounded-rect rings) | hero bottom-left, overview top-left, context bottom-right, solution bottom-right |
| `cursor-click.svg` | cover · cursor icon | hangs off the "UI/UX Case Study" pill |
| `figma-mark.jpg` | cover · Figma chip | Tools chip |
| `screen-add-medication.png` | cover · "screen 2" (11593:31230) | back phone mockup |
| `screen-home.png` | cover · "screen 1" (11593:31231) | front phone mockup |
| `context-stat-prevalence.png` | context · 11603:31528 | "Prevalence" stat illustration |
| `context-stat-treatment.png` | context · 11603:31536 | "Treatment gap" stat illustration |
| `context-stat-cost.png` | context · 11603:31544 | "Cost" stat illustration |

## In use — sections 4-16

| File | Figma source | Used for | Notes |
|--|--|--|--|
| `sitemap.png` | "Sitemap" (11622:32615), exported @2x | Sitemap diagram | top title band cropped off; keeps the diagram's own legend |
| `empathy-map.png` | "Mapa da Empatia" (11622:33430), exported @2x | Empathy Map panel | PT title cropped off; panel text still Portuguese |
| `wireframes.png` | "Wireframes" (11622:33683), exported @2x | Wireframe mosaic | title band cropped off |
| `target-illustration.png` | "Público-alvo" block (11622:34502), exported @2x | source for the crop below | not referenced directly |
| `target-scene.png` | cropped from `target-illustration.png` | Target Audience illustration | illustration only, text removed |
| `persona-camila.png` | personas · raw fill 1 (11622:34325 subtree) | Persona 1 avatar | |
| `persona-renata.png` | personas · raw fill 2 | Persona 2 avatar | |
| `persona-henrique.png` | personas · raw fill 3 | Persona 3 avatar | |

## In use — Product Flows section (`flows/`)

Copied verbatim from the earlier build `project asset source`
(originals untouched). Every file is a 1600×733 hi-fi screenshot strip: mint
background, teal corner wave, 2–5 phone screens in a row. App UI is in
Brazilian Portuguese. Not exported from this Figma frame.

| File(s) | Flow | Notes |
|--|--|--|
| `flows/flow-28.png`, `flow-29.png` | 01 Onboarding & account creation | flow-28 is sparse (3 phones) |
| `flows/flow-30.png`, `flow-31.png` | 02 Login & password recovery | flow-30 is sparse (2 phones) |
| `flows/flow-32.png` | 03 Home & daily navigation | empty states + quick-add sheet |
| `flows/flow-33.png`, `flow-34.png` | 04 Mood logging + feelings management | |
| `flows/flow-35.png`…`flow-39.png` | 05 Medication registration (5 posology modes) | shown as one strip + two `.filmstrip-pair` rows; the "frequency select" screen repeats as phone 1 of each |
| `flows/flow-40.png` | 06 Extra / PRN doses | |
| `flows/flow-41.png`, `flow-42.png` | 07 Integrated calendar | **flow-42** has `Sentimento 1` / `Lorem ipsum` placeholder text + a `Remver` typo — marked `data-provisional`, flagged in caption |
| `flows/flow-43.png` | 09 Medication management (suspend / resume) | |
| `flows/flow-44.png`, `flow-46.png`, `flow-47.png` | 10 Settings, notifications & privacy | **flow-47** contact form shows `Lorem ipsum` — marked `data-provisional`, flagged in caption |
| `flows/flow-45.png` | (not placed) | account management; available if flow 10 needs a fourth strip |
| `flows/flow-48.png`, `flow-49.png` | 08 Indicators (weekly / monthly dashboards) | |
| `flows/flow-50.png`, `flow-51.png` | 08 Clinical report (PDF, pp. 1–4) | paper-document mockups, shown in `.report-cards`, not a phone filmstrip |

## Still needed (later revisions)

- Methodology illustration ("Lifesavers - Study Online 1", 11622:34526) — the
  section is now rebuilt from process chips + principles, but an illustration
  could still be added.
- Competitor app icons — the table uses neutral monograms; real icons are
  third-party and not bundled.
- Approved English copy for the blocks still marked `data-provisional`
  (Role intro/tags, Empathy is now English, Target list still PT, Personas now
  English, Card Sorting now English, Visual Identity type note still PT, all
  Product Flows copy, Validation, Outcomes, Reflection).
- Cleaned or English-UI versions of `flows/flow-42.png` and `flows/flow-47.png`.
- Contact email for the footer credits (left blank pending Samantha's confirmation).
- Page length: with the flows added the page is ~34 k CSS px. Consider capping
  the sitemap / wireframes / filmstrip image heights in a later pass.
