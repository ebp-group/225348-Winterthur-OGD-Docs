[![Build documentation](https://github.com/ebp-group/225348-Winterthur-OGD-Docs/actions/workflows/build.yml/badge.svg)](https://github.com/ebp-group/225348-Winterthur-OGD-Docs/actions/workflows/build.yml)
[![Deploy to GitHub Pages](https://github.com/ebp-group/225348-Winterthur-OGD-Docs/actions/workflows/deploy.yml/badge.svg)](https://github.com/ebp-group/225348-Winterthur-OGD-Docs/actions/workflows/deploy.yml)
[![Spellcheck Text](https://github.com/ebp-group/225348-Winterthur-OGD-Docs/actions/workflows/spellcheck.yml/badge.svg)](https://github.com/ebp-group/225348-Winterthur-OGD-Docs/actions/workflows/spellcheck.yml)

# 225348-Winterthur-OGD-Docs

OGD Dokumentation für die Stadt Winterthur

This website is built using [Docusaurus](https://docusaurus.io/), a modern static website generator.

## Spellcheck

This website uses a GitHub Action to run a German spellchecker.

If new words must be added to the wordlist, please add them to `.github/wordlist_de.txt`, one word per line.

For parts that do not need a spellcheck, you can disable the spell check using the `nospell` CSS class, example:

```html
Gegenüber den Daten-Nutzenden tritt das OGD-Kompetenzzentrum als SPOC (<span class="nospell">_Single Point of Contact_</span>) auf und triagiert die Anfragen nach Zuständigkeit und Dringlichkeit.
```

## Entwicklung

### Installation

```bash
yarn
```

### Local Development

```bash
yarn start
```

This command starts a local development server and opens up a browser window. Most changes are reflected live without having to restart the server.

### Build

```bash
yarn build
```

This command generates static content into the `build` directory and can be served using any static contents hosting service.
