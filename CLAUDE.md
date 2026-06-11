# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

A GitBook documentation site (markdown content only — no build, lint, or test tooling) for Emmanuel Prada-Florez's IT portfolio. It is synced to GitBook via Git Sync: edits pushed to `main` publish to the site, and edits made in the GitBook UI are auto-committed back to this repo (commits like `GITBOOK-11: No subject`).

`skill.md` at the repo root is a complete reference for GitBook's file conventions, frontmatter fields, and custom block syntax (`{% hint %}`, `{% tabs %}`, `{% stepper %}`, etc.). Consult it before writing or restructuring content.

## Structure

- `SUMMARY.md` — the table of contents. It defines the entire site navigation; every page must be listed here exactly once, and its paths must match actual file locations. **Read it first** to understand the page hierarchy, and update it whenever pages are added, moved, or renamed.
- `README.md` — the site homepage.
- `self-hosted-it-service-desk/` — the one project section so far, with two subsections: `building-the-service-desk/` (environment setup + five ticket walkthroughs) and `knowledge-base/` (KB articles derived from tickets). Each section folder has its own `README.md` as its landing page.
- `.gitbook/assets/` — images uploaded through the GitBook UI, named `image (N).png`. Pages reference them with relative paths inside `<figure><img src="../../.gitbook/assets/...">` tags.

## Content Conventions

- Pages use YAML frontmatter for `description:` and optionally `layout:` (see `self-hosted-it-service-desk/README.md` for the full layout block GitBook generates).
- Images are embedded as `<figure>` elements with `<figcaption>` text, not plain markdown image syntax.
- Ticket pages follow a fixed format: title (`# Ticket #N – ...`), a bold metadata line (Reported by / Priority / Category / Status), an **Issue** paragraph, screenshots, then **Troubleshooting & Resolution**.
- KB articles (`kb-001.md` etc.) open with a blockquote carrying Audience / Category / Source ticket metadata and reference the ticket they came from.
- Use GitBook hint blocks (`{% hint style="info|warning|danger|success" %}`) for callouts rather than plain bold text or tables.
- Internal links must be relative file paths (e.g. `../folder/page.md`); avoid referencing the same file twice in `SUMMARY.md`.
