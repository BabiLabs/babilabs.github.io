# Phase 4.1 validation — 7 November 2026

## Completed

- Two English static pages, shared local CSS and original game branding.
- Audit and app source reviewed before writing; sources and remaining privacy
  questions documented in README.md and the public policy.
- HTML checked for balanced nesting, one H1, English language, unique IDs,
  image alternative text and absence of scripts, event handlers and embeds.
- All local routes, assets and fragment targets resolve to existing files/IDs.
- All five external provider policy URLs returned HTTP 200.
- Chromium 153 with actual emulated widths of 320, 390, 768 and 1440 CSS pixels:
  both pages have no horizontal overflow, loaded fonts and logo. FAQ summary
  clicks open answers at every tested width. Mobile and desktop screenshots
  were inspected. No JavaScript from the QA tools is included in the pages.
- No tracking, cookies, analytics, remote assets or runtime dependencies added.
- `git diff --check` passed.

## Hosting

GitHub Pages API: public, main branch root, HTTPS enforced, no custom domain.
The root site returned HTTP 200. Existing babilabs.com product URLs redirected to
Squarespace and returned HTTP 404 for both privacy and support. Domain settings
were not changed.

Deployment and final route verification are recorded below after publishing.
