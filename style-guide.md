# Prototype Wireframe Style Guide

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

| Token       | Hex     | Tailwind Class | Role                                      |
|-------------|---------|----------------|-------------------------------------------|
| Stone-50    | #FAFAF9 | `stone-50`     | Page background                           |
| Stone-100   | #F5F5F4 | `stone-100`    | Card backgrounds, subtle fills            |
| Stone-200   | #E7E5E4 | `stone-200`    | Light borders, dividers, disabled bg      |
| Gray-300    | #D1D5DB | `gray-300`     | Medium borders, input borders             |
| Gray-400    | #9CA3AF | `gray-400`     | Placeholder text, disabled text, muted    |
| Zinc-500    | #71717A | `zinc-500`     | Secondary text, captions, labels          |
| Zinc-600    | #52525B | `zinc-600`     | Body text                                 |
| Zinc-700    | #3F3F46 | `zinc-700`     | Headings, emphasis                        |
| Zinc-800    | #27272A | `zinc-800`     | Strong headings, nav text                 |
| Zinc-900    | #18181B | `zinc-900`     | Maximum contrast text (use sparingly)     |
| White       | #FFFFFF | `white`        | Card surfaces, modal backgrounds          |

### Accent Tokens (sparse use only)

These colours carry **meaning** and should only appear for their designated purpose. Never use them decoratively.

| Token       | Hex     | Tailwind Class | Role                                      |
|-------------|---------|----------------|-------------------------------------------|
| Emerald-700 | #047857 | `emerald-700`  | Primary actions, positive status          |
| Rose-800    | #9F1239 | `rose-800`     | Negative/error actions, negative status   |
| Orange-500  | #F97316 | `orange-500`   | Warning status lights only                |

Supporting shades for hover/focus states:

| Token       | Hex     | Tailwind Class | Role                                      |
|-------------|---------|----------------|-------------------------------------------|
| Emerald-800 | #065F46 | `emerald-800`  | Primary button hover                      |
| Rose-900    | #881337 | `rose-900`     | Danger button hover                       |
| Emerald-50  | #ECFDF5 | `emerald-50`   | Subtle positive background (validation)   |
| Rose-50     | #FFF1F2 | `rose-50`      | Subtle negative background (validation)   |

---

## Typography

All text uses **Balsamiq Sans** via Google Fonts. This gives the wireframe its hand-drawn, lo-fi aesthetic.

| Class Name          | Size        | Weight          | Colour   | Notes                    |
|---------------------|-------------|-----------------|----------|--------------------------|
| `type-title`        | `text-2xl`  | `font-bold`     | Zinc-800 | Main page titles         |
| `type-heading`      | `text-lg`   | `font-bold`     | Zinc-700 | Section headings         |
| `type-body`         | `text-base` | `font-normal`   | Zinc-600 | General body text        |
| `type-body-emphasis`| `text-base` | `font-bold`     | Zinc-700 | Emphasized body text     |
| `type-caption`      | `text-sm`   | `font-normal`   | Zinc-500 | Labels, helper text      |
| `type-muted`        | `text-sm`   | `font-normal`   | Gray-400 | Disabled/inactive text   |

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

| State    | Semantic Class     | Tailwind                                    | Icon alternative        |
|----------|--------------------|---------------------------------------------|------------------------|
| Positive | `.status-positive` | `w-2.5 h-2.5 rounded-full bg-emerald-700`  | `ri-checkbox-circle-fill text-emerald-700` |
| Negative | `.status-negative` | `w-2.5 h-2.5 rounded-full bg-rose-800`     | `ri-close-circle-fill text-rose-800`       |
| Warning  | `.status-warning`  | `w-2.5 h-2.5 rounded-full bg-orange-500`   | `ri-alert-fill text-orange-500`            |
| Neutral  | `.status-neutral`  | `w-2.5 h-2.5 rounded-full bg-gray-300`     | `ri-checkbox-blank-circle-fill text-gray-300` |

Usage: `<span class="status-dot status-positive"></span>`

### Inline Status — icon + text (user supplies only the copy)

These classes bundle icon, colour, and sizing. You just write the text — the icon appears automatically.

| State    | Semantic Class      | Icon (auto)                  | Colour       |
|----------|--------------------|-----------------------------|--------------|
| Positive | `.inline-positive` | `ri-checkbox-circle-fill`   | Emerald-700  |
| Negative | `.inline-negative` | `ri-close-circle-fill`      | Rose-800     |
| Warning  | `.inline-warning`  | `ri-alert-fill`             | Orange-500   |

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

## Icons (Remix Icons)

