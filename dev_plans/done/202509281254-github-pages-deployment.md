# GitHub Pages Deployment Plan

## Objectives
- Publish the Hugo-driven static site to GitHub Pages without manual uploads.
- Reuse the existing GitHub Pages account that already serves other sites, while isolating this project behind its own repository and custom domain.
- Automate builds on every push to `main`, deploying production-ready assets only after successful Hugo builds.

## Assumptions & Inputs
- Hugo Extended is available in GitHub Actions runners; the project stays on the `main` branch for source.
- Current user/organization GitHub Pages site already serves other content, so this project must ship as a **project site** (e.g. `github.com/<acct>/<repo>`) with a custom domain or subdomain.
- DNS registrar access is available to create/modify `A` and `CNAME` records.
- No direct pushes to the generated `public/` directory; all artifacts should be produced via CI.

## High-Level Workflow
1. **Repository Prep**
   - Ensure `public/` is excluded from version control (`.gitignore` update if required).
   - Confirm `config/_default/config.yaml` (or TOML equivalent) has an accurate `baseURL` that matches the eventual custom domain (use placeholder until DNS is ready).
   - Add deployment documentation to `README.md` describing the CI/CD flow and troubleshooting steps.

2. **GitHub Pages Configuration**
   - Create or select the GitHub repository that will back the project site (e.g. `<acct>/purendu-nuclear-hugo`).
   - In repository settings, enable GitHub Pages with "Deploy from branch" targeting the `gh-pages` branch and `/` root; keep the repository private/public per requirements.
   - If the account has a root-level `username.github.io` site already, verify there is no conflicting `CNAME` in that repo.

3. **CI/CD Pipeline (GitHub Actions)**
   - Add `.github/workflows/deploy.yml` that:
     1. Triggers on pushes to `main` (and optionally manual dispatch).
     2. Checks out the repo with submodules (Hugo themes) using `actions/checkout@v4` and `submodules: true`.
     3. Installs Hugo Extended via `peaceiris/actions-hugo@v2` pinned to a specific version.
     4. Runs `hugo --panicOnWarning` with `HUGO_ENV=production` to build into `public/`.
     5. Publishes the `public/` directory to the `gh-pages` branch using `peaceiris/actions-gh-pages@v3` with `${{ secrets.GITHUB_TOKEN }}` and `publish_dir: ./public`.
     6. Optionally caches Hugo resources (`resources/`) to speed up builds.
   - Add branch protection on `main` to require the CI workflow to pass before merging.

4. **Custom Domain Integration**
   - Decide on domain or subdomain (e.g. `nuclear.example.com`).
   - Create a `static/CNAME` file containing the desired domain so Hugo emissions include it; ensure the workflow copies it to `gh-pages`.
   - Configure DNS:
     - For apex domains: add A records pointing to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`.
     - For subdomains: add a CNAME record pointing to `<acct>.github.io`.
   - In GitHub Pages settings, set the custom domain and enable HTTPS; verify certificate provisioning completes.

5. **Smoke Testing & Verification**
   - After first deployment, visit the Pages URL and custom domain to ensure assets load and there are no mixed-content warnings.
   - Run `curl -I` checks for 200 responses and confirm `/_headers` or caching rules behave as expected (if configured).
   - Validate that future pushes trigger the workflow and redeploy automatically; test a rollback by reverting a commit and ensuring the site updates accordingly.

6. **Ongoing Maintenance**
   - Schedule regular `hugo` version bumps within the workflow; record upgrade notes in the repo.
   - Monitor GitHub Actions minutes and set up notifications for failed deploys.
   - Document manual recovery steps (e.g. re-running workflow, clearing caches) in the project README or `/docs` folder.

## Next Steps for Implementation
- Review and confirm the assumptions, especially around DNS ownership and existing GitHub Pages usage.
- Prioritize implementation of the GitHub Actions workflow, then proceed with DNS and custom domain validation.
- Once the first deployment is verified, capture screenshots and update any stakeholder documentation.

## Post-Implementation Notes (2025-09-28)
- Pin `peaceiris/actions-hugo` to a specific version in `.github/workflows/deploy.yml` so Hugo upgrades are deliberate and traceable.
- After confirming DNS and HTTPS provisioning, document certificate issuance timeline in README for future reference.
