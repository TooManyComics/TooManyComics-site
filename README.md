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

## Missing binary assets (TODO before launch)

`logo.png`, `favicon.ico`, `favicon-16.png`, `favicon-32.png`,
`apple-touch-icon.png`, `og-image.png` (1200×630). The app's icon art
is the obvious source. Pages reference these paths already.

## Hosting setup (once, when going live)

1. Create the GitHub repo, push, enable Pages (deploy from `main`).
2. DNS at the registrar: `www` CNAME → `<github-user>.github.io`;
   apex `toomanycomics.app` → ALIAS/A to GitHub Pages IPs, or redirect
   to `www`.
3. Pages settings: custom domain `www.toomanycomics.app`, enforce
   HTTPS (the `.app` TLD requires it anyway).
4. Verify every page over HTTPS, then — and only then — put the
   Support and Privacy URLs into App Store Connect.
