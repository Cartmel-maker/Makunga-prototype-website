# Implementation Plan — Makhunga Crane and Engineering Landing Page

## Overview

A premium, single-file `index.html` landing page for Makhunga Crane and Engineering. Fully self-contained with all CSS in a `<style>` tag and all JavaScript in a `<script>` tag. Zero external dependencies except Google Fonts loaded via `<link>`. Zero lorem ipsum. Zero broken references.

---

## Tech Stack

- Vanilla HTML, CSS, and JavaScript only — no frameworks, no libraries, no backend
- Single self-contained `.html` file (inline CSS, inline JS)
- All animations handled with CSS keyframes and IntersectionObserver in JS
- Form success state is frontend-only: intercept submission, hide form, display confirmation message

---

## Design System

### Backgrounds
- Primary: `#0A0A0B` (deep industrial charcoal-black)
- Section alternates: `#111113` and `#17171A` (brushed dark steel and slate tones)
- Highlight card: `#1A1A1D`

### Accent Colors
- Primary accent: `#D4A843` (crane gold / heavy machinery amber)
- Secondary accent: `#C9922A` (deeper amber for hover states and gradients)
- Border/grid lines: `#2E3036` (muted steel)

### Text
- Primary: `#F3F4F6` (clean technical off-white)
- Secondary: `#9CA3AF` (muted industrial silver-gray)

### Typography
- `Inter` (body, data text) and `Syne` (bold geometric structural headings) via Google Fonts `<link>`
- Fluid heading sizes using `clamp()` for responsive scaling
- Tracked-out uppercase for brand name and section labels

### Layout
- Blueprint grid background: CSS-generated fine, dense 1px grid lines at ~0.05 opacity using `linear-gradient` technique
- Mathematical spacing using consistent 8px base unit multiples
- Architectural grid alignment throughout

### Animations
- Scroll-triggered: fade-in + slide-up (translateY 24px to 0, opacity 0 to 1) using IntersectionObserver
- Transition duration: 0.6s ease-out, staggered per child element where applicable

---

## Responsive Behavior

- **Mobile (< 768px):** All grid sections collapse to a single column
- **Tablet (768px–1199px):** Maintain 3 columns for service cards and metric grids
- **Desktop (≥ 1200px):** Full layout as specified per section
- Smooth anchor scroll behavior via CSS `scroll-behavior: smooth`

---

## Page Sections

### 1. Sticky Navigation
- Fixed top nav, transparent on load
- Left: brand name `MAKHUNGA CRANE & ENGINEERING` in Syne, bold, tracked uppercase
- Right: dispatch status element `● DISPATCH STATUS: ACTIVE | JHB CONDUIT: < 24HRS` with pulsing amber dot
- Right: outline CTA button `"Request Operational Review"` anchoring to `#contact`
- After 80px scroll: `backdrop-filter: blur(12px)`, `background: rgba(10,10,11,0.92)`, `1px solid #2E3036` bottom border

### 2. Industrial Hero
- Full `100vh` section, blueprint grid over `#0A0A0B → #111113` gradient
- Headline: *"Zero variance. Uncompromised lifting. Maximum plant uptime."*
- Subheadline with exact specified copy
- Primary CTA `"Initiate Technical Site Review"` — solid amber, anchors to `#contact`

### 3. Core Services Grid
- Section label `"CORE CAPABILITIES"` + subheading *"What We Deliver"*
- 3-column grid (single column mobile)
- Card 1: Lifting Equipment Services (crane SVG icon)
- Card 2: Testing, Inspection & Compliance (shield-check SVG icon) + **Statutory Safety Color Chart Key** (Blue/Yellow/Red/Green swatches)
- Card 3: Engineering Support & Spares (gear SVG icon)
- Amber top-border accent and lift on hover

### 4. Compliance & Capability Split
- Heading: *"Built for plants that measure risk in seconds, not percentages."*
- Two-column layout (stacked mobile)
- Left: 4 amber checkmark items (operations requiring)
- Right: 3 muted dash items (not aligned with)

