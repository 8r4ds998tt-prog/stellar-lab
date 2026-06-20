# Stellar Lab — Project Guide & Build Playbook

This file is the single source of truth for the **Stellar Lab** learning hub. Read it first in any new session. If the user says *"let's build the next mission"*, follow the **Build Playbook** below.

> Open **this folder** (`stellar-lab`) — it is the Git repo *and* the project home. The website files sit at the repo root, the curriculum docs are in `References/` (git-ignored), and this `CLAUDE.md` travels with the repo. Edits made here show up directly in GitHub Desktop to commit + push.

---

## 1. What this is
An interactive, sci-fi-themed web learning hub built for **Lyra** — a 14-year-old in **Year 9 (UK)** at **Sir William Robertson Academy**. Each "mission" is one self-contained HTML lesson on a curriculum topic. The goal is engagement: visuals and animations first, minimal text, with a self-check quiz.

**Audience & level:** pitch at the **KS3 + GCSE bridge** — solid Year 9 fundamentals with a gentle, optional reach into GCSE depth (kept behind the "Decrypt" panel). Keep language warm and age-appropriate.

## 2. Where things live
```
stellar-lab/              ← THE WEBSITE = the Git repo root (this folder)
├─ index.html               (Station Hub — subject picker)
├─ science.html             (Science Deck — strands + mission cards + Reference Library)
├─ lessons/                 (one .html per mission)
├─ CLAUDE.md                ← this file (committed with the repo)
├─ .gitattributes           (forces LF line endings — keeps diffs clean on OneDrive/Windows)
├─ .gitignore               (ignores References/ so the PDFs aren't published)
└─ References/              ← curriculum docs, GIT-IGNORED (not on the live site)
    ├─ _Curriculum-Index.md     (links to live school PDFs)
    └─ <Subject>-Curriculum-Plan.md / -Map.md  (extracted text)
```
> The site is served from the repo root, so `index.html` must stay at the top level.
> An older mirror may still exist at `…\Claude Work\Projects\School Tutor\Learning Hub\` — that copy is retired; **work here in the repo**.

## 3. Hosting / deploy
- Hosted on **GitHub Pages**. Repo: `stellar-lab` (public) under GitHub user `8r4ds998tt-prog`.
- Live site: **https://8r4ds998tt-prog.github.io/stellar-lab/**
- Repo root = this folder (so `index.html` sits at repo root).
- **Deploy:** this folder is the live clone. After changes, open **GitHub Desktop**, review the diff, **Commit to main**, then **Push origin** — Pages rebuilds in ~1 min. (Or `git commit`/`git push` from the terminal.)
- The Reference Library links to the school's **live PDF URLs**, so nothing extra to host.

## 4. Current state
**Architecture:** `index.html` (Station Hub) → subject **deck** pages → `lessons/` missions. Subjects: Science (live, complete); Maths (live, in progress); English (locked, deck not built yet).

**Missions built (Year 9 Science) — all 3 strands complete:**
- Chemistry: `endothermic-exothermic.html`, `atomic-structure.html`, `balancing-equations.html`, `periodic-table.html`
- Biology: `cells.html`, `ecology.html`, `variation.html`, `evolution-inheritance.html`
- Physics: `waves.html`, `energy-stores.html`, `electric-circuits.html`

**Maths (`maths.html` deck live; strands Number/Algebra/Geometry/Data):**
- Algebra: `straight-line-graphs.html` (y=mx+c grapher)
- Geometry: `pythagoras.html` (squares-on-sides explorer)
- Number & Data strands show "coming soon" placeholders on the deck.
- Maths strand accents: Number=green `--num`, Algebra=blue `--alg`, Geometry=teal `--geo`, Data=lilac `--data`.

**Backlog (build in this order unless the user picks):**
1. More **Maths** missions — Number (percentages, fractions, ratio, standard form), Geometry (transformations, area & volume), Data & Probability. Update the strand "N missions ready" count + activate Number/Data sections when their first mission lands.
2. Build the **English** deck (new `english.html` deck page + unlock card on `index.html`), then Year 9 English missions (DNA, Media, Non-fiction, Creative Writing, THUG).

Curriculum source of truth: `References/` and https://www.swracademy.org/page/?title=Subject+Curriculum&pid=29 (Science is AQA-aligned; Maths uses White Rose/Edexcel).

## 5. Design system ("Stellar Lab")
Sci-fi starship console blending **Star Trek LCARS** (amber/lilac angled panels, blinking status dots), **Stranger Things** (dark starfield, red neon flicker title, drifting "spore" particles), and **Taylor Swift / Midnights** (lavender glow). Lyra likes all three.

- **Fonts (Google CDN):** Orbitron (display/headings), Rajdhani (UI/labels), Exo 2 (body).
- **Palette (CSS vars):** `--bg:#04060f`, `--ink:#eaf2ff`, `--muted:#8fa0c8`, `--amber:#ffb13b`, `--lilac:#cc88ff`, `--lav:#c8a2ff`, `--st:#ff1f3d` (title glow), plus accents `--exo:#ff3b5c`, `--endo:#2de2ff`, `--green:#46e6a0`, `--blue:#5aa6ff`, `--teal:#39d6c8`.
- **Subject accent:** Chemistry = orange/lilac, Biology = green (`--green`), Physics = cyan (`--endo`). Use it for the lesson section left-border, the hero kicker, and the deck mission card.
- **Accessibility:** always include the `@media (prefers-reduced-motion: reduce)` block that disables animations and the custom cursor.
- Each page is **one self-contained .html** (inline CSS + JS). No build step, no external JS libs. This keeps it portable.

