# CLAUDE.md — ClinicEvolve Website Project

This file is read at the start of every session. Follow every instruction here before writing any code, creating any file, or making any design decision. Do not skip any section.

---

## Who You Are Working For

You are building the marketing website for **ClinicEvolve™** — a managed enquiry-to-consultation system for IVF and Dermatology specialty clinics in India.

**Founder:** Sudheer Gudla
**Website goal:** Get the right clinic owner to book a free 30-minute Enquiry-to-Consultation Review. That is the only conversion goal. Nothing else.
**Target audience:** IVF and Dermatology clinic owners in India who already generate steady enquiries but experience inconsistent consultation bookings. These are premium practitioners running high-value practices. The site must feel like it belongs in their world.

ClinicEvolve is not a marketing agency. Not a leads vendor. Not a chatbot installer. It is an operational solution for clinics that already have demand but lose it in handling.

---

## First Session Setup — Run This Once Before Anything Else

If the project folder structure does not yet exist, create it now before doing anything else. Run the following in the terminal:

```bash
mkdir -p app/thank-you
mkdir -p components/navigation
mkdir -p components/sections
mkdir -p components/ui
mkdir -p lib
mkdir -p public/assets/logo
mkdir -p public/assets/images
mkdir -p assets/brand
mkdir -p assets/copy
mkdir -p assets/reference
```

Then confirm the structure matches the Project File Structure section below before proceeding.

This step runs once only. If the folders already exist, skip it.

---

## Mandatory First Step — Read Before Writing Any Code

Before writing any frontend code, designing any component, or making any layout decision:

1. **Use the built-in frontend-design skill** — this is a native Claude Code skill, always available. Invoke it before writing any frontend code. It governs all aesthetic, layout, motion, and spatial composition decisions.
2. **Read the brand guidelines** at `/assets/brand/ClinicEvolve_Brand_Guidelines.pdf` — governs colors, fonts, logo usage, and tone
3. **Read the website copy** at `/assets/copy/clinicevolve_website_copy_clean.md` — single source of truth for every word on the site
4. **Reference the existing site layout** at `/assets/reference/clinicevolve_existing_site.pdf` — structural reference for section flow and layout logic

This is non-negotiable. Do not skip any of these steps. Do not start coding until all are done.

---

## Tech Stack

- **Framework:** Next.js 14 (App Router)
- **Styling:** Tailwind CSS
- **Language:** TypeScript
- **Fonts:** Google Fonts — Playfair Display (headings), DM Sans (body), Poppins (logo wordmark only)
- **Animations:** Framer Motion — scroll reveals, section entry animations, hover states
- **Booking CTA:** Cal.com direct link (no embed)
- **Deployment:** Netlify

Do not introduce any library, package, or dependency not listed here without asking first.

---

## Project File Structure

```
clinicevolve/
├── CLAUDE.md
├── app/
│   ├── layout.tsx                         ← root layout, fonts, metadata, OG tags
│   ├── page.tsx                           ← home page
│   ├── thank-you/
│   │   └── page.tsx                       ← post-booking thank you page
│   └── globals.css                        ← CSS variables, base styles, font imports
├── components/
│   ├── navigation/
│   │   └── Navbar.tsx
│   ├── sections/
│   │   ├── Hero.tsx
│   │   ├── TheProblem.tsx
│   │   ├── WhereItBreaks.tsx
│   │   ├── TheFramework.tsx
│   │   ├── WhoItIsFor.tsx
│   │   ├── WhatWeAreNot.tsx
│   │   ├── HowItWorks.tsx
│   │   ├── WhoWeAre.tsx
│   │   ├── TheFounder.tsx
│   │   ├── ReviewRequest.tsx
│   │   └── Footer.tsx
│   └── ui/
│       ├── Button.tsx
│       ├── SectionLabel.tsx
│       └── GoldDivider.tsx
├── lib/
│   └── constants.ts
├── public/
│   └── assets/
│       ├── logo/
│       │   ├── clinicevolve_logo_final.svg
│       │   └── clinicevolve_logo_final.png
│       └── images/
│           └── sudheer-headshot.jpg       ← to be added before launch
└── assets/                                ← reference files only, not served
    ├── brand/
    │   └── ClinicEvolve_Brand_Guidelines.pdf
    ├── copy/
    │   └── clinicevolve_website_copy_clean.md
    └── reference/
        └── clinicevolve_existing_site.pdf
```

