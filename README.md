# Indo Workspace — website

Static site for **Indo Workspace** (indobiz.in) and its app **Indoone**.
No build step, no framework — plain HTML + one shared CSS file. Push the repo, connect the domain, done.

## Folder structure

```
indobiz.in/                       <- repo root = what the domain serves
│
├── index.html                    <- HOME                 -> https://indobiz.in/
├── 404.html                      <- shown for any missing URL
├── robots.txt                    <- tells search engines what to crawl
├── sitemap.xml                   <- list of pages, for search engines
├── README.md
│
├── apps/                         <- APPS section (a folder)
│   ├── index.html                <- the Apps page         -> /apps/
│   └── indoone/                  <- one sub-folder per app
│       ├── index.html            <- Indoone details page  -> /apps/indoone/
│       └── assets/
│           └── logo.svg          <- INDOONE's OWN logo
│
├── contact/                      <- CONTACT section (a folder)
│   └── index.html                <- the Contact page      -> /contact/
│
└── assets/                       <- shared by every page
    ├── css/
    │   └── style.css             <- the ONLY stylesheet
    └── img/
        └── logo.svg              <- the COMPANY (Indo Workspace) logo
```

Every section is a folder. Every page inside a folder is called `index.html`, which gives a clean
URL with no `.html` at the end: `apps/indoone/index.html` is served at `https://indobiz.in/apps/indoone/`.

## Logos — one per app

There are two kinds of logo, and they live in two different places:

- **Company logo** — `assets/img/logo.svg`. This is Indo Workspace's own logo, used by the site
  brand (the nav mark on every page).
- **App logo** — `apps/<app>/assets/logo.svg`. **Every app carries its own logo, inside its own
  folder.** Because each app already has its own page, its logo travels with it: nothing is shared
  between apps, so a new app can never accidentally overwrite another app's logo.

Where the Indoone logo is used:

- `apps/indoone/index.html` — the app's own page, in the hero (`<img class="applogo" src="assets/logo.svg">`).
- The Indoone card on the home page and on the Apps page (`.appcard__icon img`).

So when you add a new app, drop its logo at `apps/<name>/assets/logo.svg` and point the card and the
app page at it. Replace the placeholder SVGs with the real artwork whenever you have it.

## How a click flows through the structure

- Home `Apps` (nav) → `apps/` → the Apps page.
- Apps page → the **Indoone** card's **Details** button → `apps/indoone/` → the Indoone details page.
- Home `Contact` (nav) → `contact/` → the Contact page.

## Adding the next app

1. Make the folder: `apps/<name>/`.
2. Add its `index.html` (link `../../assets/css/style.css`, same nav/footer).
3. Add its logo: `apps/<name>/assets/logo.svg`.
4. On the home page and the Apps page, add its card and point **Details** at `apps/<name>/`.

Nothing else needs touching — each app stays self-contained.

## Connecting the domain

This repo deploys with the GitHub Actions workflow at `.github/workflows/deploy-pages.yml`, which
publishes the whole repo — including `apps/` and `contact/` — on every push to `main`.

- **GitHub Pages** — Settings → Pages → Build and deployment → Source: **GitHub Actions**.
  Then under Custom domain enter `indobiz.in` and follow GitHub's DNS instructions
  (apex `A` records + `www` `CNAME`), and tick "Enforce HTTPS".
- **Netlify / Vercel / Cloudflare Pages** — import the repo, no build command, publish directory `/`.

## Still to fill in

- Real **Download** and **Open on Web** URLs (currently placeholders).
- Real **company logo** (`assets/img/logo.svg`) and the exact brand hex codes.
- Real **app logos** for each app (`apps/<app>/assets/logo.svg`).
- **WhatsApp** number.
