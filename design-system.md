# MoodiCare — Design System

A deliberately small system: two token tiers, nine reusable components, three
exceptions, three breakpoints. Enough to keep ~20 sections coherent and to
translate cleanly into Figma later, without becoming a template.

**Identity it protects**
Off-white ground · teal (verde-água) + deep navy (azul-marinho) · Poppins ·
rounded / organic geometry (concentric rings, blob swatches, the highlighter
swipe behind section titles, pills) · overlapping tilted phone mockups · a calm,
plain-spoken, editorial voice. Sections compose differently; they are built from
the same small kit.

---

## 1. Files

| File | Role |
|--|--|
| `assets/css/tokens.css` | Two tiers — **primitive** then **semantic** — plus a small **exceptions** block. The only file with raw values. |
| `assets/css/base.css` | Reset, element defaults, `:focus-visible`, `prefers-reduced-motion`, `.container` helpers. |
| `assets/css/layout.css` | Page shell, section-band rhythm, tinted / dark bands, decorative rings, `.scroll-x`. |
| `assets/css/components.css` | The 9 components + section composition patterns. References semantic tokens only — no raw hex / rgba, no unscaled px (bar three documented exceptions). |
| `tokens.json` | The same tokens in DTCG JSON, grouped for Figma-variable translation. Primitive + semantic; only Figma-representable values (fluid type, gradients and layered shadows are noted, not exported as variables). |

Load order: `tokens → base → layout → components`.

---

## 2. Token tiers

```
PRIMITIVE   raw, context-free      --teal-500: #47b2b0
   ↓ aliased by
SEMANTIC    intent / role          --color-action-primary: var(--teal-500)
```

Components reference **semantic** tokens. Primitives are never used directly.
There is **no component-token tier** — a card that needs to deviate does so with
a local rule, documented as a content-specific style.

**Exceptions** (`:root` block, do not grow): the phone-mockup geometry
(`--phone-*`), the decorative rings (`--deco-*`), and the organic blob-swatch
radius (inline in `components.css`).

### Primitive groups (tokens.css › tier 1)
- **Colour** — `--white`; teal `700/500/200/100/050/frame/bright/grad-lite`;
  navy `900/800/700/200/300`; neutral `900/800/400/350/200/150/050`;
  `--coral-500`; amber `050/200/700/800`; `--slate-200`;
  `--overlay-05/06/12/14/35`.
- **Type** — `--font-poppins`; weights `light/regular/medium/semibold/bold/black`;
  sizes `display/title/h2/h3/lead/body/sm/xs/2xs/metric` (fluid via `clamp()`);
  line-heights `tight/snug/normal/relaxed`; tracking `tight/normal/wide/wider`.
- **Space** — `--space-1…8` (4 → 64px).
- **Radius** — `xs 8 · sm 12 · md 16 · lg 24 · pill · round`.
- **Border width** — `hairline 1 · thin 2 · thick 3`.
- **Shadow** — `sm · card · raised` (+ `--phone-shadow` exception).
- **Z-index** — `below -1 · deco 0 · base 1 · raised 2`.
- **Layout** — `--container 1240 · --container-narrow 1080 · --gutter · --section-space`.
- **Breakpoints** — `--bp-xs 480 · --bp-sm 640 · --bp-md 900` (reference; `var()`
  is invalid inside `@media`).

### Semantic groups (tokens.css › tier 2)
| Group | Tokens |
|--|--|
| text | `primary · secondary · muted · strong · accent · on-brand · on-inverse · on-inverse-muted` |
| surface | `page · card · soft · soft-alt · tinted · frame · inverse · notice · inset-inverse` |
| border | `subtle · divider · strong · muted · notice · on-inverse · on-inverse-strong` |
| action | `primary · primary-hover` · `--color-link · --color-link-hover` |
| accent | `brand · on-inverse` · `--color-title-highlight` |
| focus | `--color-focus-ring` |
| feedback | `error · notice-text · notice-heading` |
| gradient | `inverse · brand · notice` (web only; Figma → gradient styles) |
| type roles | `--text-display / -title / -h2 / -h3 / -lead / -body / -body-sm / -caption / -label / -metric` (10) + `--font-family-base` |

