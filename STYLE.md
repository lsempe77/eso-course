# STYLE.md — writing style guide

How we write everything in this course: lessons, callouts, slides, READMEs. The aim is prose a busy, capable colleague can read once and act on. When in doubt, cut words. `CLAUDE.md` references this file; read both before writing.

---

## Voice & tone

- **Plain, warm, practitioner.** Write as a knowledgeable colleague sitting beside the reader, not as a textbook or a developer.
- **Second person.** Address the reader as "you". Use "we" for shared conventions ("we standardise on VS Code").
- **Concise.** If a sentence reads the same with fewer words, cut them. Prefer short sentences and short paragraphs (2–4 sentences).
- **Encouraging, never condescending.** These are expert synthesists learning new tools. Respect that. No "simply", "just", or "obviously" — what is obvious to the author rarely is to the reader.
- **Active voice.** "Commit the file", not "the file should be committed".

## English variant

**UK / International English** throughout.

- `-ise` / `-isation`: organise, recognise, summarise, prioritise, organisation.
- `-our`: behaviour, colour, favour, labour.
- `-re`: centre, metre (but "meter" for a device).
- Other: licence (noun) / license (verb); practice (noun) / practise (verb); catalogue, dialogue, analyse, programme.
- **Important exception — software:** a computer **program**, **programming** (no "-me"); but the **course/programme** itself takes "-me". So: "write a program in R" vs "this training programme".
- Keep tool names exactly as the vendor spells them regardless of variant (see terminology).

## Terminology — use these exact forms

| Use | Not |
|---|---|
| VS Code | VSCode, vscode, Visual Studio Code (after first mention) |
| Claude Code | claude code, ClaudeCode |
| GitHub | Github, github (except in URLs/commands) |
| git | Git (lower-case for the tool in prose) |
| Quarto | quarto (capitalise in prose; lower-case in commands) |
| GitHub Copilot | Copilot (acceptable after first full mention) |
| evidence synthesis | evidence-synthesis only as a compound adjective ("evidence-synthesis workflow") |
| systematic review | sys review, SR (spell out; "SR" only after defining) |
| evidence gap map (EGM) | EGM before it is defined |
| risk of bias (RoB) | RoB before it is defined |

Define every acronym on first use: "evidence gap map (EGM)", then "EGM" thereafter. Do not assume RAISE, PRISMA, OSF, or PROSPERO are known — gloss them the first time.

## Formatting

- **Headings:** sentence case ("Working with the agent", not "Working With The Agent").
- **Emphasis:** bold for key terms and UI labels the first time; italics sparingly. Avoid bold-everywhere.
- **Lists:** use only when the content is genuinely a list. Prefer prose for explanation. Each bullet at least a clause; no one-word bullets. Always leave a blank line before a list.
- **Code:** inline `code` for commands, filenames, packages, and UI paths (`File > Open`). Fenced blocks for anything multi-line; label the language (` ```bash `, ` ```r `).
- **Links:** descriptive text, never "click here". Full URL only in reference lists.
- **Callouts (Quarto):** `note` for asides, `tip` for shortcuts/good practice, `important` for things that affect correctness, `warning` for things that can lose work or break reproducibility. Don't overuse — a page of callouts is no emphasis at all.

## Writing instructions (step-by-step)

- Use a numbered list only for ordered actions the reader performs.
- Start each step with an imperative verb: "Open the terminal", "Type `git status`".
- Show what success looks like ("You should see …") so the reader can self-check.
- Name UI elements exactly and show menu paths in code font: `Source Control > Commit`.
- Keyboard shortcuts in this form: `Ctrl/Cmd + S`.

## Citations & references

- Course materials cite sources for any factual or empirical claim. Default reference style: **APA 7th** (author–date), unless the team adopts another.
- Apply the course's own teaching: references must pass the **two-layer integrity check** before publishing — deterministic (`metacheck`/`CiteSource`) then semantic (does the source support the claim?).
- **Never fabricate a citation, quote, or statistic.** If a source can't be verified, mark it and leave it out rather than guess.

## Numbers, dates, units

- Spell out one to nine in prose; use numerals for 10+ and for anything technical (versions, counts, times). Use numerals with units ("5 GB", "20 min").
- Dates: **ISO format** in data, filenames, and logs (`2026-06-09`); a readable form in prose ("9 June 2026").
- Use a thin or comma thousands separator consistently (1,000). Use the en dash for ranges (10–12 h).

## Inclusive, accessible language

- Plain words over jargon; gloss the unavoidable jargon.
- Gender-neutral ("they"); avoid idioms that don't translate for an international audience.
- **Images:** every screenshot needs alt text describing what it shows. Don't put information only in an image — repeat key steps in text.
- Don't rely on colour alone to convey meaning.

## Quick self-check before committing prose

Could a busy colleague read it once and act? Are all terms defined and tools named correctly? Is it UK English? Is every claim cited and verified? Did you cut the words you could?
