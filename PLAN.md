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
  updated: "2026-02-26T00:00:00.000Z"
  progress: 98
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

## Phase 1: Foundation — Style Guide Document

> Goal: Create `style-guide.md` with all design tokens locked before any visual work.

- [x] **1.1** Copy structure from HexaPawn `style-guide.md` into `project-prototype-styleguide/style-guide.md`
- [x] **1.2** Define greyscale palette — multiple Tailwind grey tokens (Gray-50 through Gray-900)
- [x] **1.3** Define 3 accent colour tokens (emerald-700, rose-800, orange-500) — **Orange-500 confirmed by user**
- [x] **1.4** Update typography section — Balsamiq Sans via Google Fonts CDN, all type classes defined
- [x] **1.5** Update button styles: Primary (emerald), Danger (rose), Secondary (grey), Ghost, Disabled
- [x] **1.6** Define status light component (dots + icon alternatives): emerald, rose, orange, grey
- [x] **1.7** Add icon system section — Remix Icons via CDN, 20 recommended icons, sizing guide
- [x] **1.8** Adapt cards & containers to greyscale
- [x] **1.9** Carry forward spacing, transitions, and responsive sections
- [x] **1.10** Define CDN boilerplate snippet (Tailwind + Balsamiq Sans + Remix Icons)
- [x] **1.11** Add form elements: text input, select, textarea, checkbox, radio button, toggle, validation states
- [x] **1.12** Add progress bar component
- [x] **1.13** Create CLAUDE.md for AI session context

**Phase 1 exit criteria**: Style guide document is complete, all tokens defined, user has approved colour choices.

---

## Phase 2: Visual Validation — Mockup Screens

> Goal: Build 4 static HTML mockup screens that showcase every token from the style guide. These screens exist only to validate the style guide visually — they have no functionality.

- [x] **2.1** Create `showcase.html` with CDN boilerplate from style guide
- [x] **2.2** Section 1 — **Landing Page**: nav bar, hero, card grid with icons and status lights, footer
- [x] **2.3** Section 2 — **Form Entry**: inputs, select, textarea, checkbox, radio buttons, validation states, all button types
- [x] **2.4** Section 3 → **Section 5** — **Confirmation / Error Modal**: success variant (emerald) + error variant (rose), triggered overlay only (no static preview), title-only above divider, buttons right-aligned *(renumbered in Phase 4)*
- [x] **2.5** Section 4 → **Section 6** — **Procedural Modal**: title-only above divider, step indicators first below divider, Cancel far left / Previous+Next far right *(renumbered in Phase 4)*
- [x] **2.5a** Button tokens finalised: Primary (`ri-check-line`), Cancel (gray-300, `ri-arrow-go-back-line`), Next (`ri-arrow-right-line`), Previous (`ri-arrow-left-line`), Ghost (border added), Toggle (zinc-600 active state)
- [x] **2.5b** Form controls updated: checkboxes, radio buttons, toggle all use `accent-zinc-600` (no primary green)
- [x] **2.6** Review: verify icons, radio buttons, and any other missing elements are covered
- [x] **2.7** Visual review with user — screenshot and discuss

## Phase 2.5: Additions

> Goal: Add components discovered during Phase 2 review that were missing from the initial scope.

- [x] **2.5.1** Remove progress bar from Procedural Modal (stepper is sufficient as progress indicator)
- [x] **2.5.2** Remove `progress-track` / `progress-fill` CSS classes from showcase and style guide
- [x] **2.5.3** Rename Section 4 to "Procedural & Decision Modals"
- [x] **2.5.4** Add **Verbose Decision Modal**: heading, subheading + body text, 2-column radio options (each with label + description), Cancel left / Continue right
- [x] **2.5.5** Document Decision Modal pattern in `style-guide.md` (supports 2 or 3 options)

>

**Phase 2 exit criteria**: Single showcase page built, all tokens visually validated, user has reviewed.

---

## Phase 3: Review & Lock

> Goal: Finalize the style guide as v1.0 and prepare for reuse.

- [x] **3.1** Incorporate any final colour/style adjustments from Phase 2 review into `style-guide.md` — added `type-modal-title` token
- [x] **3.2** Verify all mockups reflect final tokens (no hardcoded values) — fixed modal headings and inline status in showcase
- [x] **3.3** Add version header to style guide: `v1.0 — Locked`
- [x] **3.4** Final user sign-off
- [x] **3.5** Initialize local git repo (done — `style-guide.md` and `showcase.html` committed)
- [x] **3.6** Pushed to GitHub — https://github.com/LarsGustavsson-au/prototype-styleguide

**Phase 3 exit criteria**: Style guide marked v1.0, all mockups consistent, optionally pushed to GitHub.

---

## Phase 4: Data Display & Layout Sections

> Goal: Add tables, charts, content sections, and field grouping to the style guide and showcase. Existing showcase sections 3–4 become 5–6 to make room.

### 4A — Style Guide: New Tokens

- [x] **4A.1** Add **Small Table** tokens to `style-guide.md` — `.table-simple`
  - Regular text size for data, bold for column headers and totals row
  - One thin horizontal rule below headers, one at bottom
  - Numbers right-aligned, text left-aligned (no "snaking")
  - No row dividers, no zebra striping, no sorting — clean and minimal
