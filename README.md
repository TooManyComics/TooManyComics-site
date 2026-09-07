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

Every phone screenshot on the site except `credits-screen.png` was taken
with **Display Zoom on** (the 750 × 1624 ratio is the tell; a regular
15 Pro frame lands at 750 × 1626). Regular zoom shows more of each screen
per frame and matches the App Store set, and several screens have new
copy since these were shot (the em-dash sweep). Five desktop shots
(`barcoding-3`, `convention-table-1/2/3`, `listing-desk-5`) are
unaffected and stay; `admin-review.jpg` is a retake for a different
reason (section I).

**How each retake lands:** Display Zoom off, shoot, AirDrop the original
to Downloads, hand over the IMG number. Processing is: resize to 750
wide (750 × 1626), JPEG for camera-heavy frames and PNG for flat UI, crop
any stray bottom text, update the `width`/`height` attributes and the alt
text on every page that uses it, then delete the raw. One copy per
picture.

**Reuse before reshoot.** Seven App Store frames in
`CBInventory/docs/AppStore-Legal/screenshots/` are the same screens at
regular zoom on public-domain books; downscaling them to 750 wide is a
retake for free. Where the page's copy quotes numbers from the old
picture, the copy changes with it (noted per row).

**Em dashes in app strings are not a gate for these retakes** (Jim,
2026-09-07). Some screens still show them; shoot anyway, and any later
app fix will simply make the next retake read differently.

### A. Capture and review (`howto/scanning-your-first-box`, `index`)

