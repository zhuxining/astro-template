# Copilot Instructions for Astro Template

## Project Overview
This is an Astro 5.x project using Bun as the package manager, with TailwindCSS 4.x (Vite plugin), DaisyUI components, and TypeScript strict mode enabled. The project follows Astro's file-based routing system and component architecture.

## Architecture & Key Patterns

### File-Based Routing
- Pages in `src/pages/` automatically become routes (e.g., `src/pages/posts/post1.md` → `/posts/post1`)
- Markdown files in pages support frontmatter for metadata and are rendered as HTML
- Use `.astro` extensions for component files with JSX-like syntax and script blocks

### Component Structure
- Layouts wrap pages: `src/layouts/Layout.astro` provides base HTML structure
- Components use Astro's syntax: script block `---` at top, then template HTML
- Import assets directly: `import astroLogo from "../assets/astro.svg"` gives you `{astroLogo.src}`
- Use `<slot />` in layouts to render child content

### Styling Strategy
- TailwindCSS 4.x configured via Vite plugin (no config file needed)
- Global styles in `src/styles/global.css` with `@import "tailwindcss"`
- DaisyUI provides component classes on top of Tailwind
- Typography plugin available via `@plugin '@tailwindcss/typography'`

## Development Workflow

### Essential Commands (use Bun)
```bash
bun dev          # Start dev server on localhost:4321
bun build        # Build to ./dist/ 
bun preview      # Preview production build locally
bun astro add    # Add integrations (e.g., bun astro add react)
```

### Content Management
- Markdown pages support frontmatter (title, pubDate, description, author, image, tags)
- Chinese content is supported (see `src/pages/posts/post1.md` example)
- Astro automatically handles asset optimization and imports

## Project-Specific Conventions

### Asset Handling
- SVG assets in `src/assets/` are imported as objects with `.src` property
- Use `fetchpriority="high"` for above-the-fold images (see `Welcome.astro`)
- Favicon goes in `public/favicon.svg` (served at root)

### TypeScript Configuration
- Extends `"astro/tsconfigs/strict"` for maximum type safety
- All files in workspace included except `dist/`
- Astro generates `.astro/types.d.ts` automatically

### Integration Points
- Sitemap integration configured for SEO (`@astrojs/sitemap`)
- TailwindCSS integrated via Vite plugin, not PostCSS
- No build step required for CSS - Tailwind processes during Astro build

## Key Files to Reference
- `src/components/Welcome.astro` - Complex component with inline styles and SVG handling
- `src/pages/index.astro` - Simple page composition pattern
- `astro.config.mjs` - Integration setup and Vite configuration
- `src/styles/global.css` - CSS plugin loading pattern
