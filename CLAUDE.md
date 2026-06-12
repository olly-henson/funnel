# Funnel Project — Claude Instructions

## What This Project Is
Custom HTML/CSS landing pages for Olly Henson Coaching, built section by section and pasted into Go High Level (GHL) custom HTML blocks.

## File Structure
```
funnel/
  sections/
    opt-in.html                  ← opt-in page (one block in GHL)
    thank-you.html             ← thank you page (one block in GHL)
    funnel-application.html    ← 1-2-1 coaching application form (one block in GHL)
  brand/
    brand-guidelines.md  ← colours, fonts, styles
  CLAUDE.md
  README.md
  ghl-setup-guide.md
  custom-css.css     ← legacy (now embedded inside opt-in.html)
```

## GHL Setup
- **Location ID:** `LRqVZmxns8f3xcJLHzBK`
- **Funnel page path:** `/meditation`
- **Thank you page path:** `/thank-you`
- **Form ID:** `inmmplT2BZ` (native GHL form — not used directly)
- **Webhook URL:** `https://services.leadconnectorhq.com/hooks/LRqVZmxns8f3xcJLHzBK/webhook-trigger/34c004b7-3a84-43b2-a783-4e24f0675388`

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
### opt-in.html
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

## Application Form — funnel-application.html

### Page Details
- **Program name:** The Heart Creator Program
- **GHL page path:** TBC (separate page in funnel)
- **Webhook URL:** `https://services.leadconnectorhq.com/hooks/LRqVZmxns8f3xcJLHzBK/webhook-trigger/20d915b2-cc20-42e1-8451-c32f38670efd`
- **GHL Workflow:** "Applications" workflow

### Form Fields (sent via webhook JSON)
- `first_name` — text input (id: `ohc_fname` — renamed to avoid GHL interception)
- `last_name` — text input (id: `ohc_lname` — renamed to avoid GHL interception)
- `email` — text input (id: `ohc_email` — renamed to avoid GHL interception)
- `whatsapp` — tel input
- `situation` — textarea
- `outcome` — textarea
- `become` — textarea (question is about blocks, not becoming)
- `tried` — textarea
- `coaching_before` — textarea

### GHL Custom Fields (all in Contact folder)
- `App Q1 - Situation` — key: `app_q1__situation`
- `App Q2 - Outcome` — key: `app_q2__outcome`
- `App Q3 - Blocks` — key: `app_q3__become`
- `App Q4 - Tried` — key: `app_q4__tried`
- `App Q5 - Coaching` — key: `app_q5__coaching` (recreated — GHL truncated the name)

### GHL Workflow Actions
1. Webhook trigger
2. Create/Update Contact — maps all fields using `{{inboundWebhookRequest.fieldname}}`
3. Send Internal Notification Email — sends to olly@ollyhenson.com

### Known GHL Quirks (learned the hard way)
- **Field name interception:** GHL strips values from inputs named `first_name`, `last_name`, `email` — use different IDs (e.g. `ohc_fname`) and map in JS
- **Internal notification emails** only support `{{contact.*}}` tags, not `{{inboundWebhookRequest.*}}` — but `{{contact.*}}` tags for custom fields don't always resolve in notification emails either
- **Custom field caching:** After recreating a custom field, close and reopen the workflow before remapping — GHL caches old field references
- **Multi line vs Single line:** Use Single line field type for custom fields that receive webhook data — multi line can cause write issues
- **Notification email formatting:** GHL strips HTML formatting from internal notification emails — plain text only works but renders on one line. Workaround: keep notification simple (name, email, WhatsApp only) and view full answers in the contact record

### Application Questions
1. Tell me about your current situation. What are you looking to change?
2. What would you like to create in your life and who would you like to become?
3. What do you think has been holding you back from creating this for yourself and becoming this version of you?
4. What books, courses, meditations or other modalities have you tried to create this life for yourself so far?
5. Have you invested in coaching before? If so, how did it go?

### Design
- Cosmic dark background matching main funnel
- White/off-white form card (`#f5f3ff`) with off-black text (`#1e0a40`)
- Deep violet accents (`#7c3aed`, `#6d28d9`)
- Hero image (woman activating heart) between headline and subheadline
- First/Last name side by side on one row
- No placeholder text in textareas — questions speak for themselves

## Meditation Delivery Page — meditation-delivery.html
- **GHL page path:** `/meditation-access`
- **URL:** `https://ollyhenson.com/meditation-access`
- Styled to match opt-in page (cosmic dark, stars, nebula glow)
- Video placeholder — replace with Vimeo/YouTube iframe when ready
- PDF practice guide button — replace `PLACEHOLDER_PDF_URL` with hosted PDF URL
- Heart Creator Program application button — replace `PLACEHOLDER_APPLICATION_URL` with application page URL

## Meditation Workflow (GHL)
- Trigger: webhook (opt-in form submission)
- Actions needed:
  1. Tag contact: "Meditation Download"
  2. Send autoresponder email — delivers link to `https://ollyhenson.com/meditation-access`
  3. Add to nurture sequence (TBC)
- Autoresponder email template: built in GHL Code Editor, delivers meditation URL

## PDF Practice Guide
- **File:** `sections/practice-guide.html`
- **Generator:** `generate-pdf.mjs` — run with `node --input-type=module --eval "import './generate-pdf.mjs'"` from funnel root
- **Hosted PDF URL:** `https://assets.cdn.filesafe.space/LRqVZmxns8f3xcJLHzBK/media/6a2c6d2b8a3c98ce5652963a.pdf`
- Puppeteer installed in funnel folder for PDF/image generation

## Logo
- **Folder:** `logo/`
- **File:** `logo/heart-logo.html` — SVG heart with chaotic → coherent waveform transformation
- **Generator:** `logo/generate-logo.mjs` — outputs `logo/heart-logo.png`
- Work in progress — cosmic palette, brand colours

## Legal Pages
- **Privacy Policy:** `sections/privacy-policy.html` → `https://ollyhenson.com/privacy-policy`
- **Terms & Conditions:** `sections/terms.html` → `https://ollyhenson.com/terms`
- Both cover UK GDPR, Data Protection Act 2018, ICO, coaching disclaimer, Skool community, HCP programme
- All funnel pages and homepage footer updated with live URLs

## Still To Complete
- [ ] Add redirect URL to `opt-in.html` after successful form submission (uncomment `window.location.href` line in JS)
- [ ] Replace video placeholder in meditation-delivery.html with real Vimeo/YouTube iframe
- [ ] Build out GHL meditation workflow nurture sequence emails
- [ ] Add autoresponder to Applications workflow for applicants
- [ ] Split test: Variant B = breathing image animation
- [ ] Canva "Heart" brand kit — manually add colours and fonts (see brand/brand-guidelines.md)
- [ ] Finalise heart logo design

## Canva Brand Kit
- **Kit name:** Heart
- **Kit ID:** needs creating manually in Canva Brand Hub
- All colours and fonts documented in `brand/brand-guidelines.md`
