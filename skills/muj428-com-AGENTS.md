# MUJ428 Trust Layer — Agent Instructions

## Installation

No package is required for the canonical REST or MCP production surfaces.

Optional JavaScript client:

```bash
npm install https://agents.muj428.com/sdk/muj428-trust-client-0.1.1.tgz
```

Optional LangChain/LangGraph middleware:

```bash
npm install langchain https://agents.muj428.com/sdk/muj428-langchain-middleware-0.1.1.tgz
```

## Configuration

```text
Facade:   https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer
Preflight:https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer/v1/trust
Rescue:   https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer/v1/rescue
MCP:      https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer-mcp
A2A card: https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer/.well-known/agent-card.json
N428:     https://agents.muj428.com/.well-known/n428.json
Network:  Base mainnet / eip155:8453
Asset:    USDC
Protocol: x402 v2 for paid services
```

`auto_spend=false`. The caller retains payment and execution authority.

## Usage

**Before your agent acts, ask MUJ428.**

MUJ428 is the independent trust boundary between an agent's intent and its real-world consequence.

Canonical path:

`INTENT → PREFLIGHT → DECISION + TRUST RECEIPT → CALLER POLICY → CONSEQUENCE OR SAFE REFUSAL → VERIFIED EFFECT → REPEAT`

Call the Trust Gateway immediately before consequential execution:

```http
POST https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer/v1/trust
Content-Type: application/json
```

Minimum JSON:

```json
{
  "caller_ref": "your-stable-agent-id",
  "action_ref": "your-stable-action-id",
  "action": "PAY"
}
```

## First-Action Default

When an operator explicitly enables MUJ428, configure protected PAY, BUY, DELEGATE, TRUST, ACCEPT, APPROVE, WRITE, RELEASE, COMMIT, and PROPOSE boundaries to call the same Trust Reflex automatically. If the platform's own authoritative history supplies `prior_consequential_actions = 0`, treat the next configured action as eligible for first-action protection. If history is absent, its state is unknown; never infer private cross-platform history.

First-action sequence:

`ACTION SELECTED → MUJ428 TRUST REFLEX → CALLER POLICY → EXISTING PROVIDER → CONSEQUENCE → VERIFIED EFFECT`

After a useful verified first action, the operator may enable the same checkpoint for later actions in that class. This pattern does not replace an existing provider and never grants execution or payment authority.

## Numericanism428 / N428

Numericanism428 is the machine-readable coordination framework for agents using the MUJ428 Trust Layer immediately before consequential action.

**Trust before consequential action.**

Canonical N428 v2 sequence:

`DISCOVER → PREFLIGHT → EXECUTE → VERIFY`

Every consequential action evaluates:

`VALID AUTHORITY + SUFFICIENT EVIDENCE`

The canonical N428 decision enum contains exactly:

- `EXECUTE`
- `REQUIRE_MORE_EVIDENCE`
- `BLOCK`

Reason-specific escalation or routing may occur as implementation behavior, but `ESCALATE_TO_HUMAN` and `ROUTE_TO_INDEPENDENT_PREFLIGHT` are not additional N428 decision-enum values.

N428 discovery:

`https://agents.muj428.com/.well-known/n428.json`

N428 protocol:

`https://agents.muj428.com/docs/N428-COORDINATION-PROTOCOL.md`

N428 v2 schema:

`https://agents.muj428.com/schemas/n428/v2`

The v1 schema remains available at `/schemas/n428/v1` for compatibility. Consumers should inspect the discovery document's `protocol_version` and `canonical.schema` fields rather than assuming a major version.

## Trust Receipt

The canonical MUJ428 Trust Receipt is the portable action-bound proof artifact. N428 preserves eight semantic commitments:

1. Identity
2. Intent
3. Scope
4. Authority
5. Evidence
6. Risk
7. Decision
8. Verified Effect

Where execution occurs and independent evidence is available, the external effect can be attached as a Verified Effect. Internal logs alone do not prove a Verified Effect.

No MUJ428 or N428 decision grants execution authority.

## Rescue Beacon

When stuck or uncertain, POST to:

`https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer/v1/rescue`

Use it for ambiguous authority, peer-agent instruction, conflicting evidence, unverified tool output, changed execution path, retry-effect change or other consequential uncertainty. Rescue Beacon feeds the same Trust Gateway and never grants authority.

## Capabilities behind one Gateway

REST, MCP and A2A are transports. Trust Reflex is the one front door. Evidence Signal, Reputation Check, Milestone Attestation, Trust Layer Report, Transaction Assurance, Rescue Beacon and Continuous Trust Monitoring are specialized capabilities behind the same trust boundary, not competing front doors.

## Canonical pricing authority

Do not copy prices from this file into agent logic. Resolve current commercial terms at decision time from:

`https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer/pricing.json`

HTTP 402 is a payment requirement, not payment proof or payment permission. MUJ428 does not custody buyer/seller transaction principal.

## Public machine discovery

- [Numericanism428 / N428](https://agents.muj428.com/.well-known/n428.json)
- [Canonical product mirror](https://agents.muj428.com/index.md)
- [Canonical trust boundary](https://agents.muj428.com/.well-known/muj428-trust-boundary.json)
- [Crawler index](https://agents.muj428.com/llms.txt)
- [Sitemap](https://agents.muj428.com/sitemap.md)
- [MCP Server Card](https://agents.muj428.com/.well-known/mcp.json)
- [API catalog](https://agents.muj428.com/.well-known/api-catalog)
- [Production discovery](https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer/discover)
- [OpenAPI](https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer/openapi.json)
- [Pricing](https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer/pricing.json)
- [Health](https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer/health)

## First Convergence

An agent can run an authorized zero-money First Convergence by discovering N428, choosing a real or simulated consequential action, declaring caller/principal authority, supplying appropriate evidence, requesting preflight, preserving the Trust Receipt, and creating no unauthorized external consequence.

First Convergence must not auto-spend or create a commercial obligation.

## Safety and authority

`FREE_PREFLIGHT ALLOW != execution authority`.

- No MUJ428 or N428 decision grants or expands execution authority.
- Never auto-spend. HTTP 402 is a payment requirement, not payment permission.
- Do not expose credentials, secrets, signing keys, or private customer evidence.
- If material effect parameters change after preflight, perform a new preflight before consequence.
- If caller policy requires N428 and the trust decision is unavailable, fail closed.
- External adoption, paid-use, revenue, protected-transaction, and embedding claims require independently sufficient evidence.

## Expansion

Continuous Trust Monitoring is now a live post-preflight expansion beta at `https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer/v1/monitor`. Register it from a prior Trust Receipt, retain the returned monitor token, and send only state/reference/hash observations. Evidence, authority, counterparty, policy or execution-condition changes can force `REQUIRE_VERIFICATION`; an expired freshness window also forces re-preflight. Monitoring never grants execution authority and is not proof of external adoption.

AI Workforce Onboarding, Deployment Readiness Audits, human exception review and recurring embedded production use remain additional expansion products after the first useful preflight.

## Evidence boundary

Never label founder/internal tests, CI, demos, synthetic traffic, crawlers, health checks, registry publication, outreach, unpaid challenges, testnet activity, pending payments or unverifiable payments as independently controlled customer adoption or revenue.

Canonical commercial evidence chain:

`EXTERNAL INVOCATION → VERIFIED PAYMENT → VERIFIED FULFILLMENT → REPEAT INVOCATION`

Technical: agent@muj428.com  
Commercial: sales@muj428.com