### 5. Technical Logistics Timeline
- Label `"OPERATIONAL SEQUENCE"` + subheading *"How We Execute"*
- 4 steps, horizontal track on desktop (vertical mobile), continuous golden line
- Steps: Site Asset Diagnostics, Component & Strain Mapping, Engineered Deployment Plan, Absolute Execution & Handover

### 6. Leadership & Accountability (NEW)
- 2-column split, minimalist, static, frontend-only
- Left: `"DIRECT ACCOUNTABILITY"` label + copy on owner-managed structure
- Right: two data-sheet style director blocks for Annalise Brown (Compliance Operations) and Chris Brown (Field Engineering Systems)

### 7. Credibility Metrics
- Heading `"OPERATIONAL CREDENTIALS"`
- 4-column grid (single column mobile)
- Metrics: `"28 Years"`, `"15–20 Years"`, `"LME 327"`, `"24-Hour"` with exact descriptors
- Large amber numbers, decorative background circle, label and descriptor

### 8. Interactive Site Self-Assessment
- Heading: *"Is your lifting infrastructure fully optimized?"*
- 8 interactive check-block divs with toggle states
- Live result feedback (0–2 low, 3–5 mid, 6–8 high) with color-coded border
- CTA button `"Secure Operational Review"`

### 9. Assessment Value Proposition Card
- Full-width highlight card, `#1A1A1D` bg, amber border
- Heading: *"The Makhunga Operational Assessment"*
- Scope matrix with 4 amber-indicator bullets
- CTA button `"Request an Operational Assessment"`

### 10. Contact Form — Dispatch Registration
- Section `id="contact"`
- Container: `#111113` bg, border, max-width 720px, centered
- Fields: Full Name, Company/Plant Name, Work Email, **Primary Infrastructure Category dropdown** (Overhead Gantries/Cranes, Hoists & Lifting Tackle, Custom Structural Fabrication, Statutory LME Inspection Only), Textarea
- Submit button `"Submit Technical Specifications"`
- Frontend-only success state with confirmation message

### 11. Final CTA Section
- Full-width `#17171A` bg
- Heading: *"When variance is not an option, precision is the only path forward."*
- CTA button + centered contact details (phone, email, address)

### 12. Footer
- `#0A0A0B` bg, top border
- Brand name, tagline, LME 327 registration line in amber, copyright
- No social links, no tracking scripts

---

## JavaScript Architecture

1. **IntersectionObserver:** Observe `.animate-on-scroll`, add `.is-visible`, staggered `transition-delay` for grid children
2. **Sticky nav scroll handler:** Toggle `.nav-scrolled` after 80px scroll (with `requestAnimationFrame` for performance)
3. **Self-assessment toggle logic:** Click handlers, toggle `.active`, recount, update result text and styling class live
4. **Form submission handler:** `preventDefault`, validate all required fields + email format, hide form, display success confirmation
5. **Smooth scroll:** Click handlers on all anchor CTA buttons to scroll to `#contact` with nav offset

---

## Authority Upgrades Incorporated

1. **Statutory Safety Color Chart Key** — rendered in Section 3, Card 2 as a miniature CSS legend with Blue/Yellow/Red/Green swatches representing active quarterly safety indicators
2. **Primary Infrastructure Category dropdown** — added to Section 9 contact form above the textarea with four specified options
3. **Dispatch Status element** — added to sticky nav as `● DISPATCH STATUS: ACTIVE | JHB CONDUIT: < 24HRS` with pulsing amber dot
4. **Leadership & Accountability section** — new minimalist 2-column section placed before the Metrics block with director data-sheet blocks for Annalise Brown and Chris Brown

---

## Output Requirements

- Complete, production-ready `.html` file
- Every section fully written with exact content — no placeholders, no lorem ipsum
- Fully responsive across mobile, tablet, and desktop
- Blueprint grid background applied to hero section using only CSS
- All hover, focus, and active states implemented
- Zero broken references, zero missing content, zero incomplete sections
