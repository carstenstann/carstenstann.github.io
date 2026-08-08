# Carsten Stann's Hugo site

This repository builds the personal website published at https://carstenstann.com. The site is generated with Hugo and published as a static site, so most maintenance is done by editing Markdown content and configuration rather than running a database or application server.

## How it works

- `content/` contains the site's pages and posts. The main content types are blog posts, an about page, a privacy page, and the photography gallery.
- `hugo.toml` defines the site title, base URL, menus, permalinks, theme selection, and basic metadata.
- `layouts/` and the theme folders under `themes/` control templates, partials, and styling.
- The repository includes two Git submodules:
  - `themes/hello-friend-ng` provides the main site theme.
  - `themes/hugo-shortcode-gallery` provides the photo gallery shortcode library used by the photography page.
- `static/` holds files that should be copied directly to the built site, such as favicons and manifest assets.
- `public/` is the generated output directory. It is rebuilt by Hugo and should not be edited manually.
- GitHub Actions in `.github/workflows/hugo.yaml` builds the site with Hugo and deploys it to GitHub Pages whenever changes are pushed to `main`.

A simple overview of the layout looks like this:

```text
.
├── archetypes/        # Front matter templates for new content
├── content/           # Site content in Markdown
├── layouts/           # Custom templates and overrides
├── static/            # Files copied directly to the published site
├── themes/            # Git submodules for the site theme and gallery plugin
│   ├── hello-friend-ng/
│   └── hugo-shortcode-gallery/
├── hugo.toml          # Main Hugo configuration
├── .github/workflows/ # Deployment workflow for GitHub Pages
└── public/            # Generated site output
```

## Local development

- Install Hugo Extended (the workflow uses Hugo 0.164.0, so matching the version is recommended).
- Start a local preview with (`-D` includes drafts):

  ```bash
  hugo server -D
  ```

- Build a production-ready version with:

  ```bash
  hugo --gc --minify
  ```

## Maintenance

- Add or edit content as Markdown files in `content/`.
- For new blog posts, create a file under `content/posts/` and keep the front matter consistent with the existing posts.
- For photography content, place images in `content/photography/images/` and update the gallery page in `content/photography/index.md` as needed.
- If you change themes or templates, test locally before publishing.
- Keep the theme submodules up to date with `git submodule update --remote --merge` when you want to pull newer theme changes.
