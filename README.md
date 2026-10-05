# PawPath

Responsive GitHub Pages version of the PawPath Framer site.

**Live:** <https://mypawpath.github.io/>

## How it deploys

The repository is named `mypawpath.github.io`, so GitHub Pages serves it at the
account root rather than under a `/pawpath/` subpath. Every asset in the page is
referenced with a relative path, so the site works at either location.

`.github/workflows/pages.yml` deploys on every push to `main` (and can be run
manually via `workflow_dispatch`). It sets `enablement: true`, so Pages turns
itself on the first time the workflow runs — there is nothing to click in
`Settings > Pages`.

## Files that make up the site

| File | Role |
| --- | --- |
| `index.html` | The whole page |
| `styles.css` | Base layout and type |
| `git-original-sections.css` | Section layouts |
| `polish.css` | Visual polish and responsive award/hero treatments |
| `responsive-fixes.css` | Small-screen corrections, loaded last |
| `script.js` | Scroll and footer-visibility behaviour |
| `assets/` | Product shots, team photos, award logos |

All four stylesheets are required — the page looks broken without any one of
them. They are cache-busted by query string in `index.html`; bump the `?v=`
value when you change one.

`.gitignore` keeps the local design-review screenshots out of the repository.
The Pages workflow uploads the entire checkout (`path: "."`), so anything
committed at the root ships with the site.

## Local preview

Because this is a static site, you can open `index.html` directly in a browser.
For a local server preview:

```bash
python3 -m http.server 8000
```
