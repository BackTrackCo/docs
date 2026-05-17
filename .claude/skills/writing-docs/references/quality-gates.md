# Quality Gates

HOW to verify a docs page before declaring done. Pre-merge checklist (7 gates) and anti-slop verification pass.

---

## Pre-Merge Checklist

| # | Gate | How to test |
|---|------|-------------|
| 1 | **Cover the code** | Read only prose (ignore code blocks). Does it tell a coherent story? |
| 2 | **Cover the prose** | Read only code blocks. Can you follow the flow? If yes, prose may be redundant. |
| 3 | **Grep for slop** | Search for kill-list words. Zero matches required. |
| 4 | **Unique info** | Annotate each paragraph: what NEW info does it add? No annotation = filler = delete. |
| 5 | **Technical accuracy** | Every signature matches `types.ts`. Every import resolves. Every address matches `config/index.ts`. |
| 6 | **Structural variety** | Compare first paragraphs across same-batch pages. >50% same pattern = rewrite outliers. |
| 7 | **Mintlify check** | `npx mintlify broken-links` passes. Preview deploy loads. Frontmatter has `title` + `description`. |

---

## Anti-Slop Verification Pass

After generating a page, run this review checklist:

1. Does the opening sentence *motivate* (not describe)?
2. Any sentences true of *any* SDK? (Generic = slop. Delete.)
3. Placeholder values that could be real addresses?
4. Consecutive paragraphs mergeable without info loss?
5. Every code block shows something the reader will actually type or run?
6. Any "allows you to" / "enables" / "provides" / "makes it easy"?
7. Any sentence a developer would skip because it states the obvious?

For each issue, suggest a concrete replacement. Then rewrite.

---

## Vale enforcement

Vale runs automatically via the PostToolUse hook in `docs/.claude/settings.json` on any `.mdx` Edit/Write. It catches:

- `Slop.yml` — filler/marketing language ("seamless", "leverage", "unlock the", etc.)
- `Enthusiasm.yml` — enthusiasm markers ("Amazing", "Exciting", etc.)
- `FirstPersonPlural.yml` — "we", "our", "let's"
- `Microsoft`, `write-good`, `proselint` — standard prose-quality packs

Run manually: `cd docs && vale path/to/file.mdx`

Fix every error and warning before claiming done. If a warning is a false positive, justify it in writing (do not silently ignore).
