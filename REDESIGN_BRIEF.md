# Site redesign brief

## Goal
Replace the current Martin Saveski–style template with a custom design
inspired by sdi.ng and mariya.fyi, with a Neo-Japanese Minimalism
sensibility (Kenya Hara/Kohei Sugiura — restraint, hairline rules,
generous whitespace, editorial grid). No actual Japanese characters or
ornament; the aesthetic should come from structure and typography
alone.

## Visual system

### Colors
- Background: #F5F1E8 (warm bone)
- Primary text: #14213D (near-black with blue undertone)
- Accent / Dodger Blue: #1E40FF
- Accent deep (hover, photo gradient): #1531C8
- Rule (hairlines): rgba(30, 64, 255, 0.18)
- Muted text: rgba(20, 30, 70, 0.55)

Dark mode: skip for v1. Single light theme is fine.

### Typography
- Display + body serif: Fraunces (variable, weights 300/400/500),
  loaded from Google Fonts. Use font-variation-settings: "SOFT" 50,
  "opsz" 96 for the display variant. Letter-spacing -0.02em on display.
- Mono: JetBrains Mono (300/400/500), Google Fonts.
- Sans fallback: system-ui.
- Sentence case everywhere. No ALL CAPS except in monospace metadata
  labels with letter-spacing 0.08em–0.2em.
- No bolding mid-sentence.

### Grid
- Max content width: 880px, centered.
- Section structure: numbered (001, 002, 003...) with two-column
  layout — 80px left rail for section number + tag, content fills
  the rest.
- 0.5px hairline rules between sections (border-top/bottom).
- Generous vertical padding (2rem between sections).

## Pages to build

### 1. `/` (index)
- Masthead: issue number left, wordmark center (with blue dot),
  nav right (Index / Papers / Notes / CV)
- Location/time/weather strip: 4 columns reading from
  `_data/location.json` — city, local time (live, JS), weather
  (fetched client-side from Open-Meteo using lat/lon — no API key
  needed), and a "since X — context" cell
- Hero: 1.5fr/1fr grid. Left = section tag, big serif name with
  italic surname and dodger-blue period, monospace credentials line,
  italic serif tagline (max 38ch), inline link cluster (scholar,
  github, arxiv, cv.pdf, email)
- Right of hero = "Plate I" portrait, aspect-ratio 4/5, with a
  thin metadata strip across the bottom of the image
- §002 Bio (one large serif sentence + smaller muted paragraph)
- §003 Reading (2 books with mini cover treatments, "all reading ↗"
  link to /reading)
- §004 Selected work (4–5 papers, "all 13 papers ↗" link to /papers)
- §005 Notes (3 most recent, with category pills, "archive ↗" link)
- Colophon: contact / wordmark / "Set in Fraunces, JetBrains Mono"

### 2. `/papers/` (full publications)
- Same masthead/nav.
- Year-grouped list of all 13 publications.
- Filter pills at top: All / AI Safety / Conformal / RL / Causal /
  Other. Filtering is JS-only, no page reload.
- Each paper row: date stamp left (monospace, 80px), title + authors
  + venue middle, paper/arxiv/code/guide links right.
- Hover: title goes italic + dodger blue.

### 3. `/notes/` (blog index)
- Masthead/nav.
- Year-grouped list of posts.
- Category filter pills: All / Research / Book review / Essay /
  Technical
- Each row: date / title / category pill / read link.

### 4. `/notes/[slug]/` (post template)
- Masthead/nav.
- Breadcrumb: ← Notes
- Tag (e.g. "Book review · 2026.04"), then big serif title, italic
  subtitle.
- Body in serif Fraunces, 18px, line-height 1.5, max 65ch.
- Code blocks in JetBrains Mono on a #EDE8DA background block.
- Pull quotes: dodger-blue left border, serif italic.
- Footer: prev/next post navigation.

### 5. `/papers/[slug]/` (field guide template — optional, only for
selected papers)
- Masthead/nav.
- Breadcrumb: ← Index.
- Title block (matches index style).
- "Result, in one sentence" — large serif, with one italic phrase
  in dodger blue.
- Hero figure (SVG or img).
- Proposition block: muted background, dodger-blue left border,
  serif italic with KaTeX-rendered math.
- Optional interactive (slider + readouts) where the paper has one
  natural knob.
- BibTeX block in mono on muted background.
- Prev/next paper.

### 6. `/reading/` (optional)
- Masthead/nav.
- Currently reading (top, larger covers).
- Recently finished (year-grouped, smaller).
- Each book: cover, title in serif, author in italic, status pill
  (reading / finished / abandoned), one-line note in muted serif.

## Data files

Create `_data/`:
- `location.json` — { city, tz, lat, lon, since, context, home_base }
- `publications.yml` — list with { title, authors, venue, year, month,
  paper_url, arxiv_url, code_url, guide_slug, tags, selected }
- `reading.yml` — list with { title, author, status, started, note,
  cover_color, cover_text }
- `nav.yml` — top-level navigation items

Posts under `_posts/` follow Jekyll convention. Add a `category`
front-matter field for filtering.

## Implementation notes
- Build as Jekyll. Keep GitHub Pages deployment.
- Use SCSS partials: `_typography.scss`, `_layout.scss`, `_components.scss`,
  `_colors.scss`. Single entry: `assets/css/main.scss`.
- No JS frameworks. Vanilla JS for: live clock, weather fetch,
  paper/notes filtering. Total JS budget: <5 KB.
- Fonts via Google Fonts with `&display=swap`. Preconnect.
- Photo: `/assets/portrait.jpg`, lazy loaded. I'll provide it.
- Open-Meteo endpoint: https://api.open-meteo.com/v1/forecast?
  latitude={lat}&longitude={lon}&current_weather=true&temperature_unit=fahrenheit
- All hover/transitions: 0.15s ease.
- Accessibility: every link has visible focus state (2px dodger-blue
  outline). Color contrast checked on the bone background.

## Phasing
1. Tear down current templates, set up new layout + index page.
2. Port all existing publications data to `_data/publications.yml`.
3. Build /papers archive page with filtering.
4. Build /notes index + first post template.
5. Build one field guide page (Oversight Game) as a template.
6. Polish: weather API, location override flow, dark mode (later).

Ship phase 1–3 first. Phases 4–6 can be incremental.