# Hartanah Notes — site cheat-sheet

Jekyll site on GitHub Pages. Same architecture as wan-aia.online, new design.

## Add a new post
Create a file in `_posts/` named `YYYY-MM-DD-your-slug.md`:

```
---
title: "Your Post Title"
date: 2026-07-15          # ALWAYS a valid date — "UNKNOWN" breaks the build
language: en              # en, bm, or en-bm
tags: [lelong]            # must match a file in tags/ to be clickable
image: /assets/your-slug/cover.png   # optional feed thumbnail
---

Post content here.
```

Put images/PDFs in `assets/your-slug/` and link them:
- Image: `![Alt text]({{ '/assets/your-slug/photo.png' | relative_url }})`
- PDF slip: copy the `<a class="attachment">` block from the sample lelong post

## Add a new topic/tag
1. Create `tags/newtag.md` (copy `tags/lelong.md`, change `tag:` and `permalink:`)
2. Add a line for it in `tags/index.md`

## Known gotchas (learned the hard way)
- `date: UNKNOWN` breaks the Jekyll build — always valid dates
- Pipe characters `|` in markdown link text break rendering (become tables) — use `&middot;` instead
- Posts MUST be in `_posts` (underscore) with dated filenames or they won't show
- Before pushing large PDFs: `git config http.postBuffer 524288000`
- zsh, not bash — no associative arrays in scripts

## When the custom domain goes live
In `_config.yml` change two lines:
- `url: "https://YOUR-DOMAIN.online"`
- `baseurl: ""`

Then add a `CNAME` file containing just the domain, set the domain in
repo Settings → Pages, and enforce HTTPS once the cert issues.

## Placeholders to replace
- `G-XXXXXXXXXX` in `_layouts/default.html` (2 places) — new GA4 property
- Site title/tagline in `_config.yml`
- Both sample posts and the sample cover/PDF in `assets/panduan-lelong/`
- `assets/og-image.png` once the final site name is chosen
