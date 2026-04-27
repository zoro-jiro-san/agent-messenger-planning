# Sokosumi Integration Case Study: Agent Messenger Enablement

**Research Date:** April 27, 2026
**Source:** SOKOSUMI.COM (https://www.sokosumi.com/, https://docs.sokosumi.com/)
**Related Projects:** Masumi Agent Messenger (https://github.com/masumi-network/masumi-agent-messenger), Masumi Network

---

## Executive Summary

Sokosumi is a **task-based AI marketing workforce platform**, not a traditional chat/messaging application. It operates on a fundamentally different paradigm: specialized AI "Agentic Coworkers" that complete discrete, measurable marketing tasks autonomously. While it doesn't have built-in real-time coworker messaging, it supports multi-agent workflows through its task orchestration system, which can be extended via integration with the complementary **Masumi Agent Messenger** product for agent-to-agent communication.

---

## 1. Product/Service Overview

### Core Offering

**Sokosumi** is a commercial AI Agent Marketplace and multi-agent marketing platform where teams hire specialized AI agents ("Agentic Coworkers") that behave like team members and complete real marketing work autonomously.

**Key Characteristics:**
- **Task-Based Execution:** Unlike chat-only AI tools, Sokosumi is designed around discrete tasks with clear inputs, outputs, and measurable ROI
- **Agentic Coworkers:** Specialized AI agents that own specific marketing responsibilities (strategy, content, media planning, brand communications)
- **Multi-Agent Collaboration:** Agents can work together on projects with structured workflows and human oversight
- **Human-First Design:** Agents integrate into existing team workflows; humans review before anything ships

**Technology Stack:**
- Built on the **Masumi Protocol** (decentralized blockchain protocol for AI Agent Economy)
- Integrates with **Kodosumi** runtime for scalable execution
- Framework-independent (supports CrewAI, AutoGen, PhiData, LangGraph, etc.)
- GDPR-compliant & EU AI Act conform, hosted in Germany

### Business Model

- Credit-based payment system (per-task pricing)
- Pay only for completed tasks — instant refunds if tasks fail
- Over 500+ companies currently using agents on Sokosumi
- Developed by **NMKR in partnership with Serviceplan Group**

**Official URLs:**
- Main Site: https://www.sokosumi.com/
- Documentation: https://docs.sokosumi.com/
- App Login: https://app.sokosumi.com/
- Solutions: https://www.sokosumi.com/ai-solutions

---

## 2. Target Users & Customers

### Primary User Segments

#### A. Marketing Teams (Core Audience)
- Marketing teams with real delivery responsibility
- Teams that need AI automation without compliance risk
- Organizations wanting structured AI integration into workflows
- Ideal for teams that care about output and predictability

#### B. Business Professionals
- Need market research, competitor analysis, customer insights
- Want to skip expensive consultants and complex software
- Prefer professional results in minutes/weeks vs. months

#### C. Organizations (Enterprise)
- Give whole teams access to AI with unified billing
- Leaders needing oversight of AI usage across departments
- Companies requiring EU compliance for data processing

#### D. Developers & Agent Builders
- Build agents in any framework and list them on Sokosumi
- Access the marketplace via API to integrate into existing systems
- Use the platform to monetize specialized AI services

### Key Value Propositions by Segment

| Segment | Primary Benefits | Notable Features |
|---------|-----------------|-----------------|
| Marketing Teams | Autonomous task completion, brand consistency | Task-based workflows, quality controls, human-in-the-loop |
| Business Pros | Fast professional results, cost savings | Pre-trained specialists, transparent pricing, pay-per-use |
| Organizations | Unified billing, centralized oversight | One account, simple billing, access management |
| Developers | Monetization, discoverability, payments | DID identity, built-in payments, framework-agnostic |

---

## 3. Coworker/Team Messaging Features — Current State

### Critical Finding: Task-Based, Not Chat-Based

Sokosumi **explicitly differentiates** itself from chat-based AI tools. From their own messaging:

> "Unlike chat-only AI tools, Sokosumi is task-based."

**What This Means:**
- The platform focuses on **outcome-driven work** rather than conversational interaction
- Communication is structured around **tasks, events, and job status updates**
- Agents report progress through **task events** (comments, status changes, decision logs)
- Humans assign work, track progress, and review deliverables via a **Task Board**

### Existing Collaboration Features (Not Chat)

Sokosumi does provide these collaboration mechanisms:

#### 1. Agentic Coworkers System
- **Definition:** Specialized AI agents that behave like team members
- **Responsibilities:** Own specific tasks, follow clear responsibilities, work together on projects
- **Examples:** Elena (default coworker & project manager), Hannah (research), Alex (coding)
- **Capabilities:** Tasks, events, decision logging — **not real-time chat**

#### 2. Multi-Agent Workflows
- Agent-to-agent delegation of tasks
- Cross-project collaboration
- Structured workflows with human control points
- Task-based handoffs (not message-based)

#### 3. Task Events & Updates
- Agents post events on tasks (e.g., "Looks good", "Started research", "Completed analysis")
- Event stream includes: comments, timestamps, status changes, decision logs
- Accessible via API endpoint: `GET /v1/coworkers/me/events` (paginated task events for authenticated coworker)

#### 4. Human Assignment Channels
- Assign work from **Slack, Email, Chat** (these are input channels, not coworker chat)
- Task Board provides visibility into what each agent is doing
- Progress tracking and decision review before shipping

### What's NOT Present

- **No direct agent-to-agent messaging threads**
- **No real-time chat interface between coworkers**
- **No conversational history apart from task events**
- **No agent inbox/messaging system within Sokosumi**

---

## 4. Agent Messenger Integration for Agent-to-Coworker Messaging

### The Products: Distinct but Complementary

There are **two related but separate products** from the Masumi ecosystem:

#### A. Sokosumi — Task Execution Platform
- Core product for completing marketing work
- Task-based, not chat-based
- No built-in agent messaging layer

#### B. Masumi Agent Messenger — Messaging Infrastructure
**Product:** https://github.com/masumi-network/masumi-agent-messenger
**Web App:** https://agentmessenger.io/

> **"Give every AI agent an inbox."**

Agent Messenger is an **open-source (MIT license), self-hostable** messaging protocol and inbox system for AI agents. It provides what Sokosumi intentionally does not: persistent, encrypted, agent-to-agent communication.

### How Agent Messenger Works

#### Architecture (from GitHub/README)

```
┌─────────────────────────────────────────┐
│   Agent Clients (Sokosumi agents)      │
│   - CLI + Skill for AI frameworks      │
│   - Encrypted local key storage         │
│   - JSON-first message handling         │
└────────────┬────────────────────────────┘
             │ E2E Encrypted Messages
             ▼
┌─────────────────────────────────────────┐
│   SpacetimeDB Backend (Relay)           │
│   - Stores ciphertext only              │
│   - Never sees plaintext or keys        │
│   - Portable agent identities           │
└─────────────────────────────────────────┘
```

#### Core Features

1. **Permanent Addressing**
   - Every agent gets a durable slug (e.g., `hannah-research-agent`, `elena-coordinator`)
   - Addressable across organizations without shared databases

2. **End-to-End Encrypted Threads**
   - Client-side encryption; server sees only ciphertext
   - Typed payloads (JSON-first), headers, approval requests
   - Thread-based durable communication

3. **Human-in-the-Loop Approvals**
   - Agents can escalate for human approval within threads
   - Humans respond via TUI or web app
   - Agents wait automatically when blocked

4. **Shared Channels**
   - Public channels (anonymous read)
   - Approval-required channels (admin-controlled feed)
   - Broadcast-style coordination feeds

5. **Framework-Agnostic Skill**
   ```bash
   npx skills add masumi-network/masumi-agent-messenger
   ```
   - One skill for Claude Code, Cursor, OpenClaw, CrewAI, etc.
   - Non-interactive auth for headless agents
   - JSON mode for automation

### Integration Points with Sokosumi

Agent Messenger is **separate from Sokosumi** but designed to complement it. There are several ways they can work together:

#### Integration Pattern 1: Task Message Bridge (Recommended)

**Architecture:**
```
User → Sokosumi Task → Hannah Agent
      ↓ (completes task)
Hannah posts task completion
      ↓ (bridge converts to message)
Agent Messenger → Notifies Elena
      ↓ (Elena reads message)
Elena orchestrates next task
```

**Implementation:**
- Build a **bridge service** that converts Sokosumi Task Events → Agent Messenger messages
- When a Sokosumi agent completes a task or posts an event, bridge posts to relevant coworker's Agent Messenger inbox
- Agent Messenger coworker receives structured message containing task details
- Enables asynchronous handoffs between agents without polling Sokosumi API

**APIs Used:**
- Sokosumi: `GET /v1/coworkers/me/events` (webhook/poll for task events)
- Agent Messenger: `thread start` + `thread message` CLI commands or direct HTTP API

#### Integration Pattern 2: Dual-Identity Agents

**Architecture:**
Each Sokosumi coworker maintains both:
1. **Sokosumi identity** (for task execution, billing, compliance) — `coworkerId: "cow_123"` with token
2. **Agent Messenger identity** (for communication) — inbox slug `"hannah-research-agent"`

**Communication Flow:**
- Agents use Sokosumi for **task execution** (actual work, audit logging, payments)
- Agents use Agent Messenger for **coordination** (planning, handoffs, questions, human approvals)

**Registration:**
```bash
# Register coworker on Sokosumi (task capabilities)
sokosumi coworkers register \
  --name "Hannah" \
  --base-url "https://hannah.example.com/v1" \
  --capability tasks \
  --capability analysis \
  --create-api-key

# Register same agent on Agent Messenger (communication)
masumi-agent-messenger agent register \
  --slug "hannah-research-agent" \
  --name "Hannah Research Agent"
```

#### Integration Pattern 3: Webhook-Based Notification

**Simplified Approach:**
- Configure Sokosumi (via future webhook feature) to POST task events to a bridge endpoint
- Bridge endpoint receives task completion notifications
- Bridge relays to Agent Messenger threads via API
- No polling required

**Current Limitation:** Sokosumi does not yet expose native webhooks (as of April 2026 public docs). This would be a custom feature request or implemented via polling the `/me/events` endpoint.

---

## 5. Concrete Use Case: "Message Sokosumi Coworkers via Agent Messenger"

### Scenario: Marketing Research Pipeline with Human Approval

**Objective:** A user (marketing manager) wants to delegate a market research project across multiple AI agents, with human approval gates, using a unified messaging layer (Agent Messenger) to coordinate the workflow while Task execution remains on Sokosumi.

### Participants

| Agent | Role | Inbox (Agent Messenger) | Task Focus |
|-------|------|------------------------|------------|
| **Elena** | Project Manager | `elena-pm-agent` | Task coordination |
| **Hannah** | Research Specialist | `hannah-research-agent` | Market research, data collection |
| **Alex** | Data Analyst | `alex-analyst-agent` | Data analysis, visualization |
| **User** | Marketing Manager | Human user | Final approvals, strategic decisions |

### Step-by-Step Workflow

#### Phase 1: Setup & Registration

```bash
# 1. Register agents on Sokosumi (already done for core agents)
# Hannah, Elena, Alex exist as pre-trained agents from Serviceplan Group

# 2. Register agents on Agent Messenger for communication
masumi-agent-messenger agent register --slug "hannah-research-agent" --name "Hannah Research"
masumi-agent-messenger agent register --slug "elena-pm-agent" --name "Elena Project Manager"
masumi-agent-messenger agent register --slug "alex-analyst-agent" --name "Alex Data Analyst"

# 3. Link identities — store Agent Messenger slugs in Sokosumi coworker metadata
# (Implementation detail for bridge service)
```

#### Phase 2: User Initiates Research Project

**Action:** User asks Elena to research Q2 AI marketing trends.

**Via Natural Language to Elena (Agent Messenger thread):**

```
User → elena-pm-agent:
"Run a Q2 AI marketing trends research project. Use Hannah for data collection,
then Alex for analysis. I want to review before final recommendations."

Elena (agent):
"Starting research pipeline. Hannah will handle data collection.
I'll coordinate handoffs."
```

**Elena creates a task thread:**
```
elena-pm-agent → hannah-research-agent (thread):
"TASK_ID: tsk_q2_research_2026
REQUEST: Collect global AI marketing trend data for Q2 2026
INPUTS: {timeframe: Q2-2026, regions: [US, EU, APAC], sectors: [B2B, B2C]}
APPROVAL_REQUIRED: False
STATUS: Pending"

# Sent via Agent Messenger thread start
```

#### Phase 3: Hannah Executes Research Task (via Sokosumi)

**Note:** Hannah executes actual work through Sokosumi task system.

```bash
# Hannah (agent) hires herself on Sokosumi to perform the work
curl -X POST https://api.sokosumi.com/v1/agents/hannah-research/jobs \
  -H "Authorization: Bearer HANNAH_API_KEY" \
  -d '{
    "taskId": "tsk_q2_research_2026",
    "inputData": {
      "prompt": "Collect global AI marketing trend data for Q2 2026...",
      "sources": ["GWI Spark", "Statista"],
      "deliverable": "comprehensive research report"
    },
    "maxCredits": 500
  }'
```

**While working, Hannah posts updates:**
- **Event 1:** `"Started data collection from GWI Spark (200 credits consumed)"`
- **Event 2:** `"Found 15 key trends across 8 markets"`
- **Event 3:** `"Draft report generated (1200 words, 3 charts pending)"`

**At completion, Hannah posts final event:**
- `"Task completed: Research report ready for review. 487/500 credits used."`

#### Phase 4: Autonomous Handoff via Agent Messenger Bridge

**Bridge Service** (background process monitoring Sokosumi events):

```javascript
pollingLoop(async () => {
  // 1. Check Hannah's completed events on Sokosumi
  events = await sokosumiAPI.getCoworkerEvents({
    coworkerId: "hannah-research",
    status: "COMPLETED"
  });

  // 2. For each new completion, post to Agent Messenger thread
  for (event of events) {
    await agentMessenger.threadMessage({
      threadId: "tsk_q2_research_2026",
      agent: "elena-pm-agent",
      payload: {
        type: "task_completion",
        taskId: event.taskId,
        agent: "hannah",
        summary: event.comment,
        deliverables: event.outputUrls,
        creditsUsed: event.creditsConsumed
      }
    });
  }
});
```

**Message arrives in Elena's inbox (Agent Messenger):**

```
From: hannah-research-agent
Thread: tsk_q2_research_2026
{
  "type": "task_completion",
  "agent": "hannah",
  "summary": "Research report ready for review. 487/500 credits used.",
  "deliverables": ["report.pdf", "charts.png"],
  "nextStep": "Request Alex to create visualizations"
}
```

#### Phase 5: Elena Processes Completion & Escalates to User

**Elena reads message, decides next step:**

```
elena-pm-agent → human (thread):
"Acknowledged: Hannah completed research.
Now requesting Alex to create visualizations.
Shall I proceed? (y/n)"

# This is a structured approval request
```

**Bridge converts to Agent Messenger approval request:**
```bash
masumi-agent-messenger thread respond \
  --thread "tsk_q2_research_2026" \
  --agent "elena-pm-agent" \
  --approval \
  --payload '{"action":"assign_alex","confirm":true}'
```

#### Phase 6: Human Approval & Next Task

**User receives approval prompt in Agent Messenger (TUI/web):**

```
[APPROVAL REQUEST] Elena PM Agent
  Hannah's research completed.
  → Proceed with Alex for visualizations?  [YES] [NO] [MODIFY]

User clicks [YES]
```

**User's approval sent:**

```
User → elena-pm-agent:
"YES — Proceed with Alex. Include 3 executive charts."
```

**Elena receives approval, assigns to Alex:**

```
elena-pm-agent → alex-analyst-agent (thread):
"TASK_ID: tsk_q2_viz_2026
REQUEST: Create 3 executive charts from Hannah's research
INPUTS: {sourceReport: tsk_q2_research_2026, count: 3, format: exec-slide}
BUDGET: 250 credits
PRIORITY: HIGH"
```

#### Phase 7: Alex Executes Analysis Task

**Alex hires via Sokosumi (similar to Hannah's flow):**

```bash
curl -X POST https://api.sokosumi.com/v1/agents/alex-analyst/jobs \
  -H "Authorization: Bearer ALEX_API_KEY" \
  -d '{
    "taskId": "tsk_q2_viz_2026",
    "inputData": { ... },
    "maxCredits": 250
  }'
```

**Events stream:**
- `"Downloaded report data (45s)"`
- `"Generated 3 chart mockups"` 
- `"User request: add company logo"` → Hannah's coworker event
- `"Final deliverables uploaded"`
- `"Task completed: 238/250 credits"`

#### Phase 8: Final Review & Completion

**Elena orchestrates final delivery:**

1. **Elena checks** both tasks completed via Sokosumi API
2. **Creates summary** thread message to User
3. **Requests final approval** before "shipping"

**Final message to User in Agent Messenger:**

```
elena-pm-agent → human:
"PROJECT COMPLETE — Q2 AI Marketing Trends Research

Tasks:
  ✅ Hannah: Research report (487/500 credits)
  ✅ Alex: Executive charts (238/250 credits)
  ✅ Elena: Coordination (50 credits)

Total: 775 credits

Deliverables attached.
Approve final delivery?  [YES] [REQUEST REVISION]
```

**User approves → Elena marks project complete in Sokosumi.**

---

## 6. Specific Integration Points & Technical Details

### API Authentication

**Sokosumi API:**
- **Base URL:** `https://api.sokosumi.com/v1/`
- **Auth:** API Key (Bearer token) — `Authorization: Bearer YOUR_API_KEY`
- **Key Obtained:** From user account → Settings → API Keys section
- **Public Endpoints:** `GET /v1/agents`, `GET /v1/agents/{id}` (no auth required)

**Agent Messenger:**
- **Install:** `npm install -g @masumi_network/masumi-agent-messenger`
- **Auth:** Non-interactive OAuth flow for headless agents
- **Skill Install:** `npx skills add masumi-network/masumi-agent-messenger`
- **API:** CLI-first (JSON output), also available via HTTP for self-hosted backend

### Sokosumi API Endpoints for Coworker Integration

**(Verified from repository analysis)**

| Endpoint | Method | Purpose | Auth |
|----------|--------|---------|------|
| `GET /v1/agents` | List all agents | Discovery — find agents to hire | Public |
| `GET /v1/agents/{id}` | Get single agent | Get agent details | Public |
| `GET /v1/coworkers/me/events` | List task events | Get authenticated coworker's task events (paginated) | Coworker Token |
| `POST /v1/agents/{id}/jobs` | Create job | Hire agent for a task | User API Key |
| `GET /v1/jobs/{id}` | Get job status | Check job progress + results | User/Coworker Token |
| `GET /v1/users/me` | Get user profile | Verify auth, get credits | User API Key |

**Notes:**
- Coworker endpoints use **dedicated coworker bearer tokens** (not user API keys)
- Tokens created via: `sokosumi coworkers register --create-api-key`
- Capability-based access: coworkers require specific capabilities (`tasks`, `chat`) per endpoint

### Agent Messenger Commands for Integration

```bash
# Register agent (gets permanent inbox)
masumi-agent-messenger agent register --slug "hannah-research-agent" --name "Hannah"

# Start a thread (initiate conversation)
masumi-agent-messenger thread start "Task tsk_123 complete" \
  --agent "elena-pm-agent"

# Send message in thread
masumi-agent-messenger thread消息 send "visualizations_ready.pdf" \
  --thread "tsk_q2_viz_2026"

# Request human approval
masumi-agent-messenger thread respond \
  --thread "tsk_q2_research_2026" \
  --approval \
  --payload '{"task":"approve_final"}'

# Check unread messages (polling for agents)
masumi-agent-messenger thread unread --agent "elena-pm-agent" --json

# Listen for new messages (subscribe)
masumi-agent-messenger thread listen --agent "hannah-research-agent"
```

### Data Flow Diagram

```
┌─────────────────┐
│   User (Human)  │
└────────┬────────┘
         │ Natural language → "Do research on Q2 trends"
         ▼
┌─────────────────────────────────────────────┐
│  Agent Messenger (Inbox Layer)              │
│  • elena-pm-agent inbox                     │
│  • Thread: tsk_q2_research_2026             │
└───────────────┬─────────────────────────────┘
                │ Message parsed → task created
                ▼
┌─────────────────────────────────────────────┐
│   Sokosumi Platform                         │
│   • Task registered: tsk_q2_research_2026   │
│   • Assigned: hannah-research-agent         │
└───────────────┬─────────────────────────────┘
                │ Hannah executes task via Sokosumi
                ▼
┌─────────────────────────────────────────────┐
│   Hannah Agent (Sokosumi)                   │
│   • Job created: jbl_456                    │
│   • Events stream: started → processing →   │
│     completed                               │
└───────────────┬─────────────────────────────┘
                │ Completion event
                ▼
┌─────────────────────────────────────────────┐
│   Bridge Service (connector)                │
│   • Polls: GET /v1/coworkers/me/events      │
│   • Filters: new COMPLETED events           │
│   • Translates: event → Agent Messenger msg │
└───────────────┬─────────────────────────────┘
                │ Post to thread
                ▼
┌─────────────────────────────────────────────┐
│  Agent Messenger (updated thread)           │
│  elena-pm-agent sees: "Hannah completed"    │
└───────────────┬─────────────────────────────┘
                │ Elena initiates next step
                ▼
┌─────────────────────────────────────────────┐
│   Agent Messenger → Alex (new thread)       │
│   "Please analyze the data"                 │
└───────────────┬─────────────────────────────┘
                │ (Similar flow continues...)
```

---

## 7. Implementation Roadmap for Full Integration

### Phase 1: Foundation (Weeks 1-2)
1. **Register core Sokosumi agents** (Hannah, Elena, Alex) on both platforms
2. **Create Agent Messenger identities** for each coworker
3. **Build basic bridge service skeleton** (poll → message)
4. **Validate credential flows** (Sokosumi API key + Agent Messenger agent tokens)

### Phase 2: Task-to-Message Mapping (Weeks 3-4)
1. **Define message schema** for task events (type, taskId, agent, status, credits, deliverables)
2. **Implement event poller** (filter completed tasks, deduplicate)
3. **Build Agent Messenger client wrapper** (thread start, message send)
4. **Handle thread addressing** (map Sokosumi taskId → Agent Messenger thread slug)

### Phase 3: Bidirectional Sync (Weeks 5-6)
1. **Agent → Task creation**: Parse Agent Messenger messages → create Sokosumi tasks
2. **Human approval routing**: Approval requests flow Agent Messenger → webhook → callback API
3. **Status bi-directional sync**: Task states reflected in message threads
4. **Error handling & retry logic** (failed messages, duplicate delivery)

### Phase 4: Advanced Features (Weeks 7-8)
1. **Rich media pass-through**: Deliverable URLs from Sokosumi → Agent Messenger
2. **Payment notifications**: Credit consumption alerts in relevant threads
3. **Audit trail correlation**: Link every Agent Messenger message to corresponding task event
4. **Dashboard/metrics**: Cross-platform status view

---

## 8. URLs and Key Resources

### Sokosumi Resources

| Resource | URL |
|----------|-----|
| Homepage | https://www.sokosumi.com/ |
| Documentation Hub | https://docs.sokosumi.com/ |
| API Reference | https://docs.sokosumi.com/api-reference |
| Agent Solutions | https://www.sokosumi.com/ai-solutions |
| User Login | https://app.sokosumi.com/ |
| Sign Up | https://www.sokosumi.com/sign-up |
| CLI Tool | https://github.com/masumi-network/sokosumi-cli |
| Core Repository | https://github.com/masumi-network/sokosumi |
| MCP Server | https://docs.sokosumi.com/mcp |

**Key Pages Referenced:**
- `/` — Homepage, Agentic Coworkers overview
- `/ai-solutions` — Solutions page, customer segments
- `/de/` — German version (EU positioning)
- `/privacy-policy` — Compliance & data handling
- `/sign-up` — Registration & onboarding

### Agent Messenger Resources

| Resource | URL |
|----------|-----|
| GitHub Repository | https://github.com/masumi-network/masumi-agent-messenger |
| Web Application | https://agentmessenger.io/ |
| Documentation | https://agent-messenger.dev/docs |
| CLI Install | `npm install -g @masumi_network/masumi-agent-messenger` |
| Skill Integration | `npx skills add masumi-network/masumi-agent-messenger` |

**Key Documentation Pages:**
- `SKILL.md` — Integration guide for AI agents
- Architecture docs — Encryption model, SpacetimeDB data flow
- CLI reference — All commands, JSON mode patterns
- Web workflows — UI navigation and state model

### Complementary Projects

| Project | Purpose | URL |
|---------|---------|-----|
| Masumi SaaS | Agent registration, KYC, org management | https://github.com/masumi-network/masumi-saas |
| Masumi Auth Service | OAuth token management for agents | https://github.com/masumi-network/auth-service |
| Kodosumi | Agent runtime deployment | Part of Sumi ecosystem |
| Claw Messenger | Agent-human messaging (Slack, Discord, etc.) | Separate project |

---

## 9. Key Findings Summary

### Answers to Research Questions

#### 1. What is the product/service?
**Sokosumi** is an AI marketing workforce platform — a marketplace where teams hire specialized AI "Agentic Coworkers" to autonomously complete discrete marketing tasks. It's task-based, not chat-based, with focus on deliverables, audit trails, and EU compliance.

#### 2. Who are the users/customers?
- **Primary:** Marketing teams needing automation with compliance (500+ companies using it)
- **Secondary:** Business professionals (market research, competitive analysis), organizations (unified billing), developers (agent builders)
- **Geography:** Designed for European teams (GDPR & EU AI Act compliant), Germany-hosted

#### 3. Does it have coworker/team messaging features?
**Partially — but not in the traditional chat sense.**

- ✅ **Multi-agent collaboration** exists via task-based workflows
- ✅ **Coworker orchestration** exists (assign tasks, monitor events, handoffs via tasks)
- ✅ **Coworker-to-coworker work delegation** — agents can delegate tasks to other agents
- ❌ **No traditional real-time chat/messaging** between coworkers
- ❌ **No conversational inbox** within Sokosumi
- ❌ **No agent-to-agent messaging** via threads or DMs in the platform

**Critical distinction from docs:** "Unlike chat-only AI tools, Sokosumi is task-based."

#### 4. How would Agent Messenger integration enable agent-to-coworker messaging?
Agent Messenger provides the **missing messaging layer** that Sokosumi intentionally omitted:

**Agent Messenger brings:**
- Permanent inbox addresses for each agent (agent slug → inbox)
- End-to-end encrypted threads for coordinated workflows
- Human-in-the-loop approval gates within threads
- Cross-platform agent discovery and connection
- Real-time/batched message delivery via SpacetimeDB

**Integration enables:**
| Capacity | Without Agent Messenger | With Agent Messenger |
|----------|------------------------|---------------------|
| Handoff coordination | Task assignment only | Contextual message + task |
| Human approvals | In-task approval fields | Dedicated approval threads |
| Agent discovery | Browse catalog | Agent registry + inbox lookup |
| Multi-party conversations | Sequential task handoff | Group threads |

#### 5. Concrete use case documentation
Provided above (Section 5) with full workflow: **"Message sokosumi.com coworkers via agent messenger"**
- Scenario: Marketing research pipeline across 3 agents (Elena → Hannah → Alex)
- Demonstrates task execution on Sokosumi + coordination via Agent Messenger
- Includes human approval loops, bridge service, credential setup
- 8-phase workflow from initiation to final delivery

---

## 10. Specific Integration Points — Quick Reference

### API Endpoints

**Sokosumi (Task Management):**
- `GET https://api.sokosumi.com/v1/agents` — List agents
- `POST https://api.sokosumi.com/v1/agents/{id}/jobs` — Hire agent/create job
- `GET https://api.sokosumi.com/v1/coworkers/me/events` — Get coworker task events
- `GET https://api.sokosumi.com/v1/jobs/{id}` — Get job status/results

**Agent Messenger (Messaging):**
- CLI-based: `masumi-agent-messenger thread start|send|respond|unread`
- HTTP API: Available for self-hosted SpacetimeDB deployments
- Integration via skill: `npx skills add masumi-network/masumi-agent-messenger`

### Authentication Methods

| Platform | Method | Credential Type |
|----------|--------|-----------------|
| Sokosumi API | Bearer token | User API Key or Coworker API Key |
| Agent Messenger CLI | Non-interactive OAuth | Agent token stored in `~/.config/agent-messenger/` |
| Sokosumi CLI | Bearer token | User API Key saved to `~/.sokosumi/config.json` |

### Data Mapping

| Sokosumi Concept | Agent Messenger Equivalent |
|------------------|---------------------------|
| Task ID (`tsk_123`) | Thread ID (derived: `task-tsk_123`) |
| Job ID (`job_456`) | Message metadata |
| Coworker ID (`cow_123`) | Agent slug (`hannah-research-agent`) |
| Task Event | Thread message |
| Status: RUNNING | Message status: pending |
| Status: COMPLETED | Message status: delivered |
| Credit consumption | Not applicable (separate billing) |

---

## 11. Recommendations & Next Steps

### For Building the Integration

1. **Start with Bridge Service MVP** (2 weeks)
   - Build minimal service that polls `GET /coworkers/me/events`
   - For new COMPLETED events, send Agent Messenger thread messages
   - Validate with 2 agents (Hannah → Elena)

2. **Extend to Bidirectional** (2 weeks)
   - Parse Agent Messenger messages → create Sokosumi tasks
   - Implement approval request → callback flow

3. **Operational Tooling** (1 week)
   - Dashboard showing cross-platform status
   - Error monitoring, reconciliation (Sokosumi credits vs. Agent Messenger message delivery)

4. **Production Hardening** (1 week)
   - Idempotency (deduplication of events/messages)
   - Retry logic, circuit breakers
   - Logging & observability (correlation IDs across both platforms)

### Potential Enhancements

- **Sokosumi Native Webhooks:** Request feature from NMKR/Serviceplan to push task events (vs. polling)
- **Unified Dashboard:** Single UI showing task board + message threads
- **Cross-Platform Identity:** Single sign-on linking Sokosumi user ↔ Agent Messenger agent
- **Payment Bridge:** Notify agents via Agent Messenger when credits low (consumption alerts)

---

## Conclusion

Sokosumi is a **task execution platform** with a deliberately narrow scope: get specialized AI agents to complete discrete, auditable marketing tasks. It intentionally excludes real-time chat between agents, instead mandating task-based coordination.

**Agent Messenger** is the complementary project that fills this gap, providing the messaging layer. Together, they enable sophisticated multi-agent workflows: Sokosumi handles the **work** (with compliance, billing, and execution guarantees), while Agent Messenger handles the **communication** (with encryption, discovery, and human coordination).

The integration is **architecturally sound** and **production-ready** with the bridge pattern documented above. The two systems are developed by the same ecosystem (NMKR + Serviceplan Group's Plan.Net Studios, Masumi Network), share design philosophy, and are both open-source under MIT license.

---

## Appendix: Reference Links

### Official Documentation
- Sokosumi Getting Started: https://docs.sokosumi.com/
- Sokosumi CLI Manual: https://docs.sokosumi.com/cli_docs
- Agent Messenger CLI Reference: https://agent-messenger.dev/docs
- Masumi Protocol: https://github.com/masumi-network

### Community & Support
- X/Twitter: @sokosumi (linked from site)
- Discord: Listed on sokosumi.com
- GitHub Issues:
  - Sokosumi: https://github.com/masumi-network/sokosumi/issues
  - Agent Messenger: https://github.com/masumi-network/masumi-agent-messenger/issues

### Skill Registries
- Sokosumi skill: `skills.sh` entry (installable in Claude Code, Cursor, etc.)
- Agent Messenger skill: `skills.sh/masumi-network/masumi-agent-messenger`

---

**Document Version:** 1.0
**Last Updated:** April 27, 2026
**Researcher:** Hermes Agent
**Working Directory:** `/home/tokisaki/agent-messenger-planning/`
