# Technology-Enabled Evidence Synthesis

The course repository for the 3ie Evidence Synthesis Office programme. It contains the
**handbook** (a Quarto website) plus the governing rules, the lesson template, and the
design plan.

## How the course is delivered

- **Handbook (reading):** this Quarto site, published free via **GitHub Pages**. It is
  public — built from public/published material — so you can link it anywhere.
- **Coursework (exercises, submissions, grades):** delivered through **Google Classroom**
  on 3ie's Google Workspace, so it is automatically restricted to `@3ieimpact.org`. Paste
  the handbook URL into Classroom as a Material, and run exercises as Classroom
  assignments. See `ACCESS.md`.

## Where things live

- **GitHub (source of truth):** `https://github.com/lsempe77/eso-course`
- **Live handbook:** the GitHub Pages URL (repo **Settings → Pages**)
- **Your local copy:** `…/Desktop/Gen AI tools/teaching/eso-course` (this folder)

Treat GitHub as the master copy. If you edit locally, **Pull first** (GitHub Desktop →
*Pull origin*), then *Commit* and *Push*.

## Repository structure

```
_quarto.yml                     site config (menu, theme, what gets published)
index.qmd                       handbook home page
tiers/tier0..3/                 lessons by tier (built from the template)
templates/module-template.qmd   the lesson skeleton — copy this to start a lesson
planning/                       the design plan (not published to the site)
assets/  data/                  images and the threaded-example data
CLAUDE.md  STYLE.md             build + writing rules (read before authoring)
.github/workflows/publish.yml   CI: renders the site and deploys to GitHub Pages
```

## Editing and publishing

1. Edit the `.qmd` files (`index.qmd`, `tiers/…`). Follow `CLAUDE.md` and `STYLE.md`.
2. (Optional) Preview locally: `quarto preview`.
3. Publish: push to `main`. The GitHub Action renders the site and deploys it to GitHub
   Pages automatically. (One-time: repo **Settings → Pages → Source = GitHub Actions**.)
4. After the first deploy, set `site-url:` in `_quarto.yml` to your live Pages URL.

### No command line needed
Use **GitHub Desktop** (*Pull origin → edit → Commit → Push*) or edit `.qmd` files
directly on github.com. Either way the site rebuilds itself.
