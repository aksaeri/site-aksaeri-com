# Backlog

## Image replacements

The following project tiles on `/other-projects` previously used Unsplash placeholder photos. The photos were removed in the cleanup pass; the tiles currently render without an image (HTML comment placeholder in `src/pages/other-projects.astro`).

| Project | Removed file | Replacement notes |
|---|---|---|
| SCRUB COVID-19 Survey | `sean-horsburgh-cxyq5_64lam-unsplash.jpg` | Ideally an image of the SCRUB project itself — survey chart, dashboard screenshot, or BWA photo. |
| Scale-up Toolkit | `dustin-humes-y-esivccgdq-unsplash.jpg` | Toolkit cover, photo of the published toolkit, or BWA project page screenshot. |

To restore an image:

1. Drop the file into `src/assets/projects/<slug>.jpg`.
2. In `src/pages/other-projects.astro`, import it and replace the `<!-- TODO -->` comment with an `<Image>` tag matching the pattern used by the other project tiles.

## Other open items

- Content updates from the LinkedIn brainstorm (`~/inbox/website_briefing.md`) are still to be applied.
- After content lands, push the local `main` commit (`105c87e`) to trigger the Vercel rebuild.
