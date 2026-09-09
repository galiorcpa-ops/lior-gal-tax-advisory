# Lior Gal Tax Advisory — Website

Plain HTML/CSS, no build step. Hebrew is the default language; every page has a full English mirror under `en/`. Live domain: **gal-tax.com**.

## Structure

```
index.html, services.html, about.html, contact.html   Hebrew pages (default)
articles/index.html        Hebrew "Insights" list + "Published Elsewhere" section
articles/template.html      Starting point for a new Hebrew article

en/index.html, en/services.html, en/about.html, en/contact.html   English pages
en/articles/index.html      English mirror of Insights
en/articles/template.html    Starting point for a new English article

assets/style.css            All styling — colors, fonts, layout, RTL/LTR handling
assets/main.js               Mobile menu behavior
assets/logo-transparent.png  Your logo (transparent background)
assets/lior-gal.jpg          Your headshot

robots.txt, sitemap.xml      Search-engine files (see SEO section below)
CNAME                        Tells GitHub Pages to serve this repo at gal-tax.com
```

Every Hebrew page links to its English counterpart (and back) via the small "English" / "עברית" button in the top navigation.

## Design system

Ink (near-black) + oxblood (deep wine red) on a warm paper background — a "tax-file / ledger" motif (stamped tab labels, numbered rows, a filed-corner portrait) instead of a generic muted sage-and-gold look. The logo keeps its own navy/gold mark, used only as an image — it does not drive any of the site's own colors.

- Headings: **David Libre** (a Hebrew-rooted serif with real character)
- Body: **Assistant**
- All colors and fonts are defined once, as CSS variables at the top of `assets/style.css` — change them there and the whole site updates.

## Publishing a new article later

**Hebrew:**
1. Copy `articles/template.html` to a new file, e.g. `articles/פיצול-חברות.html`.
2. Edit the title, date, and body content inside it.
3. Open `articles/index.html`, add one card inside `<div id="article-list">` (a commented example is right there), and remove the "new content coming" placeholder once you have your first article.

**English:** same steps, inside the `en/` folder.

If an article only exists in one language, that's fine — just don't add a language-toggle link to a page that doesn't exist yet.

## "Published Elsewhere" section

On the Insights page, below your own articles, there's a second list for linking out to things you've published on other platforms (LinkedIn posts, interviews, guest articles). Add a card inside `<div id="featured-elsewhere">` the same way — a commented example is included in the file.

## SEO — what's already in place

- Hebrew and English versions are linked with `hreflang` tags, so Google shows people the right language version.
- Every page has a title, meta description, and Open Graph tags (so links look right when shared on LinkedIn/Facebook).
- The homepage includes structured data (JSON-LD) describing you as a professional service — this is what lets Google and AI search tools understand who you are and what you do, not just read your text.
- `sitemap.xml` lists every page in both languages; `robots.txt` points search engines to it.

**Still to do once you're live:**
- Submit the site in [Google Search Console](https://search.google.com/search-console) and submit `sitemap.xml`.
- Create or update your Google Business Profile with the same name, phone, and address details as the site (this matters a lot for local search).
- Link to the site from your LinkedIn profile and any other professional listings — inbound links are one of the strongest ranking signals.

## Deploying to GitHub Pages with your gal-tax.com domain

1. Create a new repository (e.g. `lior-gal-tax-advisory`) and upload everything in this `site/` folder, keeping the folder structure intact (`assets/`, `articles/`, `en/`, and the `CNAME` file must stay alongside the root HTML files).
2. In the repo settings, enable **GitHub Pages** → deploy from the `main` branch, root folder.
3. In the repo settings' Pages section, under "Custom domain", enter `gal-tax.com` (this matches the `CNAME` file already included) and save.
4. At your domain registrar (wherever you bought gal-tax.com), add these DNS records so the domain points at GitHub Pages:
   - Four **A** records for the root domain (`@` / `gal-tax.com`) pointing to: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - A **CNAME** record for `www` pointing to `<your-username>.github.io`
5. DNS changes can take anywhere from a few minutes to ~24 hours to propagate. Once GitHub detects it, tick "Enforce HTTPS" in the same Pages settings so the site serves over `https://gal-tax.com`.

## Notes

- Fonts (David Libre + Assistant) load from Google Fonts and support both Hebrew and English — an internet connection is needed for them to render; there's a plain serif fallback if that's ever blocked.
- The logo file used avoids initials, per your instruction — it's the full wordmark, as an image only.
