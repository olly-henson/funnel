# Funnel Project — Claude Instructions

## What This Project Is
Custom HTML/CSS landing pages for Olly Henson Coaching, designed to be pasted section-by-section into Go High Level (GHL) custom HTML blocks.

## How GHL Implementation Works
- Each section is a **separate HTML file** → paste each into its own GHL Custom HTML block
- Set **margin to 0** on every GHL section to avoid gaps between sections
- **custom-css.css** → paste contents into GHL > Funnel Settings > Custom CSS
- There is a **hidden GHL native form** at the bottom of the page (invisible section) — the visible HTML form submits data into this hidden form via JavaScript
- See `ghl-setup-guide.md` for full step-by-step instructions

## Page Sections (in order)
1. `sections/01-hero.html` — Headline, sub-headline, cosmic background
2. `sections/02-mockup.html` — CSS-animated meditation audio visual/mockup
3. `sections/03-form.html` — HTML overlay form (First Name, Last Name, Email + CTA) with JS bridge to hidden GHL form
4. `sections/04-social-proof.html` — Trust bullets
5. `sections/05-testimonials.html` — Isabell + Anas testimonial cards
6. `sections/06-footer.html` — Privacy Policy + Terms links only

## Design System
- **Theme:** Space / cosmos — deep purples, magenta, violet, dark backgrounds, star/nebula effects
- **Primary bg:** `#080010`
- **Dark purple:** `#1a0535`
- **Mid purple:** `#6b21a8`
- **Violet accent:** `#a855f7`
- **Magenta glow:** `#d946ef`
- **Text:** `#f8f4ff`
- **Font:** Google Fonts — Inter (body), Playfair Display (headings)
- **CTA button:** Gradient magenta→violet with shimmer animation on hover
- **Animations:** Subtle starfield, pulsing glow on mockup, shimmer on CTA

## Key Rules
- All copy is **placeholder** — Olly will replace with final copy before launch
- No navigation header on this page
- Footer has **only** Privacy Policy and Terms & Conditions links
- Form fields: First Name, Last Name, Email only
- The hidden GHL form section must remain in the page but be set to **invisible** in GHL layers
- When the hidden GHL form ID is known, update the `GHL_FORM_ID` constant in `sections/03-form.html`

## Olly's Details
- Business: Olly Henson Coaching
- Product: Meditation audio download (free lead magnet)
- Email: olly@ollyhenson.com
- GHL account is live and connected
