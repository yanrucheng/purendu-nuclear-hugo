# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hugo static site generator project for Nucleus Investment - a nuclear-related investment company website. The site uses a custom theme called "atomic-core" and is configured for Chinese language (zh-cn) by default.

## Common Development Commands

```bash
# Install Hugo (if not already installed)
# macOS: brew install hugo
# Ubuntu/Debian: apt install hugo

# Development server with draft content
hugo server -D

# Build static site
hugo

# Create new content
hugo new news/my-post.md        # New blog post
hugo new team/john-doe.md       # New team member
hugo new about/section.md       # New page section
```

## Architecture & Structure

### Configuration Hierarchy
- **Site config**: `config/_default/hugo.toml` - Main Hugo configuration including menus, privacy settings, and theme parameters
- **Company data**: `data/company.yaml` - Company information and contact details
- **Compliance data**: `data/compliance.yaml` - Legal disclaimers and compliance statements

### Theme Architecture
- **Theme location**: `themes/atomic-core/`
- **Layout templates**: `themes/atomic-core/layouts/` - Uses Hugo's template hierarchy
  - `_default/` - Base, list, and single page templates
  - `partials/` - Reusable components (head, header, footer)
  - `shortcodes/` - Custom shortcodes (currently only `button`)
- **Static assets**: `themes/atomic-core/static/` - CSS and images

### Content Structure
- **Sections**: `content/` contains main site sections (about, strategy, team, news, contact)
- **Archetypes**: `archetypes/` defines content templates for different content types
  - `default.md` - Basic page template
  - `post.md` - Blog/news post template with tags and categories
  - `person.md` - Team member template

### Key Configuration Points
- **Menu configuration**: Defined in `config/_default/hugo.toml` under `[menu.main]`
- **Theme customization**: Colors and branding in `[params]` section of config
- **Privacy settings**: External tracking disabled by default in `[privacy]` section
- **Permalinks**: News posts use `/news/:slug/` format

### Content Management
- **Multilingual**: Configured for zh-cn, can be extended for additional languages
- **Taxonomies**: Uses tags and categories for content organization
- **SEO**: Supports description field in front matter, Open Graph and JSON-LD in head template

## Development Notes

- The site prioritizes privacy and compliance with external tracking disabled by default
- Uses clean URLs (non-ugly) and generates sitemap automatically
- Theme follows modular design with partial templates for easy maintenance
- Content archetypes provide consistent structure for different content types

## Git Commit Guidelines

Use conventional commits: `feat:`, `chore:`, `bugfix:`, `docs:`, etc. No Claude Code co-authoring in messages.