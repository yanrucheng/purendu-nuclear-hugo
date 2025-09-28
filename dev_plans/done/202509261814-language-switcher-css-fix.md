# Language Switcher CSS Fix

## Issue
- The `.language-menu` no longer has a hidden default state, so the menu stays visible even when the `<details>` switcher is closed.

## Action
1. Update `themes/atomic-core/static/css/main.css` to set `.language-menu { display: none; }` by default.
2. Retain `.language-switcher[open] .language-menu { display: block; }` so the menu only appears when the switcher is expanded.
3. Rebuild/preview (`hugo server -D`) to verify the menu hides correctly when collapsed and remains accessible via keyboard.
