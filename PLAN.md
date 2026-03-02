---
planStatus:
  planId: plan-prototype-styleguide
  title: Prototype Wireframe Style Guide
  status: active
  planType: system-design
  priority: high
  owner: lars
  stakeholders: []
  tags:
    - styleguide
    - prototype
    - wireframe
    - balsamiq
    - tailwind
  created: "2026-02-21"
  updated: "2026-03-02T00:00:00.000Z"
  progress: 85
---
# Prototype Wireframe Style Guide

A Balsamiq-inspired greyscale style guide for rapid prototyping, adapted from the HexaPawn style guide. Greyscale UI with very sparse colour accents for primary actions, negative states, and warnings.

---

## Design Principles

- **Greyscale first** — all screen elements use Tailwind grey shades
- **Sparse colour** — only 3 accent colours, used sparingly for meaning:
  - Emerald-700: primary actions, positive status
  - Rose-800: negative/error actions, negative status
  - Orange-500: warning status lights only
- **Wireframe aesthetic** — Balsamiq Sans font, sketchy/lo-fi feel
- **Token discipline** — all mockups reference style guide tokens; style changes go through `style-guide.md` only (single source of truth)

---

## Completed Phases (Summary)

### Phase 1: Foundation — v1.0 (2026-02-21)

Created `style-guide.md` with all design tokens: greyscale palette (gray-50 to gray-900), 3 accent colours, Balsamiq Sans typography, buttons (primary/secondary/danger/ghost/disabled), status lights, Remix Icons, cards, form elements, and CDN boilerplate. Created `CLAUDE.md` for AI session context.

### Phase 2: Visual Validation — v1.0 (2026-02-22)

Built `showcase.html` — a single-page visual reference rendering all style guide tokens. Sections: Landing Page (navbar, hero, cards, status lights, footer), Form Entry (all input types, validation states, buttons), Confirmation/Error Modals, Procedural & Decision Modals. Added Verbose Decision Modal pattern during review.

### Phase 3: Review & Lock — v1.0 (2026-02-23)

Finalised style guide as v1.0. All tokens verified against showcase — no hardcoded values. Initialised git repo and pushed to GitHub: https://github.com/LarsGustavsson-au/prototype-styleguide

### Phase 4: Data Display & Layout — v1.1 (2026-02-25)

Added small tables (`.table-simple`), large report tables (`.table-report` with zebra striping, sticky headers, sort indicators), Chart.js integration (pie, bar, line charts in greyscale), content sections (`.content-section` with header/body/footer), and field rows (`.field-row` for inline grouping). Showcase sections renumbered: modals moved to Sections 5-6, tables/charts became Section 3, content sections became Section 4.

---

## Phase 5: Navigation, App Shell & Semantic Refactor — v1.2 (2026-02-27)

> Goal: Add collapsible left sidebar navigation, a right-side slide-out configuration panel, a full "app shell" showcase section, and refactor all tokens to use fully semantic names so a prototype can be re-branded by changing values in one place.

### 5A — Style Guide: Sidebar & Panel Tokens

- [x] **5A.1** Add **Left Sidebar** tokens — `.sidebar`, `.sidebar-collapsed`, `.sidebar-item`, `.sidebar-item-active`, `.sidebar-section-label`
  - Collapsible: expanded (icons + labels) / collapsed (icons only)
  - Responsive: collapses to overlay on tablet and below
- [x] **5A.2** Add **Right Panel (Slide-Out)** tokens — `.panel-right`, `.panel-right-header`, `.panel-right-body`, `.panel-right-footer`
  - Overlays content (doesn't push it), can be persistent or dismissable
- [x] **5A.3** Add **App Shell** layout tokens — `.app-shell`, `.app-shell-sidebar`, `.app-shell-content`, `.app-shell-panel`

### 5B — Showcase: App Shell Section

- [x] **5B.1** Build **Showcase Section 7 — App Shell** inside a contained browser-window frame
  - Left sidebar (6 nav items, collapsible), main dashboard content, right panel with filter controls
- [x] **5B.2** Existing sections 1-6 remain unchanged

### 5C — Review

- [x] **5C.1** All sidebar, panel, and app shell tokens verified consistent between style guide and showcase
- [x] **5C.2** User visual review confirmed after 5D refactor

### 5D — Semantic Token Refactor (Re-brand Ready)

> Goal: Make it possible to re-brand a prototype by changing only the `:root` CSS variables block.

> **Technical note:** Tailwind CDN can't resolve `bg-[var(--brand-primary)]` in `@layer components`. We use a hybrid approach: Tailwind `@apply` for layout/spacing, raw CSS `var()` for all colours.

- [x] **5D.1** Audit — all ~60 component classes now use CSS variables for colours
- [x] **5D.2** Define `:root` Brand Variables block — 5 accent variables + font variable
- [x] **5D.3** Refactor all semantic classes to hybrid approach (Tailwind for structure, CSS variables for colours)
- [x] **5D.4** Fully semantic variable naming — replaced `--grey-*` / `--white` / `--form-accent` with ~40 role-based names
  - Named by UI purpose: `--surface-page`, `--text-heading`, `--control-border`, `--chart-series-1`, etc.
  - Organised into groups: Surfaces, Borders, Text, Controls, Status, Charts, Tables
  - All CSS, Chart.js, inline styles, documentation, and re-brand instructions updated
- [x] **5D.5** User visual review confirmed

### 5E — Finalise

- [x] **5E.1** Update style guide version to `v1.2`
- [x] **5E.2** Commit and push

---

## Phase 5F: Wireframe Placeholder Text — v1.3 (2026-03-02)

> Added **Redacted Script** (Google Fonts) for hand-drawn squiggle placeholder text — like Balsamiq's lorem ipsum squiggles. Type any words and they render as wavy lines. More words = more squiggle.

- [x] **5F.1** Add Redacted Script to CDN boilerplate (combined Google Fonts link)
- [x] **5F.2** Define `wire-*` classes matching all `type-*` sizes, with 35% font-size scale-up to match Balsamiq Sans x-height
- [x] **5F.3** Showcase: Notifications card uses squiggles; Section 2 has full `wire-*` demo with usage notes
- [x] **5F.4** Version bump to v1.3, commit and push

---

## Key Decision Points

| # | Decision | Status |
| --- | --- | --- |
| D1 | Orange-500 for warning status lights | **Decided** |
| D2 | Tailwind gray-50 to gray-900 greyscale | **Decided** |
| D5 | Chart.js as CDN chart library | **Decided** |
| D6 | Content Section header: dark bg, white bold text, left-aligned | **Decided** |
| D7 | Field Row pattern for inline related fields | **Decided** |
| D8 | Left sidebar for main navigation (collapsible) | **Decided** |
| D9 | Right-side slide-out panel for config/filters | **Decided** |
| D10 | Dedicated App Shell section in showcase | **Decided** |
| D11 | Semantic CSS variables for single-place re-branding | **Decided** |

---

## Token Discipline (Anti-Circle Rule)

To prevent iterating endlessly on colours and styles:

1. **Single source of truth**: `style-guide.md` defines all tokens
2. **Mockups are read-only consumers**: they reference tokens, never define their own
3. **Change protocol**: Any style tweak goes through `style-guide.md` first, then propagates to mockups
4. **Lock points**: After each phase, tokens used so far are considered locked unless explicitly reopened
5. **Decision log**: All colour/style decisions recorded in this plan with rationale
