# CLAUDE.md — building this course

This file governs how we (and any AI agent) **build** the *Technology-Enabled Evidence Synthesis* programme for the 3ie Evidence Synthesis Office. Read it before creating or editing any course material. It is the single source of truth for how the course is made; when something here conflicts with habit, this file wins.

> This is the **build/authoring** instruction file. A separate, learner-facing `CLAUDE.md` template (for students' own review repos) is a course deliverable and lives elsewhere — do not confuse the two.

The full rationale for every decision below is in `eso-course-design-plan.qmd`. Read that for the *why*; this file is the *how*.

---

## 1. What we are building

A tiered, mostly self-paced programme (~210 h core, extensible to ~400 h) that teaches experienced evidence-synthesis colleagues a modern, technology-enabled **way of working**. The course is itself built in the stack it teaches: a Quarto site in a git/GitHub repo, authored with agent assistance.

**The final product is a suite, not a single artefact.** Every module feeds several formats:

- a **handbook** — the Quarto book/website that is the written spine of the course;
- **slides** — decks for live or cohort delivery;
- **practice notebooks** — runnable `.qmd` files the learner works through and commits;
- **videos** — short screencasts for installs, editor click-throughs, and git flows;
- supporting **templates and datasets** (e.g. the threaded example).

Design each lesson so its content can flow into all of these. The handbook is the source of truth; slides, notebooks, and videos derive from it.

## 2. Who the learners are — keep them in mind always

Experienced synthesis methodologists and reviewers who are **mostly non-coders**. They are comfortable in Word, Excel, and review platforms, and have strong methods knowledge. They are new to git, the command line, reproducible documents, and structured LLM use. Write for a capable, busy colleague — never for a developer, and never in a way that assumes prior coding.

## 3. Pedagogical principles (non-negotiable)

- **Reuse before building — search first, always.** Before writing any lesson, example, dataset, script, or skill, do a *deep search* of GitHub and the web for existing material we can adapt. The field has done much of this already: Carpentries lessons, the DIME Analytics handbook, The Turing Way, existing Quarto courses, community Claude skills, and relevant R packages. Find the best existing work, adapt it to our audience, and **credit it**. Reinvent only when nothing suitable exists — and note why. This is a standing instruction, not a one-off.
- **Workflow, not methods.** We never teach how to search, screen, extract, appraise, or meta-analyse — they know that. We teach how to do those things reproducibly, collaboratively, and transparently with tools. If a draft starts explaining a synthesis *method*, stop and refocus on the *workflow*.
- **Teach every tool through a synthesis task.** No abstract tool tours. Introduce git by versioning a screening log; introduce Quarto by writing a protocol. If a concept is not anchored to a recognisable synthesis task, it is not ready.
- **Agent-central, reproducibility as guardrail.** Learners work with the agent from day one, *and* learn to version, read, and verify everything it produces. Version control and "render from source" are taught early, before deep agent work.
- **Scaffold relentlessly.** Concrete, copy-pasteable steps. GUI before terminal. Nobody should ever be stuck on environment setup.
- **Show, then have them do.** Every lesson ends in the learner producing a real artefact, committed to their repo.

## 4. The stack we teach (locked — keep consistent everywhere)

| Layer | Tools |
|---|---|
| Engine (everyone) | git/GitHub, Quarto, Claude Code (agent), **VS Code** (editor), GitHub Copilot (in-editor assistant) |
| Synthesis wrapper | OSF / PROSPERO; a review platform (Covidence / EPPI-Reviewer / Rayyan / ASReview) |
| Plumbing (advanced) | renv, targets / Make, Docker |

Do **not** introduce alternative editors as the default. VS Code is the standard; RStudio is mentioned only as a fallback. Refer to tools by their correct names (see `STYLE.md`).

## 5. Governance & integrity rules (must appear in spirit throughout)

- Follow **RAISE** and the Cochrane/Campbell/JBI/CEE position statement: the synthesist is always responsible; AI is acceptable only when it does not compromise rigour; human oversight is required; every AI-made or AI-suggested judgement is documented.
- **Verify everything the agent produces.** Never present agent output as trustworthy without a verification step.
- **Citation integrity is two-layer:** deterministic checks (`metacheck`, `CiteSource`) answer "is this reference real and clean?"; the agent answers "does the source support the claim?" Never let a lesson imply an LLM alone can be trusted to check citations.
- **Never fabricate.** When a source or fact is inaccessible, say so — do not invent quotes, results, or citations. Model this behaviour in all examples.
- **Data rule:** course examples use published/public material only; state the published-data-only rule wherever external LLMs are used.

## 6. Writing & voice

UK / International English, plain-warm-practitioner tone. Full rules are in **`STYLE.md`** — read it before writing prose. In short: clear, concise, second person, minimal jargon, define terms on first use, no walls of bullet points.

## 7. Repo & file conventions

- **Course content** is Quarto (`.qmd`). One lesson = one `.qmd`, built from `module-template.qmd`.
- **Naming:** lower-case, hyphenated, no spaces (e.g. `tier1-02-version-control.qmd`). Order modules with a numeric prefix.
- **Structure (proposed):** `index.qmd` (home) · `tiers/` (lessons by tier) · `templates/` · `assets/` (images) · `data/` (threaded-example data) · `_quarto.yml` (site config). Confirm before restructuring.
- **Git workflow:** one branch per module or fix; descriptive commit messages in the imperative ("Add Tier 1 git lesson"); open a pull request for review; never commit directly to `main` for substantive content.
- **Never commit:** secrets, API keys, or any non-public data.

## 8. Anatomy of a module

Every lesson is built from `module-template.qmd` and contains, in order: learning outcomes → why this matters (the synthesis task) → what you need → walkthrough → try it yourself → **verify** → common pitfalls → recap → what's next → facilitator notes. Do not drop the **verify** section — it is where the reproducibility/RAISE discipline lives.

## 9. Adding a new module — checklist

1. **Search first** — look on GitHub and the web for existing lessons, datasets, or scripts to adapt; note what you found and will reuse (or why nothing fit).
2. Copy `module-template.qmd` to the right tier folder with a conventional name.
3. Fill the YAML (title, description, tier, estimated time).
4. Anchor the lesson to a concrete step of the threaded example.
5. Write to `STYLE.md`; keep code runnable.
6. Include a real artefact the learner commits, and a verify step.
7. Plan how the content carries into the other formats (slides, notebook, video).
8. Render locally (`quarto preview`) and check it builds clean.
9. Open a pull request; request review.

## 10. Build & preview commands

```bash
quarto preview        # live local preview while writing
quarto render         # build the whole site
quarto render path/to/lesson.qmd   # build one lesson
```

Always render before committing; never commit a lesson that fails to build.

## 11. Definition of done (a lesson)

Builds clean · anchored to a synthesis task · has outcomes, a learner artefact, and a verify step · follows `STYLE.md` · no fabricated content · governance rules respected · reviewed via pull request.

## 12. Do not

- Teach synthesis *methods* or statistics.
- Introduce a tool without a synthesis task around it.
- Default to any editor other than VS Code.
- Use US spelling (see `STYLE.md`).
- Present agent output without a verification step.
- Invent citations, quotes, or results in examples.
- Reinvent what already exists without searching first.
