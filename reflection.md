# Reflection — Anime Vault
**Project 2 | Web Development**

---

## What I Built

Anime Vault is a 4-page fan site covering five anime series: Naruto, One Piece, Attack on Titan, Demon Slayer, and Fairy Tail. The site includes a home page with a hero section and featured series, an about page with the site's story and team, a series page with a full grid of all five shows including episode counts and studio info, and a contact page with a form for fan messages. The design uses a dark theme with purple and cyan gradient accents meant to feel like a premium anime streaming platform, not a generic school project.

---

## Design Decisions

I committed fully to a dark theme because it suits the anime audience: fans browse anime sites at night, dark themes reduce eye strain, and the content (action-heavy shows with dramatic art) looks better against dark backgrounds than white ones.

For the accent colors I chose purple (#7c3aed) and cyan (#06b6d4) as the primary gradient pair, with each of the five series getting its own accent color for badges — orange for Naruto, red for One Piece, green for Attack on Titan, pink/magenta for Demon Slayer, and blue for Fairy Tail. This gives each series an identity while keeping the overall system cohesive.

For typography I used Rajdhani for headings — a bold, angular font that feels action-oriented without being illegible — paired with Open Sans for body text. This creates clear hierarchy: the headings feel like they belong in an anime title card, the body text stays readable at length.

---

## Responsive Approach

I used CSS Grid as the primary layout system for everything that holds multiple items. The series grid starts as 1 column on mobile, grows to 2 at 600px, 3 at 900px, and 5 at 1200px — which is the full series count. The stats row starts 2-across on mobile and expands to 4-across at 600px. The contact layout stacks on mobile and becomes side-by-side at 900px.

The three breakpoints (600px / 900px / 1200px) were chosen based on actual content breakage points: at 600px cards become cramped single-column, at 900px the contact form needs a second column to not feel like a form inside a form, at 1200px there's enough room to show all 5 series in one row.

For images: `srcset` with 480w and 800w versions plus `sizes` descriptors tells the browser exactly when to swap images. Every image has explicit `width` and `height` attributes to prevent layout shift during page load.

---

## User Testing Insights

Testing revealed two things I wouldn't have caught on my own.

First, the filter buttons on the series page looked completely inert. Two testers clicked them and nothing happened (CSS-only filtering without JS isn't implemented, which is correct per the rules), but the buttons gave no feedback — no active state, no indication they'd been pressed. I added a visible `:focus` state so at minimum the buttons acknowledge the interaction.

Second, one tester on mobile couldn't tell how many episodes each series had until they scrolled into the card body. They said "I want to know upfront if this is a 1000-episode commitment before I start." I moved the episode count to be more visually prominent inside the card, which required no structural change — just styling the info-row for studio and episodes to be the first things after the series badge.

---

## What Was Tricky

Gradient text (`-webkit-background-clip: text`) was inconsistent across elements. On some elements it worked, on others the text disappeared entirely. The fix was to always set both `-webkit-text-fill-color: transparent` AND `background-clip: text` together — never just one. This appears in multiple places in the CSS and I had to audit every instance.

The contact form two-column layout on desktop required careful grid alignment. The info column and the form box needed to align at the top with `align-items: start`, otherwise the shorter info column would stretch to match the form height and look broken.

---

## Key Insight

CSS Grid is genuinely superior to Flexbox for 2D layouts and I was underusing it in Project 1. Once I understood that Grid handles both rows AND columns simultaneously while Flexbox only handles one axis at a time, I stopped trying to nest Flexbox inside Flexbox and just used Grid. The series page layout (1 → 2 → 3 → 5 columns across breakpoints) would have been a nightmare with Flexbox `flex: 1 1 X%` math. With Grid it's three one-liners in media queries.

---

## Work Quality

⭐ Portfolio-ready as-is

The dark theme, gradient accents, typography, and grid layout all look intentional and professional. I'd add real anime images (official promotional art with proper licensing for a real site), deploy to Netlify, and run final Lighthouse scores. But the structure and code quality are strong enough to show.
