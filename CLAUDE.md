# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Fretatech documentation site built with [Mintlify](https://mintlify.com). Content is written in MDX (Markdown + JSX components). No custom application code — this is a pure docs project.

## Development Commands

```bash
# Install Mintlify CLI (requires Node.js >= 19)
npm i -g mint

# Start local dev server (http://localhost:3000, hot-reloads on save)
mint dev

# Custom port
mint dev --port 3333

# Check for broken links
mint broken-links

# Update CLI
npm mint update
```

## Architecture

- **docs.json** — Main config: navigation tabs, theme, logos, navbar, footer. All page routing is defined here.
- **MDX pages** — Each `.mdx` file is a doc page. Frontmatter has `title`, `description`, and optional `icon`.
- **OpenAPI specs** — Three YAML files in `api-reference/` auto-generate API reference pages via `docs.json` navigation entries.

### Navigation Structure (4 tabs in docs.json)

| Tab | Path | Language | Content |
|---|---|---|---|
| Documentação | `documentacao/` | Portuguese | Product features, guides with screenshots |
| Oportunidades | `api/oportunidades/` + OpenAPI | Portuguese | Opportunities/leads API |
| Integração | `api/integracao/` + OpenAPI | Portuguese | Integration API |
| CGD | `partner/` + OpenAPI | English | Partner/GDS API for TMCs, ERPs |

### Key Directories

- `images/` — Screenshots organized by doc section
- `logo/` — Light/dark SVG logos
- `snippets/` — Reusable MDX snippets (DRY content)
- `api-reference/` — OpenAPI YAML specs (`oportunidades.yaml`, `integracao.yaml`, `partner.yaml`)

## Mintlify MDX Components

Commonly used components in this codebase:

- `<Card>`, `<CardGroup cols={N}>` — Feature cards
- `<Frame>` — Image wrapper with rounded borders
- `<Steps>`, `<Step title="...">` — Numbered step guides
- `<Accordion>`, `<AccordionGroup>` — Collapsible sections
- `<Info>`, `<Tip>`, `<Note>`, `<Warning>` — Callout boxes
- `<ResponseField>`, `<Expandable>` — API response docs
- `<CodeGroup>` — Tabbed code examples

## Conventions

- Product documentation (`documentacao/`) is written in **Portuguese**.
- Partner/CGD API docs (`partner/`) are in **English**.
- Adding a new page requires updating `docs.json` navigation.
- Images go in `images/` in a subfolder matching the doc section.
- Deployment is automatic on push to main via Mintlify's GitHub app.
