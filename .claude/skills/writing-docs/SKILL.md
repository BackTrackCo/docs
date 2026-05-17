---
name: writing-docs
description: Use when writing, updating, or editing pages in the x402r Mintlify docs (docs/**/*.mdx) — including new feature documentation, guide updates, API reference pages, or any content authored for docs.x402r.org. Loads the x402r writing style, anti-slop rules, per-page creative briefs, quality gates, and source-file map. Walks through clarify → load references → match brief → read source → read neighbors → outline → draft → quality gates → vale → preview.
---

# writing-docs

Workflow for writing x402r docs that match the existing voice, structure, and technical accuracy bar.

## When this applies

- Writing a new docs page in `docs/**/*.mdx`
- Updating an existing docs page significantly (not just typo fixes)
- Documenting a newly shipped SDK feature
- Drafting reference content for `@x402r/*` packages

For tiny edits (one-line fix, typo, link update), skip the full workflow.

## Workflow

Create a TodoWrite task per step.

### 1. Clarify

Confirm:
- What's being documented (specific feature, API, concept)
- Page type (overview, installation, tutorial, guide, API reference, configuration)
- Audience (first-time reader, integrator, reference seeker)

If anything is ambiguous, ask the user before proceeding.

### 2. Load references

Read `references/style-guide.md` and `references/page-briefs.md`.

### 3. Match the page to a Creative Brief

Check `references/page-briefs.md` for a matching brief. If one exists, follow its Angle, Element table, and Omit list verbatim.

If no brief matches, pick a page type using Diataxis (reference / how-to / tutorial / explanation) and tell the user — they may want to add a brief.

### 4. Read source

From `references/source-files.md`, identify the source files relevant to this page. Read them. Never document an API without reading its implementation. Verify role availability from the table in `source-files.md`.

### 5. Read neighbors

Read 2–3 existing docs pages in the same `docs/` section. Match heading depth, intro pattern, code-block conventions, Mintlify component usage, and frontmatter shape.

### 6. Propose outline

For new pages or significant rewrites, propose the section structure and Diataxis framing before drafting. Wait for user approval.

For minor additions to existing pages, skip outline approval.

### 7. Draft

Apply `references/style-guide.md` while writing. Hard rules:

- Second person only — no "we", "our", "let's" (enforced by Vale via `FirstPersonPlural`)
- Real addresses from `x402r-sdk/packages/core/src/config/index.ts` — never `0xYourAddress` or `<CHAIN_ID>`
- Verify every export, function name, and file path exists before referencing
- Lead with WHY, code first, prose second (see `style-guide.md` § Seven Principles)
- No em dashes (`—`) — use commas, periods, or rewrite

### 8. Quality gates

Run through `references/quality-gates.md` (7 gates):
- Cover the code (prose-only readthrough makes sense?)
- Cover the prose (code-only readthrough makes sense?)
- Grep for slop (zero matches on kill-list)
- Unique info per paragraph
- Technical accuracy (every signature, import, address)
- Structural variety vs neighbor pages
- Mintlify check (broken links, frontmatter)

### 9. Vale

Run `cd docs && vale <relative-path>`. Fix every error and warning unless justified in writing as a false positive.

The PostToolUse hook in `docs/.claude/settings.json` runs Vale automatically on `.mdx` edits — fix the violations it surfaces in the next turn.

### 10. Preview

Run `npx mint dev` from `docs/`. Visually confirm the page renders correctly before declaring done.

## References

- `references/style-guide.md` — 7 principles, anti-slop list, sentence rules, style exemplar
- `references/page-briefs.md` — per-page creative briefs + drafting prompt structure
- `references/quality-gates.md` — 7-gate pre-merge checklist + anti-slop verification pass
- `references/source-files.md` — critical source files map + role availability table