---

## 3. Typography — 10 roles

| Role | token | ~px (mobile → desktop) | weight · line-height | Use |
|--|--|--|--|--|
| Display | `--text-display` | 44 → 70 | black · 1.15 | cover title |
| Section title | `--text-title` | 32 → 41 | medium (accent word bold) · 1.15 | every band title |
| H2 | `--text-h2` | 22 → 32 | bold · 1.15 | flow title, footer h2, cover tagline |
| H3 | `--text-h3` | 20 | bold · 1.35 | card titles; eyebrow (semibold); sub-heads |
| Lead | `--text-lead` | 20 → 26 | regular · 1.5 | standfirst paragraphs; context stat value |
| Body | `--text-body` | 18 | regular · 1.65 | default running copy |
| Body small | `--text-body-sm` | 15 | regular · 1.65 | card body, list items, table cells |
| Caption | `--text-caption` | 13 | regular · 1.65 | captions, sources, swatch hex — colour `text/muted` |
| Label / kicker | `--text-label` | 11.5 | bold, `.12em`, UPPERCASE | kickers, journey sub-labels, micro-badges |
| Metric | `--text-metric` | 32 → 42 | bold, `-.03em` · 1 | overview + validation big numbers |

Applied through: `.section-title`, `.eyebrow` (+ `--dot`), `.kicker`,
`.section-lead` (+ `--justify`), `.section-note`, `.card__title`, `.card__text`,
`.stat-number`, and the base element defaults.

---

## 4. Containers & rhythm

- `.container` (1240) · `.container--narrow` (1080). One `--gutter`,
  `margin-inline: auto`. `.page { overflow-x: clip }` lets rings bleed.