---

## Constants File

Define all constants in `/lib/constants.ts`. Import from here everywhere. Never hardcode these values anywhere else in the codebase.

```typescript
export const CAL_BOOKING_URL = "https://cal.com/sudheergudla/ivf-dermatology-consultation-review"
export const LINKEDIN_URL = "https://linkedin.com/in/sudheergudla"
export const SITE_NAME = "ClinicEvolve™"
export const SITE_URL = "https://clinicevolve.com"
export const THANK_YOU_PATH = "/thank-you"
```

---

## Brand — Non-Negotiable Design Rules

### Colors
Define in globals.css. Reference everywhere via CSS variables. Never hardcode hex values outside globals.css.

```css
:root {
  --color-bg-primary: #0F0F0F;
  --color-bg-surface: #1A1A1A;
  --color-bg-card: #222222;
  --color-gold: #C9A84C;
  --color-gold-light: #E2C47A;
  --color-white: #FFFFFF;
  --color-grey-light: #D4D4D4;
  --color-grey-mid: #8A8A8A;
  --color-grey-dark: #444444;
  --color-red: #C0392B;
}
```

### Typography
- **Wordmark only:** Poppins Bold, weight 700 — used exclusively in Navbar and Footer logo. Nowhere else.
- **Display headings H1, H2:** Playfair Display Bold or SemiBold.
- **Subheadings H3 and UI elements:** DM Sans SemiBold, weight 600.
- **Body copy:** DM Sans Regular, weight 400.
- **Eyebrow labels:** DM Sans Medium, weight 500, letter-spacing 2.5px, all caps, color: var(--color-gold).
- **Button text:** DM Sans SemiBold, weight 600.
- **Never use:** Inter, Roboto, Arial, system fonts, or any font not listed above.

### Logo
- Always use the SVG: `/public/assets/logo/clinicevolve_logo_final.svg`
- Never recreate the logo in code or with text elements
- Never alter logo colors
- Maintain clear space on all sides equal to cap height of the "C"
- This site is always dark — always use the dark background logo version

---

## Aesthetic Direction

**Invoke the built-in frontend-design skill before writing any code. It is the authority on aesthetic decisions. Apply it fully.**

The committed aesthetic direction is: **luxury/refined — dark, premium, authoritative.**

The single thing a visitor must remember: this is a precision operational system built for premium clinics by someone who understands how enterprise systems work. Not a generic healthcare SaaS. Not an agency.

### Spatial composition
- Generous negative space. Sections breathe — do not crowd content.
- Hero: full viewport height, content vertically centred, left-aligned on desktop.
- Alternate section backgrounds between `--color-bg-primary` and `--color-bg-surface` to create rhythm without color noise.
- Use asymmetric layouts where appropriate — not everything needs to be centred.

### Background and texture
- Subtle dot grid patterns at 4–6% opacity in key sections — gold dots on dark surface.
- Fine 1px rule lines as section dividers using `--color-grey-dark` at low opacity.
- No gradients. No blurred backgrounds. No glassmorphism.

### Motion — Framer Motion
- Hero: orchestrated load animation — headline fades and rises with staggered line delay.
- All other sections: scroll-triggered fade-up on entry, staggered delay on child elements.
- Timing: 0.5s duration, ease-out. Stagger between children: 0.1s.
- Card hover: subtle upward translate 3px, border color shifts toward `--color-gold`.
- CTA button hover: gold background fills from left, text shifts to `--color-bg-primary`, smooth 0.3s transition.
- Arrow icon on CTA buttons shifts 4px right on hover.
- No bouncing. No spinning. No attention-seeking effects.

### Cards
- Background: `--color-bg-card`
- Border: 1px solid `--color-grey-dark`
- Border radius: 8px
- Hover: border shifts to `--color-gold` at 50% opacity, card lifts 3px
- Padding: 28px desktop, 20px mobile

