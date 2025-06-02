# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Setup
- Requires Ruby 3.4.1
- Initial setup: `mise install && bundle`

### Common Commands
- **Development server**: `bin/serve` or `bundle exec jekyll serve --incremental`
- **Build site**: `bin/build` or `bundle exec jekyll build`
- **Regular serve**: `bundle exec jekyll serve`

## Site Architecture

This is a Jekyll-based GitHub Pages personal blog site using the "Panasonic Youth" theme.

### Key Structure
- **Posts**: All blog posts are in `_posts/` with date-based naming (YYYY-MM-DD-title.markdown)
- **Layouts**: Located in `_layouts/` with main templates (default.html, post.html, page.html, resume.html)
- **Includes**: Partial templates in `_includes/`
- **Sass**: Stylesheets organized in `_sass/` directory with modular SCSS files
- **Static pages**: Main pages like about.html, archive.md, resume.md in root

### Jekyll Configuration
- Uses Jekyll 4.4.1 with GitHub Actions deployment
- Pagination set to 1 post per page
- Rouge syntax highlighter enabled
- Incremental builds enabled for faster development
- Sass compilation with compressed output

### Content Management
- Blog posts use markdown with YAML front matter
- Site navigation configured in `_config.yml` under `nav` section
- Author information and site metadata in `_config.yml`

### Deployment
- Uses GitHub Actions for automatic deployment
- Workflow defined in `.github/workflows/pages.yml`
- **Production**: Deploys to rsanheim.com on push to `main` branch
- **Staging**: Branch builds verify Jekyll 4.4.1 compatibility without deployment