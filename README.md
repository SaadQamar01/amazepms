# Amaze PMS

Marketing website for **Amaze Property Management Solutions Pvt Ltd** — an integrated facility management company offering in-house Security, Housekeeping, MEP/Technical, Pest Control, Landscaping, Parking, and related services across PAN India.

This application is a multi-page marketing site built with Next.js. It presents the brand, services, clients, recruiting approach, gallery, careers, and contact information with smooth scroll and motion-led UI.

---

## What This Application Does

- Introduces Amaze PMS as a premium, in-house facility management partner
- Showcases service lines, partner companies, and client portfolios
- Explains recruiting strategy, skill development, audits, and operational strength
- Displays on-site gallery moments with a lightbox viewer
- Provides careers and contact entry points for leads and applicants
- Ships as a static/SSR marketing site ready for Vercel production

There is **no payment flow**, **no authentication**, and **no database** in the current build. Content is mostly static TypeScript data.

---

## Pages

| Route | Purpose |
|---|---|
| `/` | Home — hero, about highlight, why choose us, clients teaser, CTA |
| `/about` | Company intro, mission / vision / values, industry segments |
| `/services` | Primary & extended service catalogue + service partners |
| `/clients` | Client logos, categories, and distribution |
| `/recruitments` | Manpower sources, skill development, audits, functional approach |
| `/strength` | Operational strengths and differentiators |
| `/gallery` | Photo grid (`320px` × `35vh`) with lightbox navigation |
| `/careers` | Careers messaging and application guidance |
| `/contact` | Contact details, map, and enquiry path |

Shared chrome on every page:

- Sticky **Navbar** (primary links + More dropdown + phone CTA)
- **Floating UI** helpers
- **Smooth scroll** (Lenis)
- **Footer** (on page layouts that include it)

---

## Tech Stack

| Layer | Choice |
|---|---|
| Framework | Next.js `16` (App Router) |
| UI | React `19`, TypeScript |
| Styling | Tailwind CSS `4` |
| Motion | Framer Motion |
| Smooth scroll | Lenis |
| Icons | Lucide React |
| Font | Geist (via `next/font`) |

---

## Brand Palette

Defined in `src/app/globals.css`:

| Token | Value | Use |
|---|---|---|
| Navy / ink | `#1a1a5c` | Primary brand, text, surfaces |
| Peach / cyan accent | `#e89172` | Accents, hovers, CTAs |
| Mist background | `#fbf9fe` / `#f6f4fb` | Page background |

Keep new UI aligned with these tokens (`text-ink`, `bg-cyan`, `text-cyan`, etc.) instead of introducing one-off colours.

---

## Project Structure

```text
src/
  app/                  # App Router pages + layout + globals.css
  components/           # Page sections and shared UI
    about/
    careers/
    clients/
    contact/
    gallery/
    recruitments/
    services/
    strength/
    ui/
  lib/
    content.ts          # Almost all marketing copy & lists
    animations.ts       # Shared motion helpers / easings
public/                 # Logos, gallery images, favicons, static assets
```

### Important files

- `src/lib/content.ts` — edit copy, services, clients, gallery captions, presence, etc.
- `src/components/Navbar.tsx` — navigation links and phone CTA
- `src/app/layout.tsx` — root layout, metadata, favicons, global providers
- `public/gallery/` — gallery images
- `public/services/logos/` — service and partner artwork

---

## Local Setup

### Requirements

- Node.js 18+ (recommended: current LTS)
- npm

### Install

```bash
npm install
```

### Development server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

### Production build (local)

```bash
npm run build
npm start
```

### Lint

```bash
npm run lint
```

---

## Content Updates (How To)

| Task | Where |
|---|---|
| Change homepage / about copy | `src/lib/content.ts` + related section components |
| Add / remove a service | `SERVICE_PAGE_PRIMARY` / `SERVICE_PAGE_MORE` in `content.ts` + logo under `public/services/logos/` |
| Update client lists / logos | `CLIENT_CATEGORIES` (and related exports) in `content.ts` + assets in `public/` |
| Add gallery photos | Put images in `public/gallery/`, then add entries to `GALLERY_IMAGES` in `content.ts` |
| Update phone / contact details | Navbar, Footer, and contact components / `content.ts` as applicable |
| Change page SEO titles | Each route’s `page.tsx` metadata + root `layout.tsx` |

After content edits, refresh the local site to verify layout and image aspect behaviour.

---

## Git & Deployment

### Production GitHub repository

Production deploys from:

https://github.com/SaadQamar01/amazepms.git

```bash
git remote -v
# origin should be https://github.com/SaadQamar01/amazepms.git
```

### Pushing to production

```bash
git add .
git commit -m "Your message"
git push origin main
```

If the Vercel project is connected to this repository’s `main` branch, a **production deployment** starts automatically after a successful push.

### Vercel

1. Project linked to `SaadQamar01/amazepms`
2. Framework preset: **Next.js**
3. Build command: `npm run build`
4. Output: Next.js default (no special env vars required for the current marketing site)

Optional overrides (only if needed later):

- Environment variables go in the Vercel project settings
- Preview deployments are created for non-`main` branches / PRs when enabled

---

## Scripts Reference

| Command | Description |
|---|---|
| `npm run dev` | Start local development server |
| `npm run build` | Create production build |
| `npm start` | Serve the production build |
| `npm run lint` | Run ESLint |

---

## Notes & Conventions

- Prefer updating `src/lib/content.ts` for marketing text before hard-coding strings in components
- Keep animations consistent with helpers in `src/lib/animations.ts`
- Gallery tiles are intentionally fixed at **width `320px`** and **height `35vh`**, left-aligned in a wrapping row
- Do not reintroduce payment / Stripe routes unless product requirements change
- Before pushing for production, confirm `origin` points at **SaadQamar01/amazepms**

---

## Support Contact (Company)

Use the contact details shown on `/contact` and in the site footer/navbar phone CTA for public enquiries.

---

## License

Private project for Amaze Property Management Solutions. All rights reserved unless otherwise agreed.