Use [Remix Icons](https://remixicon.com/) via CDN. Each icon has `-line` (outlined) and `-fill` (solid) variants. Prefer `-line` for wireframes; use `-fill` for active/selected states.

### Recommended Prototype Icons

| Purpose       | Icon Class              | Preview |
|---------------|------------------------|---------|
| Home          | `ri-home-line`         | Home    |
| Search        | `ri-search-line`       | Search  |
| User/Profile  | `ri-user-line`         | User    |
| Settings      | `ri-settings-3-line`   | Gear    |
| Menu          | `ri-menu-line`         | Hamburger |
| Close         | `ri-close-line`        | X       |
| Add/Create    | `ri-add-line`          | Plus    |
| Edit          | `ri-pencil-line`       | Pencil  |
| Delete/Trash  | `ri-delete-bin-line`   | Trash   |
| Check/Success | `ri-check-line`        | Check   |
| Warning       | `ri-alert-line`        | Alert   |
| Info          | `ri-information-line`  | Info    |
| Error         | `ri-error-warning-line`| Error   |
| Arrow Right   | `ri-arrow-right-line`  | Arrow   |
| Arrow Left    | `ri-arrow-left-line`   | Arrow   |
| Chevron Down  | `ri-arrow-down-s-line` | Chevron |
| Notification  | `ri-notification-line` | Bell    |
| Calendar      | `ri-calendar-line`     | Calendar|
| Download      | `ri-download-line`     | Download|
| Upload        | `ri-upload-line`       | Upload  |

### Icon Sizing

| Size    | Class       | Usage                         |
|---------|-------------|-------------------------------|
| Small   | `text-base` | Inline with body text         |
| Medium  | `text-xl`   | Buttons, list items           |
| Large   | `text-3xl`  | Feature icons, empty states   |
| XLarge  | `text-5xl`  | Hero icons, modal status      |

Icon colour follows the same rules as text — grey by default, accent colours only for status meaning.

---

## Spacing

| Token              | Value    | Usage                                    |
|--------------------|----------|------------------------------------------|
| `spacing-page`     | `p-4`   | Page-level padding                       |
| `spacing-section`  | `gap-6` | Gap between major sections               |
| `spacing-items`    | `gap-3` | Gap between related items (e.g. buttons) |
| `spacing-internal` | `p-4`   | Internal padding for containers          |

---

## Transitions & Animations

| Token                  | Duration | Easing         | Usage                              |
|------------------------|----------|----------------|------------------------------------|
| `transition-fast`      | 150ms    | `ease-in-out`  | Hover states, colour changes       |
| `transition-standard`  | 200ms    | `ease-out`     | Element appear/disappear           |

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

| Element      | Semantic Class | Definition                                   |
|-------------|---------------|----------------------------------------------|
| Brand text  | `.navbar-brand` | `font-bold text-zinc-800 text-lg`          |
| Nav link    | `.navbar-link`  | `text-zinc-600 hover:text-zinc-900 text-base` |

---

## Footer — `.footer`

Page footer with copyright and links.
```
bg-zinc-800 text-zinc-400 px-8 py-6
flex items-center justify-between text-sm
```
Footer links: `.footer-link` — `hover:text-white transition-colors duration-150`

---

## Progress Bar

Greyscale track with emerald fill for progress indication.

| Element | Semantic Class   | Tailwind                                     |
|---------|-----------------|----------------------------------------------|
| Track   | `.progress-track` | `bg-stone-200 rounded-full h-2 w-full`     |
| Fill    | `.progress-fill`  | `bg-emerald-700 rounded-full h-2`          |

Use inline style for dynamic width: `style="width: 50%"`.

---

## Step Indicators

Used in procedural modals for multi-step flows.

| Element    | Semantic Class   | Tailwind                                                    |
|-----------|-----------------|-------------------------------------------------------------|
| Active    | `.step-active`   | `w-7 h-7 rounded-full bg-emerald-700 text-white text-sm font-bold` |
| Inactive  | `.step-inactive` | `w-7 h-7 rounded-full bg-gray-300 text-zinc-500 text-sm font-bold` |
| Connector | `.step-connector`| `w-8 h-0.5 bg-gray-300`                                    |

---

## Layout Utilities

Semantic classes for page structure (used in showcase, reusable in projects):

| Element       | Semantic Class      | Tailwind                                          |
|--------------|--------------------|----------------------------------------------------|
| Page body    | `.page-bg`         | `bg-stone-50 text-zinc-700`                       |
| Section divider | `.section-divider` | `border-b-4 border-zinc-800`                   |
| Section label | `.section-label`   | `bg-zinc-700 text-white px-8 py-2`               |
| Label text   | `.section-label-text` | `text-sm font-bold tracking-widest uppercase`  |
