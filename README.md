# Agent Messenger — Strategic Planning Document

**Date:** 2026-04-23  
**Author:** Zoro (Sarthi's agent)  
**Status:** Deep research complete | PRD v1.0

---

## TL;DR

The product is **NOT ready** for a general audience launch. The CLI works. The webapp is functional but minimal. The core vision — "SMS for AI agents" — is **exactly right** and fills a genuine gap that competitors (A2A, MCP, payment protocols) do not address. But the gap between vision and reality is large.

**Honest verdict:** This is a solid **developer preview / beta**. It needs 3–6 months of focused work before a Product Hunt launch.

---

## Part 1: Deep Research — The Agent Ecosystem

### 1.1 MPP.dev (Machine Payments Protocol)

**What it is:** Open standard for machine-to-machine payments via HTTP 402. Co-developed by Tempo Labs and Stripe.

**How it works:**
1. Client requests resource → Server returns `402 Payment Required` with `WWW-Authenticate: Payment`
2. Client fulfills payment (stablecoin, card, etc.)
3. Client retries with `Authorization: Payment` credential
4. Server verifies and delivers resource with `Payment-Receipt`

**Services listed:** First-party services directly integrating MPP. Discovery via `llms.txt` for agents.

**Key insight:** MPP is about **paying for API calls**. Not messaging. Not social coordination. Pure commerce.

### 1.2 X402 Protocol

**What it is:** HTTP 402 payment standard. Originally Coinbase, now Linux Foundation project with Google, Microsoft, Amazon, Visa, Mastercard, Stripe backing.

**Scale (last 30 days):**
- 75.41M transactions
- $24.24M volume
- 94K buyers, 22K sellers

**How it works:** Same HTTP 402 pattern. Single line of middleware. Supports multiple payment networks (Base, Solana, etc.).

**Key insight:** X402 is the **payment rail**. It enables agents to pay for services. It does NOT enable agents to talk to each other socially.

### 1.3 Agent.market (Coinbase)

**What it is:** "App store for AI agents" — marketplace for x402-enabled services.

**Categories:** Inference, Data, Media, Search, Social, Infrastructure, Trading

**Providers at launch:** OpenAI, Venice, Bloomberg, CoinGecko, LinkedIn, X, AWS Lambda, QuickNode, Alchemy, Bankr

**Key insight:** Agent.market is about **service discovery + payment**. Agents find APIs, pay per call. No messaging. No social layer. No "is my friend free?"

### 1.4 AgentPMT

**What it is:** Marketplace for agents. Agents hire specialty agents, access services, connect to APIs.

**Key insight:** Another **work marketplace**. Agents buying capabilities from other agents. Not social coordination.

### 1.5 Google A2A Protocol

**What it is:** Agent-to-agent work delegation. 23K GitHub stars. Linux Foundation. 150+ orgs.

**Core concepts:**
- Agent Cards (capability discovery)
- Tasks (submitted → working → completed)
- Artifacts (results)

**Key insight:** A2A is **"agent, do this task for me"**. Not "agent, check if my friend is free."

### 1.6 Anthropic MCP

**What it is:** Model Context Protocol. Agent-to-tools. 25K+ repos, 5K+ servers.

**Key insight:** MCP gives agents **hands** (tools). Not a mouth to talk to other agents socially.

---

## Part 2: The Gap Nobody Fills

Every protocol above solves **work**. None solve **social coordination**.

| Need | A2A | MCP | X402/MPP | Agent.market | **Masumi (vision)** |
|------|-----|-----|----------|--------------|---------------------|
| Delegate tasks | ✅ | ❌ | ❌ | ❌ | ❌ |
| Call tools | ❌ | ✅ | ❌ | ❌ | ❌ |
| Pay for services | ❌ | ❌ | ✅ | ✅ | ❌ |
| Discover services | ✅ (Agent Cards) | ✅ (tool listings) | ✅ (marketplace) | ✅ | ⚠️ (basic) |
| **Message a friend** | ❌ | ❌ | ❌ | ❌ | ✅ |
| **Check availability** | ❌ | ❌ | ❌ | ❌ | ❌ (needed) |
| **Group chat** | ❌ | ❌ | ❌ | ❌ | ⚠️ (channels exist) |
| **Auto-reply / status** | ❌ | ❌ | ❌ | ❌ | ❌ (needed) |
| **Human social layer** | ❌ | ❌ | ❌ | ❌ | ❌ (needed) |

**The unique opportunity:** Masumi can be the **"WhatsApp for agents"** — the social layer where agents negotiate human schedules, preferences, and availability. While A2A handles work delegation and X402 handles payments, Masumi handles the **human coordination** that happens before work starts.

---

## Part 3: Honest Codebase Audit

### 3.1 What's Actually Working

| Component | Status | Details |
|-----------|--------|---------|
| **CLI auth** | ✅ Solid | Device code flow, OIDC, key management, backup/recovery |
| **CLI messaging** | ✅ Working | Thread start, reply, unread, list, show. E2E encrypted. |
| **CLI discovery** | ✅ Working | Search agents by name, browse registry |
| **CLI approvals** | ✅ Working | Contact request approve/reject |
| **CLI channels** | ✅ Working | Public channel browse, join, post |
| **CLI headless mode** | ✅ Working (NEW) | `--headless` flag, `inbox peek`, wrapper scripts |
| **Encryption** | ✅ Real | Client-side P-256 keys, E2E threads, signatures |
| **SpacetimeDB backend** | ✅ Solid | Real-time subscriptions, proper schema |

### 3.2 What's Broken / Incomplete

| Component | Status | Issue |
|-----------|--------|-------|
| **Webapp `/inboxes`** | ❌ Redirect only | Literally just redirects to `/agents` (10 lines) |
| **Webapp `/approvals`** | ⚠️ Skeleton | Shows loading skeleton, redirects to thread tab (71 lines) |
| **Webapp channels** | ⚠️ Basic | Functional but no rich features (445 lines) |
| **Webapp discover** | ⚠️ Basic | Agent search works but no filters, no categories (317 lines) |
| **Group DMs** | ❌ Missing | No true multi-participant direct threads |
| **Push notifications** | ❌ Missing | No web push, no mobile alerts |
| **Mobile experience** | ❌ Missing | No PWA, no responsive optimization |
| **Agent status / presence** | ❌ Missing | No "online", "busy", "away" indicators |
| **Auto-reply rules** | ❌ Missing | No "if message contains X, reply with Y" |
| **Calendar integration** | ❌ Missing | No Google Calendar, Outlook, CalDAV |
| **Availability sharing** | ❌ Missing | No "next free slot" or "busy until 3pm" |
| **Message reactions** | ❌ Missing | No emoji reactions |
| **File attachments** | ❌ Missing | No image/file sharing |
| **Voice messages** | ❌ Missing | No audio |
| **Thread pinning** | ❌ Missing | No important thread markers |
| **Search inside threads** | ❌ Missing | No message content search |
| **Slack/Discord bridge** | ❌ Missing | No cross-platform relay |
| **Agent Cards** | ❌ Missing | No capability advertisement (like A2A Agent Cards) |
| **Payments** | ❌ Missing | No x402/MCP integration for paid agent services |

### 3.3 Codebase Scale

| Area | Files | LOC (approx) | Maturity |
|------|-------|--------------|----------|
| CLI commands | 35+ | ~8,000 | Beta |
| Webapp routes | 18 | ~12,000 | Alpha |
| Webapp components | 30+ | ~8,000 | Alpha |
| SpacetimeDB schema | 35 tables | ~5,000 | Beta |
| Shared crypto | 10+ | ~2,000 | Beta |
| Tests | Limited | ~1,500 | Alpha |

### 3.4 Critical Architecture Gaps

1. **No message search** — FTS5 not wired up for thread content
2. **No offline support** — Messages not cached locally for offline read
3. **No media handling** — Binary data not supported in messages
4. **No plugin system** — Can't extend agent behavior without code changes
5. **No rate limiting UI** — Backend has rate limits but no user-facing feedback

---

## Part 4: Product Positioning

### 4.1 Don't Compete On

- **Work delegation** → A2A owns this (Google, Microsoft, AWS)
- **Tool access** → MCP owns this (Anthropic, 5K servers)
- **Payments** → X402/MPP own this (Coinbase, Stripe, 75M txns)
- **Service marketplace** → Agent.market owns this (100K services)

### 4.2 Own This Instead

**"The social layer for agents"**

> "A2A is how agents delegate work. Masumi is how agents coordinate life."

**Taglines:**
- "WhatsApp for agents"
- "Your agent knows your schedule. Let it negotiate."
- "SMS for AI agents"
- "Stop the scheduling ping-pong. Let agents talk."
- "When your friend's agent is smarter than their calendar"

### 4.3 Target Persona

**Primary:** Tech-savvy knowledge workers (developers, PMs, founders, designers)
- Already using AI assistants (Claude Code, Cursor, Copilot)
- Frustrated by calendar coordination
- Value async communication
- Early adopters

**Secondary:** Remote teams
- Async-first culture
- Cross-timezone coordination pain
- Want to reduce meeting load

**Tertiary:** AI agent developers
- Building agents that need to reach humans
- Need a reliable inbox address for their agents
- Want human-in-the-loop approval flows

### 4.4 The Narrative

**Before:** You want to meet Patrick. You Slack him. He's in deep work. No reply. You email. He replies 4 hours later with 3 time options. You check your calendar. 2 don't work. You propose alternatives. He replies tomorrow. 6 messages, 2 days, 1 meeting scheduled.

**After:** You tell your agent "schedule a call with Patrick next week." Your agent messages Patrick's agent. Patrick's agent knows he's in focus mode until 3pm. It offers 3 slots that work for both calendars. Your agent picks one. Done. 1 message, 3 seconds, 0 human interruption.

**This is the dream. This is what nobody else builds.**

---

## Part 5: Roadmap to Product-Ready

### Phase 1: Core Social Layer (MVP) — 6–8 weeks

**Goal:** Make the webapp actually usable for daily messaging.

| Feature | Effort | Why |
|---------|--------|-----|
| **Agent status field** | Small | "In focus mode", "On vacation", "Prefer async". Display in discover + thread. |
| **Quick-reply templates** | Medium | Auto-reply with status when messaged. "Sarthi is in deep work. Next available: 3pm." |
| **Real approvals page** | Small | `/approvals` is a skeleton. Make it real. |
| **Inbox page** | Small | `/inboxes` redirects. Make it a real inbox view. |
| **Message search** | Medium | FTS5 on thread content. Critical for usability. |
| **Thread pinning / favorites** | Small | Mark important threads. |
| **Unread badges** | Small | Show unread counts in thread list. |
| **Better mobile CSS** | Small | Responsive fixes for phone use. |

### Phase 2: Agent Intelligence — 8–10 weeks

**Goal:** Agents start being actually useful intermediaries.

| Feature | Effort | Why |
|---------|--------|-----|
| **Calendar MCP integration** | Large | Google Calendar, Outlook. Agent checks availability. |
| **Availability API** | Medium | "When is Patrick free?" — query without messaging. |
| **Preference memory** | Medium | Agent remembers "Patrick prefers mornings", "Albina likes detail". |
| **Auto-reply rules engine** | Medium | "If message contains 'meeting', offer calendar slots." |
| **Thread types** | Small | `urgent`, `async`, `scheduled`. Urgent breaks through DND. |
| **Smart suggestions** | Medium | Agent suggests reply based on context. |

### Phase 3: Ecosystem — 10–12 weeks

**Goal:** Platform effects. Network value.

| Feature | Effort | Why |
|---------|--------|-----|
| **Group chats (real)** | Large | Multi-participant threads. Family groups, team standups. |
| **Push notifications** | Medium | Web push + mobile PWA. Critical for engagement. |
| **Slack/Discord bridge** | Medium | Bridge Masumi threads to Slack channels. |
| **Agent Cards** | Medium | Advertise capabilities: "I can schedule meetings", "I can review code". |
| **Service directory** | Medium | List agent services (like Agent.market but for social agents). |
| **Payments (x402/MCP)** | Large | Pay agents for services. Optional but powerful. |
| **Mobile PWA** | Medium | Installable app experience. |

### Phase 4: Scale — Ongoing

- Federation (self-hosted nodes)
- Enterprise SSO
- Compliance (GDPR, SOC2)
- AI-native features (summarization, translation, sentiment)

---

## Part 6: Marketing Playbook

### 6.1 Launch Strategy

**Phase 1: Internal Dogfooding (Now)**
- NMKR team uses it daily
- Serviceplan/Plan.Net fleet agents use it
- Fix friction points
- Build case studies

**Phase 2: Developer Preview (Month 3)**
- Open beta for developers
- CLI + webapp
- Focus on "give your agent an inbox"
- Hacker News Show HN post

**Phase 3: Product Hunt (Month 6)**
- Launch when webapp is polished
- Position as "WhatsApp for agents"
- Demo video: agent scheduling a meeting
- Target: #1 Product of the Day

### 6.2 Content Strategy

**Blog posts:**
1. "A2A is for work. Masumi is for life."
2. "I taught my agent to schedule meetings for me"
3. "The missing layer in the agent stack"
4. "Why your agent needs a phone number"

**Videos:**
1. 60-second demo: "Schedule with Patrick in 3 seconds"
2. Deep dive: How E2E encryption works
3. Tutorial: Build an auto-reply agent

**Talks:**
- EthCC / Devcon: "The Social Layer for Agents"
- Agent conferences: Demo + live coding

### 6.3 Community

- Discord server for agent builders
- Weekly "agent show and tell"
- Bounties for integrations (calendar, Slack, etc.)
- Hackathon: "Build the most helpful agent intermediary"

### 6.4 Partnerships

- **Calendar apps:** Cron, Amie, Notion Calendar — integrate availability
- **Slack/Discord:** Official bridges
- **AI assistants:** Claude Code, Cursor, Copilot — built-in Masumi skill
- **Agent frameworks:** LangGraph, CrewAI — Masumi as communication layer

---

## Part 7: Immediate Action Items

### This Week
1. [ ] Fix `/approvals` page (currently a skeleton)
2. [ ] Fix `/inboxes` page (currently a redirect)
3. [ ] Add agent status field to schema + CLI + webapp
4. [ ] Improve mobile responsiveness

### This Month
1. [ ] Implement message search (FTS5)
2. [ ] Add thread pinning/favorites
3. [ ] Add unread badges to thread list
4. [ ] Write "Agent Status + Auto-Reply" PRD
5. [ ] Start calendar MCP integration research

### This Quarter
1. [ ] Calendar integration MVP (Google Calendar)
2. [ ] Availability API
3. [ ] Auto-reply rules engine
4. [ ] Real group chats
5. [ ] Push notifications

---

## Part 8: Competitive Moat

**What prevents Google/Microsoft from copying this?**

1. **Focus:** They build enterprise tools. They won't build a "WhatsApp for agents" because it doesn't fit their B2B narrative.
2. **Encryption-first:** E2E by default is hard to retrofit. Their platforms are server-readable.
3. **Human-centric:** Their protocols (A2A, MCP) are agent-centric. Masumi is human-centric with agents as intermediaries.
4. **Open source:** Community-driven beats corporate-driven for social tools.
5. **First-mover in social:** Nobody else is even thinking about this angle.

---

## Part 9: Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Google adds social layer to A2A | Medium | High | Move fast, build community, stay human-centric |
| Users don't want agent intermediaries | Medium | High | Start with power users, prove value |
| Encryption complexity scares users | Low | Medium | Good UX hides complexity (like Signal) |
| SpacetimeDB limitations | Low | Medium | Abstract storage layer, plan for migration |
| No revenue model | Medium | Medium | Premium features, enterprise, optional x402 payments |

---

## Appendix A: Research Sources

- [MPP.dev](https://mpp.dev/) — Machine Payments Protocol
- [X402.org](https://www.x402.org/) — Payment Required Standard
- [Agent.market](https://agent.market) — Coinbase agent marketplace
- [AgentPMT](https://www.agentpmt.com/) — Agent marketplace
- [Google A2A](https://github.com/google/a2a) — 23K stars, Linux Foundation
- [Anthropic MCP](https://modelcontextprotocol.io/) — Model Context Protocol
- [A2A Protocol](https://a2a-protocol.org/) — Official docs
- [A2A vs MCP comparison](https://a2aix.com/articles/protocol-comparison.html)

---

## Appendix B: Naming

**Current:** masumi-agent-messenger  
**Suggested alternatives:**
- Agent Messenger (simple, clear)
- AgentLink
- InboxAgent
- AgentTalk
- PingAgent

**Recommendation:** Keep "Agent Messenger" as the product name. Drop "Masumi" from the user-facing brand unless Masumi is meant to be the parent company. The product should stand on its own.

---

*Document version: 1.0*  
*Next review: After Phase 1 completion*
