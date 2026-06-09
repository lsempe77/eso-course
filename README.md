# Technology-Enabled Evidence Synthesis

The course repository for the 3ie Evidence Synthesis Office programme. It is a Quarto
website (the **handbook**) plus templates, planning docs, and a publishing workflow.
Read `CLAUDE.md` before adding or editing content; `STYLE.md` governs writing.

## Working locally

> **Important:** clone this repo to a folder that is **not** inside OneDrive/Dropbox.
> Cloud-sync folders corrupt git internals and truncate files. Keep your working copy
> on local disk (e.g. `C:\dev\eso-course`).

```bash
git clone <repo-url> eso-course
cd eso-course
quarto preview        # live local preview
quarto render         # build the whole site into _site/
```

## Structure

```
_quarto.yml                 site config (nav, theme, what gets rendered)
index.qmd                   home page
tiers/tier0..3/             lessons by tier (built from the template)
templates/module-template.qmd   the lesson skeleton — copy this to start a module
planning/                   design plan (not published to the site)
assets/  data/              images and the threaded-example data
CLAUDE.md  STYLE.md         build + writing rules
.github/workflows/publish.yml   CI: render and deploy to GitHub Pages
```

## Publishing (GitHub Pages)

Publishing is automated. On every push to `main`, the Actions workflow renders the
site and deploys it to GitHub Pages.

One-time setup after creating the GitHub repo:

1. Push this repo to GitHub.
2. Repo **Settings > Pages > Build and deployment > Source = GitHub Actions**.
3. Push to `main` (or run the workflow manually). The site URL appears in the
   workflow's `deploy` step and in Settings > Pages.
4. Update `site-url:` in `_quarto.yml` to the published URL.

## Access control — 3ie staff only

**Plain GitHub Pages is fully public.** To restrict the site to `@3ieimpact.org`,
choose one of:

### Option A — GitHub Enterprise Cloud "private Pages" (org members)
If 3ie is on GitHub Enterprise Cloud: keep the repo **private/internal** and set the
Pages visibility to **private** (Settings > Pages > Visibility). The site is then
viewable only by org members with read access, enforced via 3ie's SSO (Microsoft
Entra). This restricts by **org membership**, not literally by email domain.
Org admins control allowed visibilities under Org Settings > Member privileges > Pages.

### Option B — Cloudflare Access in front of the site (matches the email domain) — recommended
Put **Cloudflare Access** (Zero Trust, free up to 50 users) in front of the site and
add an **Allow policy: emails ending in `@3ieimpact.org`** (validated by one-time PIN
or Microsoft/Google SSO). Two ways to host behind it:
- Host on **Cloudflare Pages** (connect this GitHub repo in the Cloudflare dashboard;
  build command `quarto render`, output `_site`), then add the Access policy; or
- Keep **GitHub Pages** with a custom domain proxied through Cloudflare, then add the
  Access policy to that hostname.

This is the only option that enforces the literal "`@3ieimpact.org` only" rule.

See `planning/eso-course-design-plan.qmd` for the full programme design.
