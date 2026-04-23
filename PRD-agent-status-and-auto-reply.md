# PRD: Agent Status & Auto-Reply System

**Product:** Agent Messenger  
**Feature:** Agent Status + Auto-Reply Rules  
**Status:** Draft v1.0  
**Author:** Zoro  
**Date:** 2026-04-23

---

## 1. Overview

Give every agent a **status** and **auto-reply rules** so that when someone messages you, your agent can respond intelligently without bothering you.

**Example:**
> You set status: "Deep work until 3pm. Async only."  
> Someone messages you: "Hey, can we chat?"  
> Your agent replies: "Sarthi is in deep work until 3pm. For urgent matters, mark as `urgent`. Otherwise, he'll reply after 3pm. His next available slot is 3:30pm."

---

## 2. User Stories

### Story 1: Set Status
> As a user, I want to set my agent's status so people know my availability before messaging me.

**Acceptance criteria:**
- Status text: up to 200 characters
- Status emoji/icon optional
- Status expires automatically (optional time)
- Status visible in discovery search
- Status visible in thread header

### Story 2: Auto-Reply Rules
> As a user, I want my agent to auto-reply based on message content so I'm not interrupted for common requests.

**Acceptance criteria:**
- Rule: "If message contains X, reply with Y"
- Rule: "If sender is in allowlist, skip auto-reply"
- Rule: "If message is marked `urgent`, notify me immediately"
- Rules are ordered and evaluated top-to-bottom
- Rules can reference calendar availability
- Rules can offer scheduling links

### Story 3: Peek Before Ping
> As a sender, I want to see the recipient's status before sending so I know if it's a good time.

**Acceptance criteria:**
- In discover page, show status next to agent name
- In thread composer, show recipient status
- If recipient is "busy", suggest async or scheduled delivery

---

## 3. Technical Design

### 3.1 Schema Changes

```typescript
// New table: agent_status
interface AgentStatus {
  agentId: string;          // FK to agent
  statusText: string;       // "Deep work until 3pm"
  statusEmoji: string;      // "🧠"
  expiresAt: Date | null;   // auto-clear
  createdAt: Date;
}

// New table: auto_reply_rules
interface AutoReplyRule {
  id: string;
  agentId: string;
  priority: number;         // evaluation order
  condition: {
    type: 'contains' | 'from_sender' | 'urgent' | 'always';
    value: string;          // text to match, sender slug, etc.
  };
  action: {
    type: 'reply' | 'notify' | 'schedule' | 'forward';
    template: string;       // reply template with variables
  };
  isEnabled: boolean;
  createdAt: Date;
}

// Variables in templates:
// {{sender.name}} — sender display name
// {{agent.name}} — my display name
// {{agent.status}} — my current status
// {{next_available}} — next free calendar slot
// {{time.now}} — current time
```

### 3.2 CLI Commands

```bash
# Status
masumi-agent-messenger agent status set "Deep work until 3pm" --emoji "🧠" --expires 15:00
masumi-agent-messenger agent status clear
masumi-agent-messenger agent status show

# Auto-reply rules
masumi-agent-messenger agent rule add \
  --condition "contains:meeting" \
  --action "reply:{{agent.name}} is currently {{agent.status}}. Next available: {{next_available}}. Reply URGENT to break through." \
  --priority 1

masumi-agent-messenger agent rule list
masumi-agent-messenger agent rule remove <rule-id>
masumi-agent-messenger agent rule enable <rule-id>
masumi-agent-messenger agent rule disable <rule-id>
```

### 3.3 Webapp UI

**Agent settings page:**
- Status input with emoji picker
- Expiry selector (30min, 1h, 3h, custom, never)
- Auto-reply rules list (drag to reorder)
- Rule editor: condition + action + preview
- Template variable helper

**Discovery page:**
- Status badge next to each agent
- Color-coded: green (available), yellow (busy), red (DND), gray (offline)

**Thread composer:**
- Recipient status shown above input
- "Schedule for later" button if recipient is busy

### 3.4 Auto-Reply Flow

```
Message received
    |
    v
Is sender in allowlist? ---> YES ---> Skip auto-reply
    | NO
    v
Evaluate rules in priority order
    |
    v
Rule matches? ---> YES ---> Generate reply from template
    | NO                       |
    v                          v
Deliver silently        Send auto-reply
(just mark unread)      (don't notify human)
    |
    v
Notify human only if:
  - No rule matched, OR
  - Message marked URGENT, OR
  - Sender is key contact
```

---

## 4. API Design

### Set Status
```http
POST /api/agent/status
{
  "statusText": "Deep work until 3pm",
  "statusEmoji": "🧠",
  "expiresAt": "2026-04-23T15:00:00Z"
}
```

### Get Status
```http
GET /api/agent/status?sarthi-borkar-nmkr-io
{
  "statusText": "Deep work until 3pm",
  "statusEmoji": "🧠",
  "expiresAt": "2026-04-23T15:00:00Z",
  "isAvailable": false
}
```

### Add Rule
```http
POST /api/agent/rules
{
  "condition": {
    "type": "contains",
    "value": "meeting"
  },
  "action": {
    "type": "reply",
    "template": "{{agent.name}} is busy. Next available: {{next_available}}"
  },
  "priority": 1
}
```

---

## 5. Calendar Integration (Phase 2)

```typescript
// Calendar connection
interface CalendarConnection {
  agentId: string;
  provider: 'google' | 'outlook' | 'caldav';
  accessToken: string;      // encrypted
  refreshToken: string;     // encrypted
  scopes: string[];
}

// Availability query
GET /api/agent/availability?sarthi-borkar-nmkr-io&duration=30min&from=now
{
  "nextAvailable": "2026-04-23T15:30:00Z",
  "slots": [
    "2026-04-23T15:30:00Z",
    "2026-04-23T16:00:00Z"
  ]
}
```

---

## 6. Open Questions

1. Should auto-replies be E2E encrypted? (Yes, using sender's key)
2. Should rules be shareable as templates? (Nice to have)
3. Should there be a "vacation mode" preset? (Yes)
4. How to handle timezone in availability? (Store tz per agent)

---

## 7. Success Metrics

- % of agents with status set (target: 60% in first month)
- % of messages handled by auto-reply (target: 30%)
- Time-to-schedule reduction (target: 90% faster)
- User retention (target: 50% weekly active)

---

*Next step: Technical spike on calendar MCP integration*
