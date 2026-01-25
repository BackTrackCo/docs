# Review Documentation Page

Review an MDX documentation page for quality and consistency.

## Instructions

1. Read the file(s) specified by the user
2. Run through the checklist below
3. Report findings organized by category
4. Suggest specific fixes for any issues found

## Review Checklist

### Frontmatter

- [ ] Has `title` field (required)
- [ ] Has `description` field (required, 50-160 chars)
- [ ] Description is useful for SEO (not generic)
- [ ] `icon` field present if page appears in navigation

### Voice and Tone

- [ ] Uses second-person ("you") consistently
- [ ] Active voice throughout
- [ ] Present tense for descriptions
- [ ] Direct and concise (no filler)

### Structure

- [ ] Clear heading hierarchy (H2 > H3 > H4)
- [ ] Prerequisites listed early for procedural content
- [ ] Logical flow from introduction to details
- [ ] Short paragraphs (2-4 sentences)

### Code Examples

- [ ] All code blocks have language tags
- [ ] Examples use realistic values (not foo/bar)
- [ ] Code is syntactically correct
- [ ] Complete, runnable examples where appropriate
- [ ] Package installation uses CodeGroup for npm/pnpm/yarn

### Links and References

- [ ] Internal links use relative paths
- [ ] No broken links
- [ ] No absolute URLs for docs content
- [ ] External links are appropriate

### Images

- [ ] All images have alt text
- [ ] Images use Frame component for screenshots
- [ ] Images stored in /images directory

### Mintlify Components

- [ ] Appropriate use of Note/Tip/Warning/Info callouts
- [ ] CardGroup for navigation cards
- [ ] Steps for sequential procedures
- [ ] CodeGroup for multi-language examples
- [ ] Components are properly closed

### Content Quality

- [ ] No duplicate content (check for similar pages)
- [ ] No placeholder text or TODOs
- [ ] Accurate technical information
- [ ] Appropriate depth for the audience

## Output Format

```markdown
## Review: [filename]

### Issues Found

**Frontmatter**
- Issue: [description]
  Fix: [suggested fix]

**Code Examples**
- Issue: [description]
  Fix: [suggested fix]

### Suggestions

- [Optional improvements that aren't strict issues]

### Summary

[Brief overall assessment]
```

## If No File Specified

Ask the user which file(s) to review. Suggest checking recently modified files or offer to review a specific section of the docs.
