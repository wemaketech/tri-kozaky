# Tri Kozaky

Website for Tri Kozaky Club, hosted at [tri-kozaky.com](https://tri-kozaky.com).

## How it works

The actual site content is built and hosted on [tri-kozaky.onepage.me](https://tri-kozaky.onepage.me/). This repo deploys to **Vercel**, which acts as a reverse proxy — all requests to `tri-kozaky.com` are transparently rewritten to `tri-kozaky.onepage.me` via the `vercel.json` rewrites config. The user never sees the onepage.me domain.

### Why not an iframe or GitHub Pages?

Previously, this repo used GitHub Pages with an iframe pointing to onepage.me. That broke because onepage.me sets a `Content-Security-Policy: frame-ancestors 'self'` header, which blocks embedding in iframes on other domains. A simple redirect was considered but would change the URL in the browser. The Vercel rewrite approach keeps the URL as `tri-kozaky.com` while serving onepage.me content.

## Setup

- **Vercel project** imports this GitHub repo
- **Custom domain** `tri-kozaky.com` is configured in Vercel project settings → Domains
- **DNS** points to Vercel (A record `76.76.21.21` or CNAME `cname.vercel-dns.com`)
- **`vercel.json`** contains the rewrite rule that proxies all requests to onepage.me

## If something breaks

1. Check if [tri-kozaky.onepage.me](https://tri-kozaky.onepage.me/) is still up
2. Check the Vercel dashboard for deployment status and errors
3. Verify DNS is still pointing to Vercel (not GitHub Pages)