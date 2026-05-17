# x402r Docs

Mintlify docs at docs.x402r.org. Config in `docs.json`.

## Workflow

For any non-trivial doc work, invoke the **`writing-docs` skill** — it loads the style guide, per-page creative briefs, quality gates, and source-file map, and walks the full workflow.

## Commands

```bash
npx mint dev  # Preview at localhost:3000
```

## Hard constraints

- YAML frontmatter required on all MDX files (`title`, `description`)
- Real addresses from `x402r-sdk/packages/core/src/config/index.ts` — never placeholders like `0xYourAddress` or `<CHAIN_ID>`
- Verify every export, function name, and file path exists before referencing
- Test all code examples before including
- Never use em dashes (`—`) — use a comma, period, or rewrite
- Use Mermaid for diagrams, never ASCII art
- Relative paths for internal links, alt text on images
- Components: `Note`, `Tip`, `Warning`, `Info`, `Steps`, `CardGroup`, `Tabs`, `Accordion`, `CodeGroup`

## Style

Style rules (anti-slop, voice, structure) live in:
- `.vale.ini` + `styles/x402r/` — deterministic enforcement (runs in CI and via PostToolUse hook on `.mdx` edits)
- `.claude/skills/writing-docs/references/style-guide.md` — full prose style guide (loaded by the skill)
