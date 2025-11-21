# CLAUDE.md - AI Assistant Guide for Alexander Saeri's Website

This document provides comprehensive guidance for AI assistants working on this Hugo-based academic website.

## Project Overview

**Site:** https://www.aksaeri.com/
**Framework:** Hugo v0.111.3 with Wowchemy Academic Theme v5
**Hosting:** Netlify
**Purpose:** Professional academic website showcasing research in AI governance, behavioral science, and effective altruism

## Repository Structure

```
/site-aksaeri-com/
├── config/_default/       # Site configuration (YAML)
│   ├── config.yaml       # Core Hugo settings, permalinks, taxonomies
│   ├── params.yaml       # Theme appearance, features, SEO
│   ├── menus.yaml        # Navigation bar configuration
│   └── languages.yaml    # Multi-language support (currently English only)
├── content/              # All site content (Markdown + HTML)
│   ├── _index.md        # Home page (landing page with blocks)
│   ├── other_projects.md # Other projects showcase page
│   ├── authors/admin/   # Profile page for Alexander K. Saeri
│   ├── project/         # Research projects (6 projects)
│   ├── publication/     # Academic publications
│   ├── post/            # Blog posts (currently draft)
│   ├── event/           # Talks/presentations
│   └── mockups/delphi/  # Interactive HTML prototypes (6 examples)
├── assets/media/         # Theme-level images and media
│   ├── albums/          # Gallery images
│   ├── icons/brands/    # Organization/brand icons
│   └── *.png, *.jpg     # Site icons and hero images
├── static/uploads/       # Static files served directly (PDFs, etc.)
├── data/                # Theme configuration
│   ├── fonts/           # Custom font definitions
│   └── themes/          # Theme variants
├── netlify.toml         # Build, deploy, and redirect configuration
└── go.mod               # Hugo module dependencies
```

## Key Conventions

### 1. Content Organization

#### Directory Structure for Content Types

**Projects:** `content/project/[project-slug]/`
- `index.md` - Front matter + markdown content
- `featured.jpg` - Featured image (processed by Hugo)

**Publications:** `content/publication/[type]/[publication-name]/`
- `index.md` - Full metadata + abstract
- `featured.jpg` - Optional cover image

**Posts:** `content/post/[post-slug]/`
- `index.md` - Post content
- `featured.jpg/png` - Featured image

**Mockups:** `content/mockups/[suite]/[example]/`
- `index.html` - Standalone HTML files with embedded CSS/JS
- Uses Chart.js for visualizations

### 2. Naming Conventions

- **Directories:** lowercase-with-hyphens (e.g., `climate-adaptation-mission`)
- **Content files:** Always `index.md` (Hugo leaf bundle pattern)
- **Images:** `featured.jpg`, `featured.png`, `avatar.jpg`
- **Dates:** ISO 8601 format (`2023-09-15T07:05:11.172Z`)

### 3. Front Matter Patterns

#### Universal Fields (All Content Types)
```yaml
---
title: "Display Title"              # Required
date: 2023-09-15T07:05:11.172Z     # Required (ISO 8601)
summary: "Brief description"        # Shown in listings
draft: false                        # false=published, true=hidden
featured: false                     # Highlight in collections
image:
  filename: featured.jpg            # Image filename in same directory
  focal_point: Smart               # Smart, Center, TopLeft, etc.
  preview_only: false              # Show in content body
---
```

#### Project-Specific Fields
```yaml
external_link: ""                   # Empty string or external URL
tags: []                           # Optional tag array
categories: []                     # Optional category array
```

#### Publication-Specific Fields
```yaml
authors:
  - Alexander K Saeri
  - Co-Author Name
author_notes:
  - "Equal contribution"
publication: "In *Journal Name*"
publication_short: "In *JN*"
publication_types:
  - "0"                            # 0=journal, 1=conference
doi: ""
url_pdf: ""
url_dataset: ""
url_code: ""
```

#### Author Profile Fields (`authors/admin/_index.md`)
```yaml
title: "Full Name"
role: "Job Title"
avatar_filename: avatar.jpg
bio: "Full biography text"
interests:
  - Interest 1
  - Interest 2
education:
  courses:
    - course: "PhD (Field)"
      institution: "University Name"
      year: 2015
email: "email@example.com"
social:
  - icon: linkedin
    icon_pack: fab
    link: "https://linkedin.com/..."
superuser: true                    # Main site user
```

