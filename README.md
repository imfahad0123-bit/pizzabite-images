# Pizza Bite — Customer Website (new staged repository)

Public repository for the Pizza Bite customer-facing website: landing page, menu, deals, cart, checkout and order tracking, plus the public website assets and future Admin-published images.

## Repository role

This repository (`imfahad0123-bit/pizzabite-images`) is the **new staged / main website repository** chosen ahead of the GitHub-account migration. It is structured as a complete website repository now so the site and its assets can migrate together later.

| | |
| --- | --- |
| **Current live / rollback repository** | `imfahad0123-bit/pizzaBite` — untouched, still the live reference until this repository is independently verified |
| **This repository** | staged, not published |
| **Hosting** | none enabled — no GitHub Pages, no Vercel, no DNS or domain change |
| **Status** | repository preparation and verification only |

Nothing has been switched over. This repository does not serve traffic.

## Structure

```text
.
├── index.html
├── README.md
└── assets/
    └── images/
        ├── branding/    # logo / brand marks
        ├── landing/     # landing hero, "How to Order" illustrations, menu-page hero
        ├── menu/        # menu category artwork
        ├── deals/       # deal / combo artwork
        └── svg/         # standalone SVG assets (none yet — see "Known open items")
```

`hero.jpg` and `menu-hero.jpg` are **files inside** `assets/images/landing/`. There is no `hero/` or `menu-hero/` folder.

## About this build

- The website is a **single self-contained HTML file**. CSS lives in one `<style>` block and JavaScript in one `<script>` block, both inside `index.html`. This architecture is intentional and is kept as-is — there is no build step, no bundler and no dependency installation.
- Menu food photography and deal artwork are loaded at runtime from remote CDNs and from the public menu API, so `assets/images/menu/` and `assets/images/deals/` are empty by design.
- The Pizza Bite logo in the top bar is embedded directly in the HTML as a `data:` URI, so `assets/images/branding/` needs no file for the current build.
- Icons and small graphics are **inline `<svg>` blocks inside `index.html`** (13 of them). The site references no standalone `.svg` files, which is why `assets/images/svg/` exists but is empty.

## Image files in this repository

| Path | Purpose |
| --- | --- |
| `assets/images/landing/menu.png` | "How to Order" step — Choose |
| `assets/images/landing/add-to-cart.png` | "How to Order" step — Add |
| `assets/images/landing/order-now.png` | "How to Order" step — Order |
| `assets/images/landing/app.png` | "How to Order" step — Enjoy |
| `assets/images/landing/hero.jpg` | Landing page hero, published by the Admin Panel — **test artwork** |
| `assets/images/landing/menu-hero.jpg` | Menu page hero, published by the Admin Panel — **test artwork** |

> **`hero.jpg` and `menu-hero.jpg` are TEST ARTWORK.** Both files currently contain the
> same test image, uploaded to prove the Admin publishing path end to end. They are at
> the correct production-format paths, but they are **not** the final artwork. See
> `assets/images/landing/HERO_ARTWORK_TEST_ONLY.md`.

Approved destination directories for Admin-published images:

```text
assets/images/landing/
assets/images/menu/
assets/images/deals/
assets/images/branding/
```

Nothing outside those directories can be written by the Admin, and no path is taken from
the browser — the server derives each destination from its own slot configuration and
checks it against that allowlist.

## Admin GitHub publishing configuration

The Admin Panel publisher targets this repository:

```text
Owner:       imfahad0123-bit
Repository:  pizzabite-images
Branch:      main
```

Allowed hero destinations:

```text
Landing Hero  ->  assets/images/landing/hero.jpg
Menu Hero     ->  assets/images/landing/menu-hero.jpg
```

The GitHub token is held only as a server-side Script Property. It is never present in
this repository, in the served page, in API responses or in logs.

## Running locally

Any static file server works:

```bash
npx serve .
```

Then open the served page in a browser.

## Known open items

1. **`pizza_bite_gate_bg.jpg`** (fulfillment-gate / hero fallback background) is referenced by `index.html` but is not present in this repository, nor anywhere in the project working files. It has **not** been substituted with any other image. This is tracked as an open item rather than silently replaced.
2. **`assets/images/svg/` is empty.** The site has no standalone SVG asset files; all 13 SVGs are inline in `index.html`. The folder exists so the target structure is in place.
3. **Hero artwork is test artwork.** `hero.jpg` and `menu-hero.jpg` need real artwork before this repository can go live.

## What has deliberately not been done

- GitHub Pages not enabled; no Vercel, hosting, DNS or domain change.
- The live repository `imfahad0123-bit/pizzaBite` was not modified, renamed, redirected or deleted.
- Production Admin, production Apps Script, POS, backend and Google Sheets were not changed.
- The GitHub account migration has not been performed.

## Notes

- This repository contains **public website files only**. Admin tooling, backend scripts, credentials and private configuration are intentionally excluded.
- `index.html` in this repository is byte-identical to the verified staged source
  `GitHub_Staging/Website/index.html`. No pricing, checkout, fulfillment, Offers, tracking,
  API, POS or business-logic change has been made.
