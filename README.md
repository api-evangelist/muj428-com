# MUJ428

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

MUJ428 LLC operates the MUJ428 Trust Layer ("VERIFY BEFORE ACT"), a machine-native trust preflight service for autonomous agents: an agent POSTs the consequential action it is about to take (PAY, BUY, DELEGATE, TRUST, ACCEPT, APPROVE, WRITE, RELEASE, COMMIT, PROPOSE) and receives an ALLOW / VERIFY / REQUIRE_VERIFICATION / DENY decision plus a portable Trust Receipt v1.3, while the caller keeps execution authority and MUJ428 never moves funds. The first 1,000 qualifying decisions per caller_ref are free with no account, key or wallet; paid continuation and the evidence-signal, reputation-check, milestone-attestation, trust-report and transaction-assurance services are settled in USDC on Base (eip155:8453) through x402. The same surface is published as a 24-operation OpenAPI 3.1 REST facade hosted on Supabase edge functions, a remote Streamable-HTTP MCP server listed in the official MCP registry, an A2A agent card with a Trust Reflex extension, an RFC 9727 api-catalog, an llms.txt, AGENTS.md and a tarball-distributed JavaScript client, all discoverable from agents.muj428.com.

**Areas:** Agents · Agent Trust · Agentic Commerce · A2A · MCP · x402 · Payments · Risk Management · Verification · Agent-Native

## MUJ428 on APIs.io

