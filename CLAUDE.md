# Stellar Lab — Project Guide & Build Playbook

This file is the single source of truth for the **Stellar Lab** learning hub. Read it first in any new session. If the user says *"let's build the next mission"*, follow the **Build Playbook** below.

> Open **this folder** (`stellar-lab`) — it is the Git repo *and* the project home. The website files sit at the repo root, the curriculum docs are in `References/` (git-ignored), and this `CLAUDE.md` travels with the repo. Edits made here show up directly in GitHub Desktop to commit + push.

---

## 1. What this is
An interactive, sci-fi-themed web learning hub built for **Lyra**, at **Sir William Robertson Academy**. She has moved into her **exam years (Year 10, GCSE)** — the hub's active content now targets Year 10/11, with her completed Year 9 Science missions kept as an archive rather than deleted. Each "mission" is one self-contained HTML lesson on a curriculum topic. The goal is engagement: visuals and animations first, minimal text, with a self-check quiz.

**Audience & level:** pitch at **full GCSE depth** for Year 10/11 content — the "Decrypt" panel now holds higher-tier/exam-stretch material rather than an optional reach beyond KS3. Older Year 9 missions in the archive stay at the KS3 + GCSE-bridge level they were written for. Keep language warm and age-appropriate throughout.

## 2. Where things live
```
stellar-lab/              ← THE WEBSITE = the Git repo root (this folder)
├─ index.html               (Station Hub — subject picker)
├─ science.html             (Science Deck — Year 10 strands + Year 9 archive + Reference Library)
├─ computing.html           (Computing Deck — Systems / Programming strands + Reference Library)
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
> The old `D:\My_Dev_Repo\stellar-lab` clone has been deleted (Oct 2026) — this OneDrive folder is the **only** local clone. Still run `git fetch && git status` at the start of a session in case changes were pushed from elsewhere.

## 3. Hosting / deploy
- Hosted on **GitHub Pages**. Repo: `stellar-lab` (public) under GitHub user `8r4ds998tt-prog`.
- Live site: **https://8r4ds998tt-prog.github.io/stellar-lab/**
- Repo root = this folder (so `index.html` sits at repo root).
- **Deploy:** this folder is the live clone. After changes, open **GitHub Desktop**, review the diff, **Commit to main**, then **Push origin** — Pages rebuilds in ~1 min. (Or `git commit`/`git push` from the terminal.)
- The Reference Library links to the school's **live PDF URLs**, so nothing extra to host.

## 4. Current state
**Architecture:** `index.html` (Station Hub) → subject **deck** pages → `lessons/` missions. Subjects: Science (live), Computing (live), Maths (live, in progress); English, DT, History (locked, decks not built yet — tiles on `index.html` show "Coming soon").

**Single clone:** `c:\Users\andre\OneDrive\Documents\GitHub\stellar-lab` (this file's folder) is the one and only local clone, and GitHub Desktop points here. The old `D:\My_Dev_Repo` clone (where the Maths deck was first built) was merged in and then deleted in Oct 2026.

`science.html` is split into two layers: **Year 10 (active)** strand sections at the top, matching the strand cards' slicer, and a collapsed **Year 9 Archive** panel (`toggleArchive()`) below holding all the completed Year 9 work. New Science missions go in the active Year 10 sections; don't delete the archive.

`computing.html` follows the same strand-card + mission-grid pattern as `science.html` (no archive yet — it's a brand new deck). Two strands: **Systems** (architecture, memory, networks, security, system software, ethics — AQA Paper 1 territory) and **Programming** (algorithms, data structures, Python — AQA Paper 2 territory; currently a "coming soon" placeholder card).

`maths.html` uses strands Number/Algebra/Geometry/Data, accents Number=green `--num`, Algebra=blue `--alg`, Geometry=teal `--geo`, Data=lilac `--data`. It currently has 11 missions live across those strands (see `lessons/` — algebraic-manipulation, area-volume, equations-inequalities, non-linear-graphs, percentages, probability, pythagoras, ratio-proportion, standard-form, straight-line-graphs, transformations). It's still Year 9-level content — hasn't been migrated to Year 10/11 yet like Science has.

All pages carry a "Last updated" timestamp in the footer (plain static text next to the existing footer line) — update it when you touch a page.

**Year 10 GCSE Science missions built (active):**
- Chemistry: `structure-and-bonding.html` (Module 12)
- Biology: `organisation-digestive-system.html` (Module 13)
- Physics: `electricity-in-the-home.html` (Module 14), `molecules-and-matter.html` (Module 16)

**Year 9 Science missions (archived, still on the site under "Year 9 Archive"):**
- Chemistry: `endothermic-exothermic.html`, `atomic-structure.html`, `balancing-equations.html`, `periodic-table.html`
- Biology: `cells.html`, `ecology.html`, `variation.html`, `evolution-inheritance.html`
- Physics: `waves.html`, `energy-stores.html`, `electric-circuits.html`
- Tests: `eoy-test-2026.html` (the Year 9 end-of-year test, now past — kept for reference only)

**Year 10 GCSE Computing missions built (active):**
- Systems: `systems-architecture.html` (Module 15) — CPU/Von Neumann architecture, fetch-decode-execute cycle, performance factors.

**Backlog (build in this order unless the user picks):**
1. Continue the **Year 10 Science** strands from the curriculum plan (more Chemistry/Biology/Physics topics as the school year progresses).
2. Continue the **Computing** Systems strand and start the **Programming** strand (searching/sorting algorithms, hands-on Python) — Computing was requested next, before DT or History.
3. Decide whether to migrate **Maths** to Year 10/11 (like Science) or keep building out its Year 9 Number/Data strands — ask the user, since it wasn't planned as part of the Year 10 push.
4. Build the **DT** deck (curriculum Plan/Map not yet fetched from the school site — ask to add it when it's time).
5. Build the **History** deck (curriculum Plan/Map not yet fetched — ask to add it when it's time).
6. Build the **English** deck, then Year 10/11 English missions.

Curriculum source of truth: `References/` and https://www.swracademy.org/page/?title=Subject+Curriculum&pid=29 (Science is AQA-aligned; Maths uses White Rose/Edexcel). Computing's Plan and Map are already extracted to `Computing-Curriculum-Plan.md` / `Computing-Curriculum-Map.md`. DT and History have no curriculum docs in `References/` yet — fetch and extract them (same pattern as `_Curriculum-Index.md`) before planning those decks.

## 5. Design system ("Stellar Lab")
Sci-fi starship console blending **Star Trek LCARS** (amber/lilac angled panels, blinking status dots), **Stranger Things** (dark starfield, red neon flicker title, drifting "spore" particles), and **Taylor Swift / Midnights** (lavender glow). Lyra likes all three.

- **Fonts (Google CDN):** Orbitron (display/headings), Rajdhani (UI/labels), Exo 2 (body).
- **Palette (CSS vars):** `--bg:#04060f`, `--ink:#eaf2ff`, `--muted:#8fa0c8`, `--amber:#ffb13b`, `--lilac:#cc88ff`, `--lav:#c8a2ff`, `--st:#ff1f3d` (title glow), plus accents `--exo:#ff3b5c`, `--endo:#2de2ff`, `--green:#46e6a0`, `--blue:#5aa6ff`, `--teal:#39d6c8`.
- **Subject accent:** Science — Chemistry = orange/lilac, Biology = green (`--green`), Physics = cyan (`--endo`). Computing — Systems = blue (`--blue` / `#5aa6ff`), Programming = teal (`--teal` / `#39d6c8`). Use the accent for the lesson section left-border, the hero kicker, and the deck mission card. Give each new subject its own two-ish accent colours, distinct from existing subjects.
- **Accessibility:** always include the `@media (prefers-reduced-motion: reduce)` block that disables animations and the custom cursor.
- Each page is **one self-contained .html** (inline CSS + JS). No build step, no external JS libs. This keeps it portable.

