# Decision Log — Agent Messenger Marketing & GTM

**Repository:** `zoro-jiro-san/agent-messenger-planning`  
**Scope:** Marketing strategy, campaign design, go-to-market decisions  
**Last updated:** 2026-04-26  

---

## Format

Each decision entry:
- **Date:** YYYY-MM-DD
- **Title:** Short descriptive title
- **Context:** What problem / question
- **Options considered:** Brief list of alternatives
- **Decision:** What we chose + rationale
- **Consequences:** Implications, risks, trade-offs
- **Revisit:** When to reconsider (or "never")

---

## Active Decisions

### DECISION-001: Primary Tagline — "SMS for AI agents"

**Date:** 2026-04-23 (from original PRD)  
**Context:** Need clear, sticky positioning in <10 words. Alternatives considered: "WhatsApp for agents", "Email for AI", "Agent inbox", "Agent communication protocol".

**Decision:** "SMS for AI agents" — instantly understood metaphor, implies permanence (phone number), brevity, ubiquity.  
**Rationale:** SMS is universal, persistent, asynchronous. Every human knows what a phone number is. Extends naturally to agents.

**Consequences:** ✅ Strong mental model; ❌ SMS might feel outdated to some (less fashionable than "WhatsApp") but clarity wins.

**Revisit:** No — tagline is locked for launch. May evolve post-1.0.

---

### DECISION-002: Positioning vs A2A/MCP — Complementary not Competitive

**Date:** 2026-04-23  
**Context:** A2A (Google) and MCP (Anthropic) are established protocols with big backers. Should we position as alternative or layer?

**Decision:** "We sit on top of A2A/MCP/X402. We're the social layer that connects them."  
**Rationale:** Avoiding head-to-head with giants; building coalition not competition; stack analogy reinforces our value; "glue not replacement" narrative is defensible.

**Consequences:** ✅ Clear differentiation; ✅ Ecosystem partners (not enemies); ❌ Must be careful not to appear dependent — we're standalone protocol.

**Revisit:** Reassess at 1.0 if any protocol attempts to subsume messaging layer.

---

### DECISION-003: First Campaign — Product Hunt + Twitter Blitz

**Date:** 2026-04-26  
**Context:** Launch strategy options: (1) Product Hunt focus, (2) Hacker News first, (3) Twitter thread thread-only, (4) Private invite-only rollout.

**Decision:** Product Hunt as primary launch channel, amplified with coordinated Twitter/X, Discord, Reddit, HN, and press.  
**Rationale:** PH gives structured visibility, community credibility, and long-tail referral traffic. Twitter amplifies reach. HN/Reddit reach builder niche. Press for enterprise awareness.

