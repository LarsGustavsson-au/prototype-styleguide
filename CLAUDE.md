# Prototype Wireframe Style Guide

## Project Purpose

This is a reusable Balsamiq-inspired wireframe style guide for rapid prototyping. It defines a greyscale visual language with sparse colour accents, intended to be copied into real prototype projects as a starting kit.

## Key Files

- `PLAN.md` — Implementation plan with phases, decision log, and checkboxes
- `style-guide.md` — Single source of truth for all design tokens (colours, typography, buttons, components, spacing, icons)
- `showcase.html` — Single-page visual reference that renders all style guide tokens. Includes all mockup sections (landing page, form, modals) and can be opened directly in a browser.

## Design Principles

- **Greyscale first**: All UI elements use Tailwind grey shades by default
- **Sparse colour**: Only 3 accent colours, used for meaning only:
  - `emerald-700` (#047857) — primary actions, positive status
  - `rose-800` (#9f1239) — negative/error actions, negative status
  - `orange-500` (#f97316) — warning status lights only
- **Wireframe aesthetic**: Balsamiq Sans font (Google Fonts CDN), lo-fi prototype feel
- **Token discipline**: All visual decisions live in `style-guide.md`. Mockups and showcase only reference tokens — never define their own styles.

## External Dependencies (CDN only)

- **Tailwind CSS**: via CDN `<script>` tag
- **Balsamiq Sans**: via Google Fonts `<link>` tag
- **Remix Icons**: via CDN `<link>` tag

No build tools, no npm, no bundler. Everything runs from a single HTML file opened in a browser.

## User Context

The user (Lars) is a **product manager**, not a developer. He has a solid understanding of timeless programming concepts from 30 years old experience, but is not well-versed in modern tooling like Tailwind CSS, GitHub workflows, npm, or current frontend frameworks. When communicating:

- **Explain the "why"**, not the syntax — he gets the concepts, just not the tool-specific details
- **Avoid jargon** like "utility classes", "CDN", "build pipeline" without brief context
- **Show visual results** whenever possible — screenshots and rendered output are more useful than code snippets
- **Don't assume he knows** git commands, Tailwind class naming conventions, or how to open dev tools
- **Do assume he understands** software architecture, design patterns, data structures, and can reason about trade-offs

## Working Rules for AI Sessions

1. **Read \****`style-guide.md`**\*\* first** before making any visual changes
2. **Never hardcode colours or sizes** in HTML — always use the Tailwind classes defined in the style guide
3. **Style changes go through \****`style-guide.md`**\*\* only** — update the token there first, then update the showcase
4. **Check PLAN.md** for current progress and next steps
5. **Keep it simple** — no frameworks, no build steps, no JS except minimal modal toggling
6. **Recommended model**: Sonnet 4.5 is sufficient for all styling and HTML work on this project

## How to Reuse This Kit

To use this style guide on a new prototype project:
1. Copy `style-guide.md` and `showcase.html` into the new project
2. Create a project-specific `CLAUDE.md` that references the style guide
3. Adapt the colour accents if needed (but keep the greyscale-first principle)
4. Use the showcase as a component reference while building screens