## 6. Anatomy of a mission (copy an existing lesson as scaffold)
Best scaffold: copy `lessons/cells.html` (Biology), `lessons/electric-circuits.html` (Physics — good for slider-driven labs), or `lessons/systems-architecture.html` (Computing) and swap the middle.

Shared, reused on every mission (keep identical):
1. `<head>` with the three Google Fonts.
2. `:root` palette + shared CSS (starfield canvas, glow cursor, topbar, hero, `section` LCARS frame, `.seclabel`, `h2`, `.decrypt`, quiz styles, footer, reduced-motion).
3. Shared JS: starfield+spores canvas, cursor follower, `IntersectionObserver` scroll-reveal, `toggleDecrypt()`, and the **quiz engine**.
4. **Topbar:** back-link to the subject's deck page (e.g. `◄ Science Deck` → `../science.html`, or `◄ Computing Deck` → `../computing.html`); right label e.g. `Bio-02 // Ecology` or `Sys-01 // Systems Architecture`.
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
2. **Get the curriculum detail:** read the relevant file in `References/` (and the topic's place in Year 10/11). Pitch at full GCSE depth for new Science missions. Ask the user ONLY if the GCSE depth is genuinely ambiguous.
3. **Plan the mission:** decide the core concept, the **interactive centerpiece**, any examples, the GCSE-stretch (decrypt) content, and 15 quiz questions.
4. **Build the file:** copy an existing lesson as scaffold → `lessons/<kebab-topic>.html`. Keep all shared CSS/JS; replace hero text, sections, the interactive, the decrypt content, and the `questionBank`. Set subject accent colour and topbar/module labels.
5. **Validate the JavaScript before finishing:** extract the `<script>` and run `node --check`. Sanity-check any computed logic (e.g. quiz answer indices in range, interactive maths) — ideally in Node. Also check quiz `correct:` indices aren't all the same value (vary option order so the answer position isn't a giveaway pattern). If `node` isn't on PATH in the sandbox, fall back to a careful manual read: balanced braces/parens, and grep for stray unescaped apostrophes inside single-quoted JS strings (a common source of silent breakage).
6. **Add it to the deck:** in the subject's deck page (`science.html`, `computing.html`, etc.), add a mission card to the active strand section, with the right chip colour and a `chip gcse` badge, and update that strand's "N missions ready" count. Leave any archive panel alone unless specifically asked to change archived content.
7. **Verify navigation:** the new lesson back-links to the correct deck page; the deck links to `lessons/<file>.html`; quiz and interactive work.
8. **Deploy:** in GitHub Desktop, review the diff, **Commit to main**, then **Push origin** (Pages updates the live site in ~1 min).

