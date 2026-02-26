# Prototype Wireframe Style Guide
### v1.1 — 2026-02-26

This document defines the shared visual language for wireframe prototypes. It uses a greyscale-first approach inspired by Balsamiq, with sparse colour accents for primary actions, errors, and warnings. All tokens use Tailwind CSS classes, wrapped in **semantic component classes** (e.g. `.btn-primary`, `.card-standard`). In HTML you use the semantic class name — never raw Tailwind. To rebrand, you change the class definitions in the `<style>` block; the HTML stays untouched.

---

## CDN Boilerplate

Add this to the `<head>` of any prototype HTML file:

```html
<!-- Tailwind CSS -->
<script src="https://cdn.tailwindcss.com"></script>

<!-- Balsamiq Sans Font -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Balsamiq+Sans:wght@400;700&display=swap" rel="stylesheet">

<!-- Remix Icons -->
<link href="https://cdn.jsdelivr.net/npm/remixicon@4.6.0/fonts/remixicon.css" rel="stylesheet">

<!-- Chart.js (for prototypes with charts) -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<!-- Apply Balsamiq Sans globally -->
<script>
  tailwind.config = {
    theme: {
      extend: {
        fontFamily: {
          sans: ['"Balsamiq Sans"', 'cursive'],
        }
      }
    }
  }
</script>
```

---

## Colour Palette

### Greyscale Tokens (primary palette)

All UI elements default to greyscale. The palette mixes Stone (tints), Gray (lighter shades), and Zinc (mid-range) for visual warmth and depth.

| Token | Hex | Tailwind Class | Role |
| --- | --- | --- | --- |
| Stone-50 | #FAFAF9 | `stone-50` | Page background |
| Stone-100 | #F5F5F4 | `stone-100` | Card backgrounds, subtle fills |
| Stone-200 | #E7E5E4 | `stone-200` | Light borders, dividers, disabled bg |
| Gray-300 | #D1D5DB | `gray-300` | Medium borders, input borders |
| Gray-400 | #9CA3AF | `gray-400` | Placeholder text, disabled text, muted |
| Zinc-500 | #71717A | `zinc-500` | Secondary text, captions, labels |
| Zinc-600 | #52525B | `zinc-600` | Body text |
| Zinc-700 | #3F3F46 | `zinc-700` | Headings, emphasis |
| Zinc-800 | #27272A | `zinc-800` | Strong headings, nav text |
| Zinc-900 | #18181B | `zinc-900` | Maximum contrast text (use sparingly) |
| White | #FFFFFF | `white` | Card surfaces, modal backgrounds |

### Accent Tokens (sparse use only)

These colours carry **meaning** and should only appear for their designated purpose. Never use them decoratively.

| Token | Hex | Tailwind Class | Role |
| --- | --- | --- | --- |
| Emerald-700 | #047857 | `emerald-700` | Primary actions, positive status |
| Rose-800 | #9F1239 | `rose-800` | Negative/error actions, negative status |
| Orange-500 | #F97316 | `orange-500` | Warning status lights only |

Supporting shades for hover/focus states:

| Token | Hex | Tailwind Class | Role |
| --- | --- | --- | --- |
| Emerald-800 | #065F46 | `emerald-800` | Primary button hover |
| Rose-900 | #881337 | `rose-900` | Danger button hover |
| Emerald-50 | #ECFDF5 | `emerald-50` | Subtle positive background (validation) |
| Rose-50 | #FFF1F2 | `rose-50` | Subtle negative background (validation) |

---

## Typography

All text uses **Balsamiq Sans** via Google Fonts. This gives the wireframe its hand-drawn, lo-fi aesthetic.

| Class Name | Size | Weight | Colour | Notes |
| --- | --- | --- | --- | --- |
| `type-title` | `text-2xl` | `font-bold` | Zinc-800 | Main page titles |
| `type-modal-title` | `text-xl` | `font-bold` | Zinc-800 | Modal/dialog headings |
| `type-heading` | `text-lg` | `font-bold` | Zinc-700 | Section headings |
| `type-body` | `text-base` | `font-normal` | Zinc-600 | General body text |
| `type-body-emphasis` | `text-base` | `font-bold` | Zinc-700 | Emphasized body text |
| `type-caption` | `text-sm` | `font-normal` | Zinc-500 | Labels, helper text |
| `type-muted` | `text-sm` | `font-normal` | Gray-400 | Disabled/inactive text |

