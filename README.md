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
| `index.html` | Marketing / landing | **Mostly real**: hero, the eight key features, the organized-collecting warning, and the measured storage section. Still needs screenshots, the App Store badge + link, and hero art |
| `scenarios.html` | Collector scenarios | Seven stories. Six are grounded in built features (kiosk, Scan a Stack, dealer transfer, box audit, auction pack, search-by-image). **LAUNCH BLOCKER on the seventh:** the buying scenario describes **Evaluate a stack**, DESIGNED but not built (app repo `docs/features/evaluations-and-offers.md`). The page promises no hypotheticals, so that feature ships before the site goes public or the paragraph comes out. |
| `about.html` | The origin story | **REAL**: thousands of comics, three questions, three requirements, plus the BigBrainCorp mission verbatim |
| `faq.html` | FAQ | **Part real**: capacity, grading accuracy, and pricing answered; privacy and accounts still stubs |
| `support.html` | **ASC Support URL** | Contact live (Info@BigBrainCorp.com); intro stub |
| `help.html` | The user guide (How To) | Stub, section skeleton only |
| `privacy.html` | **ASC Privacy Policy URL** | **REAL** (2026-08-24): written against what the code actually does, verified claim by claim. Worth a lawyer's read before launch; the App Privacy questionnaire answers must match it |
| `terms.html` | Terms / EULA | Stub, and OPTIONAL: Apple's Standard EULA governs by default. Kept for the estimates disclaimer and credit terms |
| `release-notes.html` | Changelog | Stub, starts real at the first TestFlight build |
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
- **Keyword targeting** (2026-08-24): titles and descriptions aim at
  *comic book inventory app*, *comic collection app*, *catalog comic
  collection* and neighbours, NOT at the bare phrase "too many
  comics". The .com is an unrelated comics podcast with years of
  indexed content; that fight is unwinnable and unnecessary, because
  the queries that convert (comic inventory app, comic collection
  tracker) are ones a podcast does not compete for at all. The home
  page H1 stays Jim's brand line; a keyword-bearing H2 above the
  feature grid carries the phrase instead, so voice and search each
  get what they need.
- **`sitemap.xml`** carries `lastmod`/`changefreq`/`priority` per URL,
  OSSScan's shape. Update `lastmod` when a page changes materially.

## The home page's scenario teaser

`index.html` carries a nine-item teaser linking into `scenarios.html`
by anchor. The anchors are stable, human-readable slugs on each
`div.scenario` (`#convention-table`, `#hot-books`, and so on), chosen
by hand rather than derived from headlines so that rewording a
headline cannot break a link.

The teaser was GENERATED from scenarios.html so the two agreed on the
day it was built. They can drift: **if you add, remove, or retitle a
scenario, update the teaser and the "Read all nine" count to match.**

## Screenshots (when they're shot)

Comic covers in screenshots are somebody else's copyright, so the
policy lives in Functions repo `docs/Phase2-Deploy.md` §4a. The short
version: these go on OUR site, not into App Store Connect, so there is
no App Review exposure; keep covers inside the phone frame and never
as decorative banner art; use verified public domain Golden Age covers
for the single-cover hero shots (Advanced Grading, detail,
search-by-image); Jim's own photos are fine for grid and browse
screens; swap the sample seeder's real series names first; and keep
sources organized so any one image can be replaced in five minutes.

## Screenshot retake list (2026-09-07)

The criterion is **not current**, not "shot with Display Zoom on" (they
all were, and that alone is not a reason). An image is stale when it
shows something the app no longer does. Checked 2026-09-07 against every
image on the site: the one visible change is the title rules, which
landed after these were shot, so any list that mixes "BATMAN" with
"Batman" or "THE TOMB OF DRACULA" with "The Tomb of Dracula" is showing
a library the app has since cleaned up. Ten images do; one more is a
bad file. Everything else stays, `credits-screen.png` included (redone
2026-09-07).

**How each retake lands:** AirDrop the original to Downloads, hand over
the IMG number. Processing is: resize to 750 wide, JPEG for camera-heavy
frames and PNG for flat UI, crop any stray bottom text, update the
`width`/`height` attributes and the alt text on every page that uses it,
delete the raw. One copy per picture.

| File | Pages | What is stale | Shoot |
|---|---|---|---|
| `admin-review.jpg` | admin how-to | **Done 2026-09-07**: 1,279 books, consistent titles, the new filter row, the side panel on All-Star Comics #63 | The how-to still has no paragraph on series rows |
| `after-the-show-1.jpg` | after-the-show scenario | **Done 2026-09-07** | |
| `after-the-show-3.jpg` | after-the-show scenario, accuracy how-to | **Done 2026-09-07**: CB-2, 115 confirmed, 3 not seen (and -2 retaken with it) | |
| `after-the-show-5.jpg` | after-the-show scenario | **Done 2026-09-07** | |
| `after-the-show-6.jpg` | after-the-show scenario, accuracy how-to | **Done 2026-09-07** | |
| `ballpark-run-1.jpg` | ballpark how-to | "The Tomb of Dracula" then "THE TOMB OF DRACULA", "Marvel Comics Group" then "MARVEL" | A freshly scanned box, graded, unpriced |
| `barcoding-1.jpg` | barcoding how-to | "WEREWOLF BY NIGHT" rows behind the menu | Box menu open with Print box labels and Mark box as labeled |
| `backup-reminder.jpg` | sharing how-to | "WEREWOLF BY NIGHT" above "Werewolf By Night", and a 50,000-book test library | Collections screen with the Backup due banner; a real collection behind it |
| `convention-table-2.jpg` | convention-table scenario | Kiosk cards read "THE TOMB OF DRACULA", publishers "MARVEL COMICS GROUP" and "MARVEL" | Desktop: re-export the kiosk (it also gained label QR codes on 2026-08-29), search "Tomb", screenshot |
| `export-1.jpg` | sharing how-to | "KNIGHT · MARVEL COMICS GROUP" beside "Meta-morpho The Element Man" | Selection mode, three checked, menu open on Export 3 selected |
| `voice-scan-1.jpg` | scanning how-to | Not stale, just 360 × 778: the weakest file on the site | Voice scan mid-session, New comic badge, a spoken comment transcribed under the book |

Close calls that stay: `ballpark-run-3/4/5` show only the "The Tomb of
Dracula" rows behind their sheets; `back-issue-bin-1` shows three
"Action Comics" rows (its caption's "841 books" is out of date, the
picture is not); `after-the-show-4` is a menu with no titles.

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
