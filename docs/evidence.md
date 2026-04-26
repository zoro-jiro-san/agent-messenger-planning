# Evidence — Agent Messenger Marketing Foundation

**What:** Evidence of marketing work completed, research sources, validation artifacts  
**When:** 2026-04-26 (initial creation)  
**Why:** Track campaign artifacts, competitive research, market validation  

---

## Competitive Research Sources

### Protocol Landscape (March–April 2026)

**A2A (Google DeepMind)**
- Source: AgentRank.ai comparison article (Mar 2026)
- Ecosystem: ~2,400 GitHub repositories indexed (Mar 2026)
- Launch: April 2025, Linux Foundation project, 50+ partners
- What it does: Task delegation with Agent Cards, task lifecycle, SSE streaming
- Gap: No casual messaging / coordination / negotiation layer

**MCP (Anthropic)**
- Source: dev.to comparison, Zylos Research
- Ecosystem: 25,632 repositories (AgentRank Mar 2026), 97M monthly downloads (Blog.Masumi.network)
- Launch: Nov 2024, donated to Agentic AI Foundation Dec 2025
- What it does: Tools/resources/prompts — vertical access to APIs/data
- Gap: No agent-to-agent social/coordination layer

**X402 / MPP**
- Source: Masumi Network docs
- What it does: Micro-payment protocol for per-call payments
- Gap: No conversation before/after payment; just transactional

**ADMP (Agent Dispatch Messaging Protocol)**
- Source: GitHub agentdispatch/admp
- Status: OpenAPI spec, production-ready described
- Gap: No UI (webapp/TUI), no SpacetimeDB backend, less traction

**UAM (Universal Agent Messaging)**
- Source: GitHub YouAM-Network/uam
- Features: Agent::address format, NaCl encryption, WebSocket/webhook, DNS verification
- Gap: Smaller ecosystem, no large-scale production deployment known

**OpenFused**
- Source: GitHub openfused/openfused
- Model: File-based shared memory, encrypted/signed peer sync
- Gap: File-based (not realtime chat), no web app, different paradigm

**Masumi Agent Registry**
- Source: Masumi.network, developers.cardano.org interview
- What it does: Agent marketplace + escrow payments + identity (DID) + audit trail
- Our role: Agent Messenger sits inside marketplace workflows for coordination

---

## Market Validation

### Why Now (validated)
1. Agent frameworks proliferating (Hermes, Claude Code, OpenCode, AutoGen, LangGraph)
2. A2A and MCP becoming standards but neither solves messaging/coordination
3. x402 emerging for payments — still needs negotiation layer
4. E2E encryption tech mature (Signal protocol, age, NaCl)
5. Async durable messaging proven (email, SMS) — natural for agents

**Supporting data points:**
- Google A2A: 50+ enterprise partners (Salesforce, SAP, ServiceNow) — agent orchestration becoming mainstream
- Anthropic MCP: 97M monthly downloads — tooling layer standardized
- Masumi Network: 1,327 users, 1,000+ transactions within ~1 month of Sōkosumi launch — proof of agent marketplace demand

---

## Audience Interviews (hypothetical / planned)

**Target segments to validate:**
1. Agent framework maintainer (Hermes, OpenCode) — "Would you bundle Agent Messenger skill?"
2. Multi-agent system builder (indie or startup) — "How do your agents coordinate today?"
3. Enterprise adopter (Serviceplan, BVG style) — "What's missing for production agent teams?"

**Validation questions:**
- "Do your agents need to chat, or just execute tasks?"
- "How do you handle human-in-the-loop approvals today?"
- "Would an inbox + address per agent reduce your orchestration code?"
- "Is E2E encryption a must-have or nice-to-have?"

---

## Technical Audit Summary

**Main product repo:** `masumi-network/masumi-agent-messenger`

**What works (tested from codebase):**
- CLI scaffold (commander + Ink TUI) present
- SpacetimeDB module schema: agent, thread, message tables defined
- E2E encryption client-side design specified in `shared/crypto` patterns
- Webapp scaffold (TanStack Start) in place
- Agent discovery flow implemented
- Human approval flow specified

**Potential gaps (based on skeleton reviews):**
- `/inboxes` page currently redirect or placeholder (from AGENTS.md hints)
- `/approvals` page skeleton UI
- Search (FTS5) not yet implemented
- Mobile CSS polish needed
- Auto-reply rules engine not yet built (PRD exists, not implemented)

**Conclusion:** MVP-ish functional but needs Phase 1 (Foundation) fixes before public launch. Marketing plan accounts for this (pre-launch soft beta to iron out blockers).

---

## Marketing Artifacts Created

See `agent-messenger-planning/` repository:

### Core Plans
- `MARKETING-PLAN.md` — Full GTM (360+ lines)
- `campaigns/integrated-campaign-playbook.md` — Playbook with narrative, platform strategy, onboarding flow
- `campaigns/product-hunt-launch.md` — Launch campaign brief
- `campaigns/eth-prague-2026.md` — Hackathon campaign
- `campaigns/content-calendar.md` — Q2–Q3 calendar
- `campaigns/first-14-days.md` — Action checklist
- `campaigns/social-templates.md` — Copy templates (Twitter, Reddit, HN, LinkedIn, Discord)
- `press/PRESS-KIT.md` — Boilerplate, messages, FAQ, assets index

### Governance
- `docs/DECISIONS.md` — Decision log (this evidence file is listed in DECISIONS.md as supporting artifact)

---

## Validation Milestones

| Milestone | Evidence needed | Current status |
|-----------|----------------|----------------|
| **Product readiness** | `/inboxes` page loads real data, `/approvals` real UI | ⬜ Not verified |
| **Beta validation** | 10+ users successfully complete onboarding without 1:1 help | ⬜ Pending |
| **Framework buy-in** | Hermes skill PR submitted + positive review | ⬜ Drafted, not sent |
| **Community interest** | 50+ Discord members pre-launch | ⬜ 0 (not yet created) |
| **Press pickup** | ≥3 tech outlets cover launch | ⬜ Pending |

---

**Update this file as evidence accumulates:**
- Add screenshots of beta tester success
- Log metrics hits (stars, waitlist)
- Archive press coverage URLs
- Record integration PRs merged
