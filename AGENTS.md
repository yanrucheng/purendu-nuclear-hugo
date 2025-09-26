# Repository Guidelines

## Project Structure & Module Organization
The Hugo root keeps page content under `content/` (About, Strategy, Team, News, Contact), with reusable archetypes in `archetypes/` and metadata in `data/`. Custom theme assets, layouts, partials, and shortcodes live in `themes/atomic-core/`, while shared static files such as favicons or robots rules belong in `static/`. generated output in `public/` should be treated as disposable—rebuild instead of editing it.

## Build, Test, and Development Commands
Install the Hugo Extended binary before editing. Use `hugo server -D` to preview drafts locally, `hugo` for a release build, and `hugo --panicOnWarning` before submitting changes to catch template regressions. Create new posts with `hugo new news/my-post.md` to leverage the `post` archetype.

## Coding Style & Naming Conventions
Keep Hugo templates and partials two-space indented and limit complex logic—extract shared fragments into `layouts/partials/`. Use lowercase, hyphenated slugs for Markdown files (e.g. `content/news/market-outlook.md`) and store front matter/data in YAML with two-space indentation. Extend styling in `themes/atomic-core/static/css/main.css`, following lightweight BEM naming and preferring system font stacks unless brand guidelines require otherwise.

## Testing Guidelines
This project relies on manual QA. Run `hugo server -D` to review responsive breakpoints and localized text, and `hugo --panicOnWarning` to ensure clean builds. Document visual or copy changes with screenshots and confirm generated assets appear correctly under `public/` after rebuilding.

## Commit & Pull Request Guidelines
Commits follow Conventional Commit prefixes such as `feat:`, `chore:`, or `bugfix:`; keep each change focused and include brief English or Simplified Chinese summaries when helpful. Project policy forbids Claude Code co-authoring—ensure your commits list only human contributors. Pull requests should describe scope, enumerate config/content impacts, link tracking tasks, and attach before/after images for noticeable UI updates once the branch builds without warnings.
