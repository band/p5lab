# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static website for p5lab.net, the Praxis101 laboratory for work and play. The site is built using the Skeleton CSS framework (version 2.0.4), a minimal responsive boilerplate. This is a personal website with historical/archival content rather than an active development project.

## Architecture

### Directory Structure

- **Root `index.html`**: Main landing page for p5lab.net
- **`public/`**: Contains an alternative/historical version of the Praxis101 site
  - `public/index.html`: Different landing page emphasizing "present and past"
  - `public/works/`: PDF documents and other work artifacts
- **`blogs/`**: Blog index page that links to external blog archives
- **`css/`**: Styling files
  - `normalize.css`: CSS reset/normalization
  - `skeleton.css`: Core Skeleton framework grid and components
  - `custom.css`: Site-specific customizations
- **`images/`**: Site images including favicon and photos
- **`Skeleton-gh-pages/`**: Reference copy of the original Skeleton framework (for reference only, not actively used)

### Multiple Entry Points

This site has multiple HTML entry points that serve different purposes:
- `/index.html` - Current p5lab landing page
- `/public/index.html` - Historical Praxis101 page with different navigation
- `/blogs/index.html` - Simple blog archive link page

All three pages use the same CSS framework but have different content focuses and navigation structures.

### JavaScript

The site references `js/site.js` in the root `index.html`, but this file doesn't exist in the repository root. The JavaScript functionality (smooth scrolling, sticky nav, popovers) is borrowed from the Skeleton reference implementation at `Skeleton-gh-pages/js/site.js`. If JavaScript features are needed, copy this file to a `js/` directory in the root.

The site.js provides:
- Smooth scrolling for anchor links
- Sticky navigation on scroll
- Popover menus (used in "More?" navigation item)
- Code snippet HTML escaping

### Dependencies

- **Skeleton CSS Framework** (v2.0.4): Minimal responsive grid system
- **jQuery** (2.1.1): Loaded from CDN for site.js functionality
- **Google Fonts**: Raleway font family
- **Google Code Prettify**: Code syntax highlighting (referenced but may not be actively used)

All dependencies are loaded from CDNs; there is no package.json or build system.

## Development

This is a static HTML site with no build process or development server required.

### Local Development

Open HTML files directly in a browser, or use any static file server:

```bash
python -m http.server 8000
# or
python3 -m http.server 8000
```

Then navigate to `http://localhost:8000`

### Editing Content

- HTML files can be edited directly
- CSS customizations go in `css/custom.css`
- The site uses inline styles minimally; prefer CSS classes

### Deployment

This appears to be deployed as a static site. Simply update HTML/CSS files and push changes. No build step required.

## Important Notes

- This is an archival/personal website, not an active application
- The `Skeleton-gh-pages/` directory is a reference copy and should not be modified
- The site has legacy dependencies (jQuery 2.1.1, old Google Prettify URL)
- Multiple HTML files may need updating if making site-wide navigation changes
- The `js/site.js` file is referenced but missing from root - copy from `Skeleton-gh-pages/js/site.js` if needed
