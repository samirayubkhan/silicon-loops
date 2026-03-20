# Silicon Loops Website — Context

## Overview

Static landing page for Silicon Loops (siliconloops.com) — an AI automation agency. The site is a single HTML file using Tailwind CSS via CDN, hosted on Vercel.

## File Structure

```
Website/
├── index.html        # Landing page (Tailwind CSS, Manrope font, dark theme)
├── .env.local         # Local env vars (Vercel OIDC token, Namecheap API key) — gitignored
├── .gitignore         # Ignores .vercel/ and .env*.local
├── .vercel/           # Vercel project config (gitignored)
└── context.md         # This file
```

## Hosting & Deployment

- **Platform:** Vercel (project: `silicon-loops`, owner: `samirayubkhan`)
- **GitHub repo:** https://github.com/samirayubkhan/silicon-loops
- **Domain:** siliconloops.com (DNS managed on Namecheap)
- **Framework:** None — static HTML, no build step

### How to Deploy

Pushing to `main` on GitHub triggers an automatic Vercel deploy (once Git integration is connected in Vercel dashboard).

```bash
# From the Website/ directory:
git add <files>
git commit -m "description of changes"
git push origin main
```

For a manual deploy without pushing to GitHub:

```bash
vercel --prod
```

### DNS Records (Namecheap → Advanced DNS)

| Type  | Host           | Value                                    | TTL   |
|-------|----------------|------------------------------------------|-------|
| A     | @              | 76.76.21.21                              | 1 min |
| CNAME | www            | cname.vercel-dns.com                     | 1 min |
| CNAME | 7jocynmch22e   | gv-7vkjkr4yzj2h4i.dv.googlehosted.com.  | 1 min |

> The third CNAME is Google domain verification — do not remove.

## Tech Stack

- **HTML** with inline Tailwind config (dark mode, custom Material Design 3 color tokens)
- **Tailwind CSS** via CDN (`cdn.tailwindcss.com` with forms + container-queries plugins)
- **Fonts:** Manrope (text), Material Symbols Outlined (icons)
- **No JS framework, no build tools, no package.json**

## Routing Notes

- Single-page static site — all traffic serves `index.html`
- Vercel handles this by default for static deployments (no `vercel.json` needed)
- If additional pages are added, place them as `.html` files in the root (e.g., `about.html` → `siliconloops.com/about`)
