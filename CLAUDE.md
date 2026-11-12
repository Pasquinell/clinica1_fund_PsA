# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

The parent folder's `../CLAUDE.md` covers what the three sibling sites share: architecture, content rules, verification and publishing. This file records only what is specific to this repo. **Read `doc/README.md` before editing.** It holds the block list (`b1`…`b23`), content corrections, temporality decisions, design tokens and known gaps. Update it when you change something it describes.

## What this repo is

Freud read in the order of the Clínica I syllabus (Facultad de Psicología, Udelar, 2026). Everything lives in `index.html` (~370 KB, HTML + CSS + JS inline, no build). It is published on GitHub Pages from `main` / root: https://pasquinell.github.io/clinica1_fund_PsA/

Terminology follows Amorrortu/Etcheverry (pulsión, investidura, sepultamiento…).

## Commands (run from the repo root)

```bash
python3 -I doc/tools/figs_preview.py     # all 32 diagrams in final state -> doc/tools/out/figs_N.html (6 per page; no dark-mode arg here)
google-chrome --headless=new --no-sandbox --hide-scrollbars --window-size=1360,1560 \
  --virtual-time-budget=3000 --screenshot=doc/tools/out/figs_0.png "file://$PWD/doc/tools/out/figs_0.html"
node doc/tools/cdp.mjs "file://$PWD/index.html" doc/tools/out/shot 1400 900 "b10:4200" "b13:2600"   # desktop
node doc/tools/cdp.mjs "file://$PWD/index.html" doc/tools/out/mob 390 844 "b10:16500"               # mobile, no horizontal overflow allowed
```

`python3 -I doc/tools/check.py` checks tag balance, `data-s` vs step count, duplicate ids, broken `#links` and missing images (copied from `../tcc_terapia`).

## Differences from the sibling sites

- **Step activation uses `IntersectionObserver` rootMargin bands**, not the "last card above 58 %" computation that the parent CLAUDE.md describes. Desktop band is `-42% 0px -42% 0px`, mobile (≤ 900 px) is `-66% 0px -22% 0px`. Section tracking for the top bar uses `-38% 0px -58% 0px`. See the script near the end of `index.html` (around line 2715).
- Only `data-s` exists. There is no `data-off`/`.fade` and no `data-show`.
- Grouping attributes are `data-parcial` (`0` general, `1`, `2`, `3` = fuera de parciales: b17–b23) + `data-tema`. Sections also carry `data-year`. The top bar is a 1890–1935 ruler that shows "↩ retrocede N años" / "→ avanza N años" when the syllabus jumps in time.
- SVG vocabulary: boxes `.box .boxs .bt .bo .bc .bp .bb`, lines `.ln .lnd .lo .lt .lc .lp .lb`, text `.ti .sm .xs .ser`, markers `#ar #aro #art #arc #arp #arb`. Callout classes: `.call ant` (Anticipación), `.call rec` (Recontextualización), `.call caso`, `.call nota`, `.call warn` (Trampa).
- `b10` (Conferencias 17, 18, 19, 23) has four sub-scrollies and is the reference for diagram quality.

## Repo hygiene

- `.gitignore` excludes only the course input files (`Guía General*.md`, `Preguntas de Preparación*.md`). It does **not** exclude `doc/tools/out/`. Write previews and screenshots there or in a scratch dir, and do not commit them with `git add .`.
- `doc/` is tracked and public.
- Images: `img/freud.jpg` (Halberstadt c. 1921, public domain, Wikimedia Commons) and `img/freud_queer.jpg` (cover portrait). Freud's photo appears only on the cover.
