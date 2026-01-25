# Create New Documentation Page

Create a new MDX documentation page for the x402r docs.

## Before Starting

1. Ask the user which section/category this page belongs to
2. Ask what the page should cover (topic, scope)
3. Check if similar content already exists to avoid duplication

## Page Template

Create the file with this structure:

```mdx
---
title: "Page Title"
description: "50-160 character description for SEO"
icon: "appropriate-icon"
---

## Overview

Brief introduction explaining what this page covers and why it matters.

## Prerequisites

<Note>
List any requirements before following this guide:
- Required packages or tools
- Prior knowledge assumed
- Configuration needed
</Note>

## Main Content

[Content sections with clear H2 headings]

### Subsection

[Detailed content with code examples]

```typescript
// Include tested, realistic code examples
import { refundable } from '@x402r/extensions';
```

## Next Steps

<CardGroup cols={2}>
  <Card title="Related Topic" icon="arrow-right" href="./related-page">
    Brief description of what they'll learn next.
  </Card>
</CardGroup>
```

## Checklist Before Finishing

- [ ] Frontmatter includes title, description, and icon
- [ ] Description is 50-160 characters
- [ ] All code blocks have language tags
- [ ] Code examples are realistic and tested
- [ ] Internal links use relative paths
- [ ] Images have alt text
- [ ] Content follows second-person voice ("you")
- [ ] Page renders correctly in `npx mint dev`

## Ask User

After creating the page skeleton, ask the user:
1. Does the structure look right for what you need?
2. Should I add more sections or components (Steps, Accordion, Tabs)?
3. Are there specific code examples you want included?
