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
├── form.html               # Intake form
├── styles.css              # Brand system (tokens, components)
├── assets/                 # Photography (players, gym, coaching)
├── fidonce-logo.avif       # Brand mark
├── vercel.json             # Clean URLs + cache headers
└── README.md
```

## Brand notes

- **Type:** futura-pt (via Adobe Typekit) — make sure the production domain is whitelisted in the kit's allowed-domains list before launch.
- **Colors:** `#000` (black), `#f7931d` (orange accent), `#f6f5f1` (paper). Defined as CSS custom properties in `styles.css`.
- **Voice:** uppercase, terse, brand-forward. "THE STANDARD OF CHESTER." Match this when adding new copy.
- **Pricing/age bands** (`$25` intro, `8–11` / MS / HS) appear in multiple pages — update all occurrences together.