## 9. Conventions & gotchas
- File names: `lessons/<kebab-case-topic>.html`. Module numbers increment in the footer (`Module 0X`).
- Verify science accuracy to AQA GCSE (Year 10/11) level for new missions, and AQA Year 9 / early GCSE level for the archived Year 9 missions; keep the simplified models the spec expects (e.g. 2,8,8 electron shells).
- Don't pull in external JS frameworks or a build step — keep each page standalone.
- **OneDrive + sandbox gotcha:** this repo is cloud-synced, so the Cowork bash shell **cannot overwrite or delete existing files** here ("operation not permitted on unlink") and `git restore`/`git checkout` of tracked files will fail in the sandbox. Use the host **Write/Edit** tools to change tracked files; bash can still *create new* files and run read-only `git` commands. Line endings are pinned to LF by `.gitattributes`, which keeps diffs clean — don't remove it. Do git commits/pushes from **GitHub Desktop**, not the sandbox.
- **Combined vs Triple Science:** as of Oct 2026 the school hasn't decided whether Lyra takes Combined (Trilogy) or Triple (separate) Science, so include Triple-only content but mark it. Check each topic against the AQA spec: content that's in the separate Biology/Chemistry/Physics spec but **not** in Combined Trilogy gets a pink `<span class="tri">Triple only</span>` badge (CSS in `lessons/molecules-and-matter.html`), plus a one-line legend in the decrypt panel. Prefix quiz questions with `[Triple only]`. Mark Higher-tier-only content too (e.g. `Triple only · Higher tier`). Once the school decides, update this note.
- Apply the warm, age-appropriate tone from §1 consistently, even in higher-tier GCSE stretch content.