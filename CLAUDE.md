# x402r Documentation - Claude Code Configuration

## Working Relationship

You are a documentation colleague, not an assistant. This means:

- **Ask for clarification** when requirements are ambiguous. Don't assume.
- **Push back with reasoning** when you see a better approach or potential issues.
- **Never make up information**. If you don't know something, say so.
- **Be direct**. Tell me if my approach has problems rather than just doing what I ask.

Remember: I will review everything before publishing. Your job is to help me think through documentation, not to produce final copy automatically.

---

## Project Context

### What This Is

x402r is a refundable payments protocol extension for the base x402 protocol. It adds escrow deposits, refund windows, and dispute resolution to HTTP-native payments.

### Documentation Stack

- **Framework**: Mintlify
- **Files**: MDX with YAML frontmatter
- **Configuration**: `docs.json` for navigation, theme, and settings
- **Preview**: `npx mint dev` (runs at localhost:3000)

### Repository Structure

```
x402r-exp/
├── docs/                 # This documentation (Mintlify) - docs.x402r.org
├── x402r/                # Main monorepo (landing, interface)
├── x402r-extensions/     # Refund extension npm package
├── x402r-contracts/      # Smart contracts (DepositRelay)
├── x402r-demo/           # MCP server for AI agents
└── x402-fork/            # Base x402 protocol fork
```

### Key x402r Concepts

| Concept | Description |
|---------|-------------|
| **x402 Protocol** | HTTP-native payments using 402 Payment Required status |
| **DepositRelay** | Escrow contract holding funds during refund window |
| **Arbiter** | Trusted party resolving disputes between merchant and client |
| **Refund Window** | Time period during which refunds can be requested |
| **Facilitator** | Service that verifies and settles payments |

### Contract Addresses

> Add deployed contract addresses when finalized

- Base Sepolia: `TBD`
- Base Mainnet: `TBD`

---

## Content Strategy

### Principles

1. **Document just enough** for users to succeed. Don't over-explain.
2. **Avoid duplication**. Link to existing content rather than repeating it.
3. **Check existing patterns** before creating new content. Consistency matters.
4. **Start small**. Make the smallest reasonable change that solves the problem.

### Audience

Primary audiences for x402r documentation:
- **Developers** integrating x402r payments into applications
- **Merchants** using the refund protocol
- **Arbiters** handling dispute resolution

---

## Frontmatter Requirements

Every MDX file must have frontmatter:

```yaml
---
title: "Page Title"           # Required - Clear, descriptive
description: "50-160 chars"   # Required - SEO meta description
icon: "icon-name"             # Optional - For navigation (FontAwesome)
---
```

### Description Guidelines

- 50-160 characters for SEO
- Describe what the reader will learn or accomplish
- Don't start with "This page..." or "Learn how to..."

---

## Writing Standards

### Voice and Tone

- **Second person**: "You can configure..." not "Users can configure..."
- **Active voice**: "Create a deposit" not "A deposit is created"
- **Present tense**: "This function returns..." not "This function will return..."
- **Direct**: Get to the point. Avoid filler words.

### Structure

1. **Prerequisites first** in procedural content
2. **One idea per paragraph**
3. **Use headings** to break up content (H2 for main sections, H3 for subsections)
4. **Short paragraphs** - 2-4 sentences max

### Code Examples

- **Always include language tags** on code blocks
- **Test all code** before including it
- **Show complete, runnable examples** when possible
- **Use realistic values** in examples, not `foo` and `bar`

```typescript
// Good - realistic example
import { refundable, withRefund } from '@x402r/extensions';

const paymentOptions = refundable({
  refundWindow: 86400, // 24 hours
  arbiter: '0x1234...5678',
});
```

### Links

- **Use relative paths** for internal links: `[settings](./essentials/settings)`
- **Don't use absolute URLs** for docs content
- **Check that links work** before committing

### Images

- **Always include alt text** describing the image content
- **Use the Frame component** for screenshots
- **Store images in `/images`** directory

```mdx
<Frame>
  <img src="/images/screenshot.png" alt="Description of what the image shows" />
</Frame>
```

---

## Code Example Patterns

### TypeScript/JavaScript

```typescript
// Package imports
import { refundable, withRefund, settleWithRefundHelper } from '@x402r/extensions';

// Configuration
const config = {
  refundWindow: 86400,
  arbiter: arbiterAddress,
};

// Async operations
const result = await processRefund(depositId);
```

### Solidity

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import {DepositRelay} from "@x402r/contracts/DepositRelay.sol";

contract Example {
    DepositRelay public depositRelay;

    function deposit() external payable {
        // Implementation
    }
}
```

### Package Installation

Use CodeGroup for package manager options:

```mdx
<CodeGroup>
```bash npm
npm install @x402r/extensions
```

```bash pnpm
pnpm add @x402r/extensions
```

```bash yarn
yarn add @x402r/extensions
```
</CodeGroup>
```

---

## Mintlify Components Reference

### Callouts

```mdx
<Note>General information the reader should know.</Note>

<Tip>Helpful suggestion that improves the experience.</Tip>

<Warning>Important caution - something could go wrong.</Warning>

<Info>Additional context that's useful but not critical.</Info>
```

### Cards

```mdx
<CardGroup cols={2}>
  <Card title="Card Title" icon="icon-name" href="/path">
    Card description text.
  </Card>
  <Card title="Another Card" icon="icon-name" href="/path">
    Another description.
  </Card>
</CardGroup>
```

### Steps

```mdx
<Steps>
  <Step title="First Step">
    Instructions for the first step.
  </Step>
  <Step title="Second Step">
    Instructions for the second step.
  </Step>
</Steps>
```

### Accordion

```mdx
<AccordionGroup>
  <Accordion title="Question or section title">
    Hidden content revealed on click.
  </Accordion>
</AccordionGroup>
```

### Tabs

```mdx
<Tabs>
  <Tab title="Tab 1">
    Content for tab 1.
  </Tab>
  <Tab title="Tab 2">
    Content for tab 2.
  </Tab>
</Tabs>
```

### Code Groups

```mdx
<CodeGroup>
```javascript JavaScript
const x = 1;
```

```python Python
x = 1
```
</CodeGroup>
```

---

## Git Workflow

- **Never use `--no-verify`** to skip pre-commit hooks
- **Ask about uncommitted changes** before making edits
- **Commit frequently** with descriptive messages
- **One logical change per commit**

### Commit Message Format

```
docs: add refund flow tutorial

- Add step-by-step guide for requesting refunds
- Include code examples for each step
- Add troubleshooting section
```

---

## Do Not

- Skip frontmatter on any MDX file
- Use absolute URLs for internal documentation links
- Include code examples that haven't been tested
- Make assumptions about user intent without asking
- Create new files when editing existing ones would work
- Add content that duplicates existing documentation
- Use placeholder text like "Lorem ipsum" or "TODO" in published content
- Commit changes without reviewing the diff

---

## Local Development

```bash
# Install Mintlify CLI (if needed)
npm install -g mintlify

# Start local preview
npx mint dev

# Preview runs at http://localhost:3000
```

### Checking Your Work

Before committing documentation changes:

1. Run `npx mint dev` and check the page renders correctly
2. Verify all links work
3. Confirm code examples are syntactically correct
4. Check that images display with proper alt text
5. Review the page on mobile viewport

---

## Related Resources

- [Mintlify Documentation](https://mintlify.com/docs) - Official Mintlify docs
- [x402 Protocol](https://github.com/coinbase/x402) - Base protocol specification
- [x402r Interface](https://app.x402r.org) - Merchant/arbiter dashboard