---

## Buttons

### Primary Button — `.btn-primary`
Main call-to-action. The only button with colour. Always includes a leading check icon.
```
bg-emerald-700 hover:bg-emerald-800 text-white
font-bold
px-6 py-2.5
rounded-lg
border-none
shadow-sm
transition-colors duration-150
cursor-pointer
```
Icon + label pattern: `<i class="ri-check-line"></i> Action Label`

### Secondary Button — `.btn-secondary`
Alternative or less prominent action. Grey background.
```
bg-stone-200 hover:bg-gray-300 text-zinc-700
font-bold
px-6 py-2.5
rounded-lg
border border-gray-300
shadow-sm
transition-colors duration-150
cursor-pointer
```

### Danger Button — `.btn-danger`
Destructive or negative action. Used sparingly.
```
bg-rose-800 hover:bg-rose-900 text-white
font-bold
px-6 py-2.5
rounded-lg
border-none
shadow-sm
transition-colors duration-150
cursor-pointer
```

### Ghost Button — `.btn-ghost`
Minimal emphasis, transparent background. Always has a border so it's visible on white backgrounds.
```
bg-transparent hover:bg-stone-100 text-zinc-600
font-bold
px-6 py-2.5
rounded-lg
border border-gray-300
transition-colors duration-150
cursor-pointer
```

### Cancel Button — `.btn-cancel`
Dismisses a dialog or backs out of a flow. Always paired with a primary action. Has its own grey background to distinguish it from the page. Uses `ri-arrow-go-back-line` icon.
```
bg-gray-300 hover:bg-gray-400 text-zinc-700
font-bold
px-6 py-2.5
rounded-lg
border border-gray-400
transition-colors duration-150
cursor-pointer
```
Icon + label pattern: `<i class="ri-arrow-go-back-line"></i> Cancel`

### Next Button — `.btn-next`
Advances to the next step in a multi-step flow. Secondary style with a trailing arrow-right icon. Always sits to the right of Previous.
```
bg-stone-200 hover:bg-gray-300 text-zinc-700
font-bold
px-6 py-2.5
rounded-lg
border border-gray-300
shadow-sm
transition-colors duration-150
cursor-pointer
```
Icon + label pattern: `Next <i class="ri-arrow-right-line"></i>`

### Previous Button — `.btn-previous`
Returns to the prior step in a multi-step flow. Secondary style with a leading arrow-left icon.
```
bg-stone-200 hover:bg-gray-300 text-zinc-700
font-bold
px-6 py-2.5
rounded-lg
border border-gray-300
shadow-sm
transition-colors duration-150
cursor-pointer
```
Icon + label pattern: `<i class="ri-arrow-left-line"></i> Previous`

### Disabled Button — `.btn-disabled`
Inactive state for any button.
```
bg-stone-100 text-gray-400
cursor-not-allowed
px-6 py-2.5
rounded-lg
border border-stone-200
```

---

## Text Links — `.text-link`

Inline clickable text. Uses underline for universal affordance. Greyscale to stay within the wireframe palette — not blue.
```
text-zinc-600 underline underline-offset-2
hover:text-zinc-900
transition-colors duration-150
```
Usage: `<a href="#" class="text-link">link text</a>`

---

## Form Elements

### Text Input (default) — `.form-input`
```
w-full
bg-white
border border-gray-300
rounded-lg
px-3 py-2
text-zinc-700
placeholder-gray-400
focus:outline-none focus:border-zinc-500 focus:ring-1 focus:ring-gray-300
```

### Text Input (error state) — `.form-input-error`
```
border-rose-800 focus:border-rose-800 focus:ring-rose-800
```
Pair with error message: `text-sm text-rose-800 mt-1`

### Text Input (success state) — `.form-input-success`
```
border-emerald-700 focus:border-emerald-700 focus:ring-emerald-700
```

### Text Input (disabled) — `.form-input-disabled`
```
bg-stone-100 text-gray-400 border-stone-200 cursor-not-allowed
```

### Label — `.form-label`
```
text-sm font-bold text-zinc-700 mb-1 block
```

### Helper Text — `.form-helper`
```
text-sm text-zinc-500 mt-1
```

