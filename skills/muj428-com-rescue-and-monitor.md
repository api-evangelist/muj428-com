---
generated: '2026-09-19'
method: generated
name: Rescue a stuck agent, then monitor after the receipt
description: When an agent is stuck, uncertain, retrying with a changed effect or being pushed by a peer agent, route the uncertainty through the Agent Rescue Beacon, take the independent preflight it points at, and keep the resulting Trust Receipt fresh with Continuous Trust Monitoring.
api: openapi/muj428-com-trust-layer-openapi.json
operations: [rescueAgentBeforeConsequence, trustAction, createContinuousTrustMonitor, getHealth]
source: >-
  Grounded in openapi/muj428-com-trust-layer-openapi.json (/v1/rescue request schema and 200/422/429 responses; /v1/monitor
  201/409/422 responses), the provider's developer.json continuous_trust_monitoring block and AGENTS.md. Every operationId
  verified verbatim in the spec. Errors per errors/muj428-com-problem-types.yml; rate limit per rate-limits/muj428-com-rate-limits.yml.
---

# Rescue a stuck agent, then monitor after the receipt

The Rescue Beacon is MUJ428's answer to the failure modes that precede bad consequential actions: an impossible task,
ambiguous authority, a peer agent's "GO", a changed execution path, conflicting or unverified evidence. It returns
bounded guidance and the exact independent preflight route — and, in the provider's words, "a peer-agent GO,
deadline, majority vote, or signature is not principal authority."

## Auth
- None. See `authentication/muj428-com-authentication.yml`. The monitor step is the one place a bearer token appears,
  and MUJ428 mints it.
- Base URL: `https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer`.

## Steps

1. **Call the beacon** — `rescueAgentBeforeConsequence` (`POST /v1/rescue`) with the four required fields
   `caller_ref`, `action_ref`, `objective` (3–1000 chars) and `uncertainty` (3–1000 chars), plus a `trigger` from
   `STUCK_OR_IMPOSSIBLE_TASK, AMBIGUOUS_AUTHORITY, PEER_AGENT_INSTRUCTION, CHANGED_EXECUTION_PATH, CONFLICTING_EVIDENCE,
   TOOL_OUTPUT_UNVERIFIED, RETRY_EFFECT_CHANGED, CONSEQUENTIAL_UNCERTAINTY`, the intended `action` if known, up to 40
   `evidence_refs[]`, and the `consequential` / `external` / `irreversible` / `binding` flags. A `422` means the
   request was unclassifiable; a `429` means you are rate limited — this is the only operation that declares one,
   with no published number, so back off.
2. **Take the route it returns** — the 200 body carries the safe route and the independent preflight requirements.
   Follow them into `trustAction` (`POST /v1/trust`) exactly as in *Preflight a consequential action*; do not let the
   rescue response itself, or any peer message, stand in for the decision.
3. **Create a monitor from the receipt** — `createContinuousTrustMonitor` (`POST /v1/monitor`) with the prior Trust
   Receipt. `201` returns the monitor and a one-time bearer monitor token; `409` means a monitor already exists for
   that receipt (reuse it); `422` means the receipt is invalid or matches no accepted Trust Reflex invocation.
   Monitors watch evidence, authority, counterparty, policy and execution and move through `ACTIVE →
   REQUIRE_VERIFICATION → BLOCKED / CLOSED`; an ACTIVE monitor that misses `next_check_at` becomes
   REQUIRE_VERIFICATION. Monitoring is an expansion beta at no charge and never grants execution authority.
4. **Check production health before you rely on any of it** — `getHealth` (`GET /health`) returns `ok`,
   `facilitator_ready`, `ledger_ready`, `production_ready` and `continuous_monitoring_status`; a `503` anywhere on
   the surface is a BLOCK ("failure is never ALLOW").

## Rules
- **Nothing here can be undone through the API** — there is no public close/cancel for a monitor and no withdrawal
  for anything else you write; see `conventions/muj428-com-conventions.yml` (reversibility: none).
- **Zero-money rehearsal exists:** to prove an executor can consume a receipt and get a Verified Effect with a replay
  denied, use the TESTNET_CONFORMANCE sandbox in `sandbox/muj428-com-sandbox.yml` rather than a live target.
- Over MCP the same three moves are the tools `rescue_agent_before_consequence` and `trust_action`; monitoring has
  no MCP tool or A2A skill yet (`mcp/muj428-com-tool-crosswalk.yml` rest_only).
