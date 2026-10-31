# aqwire.co (static mirror)

Rebuilt from Internet Archive / Wayback Machine captures of `aqwire.co`
(15 HTML pages, 100+ images, Tailwind CSS build — site was fully static).

## Publish to GitHub Pages

```bash
git init -b main
git add -A
git commit -m "Rebuild aqwire.co"
git remote add origin git@github.com:<you>/<repo>.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Deploy from a branch → `main` / `(root)`**.

`.nojekyll` is included so Pages serves every file as-is (needed for `src/`
and underscore-prefixed assets).

## Rebuild notes

- Sources: latest 200-status capture per URL from the Wayback CDX index
  (main pages: Nov 2025 – Jul 2026 era; news articles: Jan 2026 era).
- Raw captures fetched via the `id_` endpoint (no Wayback toolbar injected;
  zero `web.archive.org` references remain).
- Fixed two bugs inherited from the original site: header nav used `./`-relative
  links that 404'd from subpages, and a Terms-of-Service link pointed to
  `../Privacy Policy/` (nonexistent path). Both now resolve.
- Filenames with spaces are duplicated in literal-space and `%20` forms so the
  site works on any static server (browsers encode spaces; servers differ on
  decoding).
- 16 images were never captured by the Internet Archive in any form and the
  origin domain is offline. They are replaced with branded SVG placeholders
  (`*dashboard*`, `barChart`, news article images, `_Background mask`) or
  substituted from the nearest archived equivalent (`jCB .png` ← `jCB.png`,
  `Star icon.png` ← `star-icon.png`, app-store badges ← hyphenated names).
- `robots.txt` from the original site intentionally omitted.
- External links (app.aqwire.io, pay.aqwire.io, socials, Intercom help center,
  Google Fonts) are kept as-is and may be dead.
