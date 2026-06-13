# Metadata Game Changers · DataCite Repository Explorer

A GitHub Pages site that displays all DOIs in the **Metadata Game Changers** DataCite repository (`sjyq.oozvia`) and shows the full activity log for each DOI.

Live data is fetched directly from the [DataCite REST API](https://api.datacite.org) — no build step, no backend, no API key required.

## Features

- **All DOIs** from client `sjyq.oozvia` loaded via the public DataCite API
- **Activity timeline** for each DOI (fetched on demand from `/dois/{id}/activities`)
- **Pulse bar** — visual heartbeat strip summarizing all activity events for a DOI
- Search by title, creator, or DOI string
- Filter by resource type and publication year
- Sort by last updated, publication year, or title
- Live stats: total DOIs, resource types, most recent year, schema version

## Deploy to GitHub Pages

1. Create a new repository (e.g. `Metadata-Game-Changers/datacite-explorer`)
2. Add this `index.html` (and optionally this `README.md`) to the root
3. Go to **Settings → Pages → Source**: select `main` branch, `/ (root)`
4. GitHub Pages will serve the site — no build step needed

The site works on any static host (Netlify, Cloudflare Pages, etc.) since it's a single HTML file with zero dependencies.

## API endpoints used

| Purpose | Endpoint |
|---|---|
| All DOIs for client | `GET /dois?client-id=sjyq.oozvia&page[size]=100` |
| DOI activity log | `GET /dois/{id}/activities` |

Both endpoints are public and CORS-enabled. The DataCite API is paginated at 100 per page; the app automatically pages through all results.

## Customization

- **Client ID**: change `CLIENT_ID` at the top of the `<script>` block
- **Page size**: change `PAGE_SIZE` (default 15 cards per page)
- **Colors**: all in the CSS `:root` block at the top

## Links

- [DataCite Commons — MGC Repository](https://commons.datacite.org/repositories/sjyq.oozvia)
- [DataCite REST API docs](https://support.datacite.org/docs/api)
- [metadatagamechangers.com](https://metadatagamechangers.com)
