# Pizza Bite — Customer Website

Public repository for the Pizza Bite customer-facing website (landing page, menu, deals, cart, checkout and order tracking).

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
        └── deals/       # deal / combo artwork
```

## About this build

- The website is a **single self-contained HTML file**. CSS lives in one `<style>` block and JavaScript in one `<script>` block, both inside `index.html`. This architecture is intentional and is kept as-is — there is no build step, no bundler and no dependency installation.
- Menu food photography and deal artwork are loaded at runtime from remote CDNs and from the public menu API, so `assets/images/menu/` and `assets/images/deals/` are empty by design.
- The Pizza Bite logo in the top bar is embedded directly in the HTML as a `data:` URI, so `assets/images/branding/` needs no file for the current build.

## Image files in this repository

| Path | Purpose |
| --- | --- |
| `assets/images/landing/menu.png` | "How to Order" step — Choose |
| `assets/images/landing/add-to-cart.png` | "How to Order" step — Add |
| `assets/images/landing/order-now.png` | "How to Order" step — Order |
| `assets/images/landing/app.png` | "How to Order" step — Enjoy |
| `assets/images/landing/hero.<ext>` | Landing page hero, published by the Admin Panel |
| `assets/images/landing/menu-hero.<ext>` | Menu page hero, published by the Admin Panel |

Approved destination directories for Admin-published images:

```text
assets/images/landing/
assets/images/menu/
assets/images/deals/
assets/images/branding/
```

Nothing outside those directories can be written by the Admin.

## Running locally

Any static file server works:

```bash
npx serve .
```

Then open the served page in a browser.

## Known open item

`pizza_bite_gate_bg.jpg` (fulfillment-gate / hero fallback background) is referenced by `index.html` but is not present in this repository. It has **not** been substituted with any other image. This is tracked as an open item rather than silently replaced.

## Notes

- This repository contains **public website files only**. Admin tooling, backend scripts, credentials and private configuration are intentionally excluded.
- The repository has not been pushed or published yet.
