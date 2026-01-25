# Update Documentation Page

Update existing documentation while preserving patterns and consistency.

## Before Making Changes

1. **Read the target file(s)** completely before proposing changes
2. **Search for related content** to understand context and avoid conflicts
3. **Confirm understanding** with the user before editing

## Update Workflow

### Step 1: Understand Current State

```
Read the file to understand:
- Current structure and sections
- Writing style and voice used
- Mintlify components in use
- Related pages that link here or are linked to
```

### Step 2: Clarify the Change

Ask the user:
- What specific content needs to change?
- Should the structure change, or just content within existing sections?
- Are there related pages that might also need updates?

### Step 3: Propose Changes

Before editing, explain:
- What will be changed
- What will be preserved
- Any related files that might need updates

### Step 4: Make Changes

When editing:
- Preserve the existing frontmatter format
- Match the voice and tone of surrounding content
- Keep existing Mintlify component patterns
- Maintain heading hierarchy
- Update only what's necessary

### Step 5: Verify

After editing:
- Confirm the page renders with `npx mint dev`
- Check that links still work
- Verify code examples are valid

## Patterns to Preserve

### Frontmatter Style

Keep the existing format:
```yaml
---
title: "Existing Title"
description: "Keep the format consistent"
icon: "existing-icon"
---
```

### Component Usage

If the page uses specific components, continue using them:
- If it uses `<Steps>`, add new steps in that format
- If it uses `<Tabs>`, add new tabs consistently
- If it uses specific callout types, match them

### Code Example Style

Match existing patterns:
- Same indentation
- Same comment style
- Same level of detail in examples

## Common Update Types

### Adding a Section

1. Find the appropriate location in the document
2. Use the same heading level as sibling sections
3. Follow the same content pattern

### Updating Code Examples

1. Ensure new code is tested
2. Keep the same level of detail
3. Update any related explanatory text

### Fixing Information

1. Identify all occurrences of incorrect info
2. Check if the same info appears in other pages
3. Update consistently across all locations

### Adding Callouts

Choose the right type:
- `<Note>` - General information
- `<Tip>` - Helpful suggestions
- `<Warning>` - Important cautions
- `<Info>` - Additional context

## Output Format

After completing updates, provide:

```markdown
## Changes Made

**File:** [path]

**Modifications:**
1. [What was changed and why]
2. [What was changed and why]

**Preserved:**
- [What was intentionally kept the same]

**Related Pages to Check:**
- [Any pages that might need corresponding updates]
```
