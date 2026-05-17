# Style Guide

Rules for HOW to write x402r docs. The Diagnostic Test, seven principles, anti-slop word list, sentence-level rules, and the style exemplar.

---

## The Diagnostic Test

Every paragraph must pass: **"Would a developer who already has the source code learn something from this sentence that the code alone does not tell them?"** If the answer is no, delete the paragraph.

---

## Seven Principles

### 1. Lead with WHY, not WHAT

**Bad:** "The x402r SDK provides TypeScript bindings for the x402r refundable payments protocol."

**Good:** "x402 payments are instant and irreversible. x402r adds escrow holds, refund windows, and dispute resolution on top."

The bad version describes the page topic. The good version tells you why you need it by establishing contrast. Open every page by answering the question the reader actually has: "Should I keep reading?"

### 2. Code first, prose second

Show the code block, then annotate only what the code does NOT make obvious. If `getChainConfig(84532)` is self-explanatory, don't add "This retrieves the chain configuration for Base Sepolia." Instead note something useful: "USDC is the only address that differs between chains — everything else is identical via CREATE3."

### 3. Real values, never placeholders

Use actual addresses from `x402r-sdk/packages/core/src/config/index.ts`:

| Use this | Not this |
|----------|----------|
| `0x3Cd5c76Fefe46CB07788Ee8f80B93B20D81941D4` | `'0xYourOperator...'` |
| `84532` | `<CHAIN_ID>` |
| `0x036CbD53842c5426634e7929541eC2318f3dCF7e` | `'YOUR_USDC_ADDRESS'` |

Where addresses are per-deployment (operator address after deploy), link to the deploy guide: "Your operator address comes from `deployMarketplaceOperator()` — see [Deploy an Operator](/sdk/guides/deploy-operator)."

### 4. Acknowledge the non-obvious

The things that trip developers up are never the things the code is explicit about. Call them out:

- `client.escrow` is `undefined` if no `escrowPeriodAddress` in config
- `refundInEscrow()` is gated by a StaticAddressCondition on the operator
- Watch callbacks currently receive `unknown` (typed events coming later)
- `eventFromBlock` must be set to enable event-based payment lookups
- Role presets require `walletClient` — omit it and you get a `ValidationError`

### 5. Vary structure page by page

| Page type | Feel | Structure |
|-----------|------|-----------|
| Overview | Landing page, orientation | Cards, quick taxonomy, "go here based on your role" |
| Installation | Shortest page on the site | One install command, one code block, done |
| Create-client | Decision tree | "Use X when Y", opinionated guidance |
| TypeScript | Reference sheet | Tables, scannable, Ctrl+F friendly |
| Guides | Story with beginning/middle/end | Setup -> Action -> Verification |
| API reference | Lookup table | Uniform format (intentionally) |

If more than half the pages in a batch start with the same structural pattern, rewrite the outliers.

### 6. Be opinionated

Save the reader from making bad decisions:

**Good:** "For most applications, use `createMerchantClient()`. Use `createX402r()` only when your app acts as multiple roles or needs read-only access without a wallet."

**Bad:** "You can use either `createX402r()` or `createMerchantClient()` depending on your needs."

The first version makes a recommendation. The second punts.

### 7. Be honest about limitations

"Event watchers currently return untyped logs (`unknown`). Cast them until typed events ship in a future release."

Honesty builds trust. Pretending the API is polished when it's v0.0.2 does not.

---

## Anti-Slop Word List

Search and destroy these patterns in every draft:

| Kill | Replace with |
|------|-------------|
| "allows you to" / "enables you to" / "provides" | Direct statement: "Release transfers escrowed funds to the receiver." |
| "powerful" / "robust" / "seamless" / "comprehensive" | Delete entirely |
| "leverage" / "empower" / "unlock" / "revolutionize" | Delete entirely |
| `!` (exclamation marks) | Period |
| "In this guide" / "In this section" | Delete — reader knows where they are |
| "Let's" / "We'll" / "We" / "Our" | Imperative: "Create a client" not "Let's create a client" |
| `0x...` / `YOUR_KEY` / `<PLACEHOLDER>` | Real address or link to where you get it |
| "makes it easy" / "simple" / "straightforward" | Show the easy thing. A 3-line example proves simplicity. |
| "cutting-edge" / "state-of-the-art" / "next-generation" | Delete |
| "Amazing" / "Great" / "Exciting" | Delete |

### Sentence-Level Rules

- Vary sentence length. Mix 5-word sentences with 20-word sentences. Uniform length = machine writing.
- Every paragraph must add information the previous paragraph did not. If two paragraphs merge without info loss, merge them.
- Comments in code blocks explain the "why," not the "what." Skip comments on self-evident lines.
- Second person, imperative mood. "Create a client" not "Creating a client."
- 2-3 sentences per paragraph max.

---

## Style Exemplar

The best existing page is `docs/x402-integration/overview.mdx`. Key patterns to replicate:

1. **Leads with contrast:** "The exact scheme works well for immediate-delivery... but creates friction for" — then lists concrete scenarios
2. **Uses dollar amounts:** "$500 → Server crashes → Money lost" — not abstract descriptions
3. **Problem/Solution pairs:** Each use case states the problem first, then shows escrow solving it
4. **Concrete scenarios:** "LLM agent making API calls", "GPU cluster for training job", "real-time data feed" — specific enough to imagine
5. **Mermaid diagrams:** Sequence diagrams for the payment flow — visual, not prose
6. **Minimal jargon introduction:** Defines terms inline with one-sentence definitions, not a glossary page
