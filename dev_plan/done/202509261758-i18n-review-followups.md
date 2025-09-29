# I18n Follow-up Plan

## Outstanding Issues
- Missing `data/homepage.zh-cn.yaml` causes the Chinese homepage to fall back to English copy.
- Language switcher links to locale roots instead of page translations.
- Skip link text is hard-coded in Chinese and ignores active locale.
- Language menu requires mouse hover; keyboard users cannot reveal it.

## Actions
1. Add `data/homepage.zh-cn.yaml` mirroring English/French structure with localized strings.
2. Update `partials/header.html` to derive switcher links from `.Page.AllTranslations` (fallback to home when unavailable) and adjust markup accordingly.
3. Replace skip-link copy in `baseof.html` with `{{ i18n "skipToContent" }}`.
4. Enhance CSS to display `.language-menu` on `:focus-within` (or adopt a `<details>` pattern) so keyboard and touch users can operate it.
5. Run `hugo --panicOnWarning` for each locale and spot-check navigation, hero copy, and footer metadata.
