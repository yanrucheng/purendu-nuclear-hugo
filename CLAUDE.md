# CLAUDE.md

Hugo site for Purendu Ltd. (普仁度). Custom atomic-core theme, Chinese language, privacy-focused.

**Company Details:**
- English: Purendu Ltd.
- Chinese: 普仁度
- Domain: purendu.com
- Email: support@purendu.com

## Commands
```bash
hugo server -D --port 1314     # Dev server (always use port 1314)
hugo              # Build site
hugo new news/post.md    # New content
```

**Local Testing:** Always use port 1314. Kill existing services first: `pkill -f "hugo server"`

## Structure
- `config/_default/hugo.toml` - Main config
- `themes/atomic-core/` - Custom theme
- `content/` - Site sections
- `data/` - Company/compliance data
- `archetypes/` - Content templates

## Data Localization Pattern
Homepage content uses locale-specific data files with English fallback:
- `data/homepage/en.yaml` - English content (fallback)
- `data/homepage/zh-cn.yaml` - Chinese content
- `data/homepage/fr.yaml` - French content

Template lookup: `{{ $data := .Site.Data.homepage }}{{ $langData := or (index . $lang) (index . "en") }}`

This structure allows Hugo to automatically load the correct language-specific data file.

## Commits
Use conventional format: `feat:`, `chore:`, `bugfix:`, etc. No Claude Code co-authoring.