Error message: `.form-error` — `text-sm text-rose-800 mt-1`
Success message: `.form-success` — `text-sm text-emerald-700 mt-1`

### Select Dropdown — `.form-select`
Same styling as text input, with `appearance-none` and a chevron icon.

### Textarea — `.form-textarea`
Same styling as text input, with `resize-y min-h-[80px]`.

### Checkbox — `.form-checkbox`
```
w-4 h-4
border border-gray-300 rounded
accent-zinc-600
```
Label inline: `.form-check-label` — `text-base text-zinc-600 ml-2`

### Radio Button — `.form-radio`
```
w-4 h-4
border border-gray-300
accent-zinc-600
```
Label inline: `.form-check-label` — `text-base text-zinc-600 ml-2`

### Toggle Switch
Use a styled checkbox with peer classes, zinc-600 for the active state, gray-300 for inactive.

---

## Status Lights

Small coloured dots to indicate state. Use inline with text or in tables/lists. Base class: `.status-dot`

| State | Semantic Class | Tailwind | Icon alternative |
| --- | --- | --- | --- |
| Positive | `.status-positive` | `w-2.5 h-2.5 rounded-full bg-emerald-700` | `ri-checkbox-circle-fill text-emerald-700` |
| Negative | `.status-negative` | `w-2.5 h-2.5 rounded-full bg-rose-800` | `ri-close-circle-fill text-rose-800` |
| Warning | `.status-warning` | `w-2.5 h-2.5 rounded-full bg-orange-500` | `ri-alert-fill text-orange-500` |
| Neutral | `.status-neutral` | `w-2.5 h-2.5 rounded-full bg-gray-300` | `ri-checkbox-blank-circle-fill text-gray-300` |

Usage: `<span class="status-dot status-positive"></span>`

### Inline Status — icon + text (user supplies only the copy)

These classes bundle icon, colour, and sizing. You just write the text — the icon appears automatically.

| State | Semantic Class | Icon (auto) | Colour |
| --- | --- | --- | --- |
| Positive | `.inline-positive` | `ri-checkbox-circle-fill` | Emerald-700 |
| Negative | `.inline-negative` | `ri-close-circle-fill` | Rose-800 |
| Warning | `.inline-warning` | `ri-alert-fill` | Orange-500 |

Usage: `<span class="inline-positive">Verified</span>` — renders as the green tick icon followed by "Verified".

---

## Cards & Containers

### Card Standard — `.card-standard`
Standard content container.
```
bg-white
rounded-xl
shadow-sm
p-4
border border-stone-200
```

### Card Light — `.card-light`
Lightweight container, minimal elevation.
```
bg-stone-50
rounded-lg
px-6 py-3
border border-stone-200
```

### Card Prominent (Dialogs & Modals) — `.card-prominent`
High-emphasis container for modals and overlays. Width is `max-w-lg` (wider than the old `max-w-sm`).
```
bg-white
rounded-xl
shadow-lg
border border-stone-200
w-full max-w-lg mx-4
text-left
```

Modal overlay backdrop — `.modal-overlay`:
```
fixed inset-0 bg-zinc-900/50 flex items-center justify-center
```

Modal internal structure (all semantic classes):
- **Header** — `.modal-header` (`px-6 py-3`): heading only above the divider.
- **Divider** — `.modal-divider`: `<hr class="modal-divider">`
- **Body** — `.modal-body` (`px-6 py-4`): body text, content area, then button row.
- **Button row** — `.modal-actions` (`flex justify-end gap-3`): buttons right-aligned. For split layout (Cancel left, Next/Previous right): `.modal-actions-split` (`flex justify-between gap-3`).
- Primary button always sits rightmost.

---

## Modal Patterns

Four named modal patterns. Each uses the same structural classes above — only the interior content differs. Copy the relevant skeleton into your prototype and fill in the content.

### 1. Confirmation Modal

Use for: success messages, simple confirmations that need a single acknowledgement action.

```html
<div id="modal-confirm" class="hidden modal-overlay">
  <div class="card-prominent">
    <div class="modal-header">
      <h3 class="type-modal-title">Modal Title</h3>
    </div>
    <hr class="modal-divider">
    <div class="modal-body">
      <p class="type-body mb-5">Body message goes here.</p>
      <div class="modal-actions">
        <button class="btn-primary">
          <span class="flex items-center gap-2"><i class="ri-check-line"></i> Continue</span>
        </button>
      </div>
    </div>
  </div>
</div>
```