## 6. Anatomy of a mission (copy an existing lesson as scaffold)
Best scaffold: copy `lessons/cells.html` (Biology) or `lessons/balancing-equations.html` (Chemistry) and swap the middle.

Shared, reused on every mission (keep identical):
1. `<head>` with the three Google Fonts.
2. `:root` palette + shared CSS (starfield canvas, glow cursor, topbar, hero, `section` LCARS frame, `.seclabel`, `h2`, `.decrypt`, quiz styles, footer, reduced-motion).
3. Shared JS: starfield+spores canvas, cursor follower, `IntersectionObserver` scroll-reveal, `toggleDecrypt()`, and the **quiz engine**.
4. **Topbar:** back-link `◄ Science Deck` → `../science.html`; right label e.g. `Bio-02 // Ecology`.
5. **Hero:** kicker, neon `<h1>` (two lines, second in `.lav`), one-line intro, scroll cue.
6. **Footer:** `Stellar Lab · Module 0X · For Lyra`.

Section order (numbered `Section 0X //`):
1. **Core Concept** — the idea in 1–2 short paragraphs + a couple of cards.
2. **The interactive centerpiece** — the "wow". Make it genuinely manipulable (build/toggle/explore), animated, with live readouts. This is the most important part.
3. (Optional) real-world examples / specialised cases as small cards.
4. **Encrypted: GCSE Stretch** — the `.decrypt` collapsible panel hiding the harder/optional GCSE content.
5. **Diagnostic** — the quiz.

Keep text minimal throughout; prefer icons, chips, and visuals.

## 7. Quiz standard (every mission)
- A `questionBank` of **15** multiple-choice questions; show **5 at a time**.
- `nextSet()` serves the next non-repeating set (cycles all 15, then reshuffles); "↻ New questions" button calls `resetQuiz()`.
- Each question: `{q, opts:[...], correct:<index>, why:"..."}` with instant feedback (green correct / red wrong + explanation). Completion line: `SET n · SCORE x/5`.
- Reuse the exact quiz engine from an existing lesson; only change `questionBank`.

## 8. BUILD PLAYBOOK — "let's build the next mission"
1. **Pick the topic:** next in the §4 backlog unless the user names one. Confirm the topic in one line.
2. **Get the curriculum detail:** read the relevant file in `References/` (and the topic's place in Year 9). Pitch at KS3 + GCSE bridge. Ask the user ONLY if the GCSE depth is genuinely ambiguous.
3. **Plan the mission:** decide the core concept, the **interactive centerpiece**, any examples, the GCSE-stretch (decrypt) content, and 15 quiz questions.
4. **Build the file:** copy an existing lesson as scaffold → `lessons/<kebab-topic>.html`. Keep all shared CSS/JS; replace hero text, sections, the interactive, the decrypt content, and the `questionBank`. Set subject accent colour and topbar/module labels.
5. **Validate the JavaScript before finishing:** extract the `<script>` and run `node --check`. Sanity-check any computed logic (e.g. quiz answer indices in range, interactive maths) — ideally in Node.
6. **Add it to the deck:** in `science.html`, add a mission card in the correct strand section (Chemistry/Biology/Physics), with the right chip colour, and update that strand's "N missions ready" count. If it's the first mission of a new strand, add a new `... · Missions` section and activate the strand.
7. **Verify navigation:** the new lesson back-links to `../science.html`; the deck links to `lessons/<file>.html`; quiz and interactive work.
8. **Deploy:** in GitHub Desktop, review the diff, **Commit to main**, then **Push origin** (Pages updates the live site in ~1 min).

## 9. Conventions & gotchas
- File names: `lessons/<kebab-case-topic>.html`. Module numbers increment in the footer (`Module 0X`).
- Verify science accuracy to AQA Year 9 / early GCSE level; keep the simplified models the spec expects (e.g. 2,8,8 electron shells).
- Don't pull in external JS frameworks or a build step — keep each page standalone.
- **OneDrive + sandbox gotcha:** this repo is cloud-synced, so the Cowork bash shell **cannot overwrite or delete existing files** here ("operation not permitted on unlink") and `git restore`/`git checkout` of tracked files will fail in the sandbox. Use the host **Write/Edit** tools to change tracked files; bash can still *create new* files and run read-only `git` commands. Line endings are pinned to LF by `.gitattributes`, which keeps diffs clean — don't remove it. Do git commits/pushes from **GitHub Desktop**, not the sandbox.
- Apply the warm, age