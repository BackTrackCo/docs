# Source Files & Role Availability

WHERE to find the source code that backs each docs page, and which roles can call each method.

---

## Critical Source Files

| Purpose | Path |
|---------|------|
| Action group interfaces + role Pick types | `x402r-sdk/packages/sdk/src/types.ts` |
| Client factory + extend pattern | `x402r-sdk/packages/sdk/src/client.ts` |
| Role presets + validation | `x402r-sdk/packages/sdk/src/presets.ts` |
| Chain config + all addresses | `x402r-sdk/packages/core/src/config/index.ts` |
| Deploy presets | `x402r-sdk/packages/core/src/deploy/presets.ts` |
| Working scenarios | `x402r-sdk/examples/scenarios/` |
| Style exemplar | `docs/x402-integration/overview.mdx` |

Always read the source before documenting an API. Verify file paths still exist — the SDK reorganizes occasionally.

---

## Role Availability Reference

From `types.ts` Pick types (lines 235-379). **Verify against source before publishing** — methods get added and removed.

| Method | Payer | Merchant | Arbiter |
|--------|:-----:|:--------:|:-------:|
| `payment.authorize` | | Y | |
| `payment.charge` | | Y | |
| `payment.release` | | Y | |
| `payment.refundInEscrow` | | Y | Y |
| `payment.refundPostEscrow` | | Y | |
| `payment.approvePostEscrowRefund` | | Y | |
| `payment.getPostEscrowRefundAllowance` | | Y | |
| `payment.getState` | Y | Y | Y |
| `payment.getAmounts` | Y | Y | Y |
| `refund.request` | Y | | |
| `refund.cancel` | Y | | |
| `refund.deny` | | | Y |
| `refund.refuse` | | | Y |
| `refund.get` | Y | Y | Y |
| `refund.getByKey` | Y | Y | Y |
| `refund.getStatus` | Y | Y | Y |
| `refund.has` | Y | Y | Y |
| `refund.getStoredPaymentInfo` | Y | Y | Y |
| `refund.getPayerRequests` | Y | | |
| `refund.getReceiverRequests` | | Y | |
| `refund.getOperatorRequests` | | | Y |
| `refund.getCancelCount` | Y | Y | Y |
| `refund.getCancelledAmount` | Y | Y | Y |
| `freeze.freeze` | Y | | |
| `freeze.unfreeze` | | | Y |
| `freeze.isFrozen` | Y | Y | Y |
| `evidence.*` (all) | Y | Y | Y |
| `escrow.*` (all) | Y | Y | Y |
| `query.*` (all) | Y | Y | Y |
| `operator.getConfig` | Y | Y | Y |
| `operator.getFeeAddresses` | Y | Y | Y |
| `operator.calculateFees` | | Y | |
| `operator.calculateOperatorFeeBps` | | Y | |
| `operator.calculateProtocolFeeBps` | | Y | |
| `operator.getAuthorizedFees` | | Y | |
| `operator.getAccumulatedProtocolFees` | | Y | Y |
| `operator.distributeFees` | | Y | Y |
| `watch.*` (all) | Y | Y | Y |

---

## Protocol facts

x402r-specific accuracy notes that don't live in the code:

- Payer signs the authorization; merchant submits. Never say "merchant authorizes."
- `viem` and `@x402r/core` are regular deps of `@x402r/sdk`, not peer deps. Don't tell users to install them separately unless importing directly from `@x402r/core`.
- `@x402r/helpers` is merchant-server only — client-side utilities go in `@x402r/sdk`.
- Verify function signatures against `types.ts` and `presets.ts` before documenting.
