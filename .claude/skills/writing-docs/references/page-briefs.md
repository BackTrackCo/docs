# Page Creative Briefs

WHAT to write for each x402r SDK doc page. Per-page angle, element guidance, omit list, and source files.

For pages not listed here, pick a Diataxis type (reference / how-to / tutorial / explanation) and propose adding a brief.

---

## Variation Injection

Add a page-specific angle to prevent uniformity:

| Page type | Angle instruction |
|-----------|-------------------|
| Overview | "Write like a landing page. Reader is deciding whether to invest time." |
| Installation | "Shortest possible useful page. Zero to running in 60 seconds of reading." |
| Create-client | "Write like a decision tree. Reader picks between `createX402r()` and role presets." |
| TypeScript | "Write as a reference sheet. Someone will Ctrl+F here. Prioritize scannability." |
| Guides | "Write like a story: setup, action, verification. Reader copies and runs." |
| API reference | "Write as a lookup table. Developers arrive from other pages to check a method." |

---

## Drafting prompt structure

When drafting a page, assemble these five inputs (mentally — they shape the draft):

**Input 1 — Source files** (not just types — implementation too, for edge cases)
Read the relevant `.ts` files from `source-files.md`.

**Input 2 — Working example** from `x402r-sdk/examples/`
Find and read the relevant example file.

**Input 3 — Creative brief**
Pull the brief for this page from the sections below.

**Input 4 — Style exemplar**
Always re-read `docs/x402-integration/overview.mdx`. It leads with contrast ("exact scheme works well for immediate-delivery... but creates friction for"), uses dollar amounts, shows concrete scenarios.

**Input 5 — Positive writing rules** (from `style-guide.md`)
1. Open with a sentence that answers "why would I read this page?"
2. Show code before explaining it.
3. Use real addresses.
4. Explain non-obvious defaults and constraints; skip the obvious.
5. State tradeoffs when there are two ways.
6. Acknowledge limitations.
7. Vary sentence length.
8. Never use slop list words. No exclamation marks.
9. Every paragraph adds new information.
10. Code comments explain "why," not "what."

---

## Getting Started (4 pages)

### `sdk/overview.mdx` — "Am I in the Right Place?"

**Angle:** Landing page. Reader decides whether to invest time.

| Element | Guidance |
|---------|----------|
| Opening hook | Lead with x402 vs x402r delta (what x402r *adds*), not a definition |
| Packages | 3 cards: `@x402r/sdk` (most users), `@x402r/core` (low-level), `@x402r/helpers` (x402 server). Link each to its next page |
| Action groups | Table of 8 groups, one-line descriptions, link to API ref |
| Role presets | Brief: "TypeScript autocomplete only shows methods your role can call." |
| Chains | Real table from `x402rChains` — all chains with USDC addresses |
| Honest status | Warning: testnet-tested, mainnet deployed but less battle-tested |
| **Omit** | Don't explain escrow (link to Protocol tab). Don't explain viem. |

**Source files:** `client.ts`, `types.ts` (X402r interface), `config/index.ts`

### `sdk/installation.mdx` — "60 Seconds to Running"

**Angle:** Shortest page on the site. Zero to running in under a minute.

| Element | Guidance |
|---------|----------|
| Opening | No intro paragraph. Jump straight to install command |
| Primary install | `npm install @x402r/sdk viem` (CodeGroup: npm/pnpm/bun). One path. |
| Secondary | Accordion for `@x402r/core` and `@x402r/helpers` (for those who know they need them) |
| Viem clients | `createPublicClient` + `createWalletClient` with `baseSepolia`. Reference viem docs. |
| Chain config | `getChainConfig(84532)` showing return shape |
| **Omit** | No `.env` file ceremony. No lengthy private key warnings (guide territory). |

**Source files:** `config/index.ts` (for `getChainConfig` return type)

### `sdk/create-client.mdx` — "Choose Your Path"

**Angle:** Decision tree. Reader picks between full client and role presets.

| Element | Guidance |
|---------|----------|
| Opening | Frame as a decision, not a catalog |
| Decision guidance | When to use `createX402r()` (multi-role, read-only, admin) vs presets (most apps). Be opinionated. |
| Full client | Real config with Base Sepolia addresses. Config table — only non-obvious fields get prose. |
| Role presets | 3 concise examples. Highlight narrowing: "exposes `refund.request()` but hides `payment.authorize()` — payers don't authorize" |
| `canExecute` | One-liner. "Checks condition slots before submitting. Saves gas." |
| `createMemoryStore` | One-liner. "In-memory store for dev. Data lost on exit." |
| `.extend()` | Brief example, link to extend-plugins guide |
| **Omit** | Don't enumerate every method per role (that's typescript.mdx). Don't repeat viem setup. |

**Source files:** `client.ts`, `presets.ts`, `types.ts`, `can-execute.ts`

### `sdk/typescript.mdx` — "Reference Sheet"

**Angle:** Scannable reference. People Ctrl+F here for type names.