For a two-button confirmation (e.g. "Are you sure?"): use `.modal-actions-split` with `.btn-cancel` left and `.btn-primary` right.

---

### 2. Error Modal

Use for: failure messages, system errors, anything that requires the user to acknowledge a problem before continuing. Uses `btn-danger` for the action button.

```html
<div id="modal-error" class="hidden modal-overlay">
  <div class="card-prominent">
    <div class="modal-header">
      <h3 class="type-modal-title">Something went wrong</h3>
    </div>
    <hr class="modal-divider">
    <div class="modal-body">
      <p class="type-body mb-5">Describe what failed and what the user should do next.</p>
      <div class="modal-actions">
        <button class="btn-danger">
          <span class="flex items-center gap-2"><i class="ri-close-line"></i> Ok</span>
        </button>
      </div>
    </div>
  </div>
</div>
```

For a destructive confirmation (e.g. "Delete this item?"): use `.modal-actions-split` with `.btn-cancel` left and `.btn-danger` right.


---

### 3. Procedural Modal (Step-by-Step)

Use for: multi-step setup wizards, onboarding flows, guided tasks.

```html
<div id="modal-procedural" class="hidden modal-overlay">
  <div class="card-prominent">
    <div class="modal-header">
      <h3 class="type-modal-title">Flow Title</h3>
    </div>
    <hr class="modal-divider">
    <div class="modal-body">
      <!-- Step indicators — first element below the divider -->
      <div class="flex items-center gap-2 mb-4">
        <span class="step-active">1</span>
        <div class="step-connector"></div>
        <span class="step-inactive">2</span>
        <div class="step-connector"></div>
        <span class="step-inactive">3</span>
        <span class="type-caption ml-2">Step 1 of 3</span>
      </div>
      <!-- Step content -->
      <p class="type-body mb-4">Step description goes here.</p>
      <div class="card-light mb-5 type-caption">Step content area.</div>
      <!-- Navigation: Cancel far left | Previous + Next/Finish far right -->
      <div class="modal-actions-split">
        <button class="btn-cancel">
          <span class="flex items-center gap-2"><i class="ri-arrow-go-back-line"></i> Cancel</span>
        </button>
        <div class="flex gap-2">
          <button class="btn-previous" disabled>
            <span class="flex items-center gap-1"><i class="ri-arrow-left-line"></i> Previous</span>
          </button>
          <button class="btn-next">
            <span class="flex items-center gap-2">Next <i class="ri-arrow-right-line"></i></span>
          </button>
        </div>
      </div>
    </div>
  </div>
</div>
```


---

### 4. Verbose Decision Modal

Use for: choosing between 2–3 options that each need explanation before the user decides.

```html
<div id="modal-decision" class="hidden modal-overlay">
  <div class="card-prominent">
    <div class="modal-header">
      <h3 class="type-modal-title">How would you like to proceed?</h3>
    </div>
    <hr class="modal-divider">
    <div class="modal-body">
      <h4 class="type-heading mb-2">Subheading</h4>
      <p class="type-body mb-5">Explanatory paragraph giving context before the user chooses.</p>
      <!-- For 2 options use grid-cols-2; for 3 options use grid-cols-3 -->
      <div class="grid grid-cols-2 gap-4 mb-6">
        <label class="flex items-start gap-3 cursor-pointer">
          <input type="radio" name="decision-option" value="a" checked class="form-radio mt-1 shrink-0">
          <div>
            <span class="form-check-label font-bold block mb-1">Option A</span>
            <p class="type-caption">Description of this option and when to use it.</p>
          </div>
        </label>
        <label class="flex items-start gap-3 cursor-pointer">
          <input type="radio" name="decision-option" value="b" class="form-radio mt-1 shrink-0">
          <div>
            <span class="form-check-label font-bold block mb-1">Option B</span>
            <p class="type-caption">Description of this option and when to use it.</p>
          </div>
        </label>
      </div>
      <div class="modal-actions-split">
        <button class="btn-cancel">
          <span class="flex items-center gap-2"><i class="ri-arrow-go-back-line"></i> Cancel</span>
        </button>
        <button class="btn-primary">
          <span class="flex items-center gap-2"><i class="ri-check-line"></i> Continue</span>
        </button>
      </div>
    </div>
  </div>
</div>
```

