---
generated: '2026-09-19'
method: generated
name: Buy an x402-priced trust service
description: Quote, challenge and settle one of MUJ428's five paid services (evidence signal, reputation check, milestone attestation, trust report, transaction assurance) through the x402 402-then-retry flow, with the caller — never MUJ428 — authorizing the payment.
api: openapi/muj428-com-trust-layer-openapi.json
operations: [getPricing, getServiceCatalog, evidenceSignal, reputationCheck, milestoneAttestation, trustLayerReport, transactionAssurance]
source: >-
  Grounded in openapi/muj428-com-trust-layer-openapi.json (402 responses on the five paid operations), the provider's
  developer.json x402_flow, pricing.json, /.well-known/x402 and agents.json flows buy_evidence_signal /
  buy_reputation_check / buy_milestone_attestation. Every operationId verified verbatim in the spec. Prices per
  plans/muj428-com-plans-pricing.yml; errors per errors/muj428-com-problem-types.yml.
---

# Buy an x402-priced trust service

Five operations are priced per call and settle in USDC on Base (`eip155:8453`) through x402 v2. The pattern is
identical for all five: call once unpaid to receive the exact challenge, let the caller authorize payment under its
own wallet policy, then retry the same request with the signature.

## Auth
- None to call; payment is the gate. See `authentication/muj428-com-authentication.yml`.
- Base URL: `https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer` (the challenge-first paid facade also
  answers at `.../functions/v1/trust-layer-x402`).

## Steps

1. **Read the price you are about to pay** — `getPricing` (`GET /pricing.json`) or `getServiceCatalog`
   (`GET /services`). At capture: evidence signal 0.25 USDC, reputation check 0.10, milestone attestation 0.25,
   trust report 0.50; transaction assurance 2% ($9 min) under $50,000 and 1% ($25 min) at or above. Prices are
   reviewed roughly every 60 days and never auto-increase; the challenge, not this document, is authoritative.
2. **Send the request without a payment** — one of `evidenceSignal` (`POST /v1/evidence-signal`),
   `reputationCheck` (`POST /v1/reputation-check`), `milestoneAttestation` (`POST /v1/milestone-attestation`),
   `trustLayerReport` (`POST /v1/trust-layer-report`), `transactionAssurance` (`POST /v1/transaction-assurance`,
   fee computed from `transaction_value_usd`). The spec declares no request schema for these; the provider's
   commercial-contract.json names the per-service input shapes. An empty body is rejected with `422
   {"error":"invalid_request","service":"..."}` BEFORE any challenge, so validation failures never cost anything.
3. **Receive the challenge** — HTTP `402` with a `PAYMENT-REQUIRED` header naming the exact amount, network, asset
   (`USDC` at `0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`) and seller.
4. **Authorize under the caller's policy** — the wallet decision is the caller's; MUJ428's own rules say it "never
   fabricates or sends a payment signature", `auto_spend` is false, and paid continuation needs explicit caller
   authorization. Do not sign anything your operator's spend policy has not approved.
5. **Retry the same request with `PAYMENT-SIGNATURE`** — MUJ428 verifies, reserves, settles, fulfils synchronously
   and returns `200` plus a `PAYMENT-RESPONSE` header and the service result.

## Rules
- **No reversal is documented** for a settled call — no refund, void or cancel operation exists and no refund policy
  is published; treat a settlement as final (`conventions/muj428-com-conventions.yml` reversibility: none).
- **No idempotency key** is documented on these five operations; a retry after a timeout risks a second charge.
  Keep the 402 challenge and the signature you sent, and quote `X-Request-Id` / `sb-request-id` to
  sales@muj428.com if the outcome is unclear.
- **Quote before assurance:** for `transactionAssurance`, the MCP tool `select_assurance_tier` computes the exact fee
  without moving money (no REST equivalent).
- The same services are reachable through the MCP tool `invoke_trust_service` (call once without
  `payment_signature` to get the challenge, then again with it) and the A2A skills of the same names.