| File | Pages | Shoot | Notes |
|---|---|---|---|
| `capture-screen.jpg` | index hero, scanning how-to | **Reuse store 01** (Fight Comics #1 under the camera, box "Golden Age") | Alt and caption on both pages name Werewolf by Night #13; change to Fight Comics #1 |
| `voice-scan-1.jpg` | scanning how-to | Voice scan mid-session: New comic badge, a spoken comment transcribed beneath the book | Only 360 × 778 today, the weakest file on the site. |
| `capture-review.png` | scanning how-to | A book's record right after capture: collection and box, then the Identity fields | |
| `zoom-in.jpg` | scanning how-to | Full-screen photo viewer, "Cover, photo 1 of 1" | A Fight Comics cover keeps the page consistent with the new hero |

### B. Ballpark values (`howto/ballpark-values`, `faq`)

| File | Pages | Shoot | Notes |
|---|---|---|---|
| `ballpark-run-1.jpg` | ballpark how-to | A freshly scanned box, graded but unpriced |  |
| `ballpark-run-3.jpg` | ballpark how-to | The Instant Ballpark Value sheet with N selected and the Estimate button | |
| `ballpark-run-4.jpg` | ballpark how-to | The run in progress, "Priced 20 of 110" | |
| `ballpark-run-5.jpg` | ballpark how-to | The finished run with the total | |
| `ballpark-run-6.jpg` | ballpark how-to | A record after the run: grading service, grade, grader, Instant Ballpark | |
| `ballpark-value.png` | FAQ | The Instant Ballpark panel with reasoning, date, and disclaimer | |

### C. Advanced Grading (`scenarios/professional-grading`, `howto/advanced-grading`)

| File | Pages | Shoot | Notes |
|---|---|---|---|
| `professional-grading-1.jpg` | scenario | The intro: 16-point checklist, the views that help most | |
| `professional-grading-2.jpg` | scenario | The sheet with only the cover attached and its warning | |
| `professional-grading-3.jpg` | scenario | Retaking the cover photo, square in frame | Camera frame |
| `professional-grading-4.jpg` | scenario | Long-press menu, Use as Cover | |
| `professional-grading-5.jpg` | scenario | Photographing the back cover | Camera frame |
| `professional-grading-6.jpg` | scenario | Photographing an interior page | Camera frame |
| `professional-grading-7.jpg` | scenario | Close-up of the corner crease | Camera frame |
| `professional-grading-8.jpg` | scenario, how-to | Eight photos attached, Start assessment | |
| `professional-grading-9.jpg` | scenario, how-to | The verdict | **Reuse store 03** |
| `professional-grading-10.jpg` | scenario | Assessed checks: spine, corners, creases | Regular zoom fits more rows per frame; 10 to 12 may collapse to two frames |
| `professional-grading-11.jpg` | scenario | Surface, discoloration, writing | |
| `professional-grading-12.jpg` | scenario | Staples, bindery, pages, restoration | |
| `professional-grading-13.jpg` | scenario, how-to | Annotated photo, paper loss ringed | **Reuse store 04** |
| `professional-grading-14.jpg` | scenario | Annotated photo, the handling bend | |

### D. Labels, Scan a Stack, Audit Box (`howto/barcoding-your-books`, `howto/keeping-inventory-accurate`, `scenarios/selling-a-stack`, `scenarios/after-the-show`, `scenarios/dealer-to-dealer`)

| File | Pages | Shoot | Notes |
|---|---|---|---|
| `barcoding-1.jpg` | barcoding how-to | A box's menu open: Export, Report, Audit box, Print box labels… | |
| `barcoding-2.jpg` | barcoding how-to | The label sheet dialog |  |
| `dealer-to-dealer-1.png` | scenario, barcoding how-to | The Label section of a record: QR, short code, Label attached, Print label | |
| `selling-a-stack-1.jpg` | scenario, barcoding how-to | Scan a Stack with labels in the camera and the asking total | **Reuse store 05** (five books, $34). Scenario caption says two labels and $12; change the caption and alt, the prose is number-free |
| `after-the-show-1.jpg` | scenario | Box menu with Audit box |  |
| `after-the-show-2.jpg` | scenario, accuracy how-to | Audit mid-scan: camera on a label, here / arriving / unseen | |
| `after-the-show-3.jpg` | scenario, accuracy how-to | The audit summary | Store 07 shows 4 confirmed, 1 not seen; the scenario tells a 107-book story, so retake on a big box |
| `after-the-show-4.jpg` | scenario | Collections menu, Review inventory issues with a count | |
| `after-the-show-5.jpg` | scenario | The Inventory Issues list | |
| `after-the-show-6.jpg` | scenario, accuracy how-to | Resolving an issue: clear, undo sale, mark sold, delete | |

### E. Evaluate a Stack (`scenarios/buying-a-stack`, `howto/evaluating-a-stack`)

| File | Pages | Shoot | Notes |
|---|---|---|---|
| `buying-a-stack-2.jpg` | scenario, how-to | Evaluate mid-session with the Mine total and an ownership row | **Reuse store 06** ("Mine $500 · 1 of 3", "You own 1 · VG $500"). Both pages quote "Mine $22" and "VF $6" in captions and alt; update them |

### F. Selling and export (`scenarios/listing-desk`, `howto/selling-and-exporting`)

| File | Pages | Shoot | Notes |
|---|---|---|---|
| `listing-desk-1.jpg` | scenario, how-to | The For Sale dialog with the price prefilled |  |
| `listing-desk-2.jpg` | scenario | The For Sale tab with a listing pill | |
| `listing-desk-3.jpg` | scenario, how-to | The For Sale tab's menu, Export auction pack | |
| `listing-desk-4.jpg` | scenario, how-to | The auction pack export sheet | |

### G. Sharing, backup, restore (`howto/sharing-backup-restore`)

| File | Pages | Shoot | Notes |
|---|---|---|---|
| `export-1.jpg` | how-to | Selection mode, three checked, Export 3 selected | |
| `export-2.jpg` | how-to | The Export sheet | **Reuse store 09** |
| `airdrop-receive-1.jpg` | how-to | The arrived .cbshare on the receiving phone | Needs a second phone |
| `airdrop-receive-2.jpg` | how-to | The Import sheet with the sender's-appraisals choice | second phone |
| `backup-reminder.jpg` | how-to | Collections screen with the Backup due banner | the banner appears when a backup is overdue |
| `settings-backup.jpg` | how-to | Settings, the Backup section | |

### H. Browse, Hot Books (`scenarios/back-issue-bin`, `scenarios/hot-books`, `howto/hot-books`)

| File | Pages | Shoot | Notes |
|---|---|---|---|
| `back-issue-bin-1.png` | scenario | All Comics with the collection picker, search, filter chips, and the book count | Caption says 841 books; the count is now about 1,275, so the caption and the alt change.  |
| `hot-books-1.png` | scenario, how-to | Hot Books, one story mapped to its key issues and a matched owned book | **Reuse store 08** (the Lanterns story). Caption and alt describe the Shang-Chi story; rewrite.  |
| `credits-screen.png` | FAQ, credits how-to | Done 2026-09-07 from store 10 | |

### I. Admin review (`howto/admin-review`), desktop

| File | Pages | Shoot | Notes |
|---|---|---|---|
| `admin-review.jpg` | admin how-to | Export Admin review from the app, open the page in a Mac browser, screenshot the grid with a series row open | The page changed on 2026-09-07 (series rows that rename a volume, scope by publisher, show how spellings differ, and outline the covers that would change). Not a phone frame: capture at the browser's size, then resize to about 1400 wide like the current file. Check the how-to's prose against the new rows; it may need a paragraph |

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