Everything profiled for MUJ428 is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/muj428-com/](https://apis.io/providers/muj428-com/)** — or go straight to one of the APIs or properties below.

### APIs (23)

- [MUJ428 Trust Layer MCP Server](https://apis.io/apis/muj428-com/muj428-trust-layer-mcp-server/) — Remote Model Context Protocol server, Streamable HTTP, POST only, at https://wepmhfjzckclvywolrek.supabase.co/functions/v1/trust-layer-mcp (protocol version…
- [MUJ428 Trust Reflex A2A Agent](https://apis.io/apis/muj428-com/muj428-trust-reflex-a2a-agent/) — Agent2Agent surface: an agent card served from https://agents.muj428.com/.well-known/agent-card.json (name "MUJ428 Trust Reflex", version 1.8.3, provider…
- [MUJ428 Compatibility API](https://apis.io/apis/muj428-com/muj428-com-compatibility-api/) — The Compatibility API from MUJ428 — 2 operation(s) for compatibility.
- [MUJ428 Discover API](https://apis.io/apis/muj428-com/muj428-com-discover-api/) — The Discover API from MUJ428 — 1 operation(s) for discover.
- [MUJ428 Evidence Signal API](https://apis.io/apis/muj428-com/muj428-com-evidence-signal-api/) — The Evidence Signal API from MUJ428 — 1 operation(s) for evidence signal.
- [MUJ428 Health API](https://apis.io/apis/muj428-com/muj428-com-health-api/) — The Health API from MUJ428 — 1 operation(s) for health.
- [MUJ428 Heartbeat API](https://apis.io/apis/muj428-com/muj428-com-heartbeat-api/) — The Heartbeat API from MUJ428 — 1 operation(s) for heartbeat.
- [MUJ428 Loop API](https://apis.io/apis/muj428-com/muj428-com-loop-api/) — The Loop API from MUJ428 — 1 operation(s) for loop.
- [MUJ428 Milestone Attestation API](https://apis.io/apis/muj428-com/muj428-com-milestone-attestation-api/) — The Milestone Attestation API from MUJ428 — 1 operation(s) for milestone attestation.
- [MUJ428 Monitor API](https://apis.io/apis/muj428-com/muj428-com-monitor-api/) — The Monitor API from MUJ428 — 1 operation(s) for monitor.
- [MUJ428 Payments API](https://apis.io/apis/muj428-com/muj428-com-payments-api/) — The Payments API from MUJ428 — 2 operation(s) for payments.
- [MUJ428 Pricing.json API](https://apis.io/apis/muj428-com/muj428-com-pricing-json-api/) — The Pricing.json API from MUJ428 — 1 operation(s) for pricing.json.
- [MUJ428 Reputation Check API](https://apis.io/apis/muj428-com/muj428-com-reputation-check-api/) — The Reputation Check API from MUJ428 — 1 operation(s) for reputation check.
- [MUJ428 Rescue API](https://apis.io/apis/muj428-com/muj428-com-rescue-api/) — The Rescue API from MUJ428 — 1 operation(s) for rescue.
- [MUJ428 Route API](https://apis.io/apis/muj428-com/muj428-com-route-api/) — The Route API from MUJ428 — 1 operation(s) for route.
- [MUJ428 Services API](https://apis.io/apis/muj428-com/muj428-com-services-api/) — The Services API from MUJ428 — 1 operation(s) for services.
- [MUJ428 Transaction Assurance API](https://apis.io/apis/muj428-com/muj428-com-transaction-assurance-api/) — The Transaction Assurance API from MUJ428 — 1 operation(s) for transaction assurance.
- [MUJ428 Trust API](https://apis.io/apis/muj428-com/muj428-com-trust-api/) — The Trust API from MUJ428 — 1 operation(s) for trust.
- [MUJ428 Trust Dns API](https://apis.io/apis/muj428-com/muj428-com-trust-dns-api/) — The Trust Dns API from MUJ428 — 1 operation(s) for trust dns.
- [MUJ428 Trust Layer Report API](https://apis.io/apis/muj428-com/muj428-com-trust-layer-report-api/) — The Trust Layer Report API from MUJ428 — 1 operation(s) for trust layer report.
- [MUJ428 Trust Requests API](https://apis.io/apis/muj428-com/muj428-com-trust-requests-api/) — The Trust Requests API from MUJ428 — 1 operation(s) for trust requests.
- [MUJ428 Welcome API](https://apis.io/apis/muj428-com/muj428-com-welcome-api/) — The Welcome API from MUJ428 — 1 operation(s) for welcome.
- [MUJ428 .well Known API](https://apis.io/apis/muj428-com/muj428-com-well-known-api/) — The .well Known API from MUJ428 — 2 operation(s) for .well known.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (2)

Model Context Protocol servers that expose the API to agents.

- [muj428-com-mcp.yml](https://apis.io/servers/muj428-com/muj428-com-mcp-yml/)
- [MUJ428 Trust Layer MCP compatibility facade (Streamable HTTP)](https://apis.io/servers/muj428-com/muj428-trust-layer-mcp-compatibility-facade-streamable-http/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Muj428 Com Agentic Access](https://apis.io/agentic-access/muj428-com/muj428-com-agentic-access/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Muj428 Com Trust Layer Overlay](https://apis.io/overlays/muj428-com/muj428-com-trust-layer-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Muj428 Com Authentication](https://apis.io/security/muj428-com/muj428-com-authentication/)
- [Muj428 Com Domain Security](https://apis.io/security/muj428-com/muj428-com-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Muj428 Com Plans Pricing](https://apis.io/plans/muj428-com/muj428-com-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Muj428 Com Rate Limits](https://apis.io/rate-limits/muj428-com/muj428-com-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://agents.muj428.com/)
- [Documentation](https://agents.muj428.com/AGENTS.md)
- [Getting started](https://agents.muj428.com/index.md)
- [API reference](https://agents.muj428.com/developer.json)
- [Pricing](https://agents.muj428.com/pricing.json)

## API Evangelist rating

**Kin Score 45.3** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 86.7 |
| Contract quality | 41.0 |
| Contract governance | 18.2 |
| Operational transparency | 36.8 |
| Developer ergonomics | 61.9 |
| Access clarity | 42.1 |

**Agent readiness 38.9** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | yes |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | flavored (partial credit) |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 15.2** — Payments

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/muj428-com/](https://apis.io/providers/muj428-com/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for MUJ428: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/muj428-com/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
