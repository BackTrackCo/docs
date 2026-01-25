# x402r Documentation

Documentation for the x402r refundable payments protocol, built with [Mintlify](https://mintlify.com).

**Live site:** [docs.x402r.org](https://docs.x402r.org)

## Development

### Prerequisites

- Node.js >= 20
- npm or pnpm

### Local Preview

```bash
# Install Mintlify CLI (if needed)
npm i -g mintlify

# Start local dev server
npx mint dev
```

View your local preview at `http://localhost:3000`.

### Using Claude Code

This repo includes Claude Code configuration for documentation development:

```bash
# Start Claude Code in the docs folder
cd docs && claude

# Available skills:
# /docs-new-page   - Create a new documentation page
# /docs-review     - Review a page for quality issues
# /docs-update     - Update existing documentation
```

See `CLAUDE.md` for writing standards and guidelines.

## Project Structure

```
docs/
├── .claude/commands/     # Claude Code skills
├── api-reference/        # API documentation
├── essentials/           # Core documentation guides
├── images/               # Documentation images
├── logo/                 # Brand logos
├── snippets/             # Reusable MDX snippets
├── .mintignore           # Files excluded from Mintlify
├── CLAUDE.md             # Claude Code configuration
├── docs.json             # Mintlify configuration
└── index.mdx             # Homepage
```

## Publishing

Changes pushed to the default branch are automatically deployed via Mintlify's GitHub integration.

## Troubleshooting

- **Dev server not starting:** Run `mint update` to get the latest CLI version
- **404 on a page:** Ensure the page is listed in `docs.json` navigation
- **Build errors:** Check MDX syntax and frontmatter format

## Resources

- [Mintlify Documentation](https://mintlify.com/docs)
- [x402r Protocol](https://x402r.org)
- [x402r App](https://app.x402r.org)
