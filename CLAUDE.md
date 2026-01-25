# x402r Documentation - Claude Code Configuration

## Working Relationship

- **Ask for clarification** when requirements are ambiguous. Don't assume.
- **Push back with reasoning** when you see a better approach.
- **Never make up information**. If you don't know, say so.

---

## Project Context

**x402r** is a refundable payments protocol extension for x402. It adds escrow deposits, refund windows, and dispute resolution to HTTP-native payments.

**Key concepts:** DepositRelay (escrow contract), Arbiter (dispute resolver), Refund Window (claim period), Facilitator (payment verifier).

**Stack:** Mintlify, MDX with YAML frontmatter, `docs.json` for config.

**Preview:** `npx mint dev` → localhost:3000

---

## Frontmatter (Required)

```yaml
---
title: "Clear Page Title"
description: "50-160 chars for SEO - what the reader will learn"
icon: "icon-name"  # Optional, for navigation
---
```

---

## Writing Standards

- **Second person:** "You can..." not "Users can..."
- **Active voice:** "Create a deposit" not "A deposit is created"
- **Prerequisites first** in procedural content
- **Short paragraphs:** 2-4 sentences max

### Code Blocks

- Always include language tags
- Test code before including
- Use realistic values, not `foo`/`bar`

### Links & Images

- Relative paths for internal links: `[page](./path/to/page)`
- Images need alt text, use `<Frame>` for screenshots

---

## Mintlify Components

Use these where appropriate:

- `<Note>`, `<Tip>`, `<Warning>`, `<Info>` - Callouts
- `<Steps>` / `<Step>` - Sequential procedures
- `<CardGroup>` / `<Card>` - Navigation cards
- `<CodeGroup>` - Multi-language examples
- `<Tabs>` / `<Tab>` - Tabbed content
- `<Accordion>` - Collapsible sections

See [Mintlify docs](https://mintlify.com/docs) for syntax.

---

## Do Not

- Skip frontmatter on MDX files
- Use absolute URLs for internal links
- Include untested code examples
- Make assumptions without asking
- Add duplicate content
- Use placeholder text in published content

---

## Before Committing

1. Preview with `npx mint dev`
2. Verify links work
3. Check code syntax
4. Review the diff
