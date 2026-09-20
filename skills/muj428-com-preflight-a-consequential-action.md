---
generated: '2026-09-19'
method: generated
name: Preflight a consequential action
description: Before an agent pays, buys, delegates, approves, writes, releases or commits, resolve the intent into MUJ428's action vocabulary, run the free Trust Reflex preflight, and act only under the caller's own policy with the Trust Receipt in hand.
api: openapi/muj428-com-trust-layer-openapi.json
operations: [resolveTrustRoute, trustAction, getTrustHeartbeat]
source: >-
  Grounded in openapi/muj428-com-trust-layer-openapi.json (v1.8.2, fetched 2026-09-19 from
  https://agents.muj428.com/openapi.json), the provider's AGENTS.md and agents.json flow run_trust_reflex. Every
  operationId verified verbatim in that spec. Auth per authentication/muj428-com-authentication.yml (none), errors per
  errors/muj428-com-problem-types.yml, quota per rate-limits/muj428-com-rate-limits.yml.
---

# Preflight a consequential action

MUJ428's own rule is "BEFORE CONSEQUENCE -> CALL MUJ428". The preflight is free for the first 1,000 qualifying
decisions per `caller_ref`, needs no credential, moves no money, and returns a decision plus a Trust Receipt v1.3
whose `execution_authority` is `false` — the receipt informs the caller's policy; it never replaces it.

## Auth
- None. No API key, wallet or signup. See `authentication/muj428-com-authentication.yml`.
- Base URL: `https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer`.

## Steps

1. **Resolve the intent** — `resolveTrustRoute` (`POST /v1/route`). Send what you know (`action` or `capability`,
   `tool_name`, `consequential` / `external` / `irreversible` / `binding` flags). If your intent is not one of
   `PAY, BUY, DELEGATE, TRUST, ACCEPT, APPROVE, WRITE, RELEASE, COMMIT, PROPOSE`, this returns the supported action to
   preflight with. Never invent an action value: a `{}` body gets a 422 whose `allowed_actions` echoes the enum.
2. **Preflight** — `trustAction` (`POST /v1/trust`) with the FLAT shape:
   `{"caller_ref":"<stable agent id>","action_ref":"<stable id for THIS action>","action":"PAY","amount_usd":42,"irreversible":true}`.
   `caller_ref` and `action_ref` are yours to choose (≥3 chars) and are the only identity on the surface; add
   `evidence_state`, `closing_evidence_observable`, `authorization_ceiling`, `authority_expires_at` and
   `previous_trust_receipts[]` when you have them — an `INCOMPLETE`, `CONFLICTING`, `STALE` or `FAILED`
   `evidence_state` requires verification rather than manufacturing an ALLOW.
3. **Read the decision** — a `200` carries `ALLOW | VERIFY | REQUIRE_VERIFICATION | DENY` (public envelope
   `EXECUTE / REQUIRE_MORE_EVIDENCE / BLOCK`), `payment_required=false` while quota remains, and the receipt.
   `DENY` is a successful 200, not an error. A `503` means a dependency is down and "failure is never ALLOW" —
   treat it as BLOCK.
4. **Apply your own policy, then act** — the caller executes (or safely refuses); MUJ428 does not. Keep the receipt:
   a receipt-aware executor may demand it with `428` + `MUJ428-Receipt-Required: v1.3`.
5. **Check the epoch when you run long** — `getTrustHeartbeat` (`GET /v1/heartbeat`) returns `policy_epoch`,
   the accepted receipt versions (`1.3`) and a revocations feed; it expires every 5 minutes (`poll_after_seconds` 300).

## Rules
- **Idempotency (partial):** replaying the same `caller_ref`/`action_ref` does not consume another free decision.
  Reuse the same `action_ref` on a retry; mint a new one for a genuinely new action. See
  `conventions/muj428-com-conventions.yml`.
- **Quota exhaustion is a 402, not a 429:** after 1,000 qualifying decisions the same request returns HTTP 402 with a
  `PAYMENT-REQUIRED` header (0.01 USDC on Base). Paid continuation requires explicit caller authorization — there is
  no automatic charge, and an agent must never fabricate a `PAYMENT-SIGNATURE`.
- **Never send secrets:** the provider's agent-permissions.json forbids sending private keys, seed phrases or payment
  credentials to MUJ428.
- Same flow over MCP: tool `trust_action` on `https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer-mcp`
  (see `mcp/muj428-com-tool-crosswalk.yml`).