---

## Icons (Remix Icons)

Use [Remix Icons](https://remixicon.com/) via CDN. Each icon has `-line` (outlined) and `-fill` (solid) variants. Prefer `-line` for wireframes; use `-fill` for active/selected states.

### Recommended Prototype Icons

| Purpose | Icon Class | Preview |
| --- | --- | --- |
| Home | `ri-home-line` | Home |
| Search | `ri-search-line` | Search |
| User/Profile | `ri-user-line` | User |
| Settings | `ri-settings-3-line` | Gear |
| Menu | `ri-menu-line` | Hamburger |
| Close | `ri-close-line` | X |
| Add/Create | `ri-add-line` | Plus |
| Edit | `ri-pencil-line` | Pencil |
| Delete/Trash | `ri-delete-bin-line` | Trash |
| Check/Success | `ri-check-line` | Check |
| Warning | `ri-alert-line` | Alert |
| Info | `ri-information-line` | Info |
| Error | `ri-error-warning-line` | Error |
| Arrow Right | `ri-arrow-right-line` | Arrow |
| Arrow Left | `ri-arrow-left-line` | Arrow |
| Chevron Down | `ri-arrow-down-s-line` | Chevron |
| Notification | `ri-notification-line` | Bell |
| Calendar | `ri-calendar-line` | Calendar |
| Download | `ri-download-line` | Download |
| Upload | `ri-upload-line` | Upload |

### Icon Sizing

| Size | Class | Usage |
| --- | --- | --- |
| Small | `text-base` | Inline with body text |
| Medium | `text-xl` | Buttons, list items |
| Large | `text-3xl` | Feature icons, empty states |
| XLarge | `text-5xl` | Hero icons, modal status |

Icon colour follows the same rules as text — grey by default, accent colours only for status meaning.

---

## Spacing

| Token | Value | Usage |
| --- | --- | --- |
| `spacing-page` | `p-4` | Page-level padding |
| `spacing-section` | `gap-6` | Gap between major sections |
| `spacing-items` | `gap-3` | Gap between related items (e.g. buttons) |
| `spacing-internal` | `p-4` | Internal padding for containers |

---

## Transitions & Animations

| Token | Duration | Easing | Usage |
| --- | --- | --- | --- |
| `transition-fast` | 150ms | `ease-in-out` | Hover states, colour changes |
| `transition-standard` | 200ms | `ease-out` | Element appear/disappear |

Keep transitions minimal for a wireframe feel. Avoid elaborate animations.

---

## Responsive Behaviour

- Minimum supported width: 320px
- On narrow screens: stack sections vertically
- Button touch targets: minimum 44px height
- Content scales proportionally on smaller screens

---

## Nav Bar — `.navbar`

Top navigation bar with brand, links, and optional action button.
```
bg-white border-b border-stone-200 px-8 py-3
flex items-center justify-between shadow-sm
```

| Element | Semantic Class | Definition |
| --- | --- | --- |
| Brand text | `.navbar-brand` | `font-bold text-zinc-800 text-lg` |
| Nav link | `.navbar-link` | `text-zinc-600 hover:text-zinc-900 text-base` |

---

## Footer — `.footer`

Page footer with copyright and links.
```
bg-zinc-800 text-zinc-400 px-8 py-6
flex items-center justify-between text-sm
```
Footer links: `.footer-link` — `hover:text-white transition-colors duration-150`

---

## Step Indicators

Used in procedural modals for multi-step flows.

| Element | Semantic Class | Tailwind |
| --- | --- | --- |
| Active | `.step-active` | `w-7 h-7 rounded-full bg-emerald-700 text-white text-sm font-bold` |
| Inactive | `.step-inactive` | `w-7 h-7 rounded-full bg-gray-300 text-zinc-500 text-sm font-bold` |
| Connector | `.step-connector` | `w-8 h-0.5 bg-gray-300` |
On the final step, replace `btn-next` with `btn-primary` and label it "Finish" with `ri-check-line`.
---

## Tables

### Small Table — `.table-simple`

A compact, minimal table for inline data display. No frills — just clean rows of data.

| Element | Semantic Class | Tailwind |
| --- | --- | --- |
| Table wrapper | `.table-simple` | `w-auto text-sm border-collapse` |
| Header cell | `.table-simple th` | `font-bold text-zinc-700 text-left py-2 px-3 border-b border-gray-300` |
| Body cell | `.table-simple td` | `text-zinc-600 py-2 px-3` |
| Totals row | `.table-simple .table-totals td` | `font-bold text-zinc-700 border-t border-gray-300` |
| Number cell | `.table-num` | `text-right` (apply to both `th` and `td`) |

Rules:
- Numbers right-aligned, text left-aligned
- One thin horizontal rule below headers, one above totals row
- No row dividers, no zebra striping, no sorting
- Regular text size for data, bold for column headers and totals row

```html
<table class="table-simple">
  <thead>
    <tr>
      <th>Item</th>
      <th class="table-num">Qty</th>
      <th class="table-num">Price</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Widget A</td><td class="table-num">12</td><td class="table-num">$48.00</td></tr>
    <tr class="table-totals"><td>Total</td><td class="table-num">12</td><td class="table-num">$48.00</td></tr>
  </tbody>
</table>
```

---

### Large Table — `.table-report`

A full-width report table for data-heavy screens. Always placed inside a Content Section (see below).

| Element | Semantic Class | Tailwind |
| --- | --- | --- |
| Table wrapper | `.table-report` | `w-full text-sm border-collapse` |
| Header row | `.table-report thead tr` | `bg-zinc-600 text-white` |
| Header cell | `.table-report th` | `font-bold text-left py-2.5 px-3 sticky top-0 bg-zinc-600` |
| Body row (even) | `.table-report tbody tr:nth-child(even)` | `bg-stone-50` |
| Body row (odd) | `.table-report tbody tr:nth-child(odd)` | `bg-white` |
| Body cell | `.table-report td` | `text-zinc-600 py-2 px-3` |
| Sortable header | `.table-sort` | Append sort icon: `ri-arrow-up-s-line` / `ri-arrow-down-s-line` |
| Number cell | `.table-num` | `text-right` |
| Footer | `.content-section-footer` | `bg-stone-100 border-t border-stone-200 px-4 py-3` |

Rules:
- Full width, inside a Content Section container
- Zebra striping: alternating `white` / `stone-50` rows
- Sticky header row (stays visible on scroll)
- Sortable columns show up/down chevrons next to header text
- Number columns right-aligned
- Results/totals sit in a **non-scrollable footer** below the scrollable table body
- Content section header uses `zinc-700` (darker); table column headers use `zinc-600` (lighter) — two distinct grey levels

```html
<div class="content-section">
  <div class="content-section-header">Sales Report</div>
  <div class="content-section-body p-0 overflow-auto max-h-64">
    <table class="table-report">
      <thead>
        <tr>
          <th>Product <i class="ri-arrow-up-s-line table-sort"></i></th>
          <th class="table-num">Revenue</th>
        </tr>
      </thead>
      <tbody>
        <tr><td>Widget A</td><td class="table-num">$12,400</td></tr>
        <tr><td>Widget B</td><td class="table-num">$8,200</td></tr>
      </tbody>
    </table>
  </div>
  <div class="content-section-footer">
    <span class="font-bold text-zinc-700">Total Revenue: $20,600</span>
  </div>
</div>
```

---

## Charts

CDN dependency: **Chart.js** — a single lightweight charting library, no build tools required. Can be swapped for more powerful alternatives (D3.js, Apache ECharts) if the prototype evolves into production.

### Chart Greyscale Palette

Charts use greyscale tones to stay within the wireframe aesthetic:

| Series | Hex | Tailwind Equivalent | Usage |
| --- | --- | --- | --- |
| Primary | #3F3F46 | `zinc-700` | First/main series |
| Secondary | #71717A | `zinc-500` | Second series |
| Tertiary | #D1D5DB | `gray-300` | Third series |
| Quaternary | #E7E5E4 | `stone-200` | Fourth series |

Gridlines and axes use `stone-200` (#E7E5E4). Axis labels use `zinc-500`.

### Defined Chart Types

**Bar Chart**
- Bars: `zinc-500`
- Gridlines: `stone-200`
- X-axis labels visible, Y-axis with grid

**Line Chart**
- Line: `zinc-700`, 2px weight
- Data points: filled circles in `zinc-700`
- Gridlines: `stone-200`

**Pie Chart**
- Segments: `zinc-700`, `zinc-500`, `gray-300`, `stone-200` (in order for up to 4 segments)
- Legend below chart

### Chart.js Configuration Defaults

```javascript
// Apply these defaults at the top of your script
Chart.defaults.font.family = '"Balsamiq Sans", cursive';
Chart.defaults.color = '#71717A';           // zinc-500 for labels
Chart.defaults.borderColor = '#E7E5E4';     // stone-200 for gridlines
Chart.defaults.plugins.legend.labels.usePointStyle = true;
```

---

## Content Sections

### Content Section — `.content-section`

A grouping container for form fields, tables, or mixed content on busy screens. Gives visual structure with a coloured header bar.

| Element | Semantic Class | Tailwind |
| --- | --- | --- |
| Wrapper | `.content-section` | `border border-stone-200 rounded-lg overflow-hidden` |
| Header | `.content-section-header` | `bg-zinc-700 text-white font-bold text-sm px-4 py-2` |
| Body | `.content-section-body` | `bg-white px-4 py-4` |
| Footer | `.content-section-footer` | `bg-stone-100 border-t border-stone-200 px-4 py-3` |

Layout rules:
- **Single section**: full width
- **Two sections side by side**: use `grid grid-cols-1 md:grid-cols-2 gap-6`
- A section never wraps mid-content to a second column
- Responsive: two-column sections stack vertically on mobile

```html
<!-- Two side-by-side content sections -->
<div class="grid grid-cols-1 md:grid-cols-2 gap-6">
  <div class="content-section">
    <div class="content-section-header">Personal Information</div>
    <div class="content-section-body">
      <!-- form fields here -->
    </div>
  </div>
  <div class="content-section">
    <div class="content-section-header">Address</div>
    <div class="content-section-body">
      <!-- form fields here -->
    </div>
  </div>
</div>
```

---

## Field Rows

### Field Row — `.field-row`

Inline grouping for related form fields that belong on the same line (e.g. First + Last name, City + State + Postcode).

| Element | Semantic Class | Tailwind |
| --- | --- | --- |
| Row wrapper | `.field-row` | `flex flex-col sm:flex-row gap-4` |
| Equal-width child | (default) | `flex-1` on each child `<div>` |
| Unequal widths | utility override | e.g. `flex-[3]` + `flex-[2]` for 60/40 split |

Rules:
- Children grow equally by default (each gets `flex-1`)
- For unequal widths, use `flex-[N]` on the child wrapper
- Collapses to stacked layout on narrow screens (below `sm:` breakpoint)
- Each child contains a standard `form-label` + `form-input` pair

```html
<!-- Equal widths: First Name + Last Name -->
<div class="field-row">
  <div class="flex-1">
    <label class="form-label">First Name</label>
    <input type="text" class="form-input" placeholder="Jane">
  </div>
  <div class="flex-1">
    <label class="form-label">Last Name</label>
    <input type="text" class="form-input" placeholder="Smith">
  </div>
</div>

<!-- Unequal widths: City (wider) + State + Postcode -->
<div class="field-row">
  <div class="flex-[3]">
    <label class="form-label">City</label>
    <input type="text" class="form-input" placeholder="Melbourne">
  </div>
  <div class="flex-[2]">
    <label class="form-label">State</label>
    <input type="text" class="form-input" placeholder="VIC">
  </div>
  <div class="flex-[1]">
    <label class="form-label">Postcode</label>
    <input type="text" class="form-input" placeholder="3000">
  </div>
</div>
```

---

## Layout Utilities

Semantic classes for page structure (used in showcase, reusable in projects):

| Element | Semantic Class | Tailwind |
| --- | --- | --- |
| Page body | `.page-bg` | `bg-stone-50 text-zinc-700` |
| Section divider | `.section-divider` | `border-b-4 border-zinc-800` |
| Section label | `.section-label` | `bg-zinc-700 text-white px-8 py-2` |
| Label text | `.section-label-text` | `text-sm font-bold tracking-widest uppercase` |
