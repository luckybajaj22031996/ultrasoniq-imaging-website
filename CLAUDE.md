# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

UltraSoniq Imaging & Interventions — a static website for a sports injury imaging & pain clinic in Bhopal, led by Dr. Suvinay Saxena and Dr. Satya Jha.

- **Live URL:** https://www.ultrasoniqimaging.in
- **Netlify subdomain:** https://ultrasoniq-imaging.netlify.app (still works, redirects to www)
- **GitHub repo:** luckybajaj22031996/ultrasoniq-imaging-website

## Architecture

Single-page static site: one `index.html` file with all CSS and JS embedded inline. No build step, no framework, no dependencies.

**Images (repo root):**
- `img1.png` — 32×32 favicon
- `img2.png` — 48×48 nav logo
- `img3.jpg` — 424×500 Dr. Suvinay Saxena photo
- `img4.jpg` — 981×1472 Dr. Satya Jha photo
- `og-image.jpg` — OG/social share image (1200×630) — **not yet created, needs to be made**

**External images (Pexels CDN):**
- Hero: `pexels-photo-34778969.jpeg`
- Slideshow: 7108425, 34779532, 6285395, 7089333

**Fonts:** Google Fonts — DM Serif Display (weight 400 only, italic variant included) + Plus Jakarta Sans (400/500/600/700)

**Design tokens** (CSS variables in `:root`):
- Primary teal: `--primary: #0C7792`, `--primary-deep: #095E73`, `--primary-light: #F0F7F9`
- Neutral backgrounds: `--warm: #F7F8F9`, `--cream: #FCFCFD`
- Text: `--charcoal: #1A2332`, `--slate: #2D3748`, `--muted: #5A6577`
- Doctor colours: `--dr-suvinay: #0C7792`, `--dr-satya: #B5446E`, `--both: #6C5CE7`
- Typography: `--ff-display: 'DM Serif Display'`, `--ff-body: 'Plus Jakarta Sans'`

## Clinic Details (pulled from site content)

- **Address:** 7, Saket Nagar, Habib Ganj, Bhopal, MP 462024
- **Phone (landline):** 0755 4543589
- **WhatsApp:** +91 99810 86767 (used in all wa.me links — do not change)
- **Email:** ultrasoniqimaging@gmail.com
- **Hours:** Mon–Sat 12:00 PM–9:00 PM, Sun 10:00 AM–1:00 PM

## Key Rules

- **Never alter visible content** — doctor bios, qualifications, achievements, testimonials, service descriptions, or any body copy must not be changed unless explicitly asked. This has caused issues before.
- **WhatsApp links use +91 99810 86767** — do not change these even if the visible phone number changes.
- **DM Serif Display is weight 400 only** — never set font-weight other than 400 on elements using `--ff-display`.

## Page Structure (sections in order)

1. `<head>` — SEO meta, OG, Twitter Card, WebSite + MedicalClinic JSON-LD, canonical
2. Topbar — hours + phone
3. Nav — logo, links, Book Appointment CTA
4. `#home` — Hero with H1, stats, Pexels image
5. `#about` — Slideshow (CSS background-image, not `<img>`), about copy
6. `#services` — 6 service cards (H3 headings)
7. `#testimonials` — 6 Google review cards, scroll-snap
8. `#doctors` — CSS Grid cards (1fr/1.8fr), Dr. Suvinay + Dr. Satya
9. CTA section — WhatsApp + call buttons
10. `#contact` — hours, address, map iframe, contact details
11. Footer
12. WhatsApp float button
13. `<script>` — all JS inline at end of body

## SEO State (as of May 2026)

- Canonical: `https://www.ultrasoniqimaging.in/`
- `lang="en-IN"` on `<html>`
- Full OG + Twitter Card tags
- WebSite JSON-LD (name, alternateName, url)
- MedicalClinic + LocalBusiness JSON-LD (address, geo, hours, services, physicians)
- `sitemap.xml` and `robots.txt` in repo root
- Google Search Console: verified on `https://www.ultrasoniqimaging.in/`, sitemap submitted, indexing requested
- Google Site Verification meta tag present in `<head>`
- OG image (`og-image.jpg`) referenced in tags but **file does not exist yet**

## DNS / Hosting Notes

- Domain registrar: Hostinger
- Hosting: Netlify (auto-deploy on push to `main`)
- `www.ultrasoniqimaging.in` is the **primary domain** in Netlify — keep it this way
- `ultrasoniqimaging.in` (non-www) has a pending DNS verification issue in Netlify — do not switch primary away from www again
- All hardcoded URLs in code use `https://www.ultrasoniqimaging.in/`

## Development

```bash
# Local preview
python3 -m http.server 8000
# Then visit http://localhost:8000
```

No build, lint, or test commands exist.

## Deployment

Push to `main` triggers automatic Netlify deployment. No staging environment — changes go live immediately.
