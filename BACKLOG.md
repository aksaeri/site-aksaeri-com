# Backlog

## Portrait swap

The About section currently uses the legacy avatar (`src/assets/avatar.jpg`) as a placeholder. Drop in a new portrait by overwriting that file with the same path and name — everything else (sizing, circular crop, responsive variants) is handled automatically.

If the new portrait has a meaningfully different aspect ratio, you may want to bump the `widths={[200, 400]}` array in `src/pages/index.astro`.

## Unused project images

`src/assets/projects/` still holds four images that were used by the now-removed `other-projects.astro` page:

- `climate-adaptation.jpg`
- `ready-research.jpg`
- `safe-and-responsible-ai.jpeg`
- `survey-assessing-risks-ai.jpg`

Left in place in case a portfolio / projects page is reintroduced later. Safe to `git rm` if not.

## Eventual extensions (from website briefing)

- Dedicated consulting / advising / speaking services section with offerings and rates.
- Featured / case studies section.
- Newsletter or subscribe option.

## After content is final

- Push `main` to origin to trigger the Vercel rebuild and update the live site.
