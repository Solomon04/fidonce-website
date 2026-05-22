# FiDonce Website

Static marketing site for FiDonce Player Development — Chester, PA.

## Stack

- Plain HTML + CSS, no build step
- Adobe Typekit (Futura · kit `spc3qbq`)
- Deployed on Vercel as static files

## Pages

| File | URL | Purpose |
|------|-----|---------|
| `index.html` | `/` | Homepage — Develop people. |
| `offerings.html` | `/offerings` | Programs · Training, AAU, Facility |
| `facility.html` | `/facility` | Court rentals, events, training add-ons |
| `about.html` | `/about` | The story · Founder Eric Evans |
| `form.html` | `/form` | $25 intro evaluation intake |

Clean URLs are enabled in `vercel.json`, so `/offerings` resolves to `offerings.html` in production.

## Run locally

```
python3 -m http.server 8000
```

Open http://localhost:8000. Note that local dev uses the `.html` extension (`/offerings.html`), since the clean-URL rewrite only runs on Vercel.

## Deploy

Connected to Vercel via Git. Push to `main` → auto-deploys. First-time setup:

1. Import the repo at [vercel.com/new](https://vercel.com/new)
2. Framework preset: **Other** (or "Static")
3. No build command, no output directory — Vercel serves the repo root
4. Add the custom domain in Project Settings → Domains

## Project layout

```
.
├── index.html              # Homepage
├── offerings.html          # Programs page
├── facility.html           # Court rentals, events, add-ons
├── about.html              # About / founder story
├── form.html               # Intake form
├── styles.css              # Brand system (tokens, components)
├── assets/                 # Photography + og-image.jpg
├── fidonce-logo.avif       # Brand mark
├── favicon.png             # 32×32 PNG favicon
├── apple-touch-icon.png    # 180×180 iOS home-screen icon
├── sitemap.xml             # XML sitemap (submit to Search Console)
├── robots.txt              # Allow all, points to sitemap
├── vercel.json             # Clean URLs + cache headers
└── README.md
```

## SEO

Each page ships with:
- Unique `<title>`, `<meta description>`, and `<meta keywords>`
- Canonical URL
- Open Graph + Twitter Card meta (OG image lives at `/assets/og-image.jpg`)
- Geo meta (US-PA / Chester) for local search
- Page-specific JSON-LD structured data:
  - **Home:** `LocalBusiness` + `SportsActivityLocation`, `Person` (Eric Evans), `WebSite`
  - **Programs:** `BreadcrumbList`, three `Service` entries (Training, AAU, Facility) + `Offer`
  - **Form:** `BreadcrumbList`, `ContactPage`, `Offer` ($25 intro)

After deploying, submit `https://fidonce.com/sitemap.xml` to Google Search Console (Marketing → SEO Tools → Sitemap submission). The site is referenced as `https://fidonce.com` throughout — if the production domain differs, find-replace it across `*.html`, `sitemap.xml`, and `robots.txt`.

## Brand notes

- **Type:** futura-pt (via Adobe Typekit) — make sure the production domain is whitelisted in the kit's allowed-domains list before launch.
- **Colors:** `#000` (black), `#f7931d` (orange accent), `#f6f5f1` (paper). Defined as CSS custom properties in `styles.css`.
- **Voice:** uppercase, terse, brand-forward. "THE STANDARD OF CHESTER." Match this when adding new copy.
- **Pricing/age bands** (`$25` intro, `8–11` / MS / HS) appear in multiple pages — update all occurrences together.
