# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page static landing page for Jun Chen's (@realjunchen) 21-day body
transformation program ("21D 體態管理計畫"), which doubles as a funnel page for
the WeDo Elite Circle community and a Herbalife-based social media business.
The entire site is one self-contained file: `index.html`.

There is no build system, package manager, test suite, linter, or framework.
All CSS lives in a `<style>` block and all JavaScript in a `<script>` block
inside `index.html`. To preview changes, open `index.html` in a browser (or
`python3 -m http.server` and visit localhost).

The file must remain named `index.html` at the repo root — the git history
shows repeated renames to `index.html`, which is required for static hosting
(GitHub Pages-style serving).

## Content and language conventions

- All user-facing copy is Traditional Chinese (`lang="zh-TW"`), written in a
  personal, first-person voice (Jun speaking to the reader). Match this tone
  and language when editing or adding copy.
- Typography: `Noto Serif TC` for headings/quotes (`.serif`), `Noto Sans TC`
  for body text, loaded from Google Fonts.
- The color system is defined as CSS custom properties on `:root` (dark
  background `--bg`, gold accent palette `--gold`/`--gold-light`/`--gold-dim`,
  `--red` for negative points). Use these variables rather than hardcoding new
  colors.

## Page structure

Sections appear in a deliberate narrative order (a marketing funnel): hero →
story (who Jun is) → two paths (`#paths`) → reality check (`#reality`) → how
the system works (`#how`) → independent individual disclaimer
(`#independent`) → origin/disclosure (`#origin`) → why Herbalife → selection
criteria (`#why`) → Herbalife Gold Standard guarantees (`#guarantee`) → FAQ
(`#faq`) → no-pitch promise (`#promise`) → CTA (`#cta`, links to the Skool
community) → footer. Preserve this order unless asked to restructure.

Alternating sections use `var(--bg2)` backgrounds for rhythm, separated by
`.divider` elements. Earlier sections use CSS classes; later-added sections
lean on inline styles — follow the local style of whichever section you edit.

## Scroll animations

Two animation mechanisms coexist:
- Hero uses `fade-up` + `.delay-N` classes (pure CSS, plays on load).
- Everything else uses `.reveal`, toggled to `.visible` by the
  `IntersectionObserver` in the bottom `<script>`. New content sections should
  get the `reveal` class so they animate in on scroll.

## Accuracy constraints

The page makes specific factual/legal claims: Herbalife company facts (founded
1980, 95 countries, NYSE-listed), Taiwan Herbalife Gold Standard guarantees
(30-day customer refund, 90-day distributor refund, 12-month buyback, no
inventory requirements), the @fitcouple upline relationship, and the explicit
"no pitching / no DMs / no recruiting" promises in `#promise` and `#origin`.
Do not alter, exaggerate, or remove these claims without explicit instruction —
they are compliance-sensitive for a direct-selling business.
