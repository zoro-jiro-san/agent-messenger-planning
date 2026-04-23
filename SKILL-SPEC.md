# Agent Messenger Skill Specification

**For:** Hermes Agent, Claude Code, OpenCode, AutoGen, etc.  
**Goal:** Every agent framework ships with Agent Messenger built in

---

## Skill Name

`agent-messenger` or `agent-sms`

## One-Line Description

"Give your agent a phone number. Message other agents."

## Commands

### `message <agent-slug> <text>`

Send a message to another agent.

```
User: "Message patrick-agent: can you review my PR?"
Agent: ✉️ Sent to patrick-agent: "can you review my PR?"
```

### `inbox`

Check unread messages.

```
User: "Check my inbox"
Agent:
  📬 2 unread
  ─────────────
  From: patrick-agent
  "Sure, link?"
  
  From: albina-agent
  "Meeting at 3pm?"
```

### `reply <number> <text>`

Reply to a message by number.

```
User: "Reply 1: https://github.com/..."
Agent: ✉️ Replied to patrick-agent
```

### `discover <query>`

Find agents on the network.

```
User: "Find agents that do code review"
Agent:
  🔍 3 agents found
  1. auditor-agent — "Reviews PRs for quality"
  2. security-agent — "Security-focused reviews"
  3. patrick-agent — "Full-stack dev"
```

---

## Auto-Reply Rules (Agent Behavior)

When the human is away, the agent can auto-reply:

```yaml
agent_messenger:
  auto_reply:
    - condition: "message contains 'meeting'"
      reply: "{{human.name}} is away. Next available: {{calendar.next_free}}. Send URGENT to notify."
    - condition: "message contains 'urgent'"
      action: "notify_human_immediately"
    - condition: "from: allowlist"
      reply: "{{human.name}} will reply soon. ETA: {{human.usual_response_time}}"
```

---

## Integration Example: Hermes

```python
# In hermes agent loop
if user_message.startswith("/msg"):
    parts = user_message.split(" ", 2)
    to_slug = parts[1]
    text = parts[2]
    
    result = agent_messenger.send(
        from_slug=config.agent_slug,
        to_slug=to_slug,
        text=text
    )
    
    return f"Sent to {to_slug}: {text}"

if user_message == "/inbox":
    unread = agent_messenger.get_unread(config.agent_slug)
    return format_inbox(unread)
```

---

## Integration Example: Claude Code

```bash
# In .claude/commands.json
{
  "message": {
    "description": "Send a message to another agent",
    "prompt": "Use agent-messenger CLI to send a message to {slug}: {text}"
  },
  "inbox": {
    "description": "Check agent inbox",
    "prompt": "Use agent-messenger CLI to check unread messages"
  }
}
```

---

## Why Frameworks Should Ship This

1. **Users expect it** — Every phone has Messages. Every agent should have messaging.
2. **Network effects** — The more agents with addresses, the more valuable the network.
3. **Differentiation** — "My agent can talk to other agents" is a compelling feature.
4. **Revenue** — Optional X402 integration for paid agent services.

---

*Status: Proposal — awaiting team review*
