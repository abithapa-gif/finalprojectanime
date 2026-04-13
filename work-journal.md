# Work Journal — Anime Vault

## Session 1 — Planning & Concept
- Decided on general anime fan site covering 5 series: Naruto, One Piece, Attack on Titan, Demon Slayer, Fairy Tail
- Sketched wireframes for all 4 pages at mobile and desktop sizes (photos in wireframes/)
- Page plan: Home (hero + featured cards), About (story + team + gallery), Series (full grid of all 5), Contact (info + form)
- Chose dark color theme: deep black backgrounds, purple/cyan gradient accents, card-based layout

**Design decision:** Dark theme fits the anime aesthetic better than a light theme. Purple (#7c3aed) and cyan (#06b6d4) as the accent duo creates a vibrant, high-energy feel without being overwhelming.

## Session 2 — Design System & CSS
- Built full CSS custom properties system (design tokens) for all colors, spacing, radii, shadows
- Implemented clamp() on ALL headings h1–h4
- Set up CSS Grid for: series cards, stats row, team grid, gallery, full series grid, footer, contact layout
- Set up Flexbox for: header, nav, hero buttons, filter bar, info items, showcase buttons
- Defined 3 breakpoints: 600px, 900px, 1200px
- Added 5 series-specific accent colors (--naruto, --onepiece, --aot, --demonslayer, --fairytail) for badges

**Problem encountered:** gradient text (-webkit-background-clip: text) doesn't work on all elements. Had to add both -webkit-text-fill-color: transparent and background-clip: text consistently.

## Session 3 — HTML Pages
- Built index.html: hero with eyebrow text, 4-stat row, 3 featured series cards, 3 feature cards
- Built about.html: float-image story section, 3-image gallery grid, 3 team cards, mission statement
- Built series.html: showcase banner, filter button bar, full grid of all 5 series detail cards with series-specific info
- Built contact.html: showcase banner, 2-column grid (info + form), response time table, full form

**Decision:** Named the 4th page series.html instead of gallery.html since "series" is more accurate to the content. The page is still a grid of cards satisfying the requirement.

## Session 4 — Responsive Images
- Added srcset (480w + 800w) and sizes attribute to every img element
- Added explicit width/height to all images to prevent Cumulative Layout Shift
- Created -sm naming convention for smaller image variants
- Used 1x/2x descriptors for logo images, width descriptors for content images

## Session 5 — Contact Form
- Added all required inputs: first name, last name, email, username (optional), subject (select), favourite series (optional select), message textarea
- Every label connected with for/id pairing
- aria-required="true" and aria-describedby on all required fields
- Required fields use * indicator — consistent, no mixing
- Input types: text, email, select, textarea
- HTML5 validation: required attribute on all required fields
- Styled :focus with purple glow box-shadow
- Styled .error with red border and tinted background
- .error-msg spans with role="alert" for screen reader announcements
- .success-message block with role="alert" aria-live="polite"

## Session 6 — Validation
- W3C HTML: Fixed missing lang attributes on one page, duplicate id on team card section
- W3C CSS: Fixed a missing semicolon in the gradient text block
- WAVE: Fixed 2 images missing alt text, fixed one label not associated with input
- Lighthouse: Added preconnect for Google Fonts, added explicit width/height to all images, improved from 74 → 92 on mobile

## Session 7 — User Testing & Polish
- Ran 3 user tests (see user-testing/)
- Changed: Filter buttons on series page had no visual active state — added :focus styling
- Changed: Series cards originally had no price/episode count visible without interaction — added episode counts and studio info directly visible
- Changed: Success message placeholder text was generic — rewrote to be on-brand for an anime fan community
