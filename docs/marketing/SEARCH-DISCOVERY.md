# Free search discovery checklist

Fixed monthly cost target: **$0**. No paid SEO tools.

## Structured data note (Google SoftwareApplication)

Google’s Software App rich-result docs (reviewed 31 Oct 2026) require `name`, `offers.price`, and either `aggregateRating` or `review`.

LocalFirst Migrator currently has **no authentic public reviews/ratings**. Fabricating them is forbidden.

The homepage includes truthful `SoftwareApplication` JSON-LD (name, OS, version, offer $29 USD, description) **without** ratings. That may help crawlers understand the page but **will not** unlock review-star rich results until real reviews exist and are marked up honestly.

## Operator steps (manual)

### Google Search Console

1. Add property: `https://matt1085.github.io/localfirst-migrator/`
2. Verify via HTML file upload **or** meta tag.
3. Submit sitemap: `https://matt1085.github.io/localfirst-migrator/sitemap.xml`
4. Use URL Inspection on `/`, `/features/`, `/bazzite-migration/`, `/flatpak-migration/` and request indexing.

**Meta tag readiness:** once Google gives you a verification token, add to each page `<head>` (or homepage only if sufficient):

```html
<meta name="google-site-verification" content="PASTE_TOKEN_HERE">
```

Do not commit a fake token. Paste the real token when Search Console provides it.

**Alternate:** upload `googleXXXXXXXX.html` verification file to the repo root and push (GitHub Pages will serve it).

### Bing Webmaster Tools

1. Import from Google Search Console if available, or verify the Pages site.
2. Submit the same sitemap URL.
3. Request indexing for key URLs.

### GitHub repository polish

- Description: `Local-first Flatpak migration for Bazzite. Preview, migrate, rollback. $29 founder.`
- Website: `https://matt1085.github.io/localfirst-migrator/`
- Topics (suggestions): `bazzite`, `flatpak`, `linux`, `migration`, `local-first`
- Social preview: set repository social image to `assets/og-card.jpg` in GitHub repo settings if desired (or rely on og tags on the Pages site).

### After first posts

- Share the canonical site URL (not only the Stripe link) so links consolidate.
- Do not buy backlinks or paid directories.

## Sitemap URLs (current)

- https://matt1085.github.io/localfirst-migrator/
- https://matt1085.github.io/localfirst-migrator/features/
- https://matt1085.github.io/localfirst-migrator/bazzite-migration/
- https://matt1085.github.io/localfirst-migrator/flatpak-migration/
- https://matt1085.github.io/localfirst-migrator/privacy/
- https://matt1085.github.io/localfirst-migrator/refunds/
- https://matt1085.github.io/localfirst-migrator/terms/
- https://matt1085.github.io/localfirst-migrator/support/