### Buttons
- Default: gold border, gold text, transparent background
- Hover: gold background fills in, text shifts to `--color-bg-primary`
- Transition: 0.3s ease
- Border radius: 4px — not pill-shaped
- Padding: 14px 28px desktop, 12px 24px mobile

### Gold restraint
Gold is used sparingly — it signals key moments, not decoration. Overuse kills the signal. Used on: eyebrow labels, CTA buttons, active states, dividers, key headline word highlights, numbered labels. Never as a large background fill.

---

## Layout Reference

Use `/assets/reference/clinicevolve_existing_site.pdf` as the structural reference for section flow and layout logic. Follow it for structure. Elevate it with better typography, spacing, motion, and visual detail.

### Section layout intent

**Navbar:** Logo left, CTA button right. Transparent on load, `--color-bg-surface` on scroll with subtle bottom border. Fixed position.

**Hero:** Full viewport height (100vh). Content centred vertically, left-aligned. H1 headline is largest element — 64px desktop. Three bullet points with gold dash markers. CTA below. Dot grid texture top-right quadrant at low opacity.

**TheProblem:** Two columns on desktop — situation copy left, "real issue" callout right with gold left border accent. Single column on mobile.

**WhereItBreaks:** Six points in 3×2 grid desktop, 2×3 tablet, single column mobile. Each has a gold number, bold title, and body.

**TheFramework:** Three steps — horizontal 3 columns desktop, stacked single column tablet and mobile. Each step: number, title, body, gold italicised note line. Full-width closing banner.

**WhoItIsFor:** Two clinic type cards side by side desktop, stacked mobile. Qualifying checklist full width below. Closing statement centred.

**WhatWeAreNot:** Four items in 2×2 grid desktop, single column mobile. Red X markers. Closing statement in gold.

**HowItWorks:** Four steps in vertical timeline layout — numbered, connected by a thin vertical gold line.

**WhoWeAre:** Centred. Core belief statement prominent. Three "we work with" lines. Four attribute items in a row desktop, 2×2 grid mobile.

**TheFounder:** Two columns desktop — headshot left, text right. Single column mobile — photo above text. Photo: 3:4 portrait, max-width 360px desktop.

**ReviewRequest:** Two columns desktop — three review steps with vertical connector line left, headline and CTA right. Single column mobile. Full-width closing statement below.

**Footer:** Three columns desktop, two columns tablet, single column mobile. Gold top border. Logo and tagline left, links centre, legal right.

**ThankYou page:** Centred single column, max-width 640px. Logo top links home. No navigation. No footer links.

---

## Responsive Specification

Mobile-first. Every component built mobile-first and scaled up. No exceptions.

### Breakpoints

```css
/* Mobile:  0px – 767px    → default, no Tailwind prefix  */
/* Tablet:  768px – 1023px → md: prefix                   */
/* Desktop: 1024px+        → lg: prefix                   */
/* Wide:    1280px+        → xl: prefix                   */
```

### Typography scaling

| Element | Mobile | Tablet | Desktop |
|---|---|---|---|
| H1 Hero headline | 36px | 48px | 64px |
| H2 Section headline | 28px | 36px | 44px |
| H3 Card / step title | 18px | 20px | 22px |
| Body large | 16px | 16px | 18px |
| Body small / caption | 13px | 13px | 14px |
| Eyebrow label | 10px | 10px | 11px |
| Button text | 14px | 14px | 15px |

### Navigation — mobile behaviour
- Hamburger icon right side on mobile — three horizontal lines
- On tap: full-screen dark overlay menu, links centred vertically, large text (24px)
- CTA button at bottom of mobile menu
- Close (×) icon top right of overlay
- Smooth slide-down animation open, slide-up close

### Column collapse rules

