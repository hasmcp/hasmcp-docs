# CLAUDE.md — hasmcp-docs

## Project overview

This is the HasMCP documentation site, powered by **Mintlify**. All content is written in MDX.

## Directory structure

```
/
├── docs.json              # Mintlify config: theme, navigation tabs, sidebar groups, anchors
├── index.mdx              # Homepage
├── quickstart.mdx
├── features/              # Feature overview pages (one per HasMCP capability)
│   └── index.mdx          # CardGroup listing all features — update when adding a page
├── essentials/            # Core concept guides (providers, servers, variables, clients, logs)
├── ai-tools/              # Integration guides for specific AI tools (Cursor, VS Code, etc.)
├── tutorials/             # Step-by-step tutorials
├── kb/                    # Knowledge base — short, focused articles indexed by slug
├── api-reference/         # API endpoint reference pages (mirrors REST API structure)
├── self-hosted/           # Self-hosting guide
├── licenses/              # License info
└── images/ icons/ logo/   # Static assets
```

## Navigation is managed in docs.json

Adding a new `.mdx` page does **not** automatically make it visible. You must add the page path (without `.mdx`) to the appropriate `groups[].pages` array inside `docs.json`. The Features tab lives under the `"Features"` tab entry.

## Feature page conventions

- **Frontmatter:** `title: "<Name> | HasMCP Features"` and a `description` field.
- **H1:** Feature name only (no "| HasMCP Features").
- **Sections:** Use `##` headings. Common pattern: overview paragraph, How It Works, Setup steps, sub-sections per topic, Related Reading.
- **Related Reading:** End with a `## Related Reading` section linking to relevant kb articles.
- **Tables:** Use Markdown tables for status codes, option comparisons, etc.
- **Code blocks:** Use fenced code blocks with a language identifier.

## Checklist when adding a feature page

1. Create `features/<slug>.mdx` following the conventions above.
2. Add a `<Card>` entry to `features/index.mdx` inside the existing `<CardGroup>`.
3. Add `"features/<slug>"` to the Features tab pages array in `docs.json`.
4. Commit and push — Mintlify deploys automatically from main.

## MCP server app structure (for reference when writing docs)

The HasMCP app lives at `../hasmcp-app/` relative to this repo:
- `backend/` — Go backend (controllers, handlers, repositories, models)
- `frontend/` — Vue.js frontend (views, components, stores)

When documenting a feature, read the corresponding backend controller and frontend view to understand actual behavior before writing.
