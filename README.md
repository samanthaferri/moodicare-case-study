# MoodiCare — Product Design case study (site)

Static HTML + CSS case study for **MoodiCare**, a mobile app that integrates
medication adherence and mood tracking for mental health care.

> **Status: structural scaffold.** This is a first skeleton built from the
> Figma visual reference (frame `moodicare-en`, node `11600:31363`). The
> narrative is not finalized — headings use the structural labels drawn in the
> reference and all body text is placeholder. Do not treat any copy here as
> final.

## Structure

```
index.html              Semantic skeleton: cover + 16 <section> bands
assets/css/tokens.css    Design tokens (color, type scale, spacing, radii)
assets/css/base.css      Reset + document defaults + helpers
assets/css/layout.css    Page shell, section rhythm, tinted bands, responsive
assets/css/components.css First-pass styles for recurring components
assets/img/              Figma exports (screens, mockups, illustrations)
```

Each `<section>` carries `data-figma="<node id>"` linking it to its Figma node,
and a `#slug` id. No JavaScript, no framework, no build step — open
`index.html` directly.

## Section order (matches the Figma reference)

1. Cover · 2. Project Overview · 3. The Context · 4. The Problem ·
5. The Solution · 6. My Role in the Project · 7. Sitemap ·
8. Competitive Analysis · 9. Empathy Map · 10. Target Audience ·
11. Methodology · 12. Personas · 13. Information Architecture (Card Sorting) ·
14. Wireframes · 15. Visual Identity · 16. User Journey

## Provisional in the current Figma — needs review before content

Blocks marked `data-provisional` in `index.html`:

- **The Problem** — band holds only the intro paragraph; rest is empty.
- **My Role, Empathy Map, Target Audience, Methodology, Personas,
  Information Architecture, User Journey** — reference copy is still in
  Portuguese (or bilingual). Target language for the case is English.
- **Personas** — "Personality" tags are `Label` placeholders in the Figma.
- **Wireframes** — ~17 empty grey screen rectangles (image placeholders).
- **Competitive Analysis** — column headers Portuguese; no section title drawn;
  13 rows in data vs ~9 visible in the band.
- **Visual Identity** — two empty `Group` frames; gradient swatch has no hex.
- **Methodology** — reference paragraph currently claims validation "with real
  users"; case copy must not reproduce that.
- Section frames in Figma reuse generic names (`solution`, `mapa da empatia`) —
  semantic ids were assigned here.
