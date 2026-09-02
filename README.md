# Academic website preview

Static GitHub Pages preview for Stefano Grancini. It is deliberately independent of the JMP repository and has no custom-domain configuration.

## Local preview

From this directory: `python3 -m http.server 8000`, then open `http://localhost:8000`.

## Domain configuration

The preview base URL is `https://sgrancini.github.io/academic-website-preview/`. Do not add canonical tags for the future production domain while the preview is live. At migration approval, update the base URLs in `robots.txt`, `sitemap.xml`, and JSON-LD in `index.html`, add per-page canonical tags, and only then configure the custom domain in GitHub Pages. See `DOMAIN_MIGRATION.md`.
