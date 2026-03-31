# x402r Docs

Mintlify docs at docs.x402r.org. Config in `docs.json`.

## Commands

```bash
npx mint dev  # Preview at localhost:3000
```

## Standards

- YAML frontmatter required on all MDX files (`title`, `description`)
- Second person ("You can..."), active voice, short paragraphs (2-4 sentences)
- **Never use em dashes (`—`).** Use a comma, period, or rewrite the sentence instead.
- Use Mermaid for diagrams, never ASCII art
- Relative paths for internal links, alt text on images
- Test all code examples before including, use realistic values
- All install commands must be copy-pasteable. Use `CodeGroup` with npm/pnpm/bun tabs for every install command.
- Components: `Note`, `Tip`, `Warning`, `Info`, `Steps`, `CardGroup`, `Tabs`, `Accordion`, `CodeGroup`