| Element | Guidance |
|---------|----------|
| Opening | One line: "TypeScript 5.0+ with `strict: true`." |
| Type imports | Key types from `@x402r/sdk` and `@x402r/core` |
| Role narrowing | Tables per preset: which groups, which methods. From `types.ts` Pick types (lines 235-379) |
| Conditional groups | Why `escrow`/`refund`/`evidence`/`freeze`/`query` can be `undefined`. Null-check pattern. |
| Error types | `ValidationError`, `ConfigError`, `ContractCallError` — when each is thrown |
| **Omit** | Don't repeat config table from create-client. Don't list full method signatures. |

**Source files:** `types.ts` (lines 235-379 for Pick types), `presets.ts`

---

## Guides (6 pages)

### `sdk/guides/deploy-operator.mdx` — "Get Your Operator Running"

**Hook:** "Every x402r payment flows through a PaymentOperator. Deploy one before you can authorize, release, or refund."

**Format:** Recipe. Prerequisites -> `deployMarketplaceOperator()` with real options -> What gets deployed -> Verify on basescan -> Connect result to SDK config.

**Source:** `deploy/presets.ts`, `examples/shared/anvil-setup.ts`

### `sdk/guides/accept-payments.mdx` — "Merchant Payment Lifecycle"

**Hook:** "A payment arrives when the payer's authorization hits your operator. After escrow, release the funds. If disputed, handle the refund."

**Arc:** Payment arrives (check state) -> Wait for escrow -> Release -> Handle disputes -> Post-escrow refund. Key insight: `payment.authorize()` is called by facilitator, not merchant. Merchant's first interaction is checking state.

**Source:** `examples/merchant/release-escrow.ts`, `examples/scenarios/happy-path-release.ts`

### `sdk/guides/request-refund.mdx` — "Payer Dispute Flow"

**Hook:** "Paid for something that didn't arrive? Request a refund during escrow. If ignored, freeze and submit evidence."

**Flow:** Request -> Check status -> Cancel (optional) -> Freeze -> Submit evidence -> Wait for arbiter.

**Source:** `examples/payer/request-refund.ts`, `examples/payer/freeze-payment.ts`

### `sdk/guides/resolve-disputes.mdx` — "Arbiter Decision Guide"

**Hook:** "Review refund requests and decide: approve, deny, or decline to rule."

**Flow:** List pending -> Review evidence -> Decide -> Unfreeze -> Distribute fees. Key insight: `refundInEscrow()` triggers RefundRequest recorder auto-approve — no separate `approve()` call.

**Source:** `examples/arbiter/approve-refund.ts`, `examples/scenarios/dispute-resolution.ts`

### `sdk/guides/watch-events.mdx` — "Real-Time Events"

Short page. 4 watchers, unsubscribe pattern, transport note, type caveat about `unknown`.

**Source:** `types.ts` (WatchActions)

### `sdk/guides/extend-plugins.mdx` — "Custom Plugins"

Short page. `.extend()` pattern, when to use, built-in plugin factories.

**Source:** `client.ts` (buildExtend function)

---

## API Reference (8 pages)

Consistent format per method (uniform is intentional for lookup material):

```
### methodName

[One sentence: what it does and when you use it]

\`\`\`typescript
const result = await client.group.methodName(param1, param2)
\`\`\`

| Parameter | Type | Description |
|-----------|------|-------------|
| param1 | `Type` | [what it means, not what it is] |

**Returns:** `Type` — [what the return value represents]
**Role availability:** Payer / Merchant / Arbiter
**Errors:** [common error cases]
```

| Page | Key notes |
|------|-----------|
| `sdk/api/payment.mdx` (9 methods) | Open with `authorize` vs `charge` difference. `getState` returns `[boolean, bigint, bigint]` — name them. |
| `sdk/api/escrow.mdx` (3 methods) | All read-only. Brief page. |
| `sdk/api/refund.mdx` (15 methods) | Split: Write ops / Read ops. Document `RefundRequestStatus` enum. |
| `sdk/api/evidence.mdx` (4 methods) | IPFS CID convention. `submit` is write, rest are read. |
| `sdk/api/freeze.mdx` (3 methods) | Payer freezes, arbiter unfreezes. |
| `sdk/api/query.mdx` (3 methods) | Explain resolver priority: store -> recorder -> events. |
| `sdk/api/operator.mdx` (8 methods) | `getConfig()` returns full slot layout. `distributeFees` is write. |
| `sdk/api/watch.mdx` (4 methods) | Unsubscribe pattern. `unknown` type note. |

---

## Configuration + Integrations (5 pages)

| Page | Content |
|------|---------|
| `sdk/config/chains.mdx` | Full chain table. All lookup functions. "Identical addresses via CREATE3. Only USDC differs." |
| `sdk/config/addresses.mdx` | Protocol, factory, singleton address tables. CREATE3 explanation. |
| `sdk/integrations/x402-server.mdx` | `forwardToArbiter()` from `@x402r/helpers`. Express + Hono examples. `@x402r/evm` peer dep. |
| `sdk/integrations/facilitator.mdx` | Minimal. Port from existing. |
| `sdk/integrations/examples.mdx` | CardGroup linking to GitHub example directories. |
