# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build & Development

```bash
# Install dependencies
bundle install

# Start local dev server (http://localhost:4000)
bundle exec jekyll serve

# Build for production
bundle exec jekyll build
```

`_site/` is the build output directory — never edit files here.

## Architecture

This is a Jekyll-powered personal academic website deployed via GitHub Pages. The `github-pages` gem in the Gemfile pins the Jekyll version and available plugins to what GitHub Pages supports.

### Pages and layouts

All content pages are flat Markdown files (e.g., `index.md`, `blog/index.md`, `research/index.md`) with YAML frontmatter for `title`. The default layout (`_layouts/default.html`) wraps every page automatically via the `defaults` block in `_config.yml`.

Blog posts with syntax highlighting can use a `blog` layout — the default template conditionally loads highlight.js only when `page.layout == 'blog'`.

### Frontmatter

`_config.yml` sets `kramdown` with GFM input for Markdown processing and configures Google Analytics (GA4). Pages only need a `title` field in their frontmatter.

### Theming

Dark/light theme is implemented with CSS custom properties on `:root` and `:root[data-theme="dark"]`. JavaScript in `_layouts/default.html` reads/writes `localStorage.getItem('theme')` and respects `prefers-color-scheme` on first visit. The theme toggle button is part of the nav.

### CSS

`css/main.css` controls all styling. Variables (colors, backgrounds, code blocks) are defined in `:root` (light) and `:root[data-theme="dark"]`. Responsive styles at `max-width: 1080px` scale font sizes up for mobile/tablet.
