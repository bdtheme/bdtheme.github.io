# BDtheme — GitHub Pages + Blogger Backend

This is a static front-end adaptation of the supplied BDtheme Blogger XML theme. The existing Blogger site remains the content backend and is not modified. Product/post cards are loaded from the public Blogger JSONP feed; product links open their original Blogger post. Cart data is stored in each visitor's browser, and checkout creates a WhatsApp order message.

## Deploy to GitHub Pages
1. Create a GitHub repository (for example `bdtheme-store`).
2. Upload **all files and folders** from this package to the repository root.
3. In GitHub: Settings → Pages → Deploy from a branch → `main` → `/ (root)` → Save.
4. Open the published Pages URL after deployment.

## Required configuration
Edit `config.js` before publishing:
- `blogUrl`: keep `https://dukan-shop.blogspot.com` (or your exact Blogger URL).
- `siteName`: your store name.
- `whatsappNumber`: international format digits only, e.g. Bangladesh `8801XXXXXXXXX` (no `+`, spaces, or hyphens). Replace the placeholder.
- `currencySymbol` and `currencyCode`: currently preserved as `$` / `USD` from the supplied theme. Change if your store uses BDT.
- `collections`: each `label` must match a Blogger post label exactly. The source theme currently had `theme`, `Mens`, `theme`, `theme`; these defaults are preserved pending your label choices.
- `categories` and `menu`: edit names/labels/links as needed.

## Blogger feed requirements
The Blogger blog must be public and its posts feed accessible. This version uses Blogger's JSONP feed endpoint to avoid browser cross-origin fetch restrictions. If the feed is disabled or restricted, posts cannot load.

## Important differences / boundaries
- Blogger remains your post editor and backend. This GitHub version reads public post data; it does not write posts into Blogger.
- Clicking a post/product opens its original Blogger permalink, so the original Blogger article page and comments remain available.
- Blogger Layout Editor widgets and XML-only template tags cannot run on GitHub Pages; the front-end settings are now in `config.js`.
- Static GitHub Pages does not provide server-side checkout, order database, customer accounts, or payment processing. WhatsApp checkout is retained as a client-side handoff.
- The visual styling is extracted from the supplied theme CSS. Some Blogger-only post/single-page and widget behavior has been replaced with feed-driven static cards.

## Files
- `index.html` — static site shell
- `assets/css/style.css` — extracted BDtheme styling with Blogger variables converted to CSS values
- `assets/js/app.js` — Blogger JSONP feed loader, search, collections, cart, WhatsApp checkout, dark mode, responsive menu
- `config.js` — site and Blogger connection settings
