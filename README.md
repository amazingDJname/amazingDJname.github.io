# HAN: the website

This repository is the website. GitHub Pages serves every file in it exactly as it is, at https://amazingdjname.github.io and, once its DNS records exist, at https://h-a-n.download. There is nothing to install or build. A page's address is its place in the folder.

| Address | File | What it is |
|---|---|---|
| `/` | `index.html` | Front page |
| `/ji-ify/` | `ji-ify/index.html` | JI-ify, version 16 |
| `/ji-ify/#perf` | the same file | JI-ify's performer window |
| `/ji-ify/manual/` | `ji-ify/manual/index.html` | The JI-ify manual, written by hand; its two staff figures are drawings copied out of JI-ify |
| `/licenses/` | `licenses/index.html` | Credits, with the two font licenses beside it |
| any wrong address | `404.html` | "No page at this address" |

`assets/` holds what the site's own pages share: `site.css` (layout, colours, type sizes), `fonts.css` and `fonts/` (IBM Plex), `notation-font.css` (the music glyphs for the front-page figure) and `favicon.svg`.

## How it is put together

- **Each tool or piece lives in its own top-level folder** and brings its own styles and scripts. JI-ify is one self-contained file. Nothing a piece does can disturb another page, and its address does not have to change when the rest of the site is reorganised around it.
- **The site's own pages** (front page, credits, 404) share `assets/site.css`. The colours are five values at the top of that file, with a dark set just below. Changing them re-skins those pages.
- **Links are relative**, so the folder works at the top of a domain, inside a sub-folder, and opened straight from disk. The one exception is `404.html`, which assumes the site sits at the top of its domain.
- **Nothing loads from other sites.** The fonts are served from here. There are no analytics, cookies or trackers.

## How it is published

- **Host.** GitHub Pages publishes the `main` branch as it is (repository Settings → Pages: Source "Deploy from a branch", branch `main`, folder `/ (root)`). A change committed to `main` is live within about ten minutes. ([Publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site))
- **`.nojekyll`** tells GitHub to serve the files untouched.
- **Domain.** `h-a-n.download` is registered at Cloudflare, which also holds its DNS records. The site needs five: an `A` record for the bare domain to each of `185.199.108.153`, `185.199.109.153`, `185.199.110.153` and `185.199.111.153`, and a `CNAME` record for `www` to `amazingdjname.github.io`. All five are set to **DNS only**: with Cloudflare's proxy on, GitHub cannot issue the site's HTTPS certificate. ([Custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site), [Cloudflare DNS records](https://developers.cloudflare.com/dns/manage-dns-records/how-to/create-dns-records/))
- **`CNAME`** (the file) is written by GitHub when the custom domain is saved under Settings → Pages. It holds one line, `h-a-n.download`.
- **Limits** ([GitHub Pages limits](https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits)): the published site may be at most 1 GB, with a soft cap of 100 GB of traffic a month, and it may not be run as a shop or a paid service. Large audio and video belong on a media host, embedded here.

## Looking at it offline

Download the repository and double-click `index.html`. The pages link to each other from disk as they do online. (Checked in Chromium. Another browser may refuse to load the text fonts from disk and show its own instead; the notation is unaffected.)

## Adding to it

- **A new tool or piece:** make a folder with its own `index.html`, then add an `<article class="entry">` to the front page (copy the JI-ify one).
- **A new text page** (about, works, contact): copy `licenses/index.html` into a new folder and replace the text.
- **A new version of JI-ify:** `ji-ify/index.html` is produced from a JI-ify build by a packaging script kept outside this repository (`package_site.py` in the JI-ify folder), together with the browser checks that are run before publishing.

## What came from elsewhere

- IBM Plex Sans and IBM Plex Mono, © 2017 IBM Corp., SIL Open Font License 1.1, unmodified (`licenses/IBM-Plex-OFL.txt`).
- The music glyphs are "JIify Notation", 61 glyphs taken from Bravura 1.482, © Steinberg Media Technologies GmbH, SIL Open Font License 1.1. The license reserves the name Bravura, so the subset carries its own name (`licenses/Bravura-OFL.txt`).
- The accidentals are those of the Helmholtz-Ellis JI Pitch Notation (Marc Sabat and Wolfgang von Schweinitz; revised 2020 with Thomas Nicholson).
