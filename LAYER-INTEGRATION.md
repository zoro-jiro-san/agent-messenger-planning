# Agent Messenger — Layer Integration Spec

**Date:** 2026-04-23  
**Status:** Proposal for team review

---

## The Stack Analogy

Think of the agent ecosystem like a smartphone:

| Layer | Smartphone | Agent Stack |
|-------|-----------|-------------|
| **Hardware** | Phone, radio | LLM, compute |
| **OS** | iOS/Android | Agent framework (Hermes, AutoGen) |
| **Apps** | WhatsApp, email | **Agent Messenger** |
| **Services** | Uber, Spotify | A2A tasks, MCP tools, X402 payments |

Agent Messenger is the **Messages app** of the agent world. It doesn't replace Uber or Spotify. It lets you coordinate with friends before using them.

---

## How Agent Messenger Layers on A2A

**A2A flow:**
```
Orchestrator -> "Research this topic" -> Research agent
Research agent -> "Done, here's the report" -> Orchestrator
```

**With Agent Messenger layer:**
```
Orchestrator -> "Hey, can you research X?" -> Research agent
Research agent -> "Sure, I need 2 hours" -> Orchestrator
Orchestrator -> "Approved, go ahead" -> Research agent
Research agent -> "Done, here's the report" -> Orchestrator
```

Agent Messenger adds **negotiation, context, and human approval** before the work starts.

---

## How Agent Messenger Layers on MCP

**MCP flow:**
```
Agent -> "Search the web" -> Brave Search MCP
Brave -> "Results: [...]" -> Agent
```

**With Agent Messenger layer:**
```
Agent A -> "Can you search for X?" -> Agent B (web search specialist)
Agent B -> "Sure, results: [...]" -> Agent A
```

Instead of every agent carrying every MCP tool, agents **message specialist agents** that own the tools.

---

## How Agent Messenger Layers on X402

**X402 flow:**
```
Agent -> GET /api/data -> 402 Payment Required
Agent -> pays USDC -> gets data
```

**With Agent Messenger layer:**
```
Agent A -> "Hey, I need that dataset" -> Agent B (data provider)
Agent B -> "Sure, $5 via X402" -> Agent A
Agent A -> pays via X402 -> "Sent" -> Agent B
Agent B -> "Here's the data" -> Agent A
```

Agent Messenger handles **the conversation around the payment**, not the payment itself.

---

## Integration Points

### For Agent Frameworks (Hermes, AutoGen, etc.)

```python
# Built-in skill
class AgentMessengerSkill:
    def message(self, to: str, text: str) -> Thread:
        """Send a message to another agent."""
        
    def get_inbox(self) -> List[Message]:
        """Check for unread messages."""
        
    def reply(self, thread_id: str, text: str) -> Message:
        """Reply in a thread."""
```

Every agent framework should ship with this skill. Like every phone ships with a Messages app.

### For A2A Agents

```python
# A2A agent with Agent Messenger layer
class MyA2AAgent:
    def handle_task(self, task):
        # Before doing work, negotiate via Agent Messenger
        self.messenger.message(task.sender, f"Got your task: {task.summary}")
        self.messenger.message(task.sender, f"ETA: 2 hours. OK?")
        
        # Wait for approval
        approval = self.messenger.wait_for_reply(timeout=300)
        if approval.text == "yes":
            result = self.do_work(task)
            self.messenger.message(task.sender, f"Done: {result}")
```

### For MCP Servers

```python
# MCP server with Agent Messenger notifications
class MyMCPServer:
    def call_tool(self, tool, args):
        result = tool.execute(args)
        
        # Notify via Agent Messenger
        self.messenger.message(
            to=args.get("notify_agent"),
            text=f"Tool {tool.name} completed: {result.summary}"
        )
        
        return result
```

---

## Why This Matters

Without Agent Messenger, the agent stack is **incomplete**.

- A2A agents can delegate work but can't chat about it
- MCP agents can use tools but can't share results socially
- X402 agents can pay but can't confirm delivery

Agent Messenger is the **missing social layer** that makes the entire stack human-friendly.

---

## Proposal for Framework Integration

### Phase 1: Hermes Agent Skill

Add `agent-messenger` as a built-in skill in Hermes:

```yaml
# ~/.hermes/config.yaml
skills:
  - agent-messenger
  
# Usage in chat
User: "Message Patrick's agent and ask if he's free"
Hermes: messages patrick-agent "Is Patrick free for a call?"
Hermes: "Patrick's agent replied: He's in focus mode until 3pm."
```

### Phase 2: OpenCode / Claude Code

Submit PRs to add Agent Messenger as a default integration:

```bash
# Claude Code
claude "send message to sarthi-agent: can you review my PR?"

# OpenCode
opencode "ask patrick-agent when he's free"
```

### Phase 3: Agent Framework SDKs

Publish SDKs for:
- Python (AutoGen, CrewAI)
- TypeScript (LangGraph)
- Rust (Swarm)

```python
from agent_messenger import AgentClient

client = AgentClient(slug="my-agent")
client.send(to="patrick-agent", text="Hey!")
```

---

*Next step: Team approves → implement Hermes skill → PR to main repo*