- **Section rhythm — one value.** `.section { padding-block: var(--section-space) }`;
  `.section + .section { padding-top: 0 }` so the gap between any two sections is
  `--section-space` **once**, never doubled. Full-bleed colour bands
  (`.section--tinted`, `.section--deep`) keep their own top padding for internal
  breathing room; the band after one restarts the rhythm. `#overview` drops its
  top padding (it follows the `<header>`, which the collapse rule can't reach).
- **Section head → content gap:** `.section__head { margin-bottom: var(--space-6) }`
  (32px) — the single title→content value; a standfirst (`.section-lead`) adds its
  own `var(--space-7)` below itself.
- **Intro → first content block:** `var(--space-6)` where the block sets its own
  `margin-top` (`.problem-grid`, `.req-grid`, `.process`, `.principles`,
  `.role-tags`, `.vstats`, `.outcomes`, `.reflect`, `.persona`, `.stat-card`,
  `.flow-index` …).
- **Grid gap** default `--space-5`; **card padding** `--space-6`
  (`--space-7 --space-6` roomy via `.card--pad-lg` / `--pad-roomy`).

---

## 5. Reusable components (9)

Contract: purpose · structure · variants · a11y. `components.css` is the source
of truth.

### 5.1 Section heading — `.section-title` (+ `--center`, `__accent`)
Poppins Medium with an organic teal-100 highlighter (`::before`) that spans the
**whole title width + ~20px each side**, sitting low like an underline (pill
ends). Emphasis word is `<span class="section-title__accent">` (Bold /
`text/accent`). On `.section--deep` it flips to white / teal-bright (rules in
`layout.css`). A11y: real `<h2>`; the accent span is styling only.

### 5.2 Eyebrow / kicker — `.eyebrow` (+ `--dot`), `.kicker`
Two roles, one component family. `.eyebrow` = H3-size, semibold, teal, sentence
case (Project Overview); `--dot` adds a 12px teal dot and left-aligns (Visual
Identity sub-heads). `.kicker` = label-size, bold, tracked, UPPERCASE, teal-700
(research question, deep-dive, outcomes year, footer credits). A11y: `<p>`
elements — decorative labels, not headings.

### 5.3 Card — `.card` (+ surface & scale modifiers)
Base: white surface, hairline `border/subtle`, `shadow/card`, `radius/lg`,
`space-6` padding.
- **Surface modifiers** — `.card--soft` (teal-050 fill), `.card--notice`
  (amber + `radius/md`), `.card--dark` (navy gradient, flips text),
  `.card--dark-inset` (translucent, for use on a dark band).
- **Scale modifiers** — `.card--pad-lg`, `--pad-roomy`, `--pad-sm`, `--radius-sm`.
  Every card carries the same `shadow/card`; there is no per-card shadow.
- **Content roles** — `.card__title` (H3), `.card__text` / any bare `<p>` (body
  small, secondary), and a bare `<ul>` auto-takes the marker-list dot treatment.
Absorbs the former `.feature`, `.req`, `.rec`, `.reflect__card`, `.pnd-card`,
`.persona__card` / `__main`, `.problem-pain`, `.audience__panel`, `.sort-card`,
`.empathy`, `.research-q`, `.method-note`, `.deepdive`, `.mode`, `.vstat` — each
now `.card` + modifiers (+ a small composition class where the section needs a
tweak: `.feature` centres, `.sort-card` flushes padding + teal-100 body,
`.research-q` adds the notice gradient + centres, `.deepdive` sets the roomy dark
padding, `.method-note` sets max-width + placement).

### 5.4 Badge — `.badge` (+ `--pill / --tag / --chip / --mono / --label / --outline`)
`--pill` solid teal · `--tag` tinted rounded-rect ·
`--chip` small soft-teal · `--mono` 30px square monogram · `--label` uppercase
micro (`--solid` teal, `--strong` navy) · `--outline` white bordered pill.
Absorbs `.pill-label` (kept as a size tweak on `--pill`), `.role-tag`,
`.persona__chip`, `.problem-pain__tag`, `.req__badge`, `.compare__mono`,
`.process__chip`.

### 5.5 Marker list — `.marker-list` (+ `--square / --none / --cols`)
Teal dot bullets. `--square` = the flow-decision marker; `--none` = emoji-led
lists (target audience); `--cols` = two columns (flow decisions), collapses at
640. Bare `<ul>` inside a `.card` gets the same treatment without a class.

### 5.6 Quote — `.quote`
Solid teal block, white text, `radius/lg`. Rendered as `<blockquote>` (personas).

### 5.7 Media frame — `.media` (+ `--center / --wide / --framed / --document`)
`.media` = image at `radius/lg`. `--center` caps + centres (wireframes);
`--wide` = horizontal scroll for an oversized diagram (sitemap); `--framed` =
bordered `surface/frame` box with an inner `.media__scroll` (screenshot
filmstrips); `--document` = paper card with `shadow/raised` (clinical report).
`.media__cap` = the caption below. `.media-pair` / `.report-cards` are grid
compositions of these.

### 5.8 Data table — `.data-table` (+ `--comparison / --journey`)
`--comparison` = white rounded table, `shadow/card`, row hairlines, `.check`
marks (`--yes` tick, `--no` faint open ring). `--journey` = `border-spacing`
gaps, tinted header + row-label cells, white body cells, coral `.is-barrier`
column, `.data-table__sub` PT labels. Both wrap in `.scroll-x` with a
`min-width`. A11y: real `<table>`/`<th scope>`; the coral column is named by its
header.

### 5.9 Stat number — `.stat-number`
Metric-size, bold, `-.03em` tracking; `<em>` segment in `accent/brand`. Shared
by the Project Overview metric grid and the Validation stat cards. (The Context
evidence card's value stays lead-sized — a content-specific style.)

---

## 6. Composition patterns

Section layouts. CSS here is **grid / position only** — they carry no box
styling of their own; they arrange the components above.

| Section | Built from |
|--|--|
| Hero (`.cover`) | logo pill · `.cover__eyebrow` · display title · h2 tagline · light description · phone mockups (exception) · rings (exception) |
| Project Overview (`.metrics` + `.metric`) | 4-cell hairline grid, each cell a `.stat-number` + label + caption |
| Context (`.stat-card` + `.stat`) | bordered card · 3 illustrated stats with teal dividers · 3 `.badge--pill` labels straddling the top edge · justified `.section-lead--justify` |
| Problem (`.problem-grid`) | 2 × `.card card--soft card--pad-lg` (+ `.badge--label`) · `.card card--pad-roomy .research-q` (gradient, centred) with a `.kicker` |
| Solution (`.feature-grid`) | 3 × `.card .feature` (centred, emoji `.feature__icon`) |
| My Role (`.role-tags`, tinted band) | centred `.section-lead` · wrap of identical `.badge--tag` |
| Methodology (`.process` + `.principles`) | `.badge--outline` chip row (aria-hidden) · 3-col principle list |
| Requirements (`.req-grid`) | asymmetric 2 × `.card card--pad-lg`, each `.req__head` with a `.badge--label` (`--solid` / `--strong`) + `.marker-list` |
| Competitive Analysis | `.scroll-x` › `.data-table--comparison` + `.section-note` |
| Target Audience (`.audience`, `align-items: start`) | `.card card--soft card--pad-roomy` + `.marker-list--none` · illustration |
| Empathy Map (tinted band) | `.card card--pad-roomy .empathy` · 2×2 `.empathy__grid` of folded-corner teal `.empathy__note` |
| Personas (`.persona`) | marker dot · `.persona__grid` [avatar `.card .persona__card` + `.quote` · bio `.card` with `.card__title` + `.badge--chip` grid] · full-width `.persona__pnd` (2 × `.card` Goals / Frustrations) · `.card card--notice .method-note` |
| User Journey | `.scroll-x` › `.data-table--journey` |
| Sitemap / Wireframes | `.media--wide` · `.media--center` |
| Visual Identity | `.eyebrow--dot` sub-heads · type specimen · `.type-weights` panel · 5 organic `.swatch__chip` (exception radius) |
| Validation (`.section--deep`, `.vstats`) | white/teal title · `.section-lead` · 3×2 `.card card--dark-inset .vstat` (`.stat-number` + text) · criterion `.section-note` |
| Product Flows (`.flow`, `.flow-index`) | jump index · 10 `.flow` blocks (badge · h2 title · goal · prose · `.marker-list--square --cols` · `.media--framed` strips); deep-dive `.card card--dark` inside flow 5; `.report-cards` in flow 8 |
| Outcomes (`.outcomes`) | 3 × `.card` (kicker year · `.card__title` · `.card__text`) |
| Reflection (`.reflect`) | 2×2 `.card card--pad-lg` |
| Close / Footer (`.section--deep`, `.site-footer`) | lead · h2 · one line · 3-col credits with `.kicker` labels · fine print |

---

## 7. Exceptions (3)

| Exception | Why |
|--|--|
| **Phone mockup** (`.phone*`, `--phone-*`) | Bespoke device geometry — 6px navy frame, `44 / 34px` radii, `-10.5deg` tilt, dedicated shadow. Identity element. |
| **Decorative rings** (`.deco*`, `--deco-*`) | Organic bleed art placed off-band. Sizes / opacity outside the scales by design. |
| **Organic blob swatch** (`.swatch__chip` radius) | `border-radius: 44% 56% 58% 42% / 54% 46% 54% 46%` — the one non-tokenised radius; expresses "formas circulares / linhas curvas". |

---

## 8. Responsive — 3 breakpoints

`max-width` media queries only. **480 · 640 · 900.**
- **900** — the workhorse: multi-column grids → 1 (or → 2 for metrics / vstats /
  principles / modes); cover stacks.
- **640** — final collapse to 1 column (problem, reflect, flow decisions, empathy,
  context stat card, principles, vstats, swatches, footer credits, flow index).
- **480** — cover phone re-position.

Wide tables + sitemap + filmstrips scroll inside `.scroll-x` / `.media__scroll`
rather than shrinking.

---

## 9. Accessibility

- Global `:focus-visible` — 3px `focus/ring`, 2px offset.
- `prefers-reduced-motion` neutralises any future animation / transition.
- Semantic HTML: one `<h1>`, `<h2>` per band, `<h3>` per card / flow; real
  `<table>` / `<th scope>`; `<article>`, `<blockquote>`, `<figure>`.
- Every content `<img>` has `alt`; decorative art is `alt=""` / `aria-hidden`;
  the duplicate process-chip row is `aria-hidden`.
- Colour is not the sole signal (journey barrier column is named; check `--no`
  is a distinct open ring).
- Known gap: `text/muted` (#9B949E) on white ≈ 2.7:1 — below AA for caption
  text; white on `action/primary` (#47B2B0) in `.quote` / `.badge--pill` ≈
  2.3:1. See §11.

---

## 10. Taking it to Figma

| Figma primitive | From |
|--|--|
| `Color / Primitive` variable collection | `color.primitive.*` |
| `Color / Semantic` variable collection (one mode; dark mode later via the `onInverse` / `overlayLight` seed) | `color.semantic.*`, each an alias of a primitive |
| `Spacing`, `Radius`, `Border width` variable collections | `spacing.*`, `radius.*`, `border.width.*` (numbers) |
| **Color styles** | `color.semantic.*` + the 3 `color.gradient.*` |
| **Text styles** (10) | `typography.semantic.*` — carry the **desktop-max** size; the section-title accent word is a Bold + `text/accent` override, not a separate style |
| **Effect styles** (3 + 1) | `shadow.sm / card / raised` + `shadow.phone` |
| **Components** | the 9 above (variant props: Card `surface` + `pad`; Badge `style`; Eyebrow `type` + `dot`; Media `type`; Data-table `variant` + cell `role`; Section-heading `align` + `accent`) |
| **Case-specific components** | Phone mockup (`screen` swap), Decorative ring (`corner` variant), Persona card, Flow step, Empathy note, Swatch |

Not Figma variables — keep in the web layer: `clamp()` fluid type (store min +
max, or the desktop max), the 3 gradients (fill styles), the layered shadows
(effect styles), `radius/round` (large number + `isCircle`), the composed
`border` (width variable + colour variable, applied as a stroke).

---

## 11. Decisions still open for visual review

The reduction is done; a few calls need eyes, not code:

1. **Muted-text contrast.** `text/muted` (#9B949E) fails WCAG AA on white for
   captions. A darker grey (~#6E7690) is the fix — changes the tone of every
   caption / source line.
2. **Text on solid teal.** `.quote`, `.badge--pill`, `.sort-card__head`,
   `.empathy__note` are white on #47B2B0 (~2.3:1). Darkening these text-bearing
   teal surfaces to #32817F would fix contrast but shift the persona quote /
   context pills / card-sort headers a shade darker.
3. **Card elevation unified.** Every card — including the Context stat card and
   the Target panel — carries the same `shadow/card` + hairline. No per-card
   shadow remains.
4. **Card fills.** `.card--soft` is teal-050 everywhere (problem cards, target
   panel). The target-audience panel was teal-100 + borderless before — now
   matches the other soft cards (lighter fill, faint hairline, standard shadow).
5. **Radius snaps.** 9→8, 14→16, 18→16, 30→24, 34/44 kept as phone exceptions.
   Sub-pixel to a few px; confirm no corner looks off.
6. **Mobile cover (< 420px).** The fixed-length tagline / description sit right
   at the viewport edge and can clip a word. Pre-existing (cover CSS is
   unchanged); worth a dedicated mobile pass — shrink the deco, or set an
   explicit mobile type size.
7. **Page length.** ~34k CSS px after the rhythm fix. Capping the sitemap /
   wireframes / filmstrip image heights is still a separate pass.
