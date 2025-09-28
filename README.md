# Purendu Ltd. — Hugo Site Skeleton

A Hugo static site foundation for nuclear-related investment companies. Design goals: clean, professional, finance-friendly, and easily extensible.

## Features Overview
- Standard Hugo structure with extensible configuration (menus, taxonomy, Sitemap, Robots, Privacy).
- Lightweight custom theme `atomic-core`: modular partials (head, header/nav, footer), basic layouts (base/list/single), minimal styling.
- Core pages: Home (Hero), About, Strategy, Team, News/Insights, Contact.
- Archetypes: `default`, `post`, `person`; Shortcodes: `button` (extensible).
- Data directory: company and compliance metadata (addresses, privacy notices, independence/neutrality statements), plus homepage content (hero, sections).

## Directory Structure
```
nuclear-invest-hugo/
  archetypes/             # Content templates
  config/_default/        # Site configuration (hugo.toml)
  content/                # Content pages (About/Strategy/Team/News/Contact)
  data/                   # Company and compliance data (company.yaml / compliance.yaml / homepage.yaml)
  static/                 # Static assets (robots.txt etc.)
  themes/atomic-core/     # Lightweight theme
    layouts/_default/     # base/list/single base templates
    layouts/partials/     # head/header/footer partials
    layouts/shortcodes/   # button and other shortcodes
    static/css/           # Theme styles (main.css)
    static/img/           # Theme images (logo.svg)
```

## Local Development
Prerequisites: Install Hugo (extended version recommended).
- macOS (Homebrew): `brew install hugo`
- Ubuntu/Debian: `apt install hugo`
- Or download binary from official Releases (extended).

Development and preview:
- Run from project root: `hugo server -D`
- Browser access: `http://localhost:1313`

Build static files:
- Run from project root: `hugo`
- Output directory: `public/`

## Content and Theme Extensions
- New articles: `hugo new news/my-post.md` (uses `archetypes/post.md`)
- New team members: `hugo new team/john-doe.md` (can switch to `data/team.yaml` approach)
- Homepage content: Edit hero/sections data in `data/homepage.yaml`, no template changes needed.
- Page descriptions and SEO: Add `description` field in content Front Matter.
- Menus: Modify `[menu.main]` in `config/_default/hugo.toml`; or declare `menu.main` in page Front Matter.
- Colors and branding: Use `[params]` in `config/_default/hugo.toml`; theme styles in `themes/atomic-core/static/css/main.css`.
- Shortcodes: Example `{{< button href="/contact/" >}}Contact Us{{< /button >}}`; add `note`, `quote` etc. in `layouts/shortcodes/`.

## Compliance and Privacy
- Site defaults to `enableRobotsTXT = true` with Sitemap; `privacy` configuration minimizes external tracking and embeds.
- Footer displays neutrality index and independence statements: content from `data/compliance.yaml`.
- Forms and data uploads not in scope; if needed later, recommend static form services or minimal backend with strict data minimization.

## Naming and Internationalization
- Default language: `en`; for ZH/FR, use Hugo multilingual configuration (add language sections in `config/_default/`).
- Microcopy and CTAs follow established patterns (independence and safety first; neutral index does not constitute endorsement).

## Maintenance and Roadmap
- Add sections as needed (Knowledge Hub, Publications, Services), maintain modularity and simplicity.
- Supplement Open Graph and JSON-LD (basic organizational structure support already in `head.html`).
- When introducing custom fonts, recommend self-hosting to avoid third-party privacy issues; currently uses system font stack.

## License
This repository provides project skeleton and sample content; replace placeholder text and data with actual company information.