- [x] **4A.2** Add **Large Table** tokens to `style-guide.md` — `.table-report`
  - Full-width, intended for report screens
  - Zebra striping: alternating `white` / `stone-50` rows
  - Sticky header row (stays visible on scroll)
  - Sortable column indicator: up/down chevrons (`ri-arrow-up-s-line` / `ri-arrow-down-s-line`) next to column headers
  - Always placed inside a Content Section (see 4A.4)
  - Non-scrollable footer (`.content-section-footer`) for totals/results
  - Content section header `zinc-700` (darker) vs table column headers `zinc-600` (lighter)
- [x] **4A.3** Add **Charts** section to `style-guide.md`
  - CDN dependency: **Chart.js** via `<script>` tag (single lightweight library, no build tools)
  - Note in style guide that Chart.js can be swapped for more powerful libraries (e.g. D3.js, Apache ECharts) if needed
  - Greyscale palette for chart elements: `zinc-700` (primary), `zinc-500`, `gray-300`, `stone-200` for series differentiation
  - Three chart types defined: **Pie**, **Bar**, **Line**
  - Bar chart: bars in `zinc-500`, gridlines in `stone-200`, X-axis labels visible
  - Line chart: line in `zinc-700`, data point dots, `stone-200` gridlines
  - Pie chart: segments use greyscale tones (`zinc-700`, `zinc-500`, `gray-300`, `stone-200`)
  - All charts show readable axis labels / legends
- [x] **4A.4** Add **Content Section** tokens to `style-guide.md` — `.content-section`
  - A grouping container for form fields, tables, or other content on busy screens
  - Section header: `zinc-700` background, white bold text, left-aligned — `.content-section-header`
  - Section body: white background, border `stone-200`, internal padding — `.content-section-body`
  - Section footer: `stone-100` background, border top — `.content-section-footer`
  - Layout: single section = full width; two sections = side by side with gap
  - Responsive: two-column sections stack vertically on mobile (`md:grid-cols-2`)
  - A section never wraps mid-content to a second column
- [x] **4A.5** Add **Field Row** tokens to `style-guide.md` — `.field-row`
  - Inline grouping for related form fields (e.g. First + Last name, Date + Time, City + State + Postcode)
  - Flex row with gap, children grow equally by default
  - Supports unequal widths via utility classes (e.g. `flex-[3]` + `flex-[2]` for 60/40 split)
  - Collapses to stacked on narrow screens
  - Documented with usage examples showing common patterns

### 4B — Showcase: New Sections & Renumber

- [x] **4B.1** Renumber existing showcase sections:
  - Section 3 (Confirmation/Error Modals) → **Section 5**
  - Section 4 (Procedural & Decision Modals) → **Section 6**
- [x] **4B.2** Build **Showcase Section 3 — Tables & Charts**
  - Small table example: 4–5 rows, mix of text and numbers, one totals row
  - Large table example: 8–10 rows with zebra striping, sortable column headers, inside a content section
  - Pie chart, bar chart, and line chart — all using greyscale palette, with readable labels
- [x] **4B.3** Build **Showcase Section 4 — Content Sections & Field Rows**
  - Two side-by-side content sections: "Personal Information" (First Name, Last Name on one row; Date of Birth) and "Address" (Street, City + State + Postcode on one row)
  - Form fields use existing `.form-input`, `.form-label` etc. from Section 2
  - Demonstrates `.field-row` for inline grouping (First + Last, City + State + Postcode)
  - Shows responsive stacking behaviour description

### 4C — CDN Boilerplate Update

- [x] **4C.1** Add Chart.js CDN `<script>` tag to the CDN Boilerplate section in `style-guide.md`
- [x] **4C.2** Add Chart.js to `showcase.html` `<head>`

### 4D — Review

- [x] **4D.1** Verify all new tokens are in `style-guide.md` before showcase references them
- [x] **4D.2** Visual review — screenshot and confirm with user
- [x] **4D.3** Update style guide version to `v1.1`
- [ ] **4D.4** Commit and push

---

## Key Decision Points

These require user sign-off before proceeding:

| # | Decision | When | Status |
| --- | --- | --- | --- |
| D1 | Orange shade for warning status lights | Phase 1.3 | **Decided: Orange-500** |
| D2 | Grey scale selection (visual comparison) | Phase 1.2 | Defined (Tailwind gray-50 to gray-900), visual review in Phase 2 |
| D3 | Mockup page layouts (before building) | Phase 2.1 | Pending |
| D4 | Final style guide approval | Phase 3.4 | Pending |
| D5 | Chart.js as CDN chart library | Phase 4A.3 | **Decided: Chart.js** |
| D6 | Content Section header: zinc-600 bg, white bold text, left-aligned | Phase 4A.4 | **Decided** |
| D7 | Field Row pattern for inline related fields | Phase 4A.5 | **Decided** |

---

## Token Discipline (Anti-Circle Rule)

To prevent iterating endlessly on colours and styles:

1. **Single source of truth**: `style-guide.md` defines all tokens
2. **Mockups are read-only consumers**: they reference tokens, never define their own
3. **Change protocol**: Any style tweak goes through `style-guide.md` first, then propagates to mockups
4. **Lock points**: After each phase, tokens used so far are considered locked unless explicitly reopened
5. **Decision log**: All colour/style decisions recorded in this plan with rationale
