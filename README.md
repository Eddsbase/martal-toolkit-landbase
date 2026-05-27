# Martal Operator's Toolkit — Landbase Edition (External)

Scaled-down, externally-shareable subset of the Operator's Toolkit. Single self-contained HTML file. No build step, no dependencies, no sign-in.

## What's inside

- **Videos & Docs** — 7 General items + 16 Landbase items, grouped by stage (Foundations, Pre-Send Check, Cold Call Training, Account Setup, Building Lists, Launching Campaigns, Campaign Maintenance, Replies & Reporting)
- **Playbooks** — 4 PDFs from the Martal Outbound Series (Cold Calling, Email & LinkedIn, Objection Handling, List-Building)

## Stack

- One HTML file (`index.html`). Inline CSS, inline JS, inline SVG logo.
- Outfit + DM Sans + DM Mono via Google Fonts CDN.
- `.nojekyll` disables Jekyll processing on GitHub Pages.

## URL routing

`routeUrl()` decides whether a link opens in the in-page modal (iframe) or in a new tab:

| Source | Mode | Transform |
|---|---|---|
| YouTube | embed | `youtube.com/embed/{id}` |
| Loom | embed | `loom.com/embed/{id}` |
| Google Drive files | embed | `/file/d/{id}/preview` |
| Google Docs / Sheets / Slides | embed | `/edit…` → `/preview` |
| Everything else (HubSpot, ChatGPT, web tools) | new tab | unchanged |

The fallback to "new tab" is intentional — sites that set `X-Frame-Options: DENY` or `frame-ancestors 'none'` (HubSpot, ChatGPT GPTs, most public web tools) cannot be iframed and would silently break.

## Updating content

All content lives in the `DATA` object near the bottom of `index.html`. Each item is:

```js
{g: "GROUP NAME", t: "Title", k: "video|doc|sheet|article|tool", u: "https://…", d: "Description"}
```

To add a video to the Landbase track:
1. Open `index.html` on GitHub.
2. Click the pencil to edit.
3. Add a new entry inside `DATA.landbase`.
4. Commit. Pages rebuilds in ~30 seconds.

To change the theme, edit the `:root` CSS variables at the top of the file (background tones, brand green `#8ed122`, type families).

## Local preview

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deployment

This repo is set up for **GitHub Pages from `main` branch, root folder**:

1. Settings → Pages
2. Source: `Deploy from a branch`
3. Branch: `main`, Folder: `/ (root)`
4. Save

Site lives at `https://<owner>.github.io/<repo>/` ~1 minute after push.

## Excluded items

- **Engagement Filter Cheat Sheet** — source spreadsheet URL is a placeholder (`http://engagement_filters_cheat_sheet/`), not a real link. Add it back to `DATA.landbase` under `CAMPAIGN MAINTENANCE` once a real URL exists.

## License

Internal Martal Group content. External-share permitted; redistribution restricted.
