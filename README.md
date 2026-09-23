# leasematching.com — shutdown notice

The static page that replaces the Lease Matching service at
**www.leasematching.com**. One HTML file, no build step, no JavaScript,
no tracking.

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire page — markup and inline CSS |
| `CNAME` | Custom domain for GitHub Pages (`www.leasematching.com`) |
| `.nojekyll` | Tells Pages to serve the files as-is |
| `assets/logo.png` | Wordmark for the header band |
| `assets/favicon.png` | Browser icon |
| `assets/og.jpg` | Preview image for links shared on social media |

The images are copies, committed to this repo on purpose. The originals
were served from Bubble's CDN, which stops working once the Bubble
subscription is cancelled — this page must not depend on anything being
shut down.

## Design

Taken from the live site so the notice still looks like Lease Matching:

- Navy `#25577c` (header band, matches the logo artwork exactly), brand
  navy `#31577d`, teal `#38a3a5`
- Text `#17212a` on headings, `#364755` on body
- Poppins, loaded from Google Fonts, falling back to the system UI font

## Publishing

Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder
`/ (root)`. The repo must be public for Pages on a free plan.

DNS, at whoever hosts the leasematching.com zone:

```
www    CNAME   leasematching.github.io.

@      A       185.199.108.153
@      A       185.199.109.153
@      A       185.199.110.153
@      A       185.199.111.153
```

The `www` CNAME is what `CNAME` in this repo expects. The four A records
make the bare `leasematching.com` work too — people type it without the
`www`. Once DNS has propagated, tick **Enforce HTTPS** in Settings →
Pages; the certificate is issued automatically and free.

## Editing the text

The copy lives directly in `index.html` between `<main>` and `</main>`.
Edit, commit, push — Pages redeploys within a minute.