### 4. Landing Pages

Landing pages use `type: landing` with Wowchemy blocks:

```yaml
---
title: Page Title
type: landing

sections:
  - block: markdown              # Custom markdown content
    content:
      title: "Section Title"
      text: |
        Markdown content here
    design:
      spacing:
        padding: ["60px", "0", "60px", "0"]
      columns: "1"

  - block: about.biography       # Author biography
    id: about
    content:
      username: admin           # Author directory name

  - block: collection           # Content collection
    content:
      title: "Recent Projects"
      count: 5
      filters:
        folders:
          - project
        exclude_featured: false
---
```

**Available Block Types:**
- `markdown` - Custom markdown sections
- `about.biography` - Author profile display
- `collection` - Filtered content collections
- `hero` - Large hero section
- `contact` - Contact form

## Development Workflows

### Adding New Content

#### 1. Adding a New Project
```bash
# Create directory
mkdir -p content/project/new-project-name

# Create index.md with front matter
# Add featured.jpg (high resolution image)
```

**Minimal `index.md`:**
```yaml
---
title: Project Title
date: 2024-01-15T00:00:00Z
summary: Brief project description with [links](https://example.com) if needed
draft: false
featured: false
external_link: ""
image:
  filename: featured.jpg
  focal_point: Smart
  preview_only: false
---

Optional markdown body content here.
```

#### 2. Adding a New Publication
```bash
mkdir -p content/publication/journal-article/paper-name
```

**Template `index.md`:**
```yaml
---
title: "Paper Title"
abstract: |
  Full abstract text here.
  Can be multi-line.
authors:
  - Alexander K Saeri
  - Co-Author
date: 2024-01-01T00:00:00Z
publishDate: 2024-01-01T00:00:00Z
publication: "In *Journal Name*"
publication_types:
  - "0"
featured: false
doi: ""
url_pdf: ""
tags: []
---
```

#### 3. Adding Interactive Mockups
```bash
# Create standalone HTML file
mkdir -p content/mockups/suite-name/example-name
```

**HTML Template:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mockup Title</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        /* Embedded styles */
    </style>
</head>
<body>
    <!-- Content -->
    <script>
        // Embedded scripts
    </script>
</body>
</html>
```

### Modifying the Home Page

Edit `content/_index.md` - uses Wowchemy blocks structure.

**Key patterns:**
- Each section is a block with `block:` type
- Content goes in `content:` object
- Design/styling in `design:` object
- Use `id:` for anchor links (e.g., `#about`)

**Linking to project images:**
```markdown
[![Project Name](/project/project-slug/featured.jpg)](/project/project-slug/)
```

### Updating Navigation

Edit `config/_default/menus.yaml`:

```yaml
main:
  - name: Display Name
    url: '/#anchor' or '/page/'
    weight: 10              # Lower = further left
```

**Special URLs:**
- `#about` - Anchor link to home page section
- `/other_projects/` - Page URL
- `uploads/resume.pdf` - Static file

### Managing Redirects

Edit `netlify.toml` redirects section:

```toml
[[redirects]]
  from = "/shortlink"
  to = "https://external-url.com"
  status = 301
  force = true
```

### Configuring Site Appearance

Edit `config/_default/params.yaml`:

**Key settings:**
```yaml
appearance:
  theme_day: earth          # earth, minimal, ocean, etc.
  theme_night: minimal
  font: olive              # Defined in data/fonts/olive.toml
  font_size: m             # s, m, l, xl

features:
  syntax_highlighter:
    theme_light: github-light
    theme_dark: dracula
  search:
    provider: wowchemy
```

### Adding Custom Fonts

Create `data/fonts/[font-name].toml`:

```toml
name = "font-name"
google_fonts = "family=FontFamily:wght@300;400;700"
heading_font = "FontFamily"
body_font = "FontFamily"
nav_font = "FontFamily"
mono_font = "Monaco"
```

Reference in `params.yaml`:
```yaml
appearance:
  font: font-name
```

## Common Tasks

### Publishing Content

**Set content to draft:**
```yaml
draft: true              # Not published
```

**Publish content:**
```yaml
draft: false             # Published
```

### Featuring Content