| Section | Desktop | Tablet | Mobile |
|---|---|---|---|
| TheProblem | 2 col | 2 col | 1 col |
| WhereItBreaks | 3×2 grid | 2×3 grid | 1 col |
| TheFramework | 3 col | 1 col | 1 col |
| WhoItIsFor cards | 2 col | 2 col | 1 col |
| TheFounder | 2 col | 2 col | 1 col (photo above) |
| ReviewRequest | 2 col | 1 col | 1 col |
| Footer | 3 col | 2 col | 1 col |

### Spacing scaling
- Section vertical padding: 48px mobile → 80px tablet → 120px desktop
- Container max-width: 1200px, centred, horizontal padding: 20px mobile → 40px tablet → 80px desktop
- Card padding: 20px mobile → 24px tablet → 28px desktop
- Grid gap: 16px mobile → 20px tablet → 24px desktop

### Touch targets
- All buttons and interactive elements: minimum 44px height on mobile
- Mobile menu links: minimum 48px height
- No hover-only interactions — all hover states have a tap equivalent

### Images
- Founder headshot: `object-fit: cover`, fixed 3:4 ratio, max-width 360px desktop, full-width mobile
- All images: Next.js `<Image>` component with `width`, `height`, `alt`
- Logo SVG: 140px wide desktop, 120px wide mobile
- Lazy load all images below the fold

---

## Copy Rules — Language Non-Negotiables

The copy document at `/assets/copy/clinicevolve_website_copy_clean.md` is the single source of truth. Do not paraphrase, shorten, or rewrite copy without being explicitly asked.

Apply these rules to every word — button labels, alt text, aria labels, placeholders, metadata:

| Always Say | Never Say |
|---|---|
| Enquiry | Lead |
| Consultation | Booking (patient-facing) |
| Confirmation | Conversion |
| System or Framework | Automation or Chatbot |
| Coordinator | Receptionist or Telecaller |
| Relevant enquiries | Quality leads |
| Appointment Stability Framework™ | The product or the tool |
| ClinicEvolve™ | ClinicEvolve (without ™ on first use per page) |

---

## Thank You Page

**Route:** `/thank-you`
**File:** `/app/thank-you/page.tsx`

Cal.com redirects here after booking. Job: reassure the clinic owner they made the right decision and tell them what happens next.

### Copy

Logo: ClinicEvolve™ (centred, links home)

Headline: Your Review Is Booked.

Subheadline: You will hear from Sudheer within 24 hours to confirm the details.

Body:
Thank you for taking the time to request a review. Most clinic owners know something is breaking between their enquiries and their consultations — very few take the step to find out exactly what.

Here is what happens next:

1. Confirmation — You will receive a calendar invite with the call details. Check your inbox and spam folder if it does not arrive within a few minutes.

2. Before the call — No preparation needed. Come as you are. If you want, have a rough sense of how many enquiries your clinic receives per month — that is the only number that matters at this stage.

3. On the call — Thirty minutes. We will examine how your clinic currently handles enquiries, identify where consultations are being lost, and give you a clear picture of what is breaking. No pitch. No pressure. Just clarity.

LinkedIn CTA: In the meantime, feel free to connect on LinkedIn.
[Connect with Sudheer on LinkedIn →]

Closing: See you on the call.
— Sudheer Gudla, Founder, ClinicEvolve™

### Thank You Page Design Rules
- Same dark brand aesthetic as main site
- Centred single column, max-width 640px
- Logo only at top — no navbar, no navigation links
- No footer links — keep the page clean and focused
- Subtle Framer Motion fade-in on load
- No CTA back to main site

---

## SEO and Metadata

Define in `app/layout.tsx`:

```typescript
export const metadata = {
  title: "ClinicEvolve™ — Appointment Stability for IVF and Dermatology Clinics",
  description: "We help IVF and Dermatology clinics in India turn steady enquiries into confirmed consultations by finding and fixing exactly where their handling is breaking down.",
  openGraph: {
    title: "ClinicEvolve™",
    description: "Turn steady enquiries into confirmed consultations.",
    url: "https://clinicevolve.com",
    siteName: "ClinicEvolve™",
    type: "website",
  }
}
```

---

## Build Order

Build in this exact order. Complete and test each before starting the next.

