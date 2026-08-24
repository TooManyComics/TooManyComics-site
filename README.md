# TooManyComics-site

The standalone website for **Too Many Comics** (the iOS comic-collection
app; repos `CBInventory` + `CBInventory.Functions` — the code keeps the
old name, the brand is user-facing only). Same approach as
`OSSScan-site`: hand-written static HTML, one self-contained file per
page, no build step, served by GitHub Pages with a `CNAME`.

Canonical host: **https://www.toomanycomics.app/** (domain purchased
2026-08-23, BigBrainCorp registrar account). The site is linked from
bigbraincorp.com's product tab; `toomanycomics.com` is an unrelated
podcast and stays that way.

The release plan that drives this site is Functions repo
`docs/Phase2-Deploy.md` §4 — its checklist §D tracks these pages, and
two of these URLs become **permanent App Store Connect fields**
(Support, Privacy Policy), which is the real deadline for de-stubbing.

## Pages and stub status

| Page | Becomes | Status |
|---|---|---|
| `index.html` | Marketing / landing | Stub — copy drafted; needs screenshots, App Store badge + link, hero art |
| `about.html` | The origin story (why I built it) | **REAL** (2026-08-23, Jim's story: thousands of comics, three questions, three requirements) |
| `scenarios.html` | Collector scenarios (life-with-the-app stories) | **REAL** (2026-08-23: the convention kiosk, the back-issue-bin own-check; both grounded in built features — the ~/Kiosk export and search-by-image). Grows as scenarios are written |
| `help.html` | The user guide (How To) | Stub — section skeleton only |
| `faq.html` | FAQ | Stub — seed questions only |
| `support.html` | **ASC Support URL** | Contact live (Info@BigBrainCorp.com); intro stub |
| `privacy.html` | **ASC Privacy Policy URL** | DRAFT skeleton — accurate architecture, needs full pass before ASC |
| `terms.html` | Terms / EULA | Stub — Apple-standard-vs-custom decision pending |
| `release-notes.html` | Changelog | Stub — starts real at first TestFlight build |
| `blog/` | Same as OSSScan-site | Empty |

## Contacts

No toomanycomics.app mailboxes exist, deliberately: public contact is
**Info@BigBrainCorp.com** (on support.html); **Jim@BigBrainCorp.com**
is the App Store Connect / registrar / internal contact. Same pattern
as the parent site.

## Mobile and SEO

Same principles as `OSSScan-site`, verified in a real browser at 375px
and 320px (no sideways scroll at either):

- **Breakpoints at the end of each page's `<style>`**, where source
  order lets them win: `max-width: 700px` for phones, `max-width:
  374px` for the SE and Display Zoom.
- **The nav wraps to its own row rather than hiding.** OSSScan hides
  its nav links on phones because it keeps a Buy button; this is a
  content site, so a phone reader still needs How To, FAQ and Support.
- **Tap targets**: nav and footer links carry vertical padding to
  ~40px. Bare text links measured 16px, which is not tappable.
- **Per page**: exactly one `<h1>`, canonical URL, description, full
  Open Graph and Twitter card, `theme-color`, and explicit logo
  width/height so nothing shifts as it loads.
- **Structured data**: `MobileApplication` on the home page,
  `FAQPage` on the FAQ. The FAQ schema is generated from the ANSWERED
  questions only, since publishing a stub as an answer would be both
  wrong and a rich-results risk. No `aggregateRating` anywhere: there
  are no ratings yet, and inventing them invites a manual action.
- **`sitemap.xml`** carries `lastmod`/`changefreq`/`priority` per URL,
  OSSScan's shape. Update `lastmod` when a page changes materially.

## Binary assets

`logo.png` (256), `apple-touch-icon.png` (180), `favicon-32.png`,
`favicon-16.png` — all derived 2026-08-23 from the app icon (the box
of comics, `CBInventory/ios/.../AppIcon.appiconset/icon-1024.png`);
re-derive with `sips -Z <size>` if the app icon changes.
`favicon.ico` is currently a copy of the 32px PNG (all modern browsers
content-sniff it; swap for a real multi-size .ico someday if it
bothers anyone). `og-image.png` is the 1200x630 social card: the app
icon padded onto the brand purple with `sips`.

## Hosting setup (once, when going live)

1. Create the GitHub repo, push, enable Pages (deploy from `main`).
2. DNS at the registrar: `www` CNAME → `<github-user>.github.io`;
   apex `toomanycomics.app` → ALIAS/A to GitHub Pages IPs, or redirect
   to `www`.
3. Pages settings: custom domain `www.toomanycomics.app`, enforce
   HTTPS (the `.app` TLD requires it anyway).
4. Verify every page over HTTPS, then — and only then — put the
   Support and Privacy URLs into App Store Connect.
