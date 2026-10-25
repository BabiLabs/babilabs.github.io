# SportiPlan website simplification — 25 October 2026

## Result

Exactly three content pages: `privacy/index.html`, `legal/index.html`,
`support/index.html`. Each contains complete English and Turkish sections at
`#english` and `#turkce`. English is the default. Uses the existing StilPlan
stylesheet/layout with SportiPlan colours and MPM-style in-page language links.
No separate translation architecture or application dependencies added.

## Removed content pages

Marketing/product landing pages, all German translations, separate Turkish
content files and the separate product-terms pages. Historical files now contain
only compatibility redirects; there are no German translation texts or navigation
links left. No changes to StilPlan, My Private Museum or their shared assets.

## Compatibility redirects

GitHub Pages-compatible immediate HTML meta refresh, canonical target and visible
fallback link. These are client-side redirects, not HTTP 301 responses.
All target a content page directly; there are no redirect chains.
Both directory URLs and explicit `index.html` URLs continue to resolve.

| Previous route under `/sporti-plan/` | Destination |
| --- | --- |
| `/` | `support/` |
| `terms/` | `legal/#english` |
| `tr/` | `support/#turkce` |
| `tr/privacy/` | `privacy/#turkce` |
| `tr/legal/` | `legal/#turkce` |
| `tr/support/` | `support/#turkce` |
| `tr/terms/` | `legal/#turkce` |
| `de/` | `support/#english` |
| `de/privacy/` | `privacy/#english` |
| `de/legal/` | `legal/#english` |
| `de/support/` | `support/#english` |
| `de/terms/` | `legal/#english` |

## App and store link inventory

Source inspected: `lib/features/about/domain/public_links.dart`,
`about_legal_section.dart`, `product_settings_screen.dart`, entitlement/purchase
sources, all HTTP(S) references in `lib`, and `docs/store_listing.md`.
The settings About/Legal section uses these exact public links:

| Purpose | URL |
| --- | --- |
| Privacy | `https://babilabs.github.io/sporti-plan/privacy/index.html` |
| Legal | `https://babilabs.github.io/sporti-plan/legal/index.html` |
| Support | `https://babilabs.github.io/sporti-plan/support/index.html` |

The store-listing document records the same three URLs. No separate terms URL
was found in the active app, licence management or purchase screens. Other
network URLs found concern Connect's local transport, not legal pages.
No Flutter files changed; app translations, billing, entitlements, Connect and
member/data management are unaffected.

Actual Play Console/App Store Connect metadata was unavailable to this session;
its account configuration was not verified. Existing route preservation protects
any references to all 15 previously present page paths. The public root, privacy,
legal and support URLs were requested through the web tool, which reported them
inaccessible; this is not evidence that the site is down. Local source/routes
were verified; live HTTP response status remains unconfirmed.

## Contractual information

All seven former terms sections in both retained languages are incorporated into
Legal Notice: licence, offers/one-time purchases, responsible use, devices and
backups, product purpose/external services, consumer rights/liability, and changes.
No required information was discarded with the old terms route. The document
continues to avoid claiming automatic contractual acceptance. Apple's Standard
EULA remains linked; no replacement custom Apple EULA was introduced.
No additional standalone legal page is introduced by this change.

## Validation

Passed using Python's HTML parser and explicit route/content assertions:

- Three content pages, each with EN/TR sections and working language anchors.
- Twelve direct redirects; all targets, canonical URLs, local links, fragments,
  stylesheet and icon resolve within the prepared tree.
- Exactly one main heading per content page and unique IDs.
- No German language sections/navigation, separate translation content, script,
  iframe or embedded remote resources.
- All three app URLs reach content without a redirect.
- Licence/offer information retained in both language sections of Legal Notice.
- Existing mobile breakpoint and added wrapping rules checked in CSS. Header and
  footer navigation wrap; page widths remain responsive.

No browser was installed, so no visual viewport/screenshot, real mobile or
screen-reader verification was performed. Flutter tests were not run because no
Flutter source changed. Whitespace validation and change-scope checks were run
in the website repository before the local commit.

Requested delivery: local commit only. No push, deployment or store-account edits.
