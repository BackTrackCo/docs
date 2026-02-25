# x402r Docs

Mintlify docs at docs.x402r.org. Config in `docs.json`.

## Commands

```bash
npx mint dev  # Preview at localhost:3000
```

## Standards

- YAML frontmatter required on all MDX files (`title`, `description`)
- Second person ("You can..."), active voice, short paragraphs (2-4 sentences)
- Use Mermaid for diagrams, never ASCII art
- Relative paths for internal links, alt text on images
- Test all code examples before including, use realistic values
- Components: `Note`, `Tip`, `Warning`, `Info`, `Steps`, `CardGroup`, `Tabs`, `Accordion`
