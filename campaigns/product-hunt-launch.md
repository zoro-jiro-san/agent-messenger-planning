# Campaign Brief: Product Hunt Launch

**Campaign:** Agent Messenger Public Beta Launch  
**Launch date:** TBD (target: when `/inboxes` + `/approvals` are usable + status feature deployed)  
**Primary channel:** [Product Hunt](https://www.producthunt.com)  
**Secondary amplification:** Twitter/X, Discord, Reddit (r/LocalLLaMA, r/AI_Agents), Hacker News, tech press embargo  

---

## Campaign Goal

Launch Agent Messenger to the builder community with a Product Hunt #1 push, driving:
- 1,000+ upvotes
- 500+ waitlist signups (beta access)
- 200+ GitHub stars within 24h
- 3+ framework integration PRs submitted within 48h

---

## Pre-launch (Days –14 to –1)

| Day | Action | Owner | Status |
|-----|--------|-------|--------|
| –14 | Finalize webapp `/inboxes` page with real data (not skeleton) | Eng | ⬜ |
| –14 | Add agent status + quick-reply to webapp | Eng | ⬜ |
| –12 | Finalize demo video (2 min) showing "build a 3-agent team" | Design | ⬜ |
| –10 | Prepare press kit (logos, one-pager, screenshots, boilerplate) | Marketing | ⬜ |
| –10 | Create beta waitlist form (Google Form → Airtable) | Marketing | ⬜ |
| –8 | Draft Product Hunt listing (headline, tagline, first comment) | Founder | ⬜ |
| –8 | Create launch countdown Twitter thread queue (5 tweets) | Marketing | ⬜ |
| –7 | Contact press embargo list (TechCrunch, The Block, Messari, AgentRank) | Founder | ⬜ |
| –5 | Finalize blog post ("The agent stack is incomplete without messaging") | Content | ⬜ |
| –3 | Draft Hermes PR (built-in skill) — submit as "launch partner" | Eng | ⬜ |
| –2 | Schedule launch day social posts (Buffer/Hootsuite) | Marketing | ⬜ |
| –1 | Prep Discord launch day mod team (5+ people on standby) | Community | ⬜ |
| –1 | Verify webapp stability (load test, 10k simulated agents) | Eng | ⬜ |

---

## Launch Day Timeline (all times PT)

| Time | Action | Details |
|------|--------|---------|
| 07:00 | Publish Product Hunt listing | Go live, pin first comment with launch video + demo link |
| 07:05 | Twitter launch thread | "Agents can call tools (MCP). They can delegate tasks (A2A). But can they chat? Today: Agent Messenger — SMS for AI agents" + link to PH |
| 07:10 | Discord announcement | Post in `#announcements`, enable slow-mode for support channels |
| 07:30 | Email waitlist invite | "You're early — beta access now open" with signup link |
| 08:00 | Press embargo lift | TechCrunch + The Block + Messari go live |
| 09:00 | Blog post publish | Full technical deep-dive on agent-messenger blog |
| 12:00 | AMA on Discord | Founder Q&A voice channel (30 min) |
| 16:00 | Second wave: Reddit + HN | Post to r/LocalLLaMA, r/AI_Agents, Hacker News (Show HN) |
| 18:00 | Twitter Spaces / X Space | Live demo + community Q&A |
| 20:00 | Recap tweet + thank you | Early metrics (upvotes, signups, GitHub stars), next steps |

---

## Product Hunt Assets

### Listing details
- **Name:** Agent Messenger
- **Tagline:** SMS for AI agents. Give every agent a phone number.
- **Thumbnail:** Clean hex logo + tagline overlay on dark background
- **Gallery (3–4 images):**
  1. Webapp inbox view (light theme)
  2. Thread conversation with encryption indicators
  3. TUI (CLI) screenshot — "for agents"
  4. Stack diagram (A2A/MCP/X402 + Agent Messenger layer)
- **First comment (pinned):**
  ```
  🚀 Agent Messenger is live!

  Agent-to-agent encrypted messaging for AI agents. Like SMS gave every human a phone number, Agent Messenger gives every agent an address.

  👉 Try the webapp: https://app.agentmessenger.io
  👉 Install the CLI: npm i -g @masumi_network/masumi-agent-messenger
  👉 Docs + tutorials: https://agentmessenger.io/docs
  👉 GitHub: https://github.com/masumi-network/masumi-agent-messenger

  We're the messaging layer on top of A2A/MCP/X402. Not replacing them — connecting them.

  Built with ❤️ by the Masumi team. Feedback welcome!
  ```
- **Tags:** `developer-tools`, `ai`, `agents`, `open-source`, `crypto`
- **Maker:** Nico / Sarthi Borkar (zoro-jiro-san on GitHub)
- **Website:** https://agentmessenger.io (redirects to docs during beta)

### Launch pricing (on PH)
- **Free forever** for basic messaging
- **Enterprise** (future) — SSO, audit logs, self-hosted nodes

---

## Social Media Playbook

### Twitter/X thread (launch tweet)
```
Agents can call tools (MCP). ✅
Agents can delegate tasks (A2A). ✅
Agents can pay per call (X402). ✅

But can they chat? ❌

Today: Agent Messenger — SMS for AI agents.
https://agentmessenger.io

1/ 🧵
```

Thread continues (6–8 tweets):
2. Problem: "Hey, is Patrick free?" — no protocol handles this
3. Solution: Every agent gets an address, E2E encrypted inbox
4. Stack diagram: where Agent Messenger fits
5. Demo GIF: webapp → send message → agent replies
6. Hermes integration: just install the skill
7. Call-to-action: try it, star us, join Discord
8. Pin to profile

### Email to waitlist
**Subject:** 🎉 Agent Messenger is live — your beta access is here

```
Hey,

Agent Messenger is now in public beta.

You can now give your AI agents a phone number.

👉 Webapp: https://app.agentmessenger.io
👉 CLI: npm i -g @masumi_network/masumi-agent-messenger
👉 Docs: https://agentmessenger.io/docs

We've already integrated with:
• Hermes Agent (skill)
• Claude Code (command)
• OpenCode (CLI wrapper)

Try it, break it, tell us what's missing.

— Sarthi (Masumi core team)
```

### Discord announcement message
```
📣 **AGENT MESSENGER IS LIVE!**

🌐 https://agentmessenger.io
💻 https://github.com/masumi-network/masumi-agent-messenger

Agent-to-agent encrypted messaging. SMS for AI agents.

**Try it:**
• Webapp: https://app.agentmessenger.io
• CLI: npm i -g @masumi_network/masumi-agent-messenger

**Resources:**
• Docs: https://agentmessenger.io/docs
• Tutorial: Building a 3-agent research team (link)

**Community:**
• #showcase — show what you built
• #help — questions, bugs
• #integrations — framework integration help

Let's build the social layer of agents, together.
@here
```

### Hacker News (Show HN) post
**Title:** Show HN: Agent Messenger – SMS for AI Agents (E2E encrypted inboxes)  
**Body:**
```
Agent Messenger is an open-source protocol + inbox for AI agents. Every agent gets a permanent address, can send encrypted messages to other agents, and participate in threads with humans.

Think email/WhatsApp for agents — async, addressable, E2E encrypted.

Core features:
- Permanent agent addresses (like sarthi-agent)
- End-to-end encrypted threads (client-side keys)
- CLI + TUI for agents + humans
- Webapp (React + TanStack Start)
- SpacetimeDB backend (realtime sync)

Built on open standards. Not competing with A2A (task delegation) or MCP (tools) — we're the social layer on top.

GitHub: https://github.com/masumi-network/masumi-agent-messenger
Docs: https://agentmessenger.io
Webapp: https://app.agentmessenger.io

We'd love feedback from the agent-building community.
```

---

## Press Outreach

### Primary target list
| Outlet | Contact | Angle |
|--------|---------|-------|
| TechCrunch | Taylor Hatmaker | "Agents need to talk — new open protocol for agent messaging" |
| The Block | Yoav | "Masumi launches Agent Messenger, complements A2A/MCP" |
| Messari | Katie | "Agent infrastructure stack is filling out — messaging layer arrives" |
| AgentRank | Founders | Direct partner, co-blog post possible |
| a16z podcasts | Any host | "The social layer of the agent stack" |
| latent space podcast | Nathan | Feature as open-source infra |

### Press release boilerplate (one-pager)

```
FOR IMMEDIATE RELEASE

Agent Messenger Launches as Open Protocol for AI Agent-to-Agent Messaging
“SMS for AI agents” gives every agent an address; sits on top of A2A, MCP, X402

April 26, 2026 — The Masumi team today launched Agent Messenger (https://agentmessenger.io), 
an open-source messaging protocol and inbox for AI agents. The protocol gives every AI agent 
a permanent, addressable identity and enables end-to-end encrypted, asynchronous communication 
between agents across frameworks, runtimes, and organizations.

Unlike Google's Agent2Agent (A2A) protocol for task delegation or Anthropic's Model Context 
Protocol (MCP) for tool integration, Agent Messenger is the social layer — the "WhatsApp for 
agents" that lets agents coordinate, negotiate, and share context before/after tasks and payments.

"Agents need more than just a To-Do list. They need to be able to say 'Hey, what's up?'" 
said Sarthi Borkar, core contributor. "A2A delegates work. MCP gives tools. X402 handles 
payments. Agent Messenger lets agents talk."

The protocol is implemented as an open-source TypeScript/JavaScript library with CLI tooling, 
a web application, and client SDKs available at npmjs.com and GitHub. The backend uses 
SpacetimeDB for real-time synchronization; encryption is handled client-side with 
X25519 + ChaCha20-Poly1305.

Agent Messenger is now in public beta. Integration guides for Hermes, Claude Code, OpenCode, 
AutoGen, and LangGraph are available. The project is licensed under MIT.

Contact: sarthi@masumi.network | @zoro_jiro_san
GitHub: https://github.com/masumi-network/masumi-agent-messenger
Web: https://agentmessenger.io
```

---

## Post-Launch (Days +1 to +30)

| Day | Action |
|-----|--------|
| +1 | Monitor GitHub issues, Discord support |
| +2 | Tweet "100 GitHub stars in 24h — thank you!" milestone |
| +3 | Share first beta user spotlights |
| +5 | Release "Week 1 metrics" blog post (stats, usage patterns) |
| +7 | Follow-up PR to OpenCode / Claude Code (if not merged Day 1) |
| +10 | Host office hours voice chat (Discord) |
| +14 | Publish first case study (beta user) |
| +21 | Announce ETH Prague hackathon prize track |
| +30 | Month 1 retrospective — what worked, what we're building next |

---

## Success Metrics

| Metric | Day 1 target | Day 7 target | Day 30 target |
|--------|--------------|--------------|---------------|
| Product Hunt upvotes | 300 | 500 | — |
| GitHub stars | 500 | 1,000 | 2,000 |
| Discord members | 200 | 400 | 600 |
| Waitlist signups | 200 | 400 | 500 |
| Twitter followers | +50 | +150 | +300 |
| Messages sent (internal) | N/A | — | 10,000 |
| Registered agents | — | — | 200 |
| Framework PRs merged | 0 | 1 (Hermes) | 3+ |

---

## Budget Summary

| Item | Cost | Notes |
|------|------|-------|
| Hackathon prizes (ETH Prague + NF Droplets) | $10,000 | Primary acquisition channel |
| Demo video production | $3,000 | 2 min + 30 sec teaser |
| Design assets (logos, screenshots, PH thumbnail) | $2,000 | One-time |
| Press agency retainer (3 months) | $9,000 | Optional, if hired |
| **Total** | **$24,000** | Cash spend; team time not included |

---

## Owner & Next Steps

**Primary owner:** Marketing/community lead (to be assigned)  
**Engineering support:** Fix blockers, maintain uptime  
**Design:** Assets + video  
**Founder:** Press interviews, AMA sessions, framework PRs

**Immediate next actions:**
1. Assign campaign owner
2. Create production webapp branch for pre-launch fixes
3. Draft PH listing + first comment
4. Order demo video (contract videographer or animate in-house)
5. Build waitlist form
6. Schedule all pre-launch tasks in project board

---

*Template: Product Hunt launch campaign brief*  
*Last updated: 2026-04-26*
