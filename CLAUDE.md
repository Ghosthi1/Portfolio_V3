# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Workflow

- **Always ask before creating new files, components, or sections.** Describe what you plan to build and wait for confirmation before writing any code.

## Project Purpose

Professional CS grad portfolio for **Callum Forsyth**. Focus areas: **Rust**, **game development**, and **embedded systems**.

Design: minimal dark theme — `bg-gray-900` (#111827), `text-gray-50` (#f9fafb), orange accent (`#f97316` / `text-orange-500`). Fonts: Inter (body) + JetBrains Mono (code/labels), loaded via Google Fonts.

## Commands

```bash
npm run dev       # start dev server at localhost:4321
npm run build     # production build to ./dist
npm run preview   # preview production build locally
```

## Stack

- **Astro 6** with TypeScript (strict mode)
- **Tailwind CSS v4** via `@tailwindcss/vite` — configured in `src/styles/global.css` using `@theme`
- No UI framework — plain Astro components only

## Component Structure

```
src/
  layouts/
    Layout.astro        # HTML shell — Google Fonts, meta tags, global CSS import
  components/
    Nav.astro           # Fixed frosted-glass nav with anchor links
    Hero.astro          # Name, tagline, bio, CTA buttons
    Projects.astro      # Project cards grid — edit the `projects` array at the top
    Skills.astro        # Skill groups — edit the `skillGroups` array at the top
    About.astro         # Bio paragraphs, terminal card, social links, footer
  pages/
    index.astro         # Assembles all components — single page
  styles/
    global.css          # Tailwind import + @theme (font vars) + base body styles
public/
  CV.pdf               # Place CV here when ready
```

## Projects (current)

All project data lives in the `projects` array in `Projects.astro`. Each entry has:
- `title`, `description`, `tags[]`, `github` (string or null), `demo` (string or null), `wip?` (boolean)

Current projects:
1. **Sprite Sheet CLI** — Rust CLI, bin-packing sprite atlas tool
2. **The Last Vestige** — Rust/Bevy top-down colony builder/defender
3. **Haunted Cottage Diorama** — WebGPU/WGSL group uni graphics project
4. **Barrel** — C#/Unity destructible props asset pack (WIP)
5. **USB HID Controller** — Rust/Embassy firmware on Raspberry Pi Pico (WIP, no GitHub yet)

## Skills (current)

All skill data lives in the `skillGroups` array in `Skills.astro`.

- **Languages:** Rust, C#, JavaScript
- **Game Dev:** Bevy, Unity, WebGPU, WGSL, ECS Architecture
- **Embedded:** Raspberry Pi Pico, Embassy, USB HID
- **Tooling:** Git, Linux, Cargo

## Architecture Notes

- Astro components use a fenced frontmatter block (`---`) for server-side logic, followed by the HTML template
- Client-side JS requires explicit `client:*` directives — none currently used
- `wip: true` on a project card renders a yellow WIP badge next to the title
- `github: null` hides the GitHub icon on a card