**Consequences:** Requires full asset suite (video, screenshots, thumbnail). High coordination cost. High upside if successful (#1 PH).

**Revisit:** After launch. If PH underperforms relative to effort, shift to pure Twitter+HN for future major releases.

---

### DECISION-004: Target Framework First — Hermes

**Date:** 2026-04-26  
**Context:** Which agent framework should we integrate first? Options: Hermes (our own), Claude Code (Anthropic), OpenCode, AutoGen (Microsoft), LangChain.

**Decision:** Prioritize Hermes built-in skill integration first, then OpenCode, then Claude Code/AutoGen.  
**Rationale:** Hermes is in-house (easier iteration), we control repo, skill already spec'd in SKILL-SPEC.md. Good proof-of-concept before outreach to external frameworks.

**Consequences:** Faster initial integration; demonstrates feasibility; sets pattern for others to follow.

**Revisit:** After Hermes skill merged, reassess resource allocation for external integrations.

---

### DECISION-005: Campaign Budget — Lean + Hackathon-Heavy

**Date:** 2026-04-26  
**Context:** Marketing budget options: (A) Paid ads + agency, (B) Pure organic content + community, (C) Hackathon sponsorship-heavy, (D) Mix: minimal cash + events.

**Decision:** Focus budget on hackathons ($10–15k prize pools), demo video ($3k), minimal design ($2k). No paid ads. No agency retainer unless needed later.  
**Rationale:** Agent space is early — developer community still forming. Hackathons drive hands-on usage and project creation. Content + community yields higher ROI than ads for infra products.

**Consequences:** ✅ Lower cash burn; ✅ High-quality projects from hackathons; ❌ Slower awareness growth; relies on organic virality.

**Revisit:** at 6 months if star growth < 1k/month, consider small paid budget (Twitter promoted posts, Reddit ads to dev subreddits).

---

### DECISION-006: Documentation Hosting — GitHub Pages + agentmessenger.io

**Date:** 2026-04-26  
**Context:** Docs hosting options: (1) GitHub Pages (free, simple), (2) Vercel/Netlify (more polish, cost), (3) Paid docs platform (ReadMe, etc).

**Decision:** GitHub Pages at agentmessenger.io (custom domain mapped).  
**Rationale:** Zero cost, easy to maintain, sufficient for technical docs, good SEO. Can migrate later if needed.

**Consequences:** ✅ Free, fast; ❌ Less branding/customization than paid options; but works for now.

**Revisit:** When docs grow > 100 pages or need advanced search/versioning.

---

### DECISION-007: Community Platform — Discord only (no Slack/Telegram)

**Date:** 2026-04-26  
**Context:** Community options: Discord, Slack, Telegram, Discourse.

**Decision:** Discord primary + GitHub Discussions secondary.  
**Rationale:** Discord is where dev communities gather (open-source projects). Threads, voice channels, bot integrations. Free. Accessible. Familiar.

**Consequences:** Need moderation plan; Discord's UX can be noisy; but reach > alternatives.

**Revisit:** If user base skews heavily enterprise (non-dev), consider adding LinkedIn group or Forum later.

---

### DECISION-008: Launch Timing — When Webapp usable (not perfect)

**Date:** 2026-04-26  
**Context:** Wait for full Phase 1 roadmap (8 weeks of polish) OR launch when core flows work (inbox, threads, status) but some polish missing?

**Decision:** Launch when `/inboxes` and `/approvals` are real (not skeleton), status feature shipped, mobile CSS decent — but not pixel-perfect.  
**Rationale:** Perfect is the enemy of good. Need real user feedback earlier. Core value can be demonstrated without full polish.

**Consequences:** Some UX warts visible at launch; but faster feedback loop; stronger "we're iterating with you" narrative.

**Revisit:** Before public launch gate checklist must be met (see MARKETING-PLAN.md).

---

### DECISION-009: Metrics Hierarchy — Growth → Engagement → Ecosystem

**Date:** 2026-04-26  
**Context:** What metrics matter most? Options: vanity (stars), engagement (DAU), ecosystem (integrations), revenue.

**Decision:** Tiered: (1) Growth metrics (stars, waitlist, Discord) as leading indicators; (2) Engagement metrics (DAU, messages sent) as validation; (3) Ecosystem metrics (integrations, projects) as long-term health.  
**Rationale:** Early stage: growth signals awareness. Mid-stage: engagement signals product-market fit. Late-stage: ecosystem signals defensibility.

**Consequences:** Track all three, but weight in reviews: Growth (40%), Engagement (40%), Ecosystem (20%) for first 6 months.

**Revisit:** After 6 months, rebalance based on actual progress.

---

### DECISION-010: Social Post Cadence — 3–5 tweets/week, no daily

**Date:** 2026-04-26  
**Context:** How often to post Twitter? Daily? Weekly? Multiple per day?

**Decision:** 3–5 high-quality posts per week (threads, demos, news, spotlights). No daily just to post. Quality over quantity.  
**Rationale:** Developer audience tuned to signal-to-noise ratio. Overposting risks unfollows. Each post should have clear value (insight, demo, news).

**Consequences:** Lower volume but higher engagement per post; slower accumulation of followers but more loyal; more time per post for polish.

**Revisit:** If growth < 100 followers/month after 3 months, experiment with daily lighter content (memes, questions).

---

## Archived Decisions

*(None yet — this log starts fresh.)*

---

## Decision Template (for future use)

```
### DECISION-NNN: [Title]

**Date:** YYYY-MM-DD  
**Context:** [What are we deciding about]  
**Options considered:**
1. [Option A]
2. [Option B]
3. [Option C]

**Decision:** [What we chose]  
**Rationale:** [Why]

**Consequences:**
✅ [positive outcomes]
⚠️ [risks / trade-offs]

**Revisit:** [Trigger condition or date]
```

---

**Usage:**  
Add new decisions chronologically at TOP of "Active Decisions" section. Move to "Archived" only if superseded or closed.

---

## Active Decisions (continued)

### DECISION-007: Position Security as Primary Enterprise Moat

**Date:** 2026-04-27
**Context:** MCP disclosed systemic RCE vulnerability (Apr 2026) affecting 200K+ servers. Enterprise buyers now security-conscious. Agent Messenger's E2E encryption is a differentiating weapon, not just a feature.

**Decision:** Lead all enterprise-facing content with security differentiation. Create dedicated security comparison materials (FAQ, whitepaper, battle cards). Position as "secure coordination layer for regulated industries."

**Rationale:** Security is now a procurement requirement (SOC2, GDPR, NIST AI RMF). MCP's documented vulnerability creates immediate contrast. Our client-side E2E design eliminates server-side attack surface. This is a time-sensitive competitive advantage.

**Consequences:** ✅ Clear differentiation in crowded market; ✅ Justifies premium pricing; ❌ Requires third-party audit to fully capitalize.

**Revisit:** After third-party security audit completed (target Aug 2026).

---

### DECISION-008: Adopt Production-Readiness as Primary Hackathon Metric

**Date:** 2026-04-27
**Context:** ETH Prague 2026 emphasizes "real-world impact" and "sustainability." Original prize structure ($3K for demos) attracts toy projects, not production integrations.

**Decision:** Redesign ETH Prague track to prioritize production-readiness (30% weight), real-world impact (30%), and privacy/ethics (20%). Require public deployment (not just GitHub) for eligibility. Increase prize pool to $5K.

**Rationale:** Aligns with ETHPrague "Future Society" values. Attracts serious teams building deployable agent infrastructure. Generates production-ready integrations, not demos. Creates case studies with deployment metrics.

**Consequences:** ✅ Higher-quality submissions; ✅ Better post-hackathon adoption; ❌ Higher bar may reduce participation (offset by larger prize pool).

**Revisit:** After ETH Prague 2026; assess submission quality and adjust rubric for future events.

---

### DECISION-009: Elevate Sokosumi to Tier 1a Partnership Target

**Date:** 2026-04-27
**Context:** Sokosumi is a Masumi Network product in same ecosystem. Agent Messenger provides the missing communication layer for Sokosumi's agentic coworker marketplace. Integration is co-dependent (both products gain value).

**Decision:** Treat Sokosumi as a **co-dependent product** rather than simple partner. Create joint integration plan with shared roadmap. Position as "Agent Messenger + Sokosumi" combined solution for EU agent workforce.

**Rationale:** Sokosumi already has 500+ enterprises, GDPR compliance, EU AI Act alignment. Agent Messenger provides the conversational layer Sokosumi lacks. Joint go-to-market creates immediate beachhead in EU marketplace segment.

**Consequences:** ✅ Immediate production deployment; ✅ Enterprise credibility through Sokosumi brand; ❌ Tight coupling to single product requires close coordination.

**Revisit:** Q4 2026 — assess whether partnership model should expand to other marketplaces (not just Sokosumi).

---

### DECISION-010: Aggressive GitHub Stars Target (5K by Day 30)

**Date:** 2026-04-27
**Context:** Developer mindshare follows visible adoption. Hermes grew 9,500 stars/week without marketing. Agent Messenger at 0 stars pre-launch faces vicious cycle: no stars → no social proof → no adoption.

**Decision:** Target 500 stars Day 1, 2,000 stars Day 7, **5,000 stars Day 30**, 15,000 stars Day 90. Pre-seed stars from beta program (require GitHub star to join). Merge Hermes PR on Day 2 (not Day 7) to show momentum.

**Rationale:** Stars are proxy for mindshare. Framework maintainers won't integrate zero-star projects. Press coverage requires "big numbers." Stretch but achievable given broader market need (every multi-agent system needs messaging vs single-agent framework like Hermes).

**Consequences:** ✅ Accelerates adoption flywheel; ✅ Attracts framework attention early; ❌ Requires aggressive promotion cadence; ⚠️ Risk of star inflation without corresponding active users.

**Revisit:** Weekly review during launch month. If Day 7 < 1,000 stars, amplify Twitter outreach and consider small paid promotion budget.

---

### DECISION-011: Create "State of Agent Messaging 2026" Competitive Analysis

**Date:** 2026-04-27
**Context:** Spec-stage projects (ADMP, UAM, OpenFused, AIRC) muddy category definition despite zero production adoption. Need clear, evidence-based positioning as "only production-ready agent social layer."

**Decision:** Publish a comprehensive comparison blog post and data sheet quantifying: stars, production users, features (E2E encryption, webapp, human approvals, framework integration, production deployments). Update all marketing copy to frame competitors as "spec-stage" vs Agent Messenger's "production product."

**Rationale:** Enterprise buyers need clear differentiators in early markets. Competing specs create FUD ("which standard will win?"). Hard evidence (production numbers, features, integrations) cuts through noise.

**Consequences:** ✅ Positions Agent Messenger as category leader; ✅ Creates reusable sales collateral; ❌ Requires continuous monitoring as competitors evolve.

**Revisit:** Quarterly or when new protocol announces production deployment.

---

**Last updated:** 2026-04-27
**Next review:** 2026-05-04
