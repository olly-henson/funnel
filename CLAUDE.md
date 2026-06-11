# Funnel Project — Claude Instructions

## What This Project Is
Custom HTML/CSS landing pages for Olly Henson Coaching, built section by section and pasted into Go High Level (GHL) custom HTML blocks.

## File Structure
```
funnel/
  sections/
    main.html        ← entire opt-in page (one block in GHL)
    thank-you.html   ← thank you page (one block in GHL)
  brand/
    brand-guidelines.md  ← colours, fonts, styles
  CLAUDE.md
  README.md
  ghl-setup-guide.md
  custom-css.css     ← legacy (now embedded inside main.html)
```

## GHL Setup
- **Location ID:** `LRqVZmxns8f3xcJLHzBK`
- **Funnel page path:** `/meditation`
- **Thank you page path:** `/thank-you`
- **Form ID:** `inmmplT2BZ` (native GHL form — not used directly)
- **Webhook URL:** `https://services.leadconnectorhq.com/hooks/LRqVZmxns8f3xcJLHzBK/webhook-trigger/e0f3bbd1-0889-4398-beba-50c2f4ca5a9d`

## How It Works
- The visible form is custom HTML/CSS — it looks great and is fully styled
- On submit, it POSTs JSON to the GHL webhook which creates the contact
- **Do NOT use the hidden form technique** — GHL loads native forms inside iframes and removes hidden sections from the DOM entirely
- The webhook approach is the correct and reliable method

## GHL Editor Rules
- Every section must have **margin and padding set to 0**
- Section width must be set to **Full Width**
- To make HTML escape GHL's container use this on `.ohc-page`:
  ```css
  width: 100vw !important;
  position: relative !important;
  left: 50% !important;
  transform: translateX(-50%) !important;
  ```
- GHL's visibility toggle removes elements from the DOM — use CSS classes to hide instead

## Images (GHL Media Library)
- **Woman meditating (focal image):** `https://assets.cdn.filesafe.space/LRqVZmxns8f3xcJLHzBK/media/6a2afe5b9bdda92b22d3bdbf.png`
- **Olly headshot (thank you page):** `https://assets.cdn.filesafe.space/LRqVZmxns8f3xcJLHzBK/media/6a2b0038e5084c4b718e68e7.png`

## External Links
- **Skool Community:** `https://www.skool.com/the-healing-code-8609`
- **GitHub Repo:** `https://github.com/olly-henson/funnel`

## Design System
- **Theme:** Space / cosmos — deep purples, magenta, violet, dark backgrounds, starfield
- **Primary bg:** `#080010`
- **Deep purple:** `#1a0535`
- **Mid purple:** `#6b21a8`
- **Violet:** `#a855f7`
- **Magenta:** `#d946ef`
- **Text:** `#f8f4ff`
- **Muted text:** `#c4b5fd`
- **Fonts:** Playfair Display (headings, 900 weight) + Inter (body)
- **CTA button:** Pill shape (border-radius: 50px), gradient magenta→mid-purple, shimmer on hover
- **Headline style:** Line 1 white, Line 2 italic gradient (magenta→violet)

## Current Page Copy
### main.html
- **Headline:** Activate Your Heart, / Create Your World.
- **Subheading:** A simple but powerful meditation to take you out of your head and into your creative power.
- **Form heading:** Where should we send it?
- **CTA button:** Send Me the Meditation →
- **Proof bullets:** Works even if you've never meditated before / Takes less than 10 minutes / Instant access — straight to your inbox
- **Testimonials:** Isabell + Anas (both "Olly Henson's Coaching Client")
- **Product name:** Heart Activation Meditation

### thank-you.html
- **Headline:** Your Meditation / is On Its Way.
- **Subheading:** Check your inbox. Your Heart Activation Meditation will be there shortly. While you wait, come join the community.
- **CTA label:** Ready to start creating?
- **CTA button:** Start Your Free Trial →
- **CTA link:** https://www.skool.com/the-healing-code-8609

## Still To Complete
- [ ] Add redirect URL to `main.html` after successful form submission (uncomment `window.location.href` line in JS)
- [ ] Add Privacy Policy URL to footer in both pages
- [ ] Add Terms & Conditions URL to footer in both pages
- [ ] Set up workflow actions after webhook trigger in GHL (tag contact, send meditation audio, add to email sequence)
- [ ] Split test: Variant B = breathing image animation (add `animation: breathe 5s ease-in-out infinite` to `.ohc-focal-image img`)
- [ ] Canva "Heart" brand kit — manually add colours and fonts (see brand/brand-guidelines.md)

## Canva Brand Kit
- **Kit name:** Heart
- **Kit ID:** needs creating manually in Canva Brand Hub
- All colours and fonts documented in `brand/brand-guidelines.md`
