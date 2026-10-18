# Indo Workspace Website

Main website for Indo Workspace, designed as a multi-product landing page.

## Repository structure

- `index.html` — responsive home page and product directory.
- `assets/images/indo-workspace-logo.png` — official supplied Indo Workspace logo (add this asset before deploying).
- `assets/images/apps/` — product logos.
- `apps/<app-name>/index.html` — individual product detail pages as products are added.

## Before deployment

1. Add the original Indo Workspace logo image at `assets/images/indo-workspace-logo.png`.
2. Add each product logo under `assets/images/apps/` and create its details page when official product information is available.
3. Connect verified download and web-app URLs only after they are supplied.
4. Configure the custom domain and hosting provider.

Eye Search is intentionally omitted because it is still in development. Indoone will be added after its logo and product details are supplied.

The page uses no local JavaScript dependencies. Its responsive styling is included directly in `index.html`.
