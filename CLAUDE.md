# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static portfolio website for Ulises Rönnau, hosted on GitHub Pages at `ulisesroennau.com`. No build process, no dependencies, no framework — pure HTML/CSS/JavaScript.

## Development

Since this is a static site, open `index.html` directly in a browser or use a local server:

```bash
# Simple local server (Python)
python3 -m http.server 8000

# Or with npx
npx serve .
```

There are no build, lint, or test commands.

## Architecture

**Component loading:** HTML "includes" (navbar, footer) are loaded at runtime via `fetch()` and injected into the DOM. Each page fetches its own variant (e.g., `navbar.html`, `navbar-project.html`, `navbar-services.html`) from the `includes/` directory.

**Project data:** `projects.json` drives the portfolio grid on `index.html`. Projects are rendered dynamically via JS — to add a new project, add an entry to `projects.json` and create a corresponding HTML file in `projects/`.

**CSS architecture:** Three stylesheets, each scoped to a page type:
- `css/style.css` — main/homepage
- `css/services_style.css` — service detail pages
- `css/project_style.css` — project detail pages

**Contact form:** Submits via Google Apps Script (not a backend — just a POST to a Google Sheets endpoint). The script URL is hardcoded in `index.html`.

**Design tokens:** Dark theme with `#080808` background and `#7BAFD4` accent blue. Mobile breakpoint at `800px`. Font: Poppins (Google Fonts CDN).

## Key Files

- `index.html` — homepage with all main sections (hero, about, services, portfolio, contact)
- `projects.json` — project metadata (name, description, link, image)
- `includes/` — reusable nav/footer HTML fragments
- `services/` — individual service pages (time series, math tutor, custom websites)
- `projects/` — individual project detail pages
- `images/UlisesRonnau_Multilingual_AI_Engineer.pdf` — linked resume