Highlight in collection listings:
```yaml
featured: true           # Shows in featured collections
```

### Linking Between Pages

**Internal page links:**
```markdown
[Link text](/project/project-name/)
[Anchor link](#section-id)
```

**Link to images:**
```markdown
![Alt text](/project/project-name/featured.jpg)
```

**Front matter references:**
```yaml
projects: [project-slug]  # Links to related project
```

### Image Best Practices

1. **Location:** Place images alongside content (e.g., `content/project/name/featured.jpg`)
2. **Resolution:** Use high-resolution images (Hugo processes them)
3. **Format:** JPEG for photos, PNG for graphics with transparency
4. **Naming:** Use `featured.jpg` for featured images, `avatar.jpg` for profiles
5. **Focal point:** Use `Smart` for auto-cropping, or specify position

**Hugo Image Processing Settings** (in `config.yaml`):
- Filter: Lanczos (high quality)
- Quality: 75%
- Anchor: Smart (intelligent cropping)

### Static Files

Place files that should be served directly in `static/uploads/`:
```
static/uploads/resume.pdf → https://aksaeri.com/uploads/resume.pdf
```

## Build and Deployment

### Local Development

```bash
# Install Hugo (v0.111.3 or compatible)
# Run local server
hugo server

# Build site
hugo --gc --minify
```

### Netlify Deployment

**Automatic deployment triggers:**
- Push to main branch
- Pull request (deploy preview)
- Branch deploy

**Build command:** `hugo --gc --minify -b $URL`
**Publish directory:** `public/`

**Environment variables:**
- `HUGO_VERSION=0.111.3`
- `HUGO_ENABLEGITINFO=true`
- `HUGO_ENV=production` (production only)

### Preview Builds

Pull requests automatically generate preview deployments with future-dated content:
```bash
hugo --gc --minify --buildFuture -b $DEPLOY_PRIME_URL
```

## Git Workflows

### Branch Strategy

- **Main branch:** Production deployments
- **Feature branches:** Use `claude/` prefix for AI assistant work
- **Format:** `claude/claude-md-[session-id]`

### Commit Messages

Follow conventional commit style:
```
feat: Add new project for AI risk assessment
fix: Correct broken image path in Other Projects
docs: Update CLAUDE.md with mockup guidelines
style: Improve responsive design for mobile
refactor: Reorganize project front matter
```

### Pushing Changes

```bash
# Always use -u flag for new branches
git push -u origin branch-name

# Retry on network failures (up to 4 times with exponential backoff)
```

## Things to Avoid

### Critical Don'ts

1. **Never commit build artifacts:**
   - `public/` directory
   - `resources/` directory
   - `.hugo_build.lock`
   - `node_modules/`

2. **Never modify theme files directly:**
   - Theme is loaded via Hugo modules
   - Customize via config files only

3. **Never hardcode base URLs:**
   - Use relative paths: `/project/name/`
   - Not: `https://aksaeri.com/project/name/`

4. **Never use placeholder images in production:**
   - Always use real, optimized images
   - Remove or replace demo content

5. **Never skip front matter validation:**
   - Missing `title` or `date` breaks builds
   - Empty strings (`""`) are preferred over omitting fields

6. **Never commit with `draft: true` unintentionally:**
   - Double-check draft status before committing
   - Draft content won't appear on live site

### Common Mistakes

1. **Image paths in markdown sections:**
   - Correct: `/project/name/featured.jpg`
   - Wrong: `project/name/featured.jpg` (missing leading slash)
   - Wrong: `../project/name/featured.jpg` (relative path)

2. **Date formatting:**
   - Correct: `2024-01-15T00:00:00Z`
   - Wrong: `2024-01-15` (missing time)
   - Wrong: `01/15/2024` (wrong format)

3. **Front matter booleans:**
   - Correct: `draft: false`
   - Wrong: `draft: "false"` (string, not boolean)

4. **Array syntax:**
   - Correct: `tags: []` or `tags: [tag1, tag2]`
   - Wrong: `tags:` (undefined)

5. **External links:**
   - Use empty string if no external link: `external_link: ""`
   - Not: `external_link:` (undefined)

## Theme-Specific Features

### Wowchemy Blocks

The theme provides pre-built content blocks:

| Block Type | Purpose | Key Fields |
|------------|---------|------------|
| `markdown` | Custom markdown content | `title`, `text` |
| `about.biography` | Author profile display | `username` |
| `collection` | Content listings | `title`, `count`, `filters` |
| `hero` | Large header section | `title`, `text`, `cta` |
| `contact` | Contact form | `email`, `form` |

### Taxonomies

Available for organizing content:
- **Tags:** Topic tags
- **Categories:** Broad categories
- **Publication Types:** Academic publication types
- **Authors:** Content authors

Access via:
- `tags: [tag1, tag2]` in front matter
- Automatic taxonomy pages generated
- Filter in collection blocks

### Search

Search is enabled via Wowchemy provider (configured in `params.yaml`):
```yaml
features:
  search:
    provider: wowchemy
```

Search indexes all content automatically.

## File Encoding and Formatting

### Editor Configuration (.editorconfig)

All files must follow:
- **Charset:** UTF-8
- **Line endings:** LF (Unix-style)
- **Indentation:** 2 spaces (no tabs)
- **Final newline:** Always present
- **Trailing whitespace:** Trimmed (except markdown)
- **Max line length (TOML):** 100 characters

### Markdown Formatting

- Use ATX-style headers (`#`, `##`, `###`)
- Two trailing spaces for line breaks (or `<br>`)
- Fenced code blocks with language identifiers:
  ````markdown
  ```python
  code here
  ```
  ````
- Reference-style links for readability in long documents

### YAML Formatting

```yaml
# Use 2-space indentation
key: value

# Arrays (multiple styles supported)
tags: [tag1, tag2, tag3]
# OR
tags:
  - tag1
  - tag2

# Multi-line strings
abstract: |
  Line 1
  Line 2
```

## Useful Resources

### Hugo Documentation
- **Hugo Docs:** https://gohugo.io/documentation/
- **Content Management:** https://gohugo.io/content-management/
- **Front Matter:** https://gohugo.io/content-management/front-matter/

### Wowchemy Documentation
- **Wowchemy Docs:** https://wowchemy.com/docs/
- **Page Builder:** https://wowchemy.com/docs/content/page-builder/
- **Theme Customization:** https://wowchemy.com/docs/getting-started/customization/

### Site-Specific
- **Live Site:** https://www.aksaeri.com/
- **Repository:** (current repository)
- **Netlify Dashboard:** (requires authentication)

## Quick Reference

### Most Common Commands

```bash
# Local development
hugo server

# Build for production
hugo --gc --minify

# Create new content
hugo new content/project/project-name/index.md

# Check Hugo version
hugo version

# List all content
hugo list all
```

### Most Edited Files

1. `content/_index.md` - Home page
2. `content/other_projects.md` - Other Projects page
3. `config/_default/params.yaml` - Site appearance
4. `config/_default/menus.yaml` - Navigation
5. `content/authors/admin/_index.md` - Profile page

### Quick Syntax Reference

```yaml
# Project front matter (minimal)
---
title: "Project Name"
date: 2024-01-15T00:00:00Z
summary: "Brief description"
draft: false
featured: false
external_link: ""
image:
  filename: featured.jpg
  focal_point: Smart
  preview_only: false
---
```

```yaml
# Landing page section (minimal)
- block: markdown
  content:
    title: "Section Title"
    text: |
      Content here
```

```toml
# Netlify redirect (minimal)
[[redirects]]
  from = "/short"
  to = "https://example.com"
  status = 301
  force = true
```

## Support and Troubleshooting

### Build Failures

**Check:**
1. Front matter syntax (YAML formatting)
2. Missing required fields (`title`, `date`)
3. Image file paths (must exist)
4. Hugo module updates needed (`hugo mod get -u`)

### Content Not Appearing

**Verify:**
1. `draft: false` in front matter
2. File is `index.md` (not `index.markdown` or other)
3. Date is not in the future (unless `--buildFuture` flag used)
4. Content is in correct directory structure

### Images Not Loading

**Confirm:**
1. Image file exists in content directory
2. `filename:` in front matter matches actual filename
3. Path is relative to content directory
4. Hugo image processing settings are correct

---

**Last Updated:** 2024-01-21
**Hugo Version:** 0.111.3
**Theme Version:** Wowchemy v5.8.1

For questions or updates to this guide, please refer to the repository documentation or contact the site maintainer.