1. `globals.css` — CSS variables, base styles, font imports
2. `lib/constants.ts` — all constants
3. `ui/Button.tsx`
4. `ui/SectionLabel.tsx`
5. `ui/GoldDivider.tsx`
6. `navigation/Navbar.tsx` — desktop and mobile
7. `sections/Hero.tsx`
8. `sections/TheProblem.tsx`
9. `sections/WhereItBreaks.tsx`
10. `sections/TheFramework.tsx`
11. `sections/WhoItIsFor.tsx`
12. `sections/WhatWeAreNot.tsx`
13. `sections/HowItWorks.tsx`
14. `sections/WhoWeAre.tsx`
15. `sections/TheFounder.tsx`
16. `sections/ReviewRequest.tsx`
17. `sections/Footer.tsx`
18. `app/page.tsx` — assemble all sections
19. `app/thank-you/page.tsx`
20. `app/layout.tsx` — metadata and font loading

---

## Coding Standards

- **TypeScript:** Proper types everywhere. No `any`.
- **Components:** Functional only. No class components.
- **Naming:** PascalCase components, camelCase variables/functions, kebab-case CSS properties.
- **Comments:** One line at top of each component file describing what it renders. No inline comments unless logic is non-obvious.
- **Props:** TypeScript interface for every component accepting props.
- **Tailwind:** Utility classes only. Brand colors via CSS variable arbitrary values — `text-[var(--color-gold)]`. No hardcoded hex in Tailwind.
- **Images:** Always `<Image>` from next/image. Never `<img>`. Always include `alt`, `width`, `height`.
- **Accessibility:** Semantic HTML. Descriptive alt text. Proper focus states. ARIA labels where needed.
- **No placeholder copy:** Never Lorem Ipsum. If copy is missing, add a TODO comment and stop.
- **Performance:** Lazy load all images below the fold.

---

## What Not To Do

- Do not invent copy — every word comes from the copy document
- Do not add sections not specified in this file
- Do not use colors outside the defined palette
- Do not use fonts outside the defined stack
- Do not hardcode the Cal.com link or LinkedIn URL — import from constants.ts
- Do not reveal pricing anywhere on the site
- Do not mention the guarantee anywhere on the site
- Do not mention UAE — India focus only
- Do not use the words: chatbot, automation, lead, booking (patient-facing)
- Do not install new packages without asking
- Do not use gradients, glassmorphism, or drop shadows on text
- Do not use pill-shaped buttons — border radius is 4px
- Do not build ahead — complete each section before starting the next
- Do not skip the mandatory first step of reading all four reference files

---

## Social Proof Placeholder

Leave this comment in `app/page.tsx` after TheFramework:

```tsx
{/* SOCIAL PROOF SECTION */}
{/* Add Testimonials.tsx component here when first client case study is available */}
{/* Position: after TheFramework, before WhoItIsFor */}
```

Do not build a placeholder UI. Just the comment.

---

## Current Build Status

- [ ] globals.css complete
- [ ] constants.ts complete
- [ ] Button.tsx complete
- [ ] SectionLabel.tsx complete
- [ ] GoldDivider.tsx complete
- [ ] Navbar.tsx complete (desktop + mobile)
- [ ] Hero.tsx complete
- [ ] TheProblem.tsx complete
- [ ] WhereItBreaks.tsx complete
- [ ] TheFramework.tsx complete
- [ ] WhoItIsFor.tsx complete
- [ ] WhatWeAreNot.tsx complete
- [ ] HowItWorks.tsx complete
- [ ] WhoWeAre.tsx complete
- [ ] TheFounder.tsx complete
- [ ] ReviewRequest.tsx complete
- [ ] Footer.tsx complete
- [ ] page.tsx assembled
- [ ] thank-you/page.tsx complete
- [ ] layout.tsx with metadata complete
- [ ] Mobile QA at 375px
- [ ] Tablet QA at 768px
- [ ] Desktop QA at 1280px
- [ ] Netlify deployment complete

Update this checklist as each item is completed.

---

*Last updated: May 2026*
*Update when: stack changes, sections added, copy updated, deployment details change, first testimonial available.*