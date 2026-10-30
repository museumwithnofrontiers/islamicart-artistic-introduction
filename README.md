# islamicart-artistic-introduction

**Artistic Introduction**, Discover Islamic Art's introduction to the art and architecture of
each Islamic dynasty of the Mediterranean, as a website of its own. On legacy
it lived inside Discover Islamic Art (`islamicart.museumwnf.org/gai/ISL/`);
here it is a product in its own right, and Discover Islamic Art links to it.

It shows what legacy showed, the way legacy showed it: the home page, each
theme's pages (Monuments, Objects) and the zoom window. Nothing on it is
written for it: every record comes from the data package, every text from
viewer-i18n or `locales/`.

Its pages are the Artistic Introduction's, in the frame of Discover Islamic Art's
virtual exhibitions, from
[`minisite-template`](https://github.com/museumwithnofrontiers/minisite-template)
and the mini-site family layer (`@museumwnf/viewer-layout/minisite`). What
is this site's own is written from its legacy folder by inventory-app's
`scripts/minisites/legacy-minisite.mjs`.

| Package | Role |
| --- | --- |
| `@museumwnf/islamicart-artistic-introduction-data` | the introduction: its collection, its themes and pages, the items they place |
| `@museumwnf/viewer-core` | application engine (routing, data access, texts, language) |
| `@museumwnf/viewer-layout` | the pages and frame (`./minisite`) |
| `@museumwnf/viewer-i18n` | the texts the Artistic Introduction shows (`./minisiteArtIntro`) |

---

## Translator — editing the website's texts

The texts the pages show — the header, the panel's tooltips, the footer — are
in [`viewer-i18n`](https://github.com/museumwithnofrontiers/viewer-i18n)'s
`minisiteArtIntro/` folder, and are edited there. The introduction's own
texts — its titles, quotes, essays and captions — arrive translated in the
data package and are not edited anywhere. `locales/` holds this website's
own texts, one file per language; it starts empty, and an entry written there
overrides the shared one of the same name for this website alone. See
`minisite-template`'s README, "Translator", for the steps in the browser.

---

## Webdesigner — theming the website

The website's look is legacy's, kept as it was:

- `theme/tokens.css` — every value legacy's `gai/ISL/_styles.css` set (then
  the site's `font-awesome.css`, and `_styles_ar.css` for Arabic), as
  `--minisite-*` tokens;
- `theme/assets/legacy/` — legacy's own pictures of the frame and the
  social-media icons; `SOURCES.json` names where each file was taken from
  and its hash, and `tests/assets.test.js` checks every file against it;
- `theme/overrides.css` — the escape hatch, empty until a need cannot be
  expressed with a token.

A change to the pages' layout itself is a request for
[`viewer-layout`](https://github.com/museumwithnofrontiers/viewer-layout)'s
`./minisite`. To preview, run `docker compose up` and open
**http://localhost:5173**.

---

## Developer notes

- `src/dataset.config.js` is the whole declaration and needs no edit;
  `src/minisite.json` holds what legacy configured for this site alone (its
  address, the home menu's second column, the social-media links).
- Every caption legacy prints is in its pages' `pageItems` script, all views
  included; a page here can be compared field by field with the page there,
  in every language.

```bash
docker run --rm -v "${PWD}:/app" -w /app node:24-alpine sh -c "npm ci && npm test && npm run lint && npm run build"
```

## Licence

See [LICENSE.md](LICENSE.md).
