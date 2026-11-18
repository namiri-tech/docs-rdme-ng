# DigiTax Nigeria API Hub

Source for the DigiTax Nigeria API Hub on [ReadMe](https://readme.com), published at
[ng.docs.digitax.tech](https://ng.docs.digitax.tech). It holds the guides (`docs/`), the API reference guide pages
and the endpoint pages generated from `reference/openapi.yaml` (`reference/`), and the files those pages link to.

The live branch is `v1.0`, which ReadMe syncs with. Make changes on a feature branch and open a pull request into
`v1.0`.

## Checks

Lint the docs as ReadMe sees them:

```sh
npx @readme/cli lint
```

Markdown style (rules in `.markdownlint.json`) and spelling (project words in `cspell-word-list.txt`):

```sh
npx markdownlint-cli2 "docs/**/*.md" "reference/**/*.md"
npx cspell "docs/**/*.md" "reference/**/*.md"
```

`reference/openapi.yaml` and the endpoint pages under `reference/DigiTax Nigeria API Endpoints/` come from the API spec in the backend
repository. Change the spec there rather than editing them by hand.

## PDF export

To export the API reference guide as a PDF, use the "Markdown PDF" VS Code extension. It reads its configuration from
`.vscode/settings.json`.

To export the API spec as a PDF, run:

```sh
npx apibake reference/openapi.yaml --title 'DigiTax Nigeria API Spec'
```
