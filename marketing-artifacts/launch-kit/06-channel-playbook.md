# Channel Playbook — Agent Messenger Marketing

**Product**: Agent Messenger  
**Audience**: AI agent developers, hackathon teams, enterprise bot builders  
**Tone**: Helpful, technical, concise, no hype

---

## GitHub (Primary Channel)

### Strategy
GitHub is the home base. Developers discover projects here, star for later, read docs. Treat README as your landing page.

### Tactics
| Tactic | Details | Frequency |
|--------|---------|-----------|
| README as landing page | Hero GIF + 1-sentence pitch + 5-step quickstart + explicit star CTA | Update per release |
| Issue response SLA | <24 hours for all issues; <2 hours during launch week | Ongoing |
| New release cadence | Semantic versioning; v0.x → v1.0 after 3 months | Every 2–4 weeks |
| Awesome list submissions | Submit to `awesome-ai-agents`, `awesome-messaging`, `awesome-crypto` | Once per list |
| GitHub Sponsors | Add sponsorships button once ≥500 stars | Month 2+ |

### Content Hierarchy (README)
1. Hero section (GIF + tagline + star button)
2. Problem statement (2–3 sentences: "Your agents can't chat")
3. Quickstart (copy-paste code, 5 min to working demo)
4. Features (bullet list with icons)
5. When to use vs alternatives (MCP/A2A comparison table)
6. Examples folder links
7. Badges (build status, license, stars)
8. Contributing + Code of Conduct links

### Metrics
- Stars/day velocity (baseline 30–50; launch target 100+)
- Traffic sources (GitHub Insights → referrers)
- Clone/download counts
- Issues opened/closed ratio

---

## Reddit (Discovery Engine)

### Strategy
Reddit drives discovery via subreddit communities. Must be genuine participant first — no shilling.

### Target Subreddits (priority order)
1. r/LocalLLaMA — highest relevance (local LLM agents)
2. r/MachineLearning — general ML audience
3. r/programming — broad developer audience
4. r/artificial — AI-focused (broader than ML)
5. r/selfhosted — if self-hosting angle emphasized

### Posting Rules
- Karma requirement: >80 comment karma before posting in target subs
- Account age: >1 week (to avoid spam filters)
- Post title format: Clear, descriptive, not clickbait
- Body: 3–5 paragraphs; include problem, solution, demo link, GitHub link
- Engage every comment (within 1 hour initially)

### Post Templates

**r/LocalLLaMA**:
```
Title: Agent Messenger — let your local LLM agents text each other

Building multi-agent systems with local LLMs? Need a way for agents to notify each other without blocking?

Agent Messenger is an open protocol + reference implementation. Every agent gets an address. Send encrypted messages between agents. Works with any framework — LangChain, CrewAI, or your own.

Key features:
- E2E encrypted by default
- Persistent message threads
- 50-line integration
- SpacetimeDB backend (no servers)

Demo: [link]
GitHub: [link]

Happy to answer questions!
```

**r/programming**:
```
Title: Open-source: Agent messaging protocol for multi-agent systems

Problem: Multi-agent systems lack a standard communication layer. A2A handles tasks, MCP handles tools, but no protocol handles sideband messaging ("hey, I'm busy", "customer responded").

Solution: Agent Messenger — an open protocol that gives each agent a phone number. Use alongside MCP + A2A.

GitHub: [link]
Demo: [link]

Built with SpacetimeDB. 50 lines to integrate. Looking for early adopters.
```

### Timing
- Best posting times: Weekdays 9–11 AM PST (peak Reddit traffic)
- Avoid: Friday afternoons, weekends, major holidays
- Cross-posting strategy: Wait 2–3 hours between subreddit posts (to avoid cross-post shadowban)

### Metrics
- Post upvote score (target: 50+ for visibility)
- Comment count (target: 10+ engaged comments)
- Traffic to GitHub from Reddit (GitHub referrer tracking)

---

## Hacker News (High-Impact Visibility)

### Strategy
HN front page drives massive traffic. Technical audience, skeptical but curious. Lead with problem, not product.

### Post Format
```
Title: Show HN: Agent Messenger — SMS for AI agents

Body:

We've open-sourced Agent Messenger, a protocol for agent-to-agent communication.

Problem:
No standard way for agents to exchange messages outside task delegation (A2A) or tool calls (MCP). Building custom message queues per agent is tedious.

Solution:
Every agent gets an address. Send encrypted messages to any other agent. Persistent threads. Simple as SMS.

Tech:
- SpacetimeDB backend (distributed, pubsub)
- Python + TypeScript SDKs
- 50-line integration

Demo: [link]
GitHub: [link]
Docs: [link]

We're looking for early adopters and feedback.

AMA!
```

### Timing
- Submit at 6–9 AM PST (early morning gets more initial upvotes)
- Day of week: Tuesday–Thursday best (avoid Monday/Friday)
- Repeat post allowed after 2 weeks if first attempt didn't front-page

### Engagement Tactics
- Top comment: Pin a reply explaining "Why this matters" (context: MCP/A2A landscape)
- Reply to every comment within 15 minutes for first hour (algorithm favors early engagement)
- Address skepticism head-on: "Yes, another protocol, but here's why this gap exists"
- Link to live demo in every response (if question is technical)

### Risks
- HN audience skeptical of "AI hype" projects
- Be prepared for tough technical questions (scalability, security, SpacetimeDB details)
- Have answers ready for "why not just use Redis?" and "how is this different from Matrix?"

### Metrics
- Front page position (target: top 10, ideally top 5)
- Points (target: 100+)
- Comments count (target: 50+)
- Referral traffic to GitHub (via UTM parameters)

---

## Twitter/X (Ongoing Engagement)

### Strategy
Twitter drives real-time conversation, announcements, and network effects. Use for launch velocity and ongoing community building.

### Post Cadence
- Daily during launch week (1–2 tweets/day)
- 3–5 tweets/week post-launch (tutorials, updates, community spotlights)
- Thread format for detailed explanations (8–12 tweet threads)

### Content Types
| Type | Frequency | Example |
|---|---|---|
| Product announcements | Launch day + major releases | "v0.1.0 is live! …" |
| Tutorial snippets | 2/week | "3 lines to send your first agent message:" + code |
| Community spotlights | 1/week | "Check out @user's bot using Agent Messenger for X" |
| Comparison/education | 1/week | "MCP vs A2A vs Agent Messenger: when to use which?" |
| Metrics updates | Milestone-based | "500 stars! Thank you!" |

### Hashtags
- Primary: #AI, #LLM, #LangChain, #CrewAI, #AutoGen
- Secondary: #MachineLearning, #Python, #TypeScript, #OpenSource
- Event-specific: #ETHGlobal, #Hackathon, #Devfolio
- Avoid overposting same hashtag (limit 2–3 per tweet)

### Engagement Strategy
- Reply to all mentions within 2 hours
- Like + retweet community posts using #agent-messenger
- Tag relevant accounts: @LangChainAI, @CrewAIInc, @AnthropicAI (if relevant)
- Use Twitter Spaces (optional): 30-min community call during launch week

### Metrics
- Impressions (target launch week: 5K+ per day)
- Engagements (likes + retweets + replies)
- Link clicks (to GitHub, demo)
- Follower growth (target: 100+ followers/week during launch)

---

## Discord (Community Hub)

### Strategy
Discord is where users get real-time help, share projects, and build community. Own this channel long-term.

### Server Structure
```
agent-messenger/
├── 📢-announcements          (read-only, launch updates)
├── 👋-welcome                (new members intro)
├── 💬-general                (general chat)
├── 🆘-help                   (support questions)
├── 💡-showcase               (user projects)
├── 🎥-demo-sharing           (demo videos, GIFs)
├── 🔧-integration-help       (LangChain/CrewAI specific)
├── 🎉-giveaways              (optional, swag later)
├── 🎓-office-hours           (scheduled AMA sessions)
└── 🛠-development            (for contributors)
```

### Onboarding Flow
1. New member joins → auto-DM with:
   - Welcome message
   - Quickstart guide link
   - Discord rules (pinned)
   - Link to #get-started channel
2. #welcome channel: "Say hi and what you're building"
3. #get-started channel: pinned resources (docs, examples, FAQ)

### Activity Targets
- Launch week: 5+ messages/day across channels (from team)
- Ongoing: 20+ messages/day community-driven (organic)
- Response time: <2 hours for #help questions
- Office hours: Weekly 4–6 PM PST voice/chat session

### Community Building
- Spotlight users weekly in #announcements
- Create "Agent of the Week" showcase
- Run AMA sessions with core maintainers
- Award roles for contributions (Contributor, Moderator)

### Metrics
- Member count (target: 300 by month 1, 500 by month 3)
- Message volume (target: 50+/day active)
- Response time SLA (target: <2 hours for help channel)
- User-generated content (#showcase posts)

---

## Dev.to / Hashnode (Technical Content)

### Strategy
Developer platforms have built-in audiences and SEO. Long-tail traffic driver.

### Posting Rules
- Canonical URL to own blog first (if you have blog), then cross-post
- Tag strategically: #python, #typescript, #ai, #agents, #llm, #langchain, #crewai, #opensource
- Engage with commenters (reply within 24h)
- Cross-post same content to both platforms (canonical on one, syndicated on other)

### Post Types
1. **Tutorials** (highest engagement): Step-by-step, copy-paste code, real use case
2. **Technical deep-dives**: Architecture decisions, tradeoffs, lessons learned
3. **Comparisons**: Bottom-of-funnel, developers deciding between solutions
4. **Behind-the-scenes**: Building-in-public stories (what worked, what failed)

### Best Practices
- Title format: "How to Build X with Agent Messenger in Y Minutes"
- Code blocks with syntax highlighting (use triple backticks)
- Screenshots/diagrams inline (max 2–3 per post)
- Call-to-action: "GitHub → try it and share what you build"
- Length: 1.5K–3K words for tutorials, 800–1.5K for comparisons

### Distribution
- Publish on Tuesday/Wednesday mornings (optimal engagement)
- Share on Twitter/X, Reddit (if relevant), Hacker News (if novel)
- Pin to own profile
- Add to series if multi-part

### Metrics
- Reads (target: 1K reads for first tutorial, 5K+ for subsequent ones)
- Reactions (💖, 🔖)
- Comments (target: 5+ per post)
- Referral traffic to GitHub (track with UTM)

---

## YouTube (Video Deep-Dives)

### Strategy
Video for complex integrations + personal connection. Partner with micro-influencers for reach.

### Content Formats
| Format | Length | Frequency | Owner |
|---|---|---|---|
| Quickstart walkthrough | 5 min | Launch week | Self |
| Integration tutorial | 10–15 min | Month 1–3 | Micro-influencer |
| Live coding session | 30–60 min | Month 2+ | Self or guest |
| Comparison review | 8–12 min | Month 3 | Influencer |
| Community showcase | 3–5 min | Ongoing | Community |

### Influencer Partnership Model
- Offer **revenue share** (not flat fee) — aligns long-term incentives
- Target: 5K–50K subscriber channels in AI/agent space
- Provide: Early access, integration template, talking points
- Deliverable: Authentic usage, not script reading

### Optimization
- Title: "Build [Use Case] with Agent Messenger" (search-oriented)
- Thumbnail: High-contrast, readable text, agent icon + code snippet
- Description: First 2 lines critical — include key value + GitHub link
- Tags: #AI, #agents, #langchain, #crewai, #python, #typescript
- Cards: Link to GitHub, demo, docs

### Metrics
- Views (target: 5K views within 30 days)
- Watch time (target: 50% retention at 30 sec)
- Click-through rate on description links (target: 2%+)
- Subscriber conversion (from video to channel sub)

---

## LinkedIn (Enterprise Angle)

### Strategy
Enterprise bot teams, engineering leadership, B2B buyers. Posts more polished, business-focused.

### Post Types
1. **Problem/solution case studies** (enterprise use case, ROI)
2. **Thought leadership** (multi-agent architecture trends)
3. **Team/company updates** (milestones, hiring)
4. **Community wins** (user case studies with logos)

### Frequency
- 2–3 posts/week
- Weekday mornings (8–10 AM PST) optimal

### Content Angles
- "Why your agent system needs a coordination layer"
- "Production checklist for multi-agent deployments"
- "How [Company] reduced escalations by 40% with agent messaging"

### Hashtags
#AI, #LLM, #EnterpriseAI, #Automation, #DevOps, #SRE

### Metrics
- Impressions (target: 5K/post)
- Engagement (likes + comments, target: 50+)
- Inquiries via LinkedIn (track via CRM)

---

## Hackathon Circuit (ETHGlobal, Devfolio)

### Strategy
Hackathon teams build with your tool → demo at event → social proof + prize eligibility.

### Tactic Checklist
- [ ] **Devfolio bounty**: "Best Agent Messenger Integration" ($2K–$5K pool)
- [ ] **ETHGlobal Discord**: Dedicated channel for questions
- [ ] **Opening ceremony demo**: 5-minute presentation, visual agents chatting
- [ ] **Starter kit**: Hardhat + Agent Messenger template repo
- [ ] **Office hours**: Weekly Discord sessions during hackathon
- [ ] **Judging criteria**: Documentation, creativity, real-world applicability
- [ ] **Prize ceremony**: Announce winners, showcase demos

### Hackathon Timeline
- **T-30 days**: Bounty published, starter kit released
- **T-14 days**: Opening ceremony presentation slot confirmed
- **T-7 days**: Discord channel created, office hours schedule announced
- **Event week**: Live office hours, rapid response to questions
- **T+1 day**: Winner announcement blog post

### Hackathon-specific Content
- Blog: "Building your first agent coordination bot in 2 hours"
- Video: "Hackathon tip: Agent Messenger for team coordination"
- Tutorial: "ETHGlobal London 2026 submission template"

---

## Email Newsletter (Optional, Month 2+)

### Strategy
Monthly digest for engaged users. Builds long-term relationship.

### Content
- Product updates (new releases, features)
- Community highlights (user projects, GitHub stars milestone)
- Tutorial roundup
- Upcoming events (hackathons, AMAs)

### Frequency
- Monthly (first Tuesday of month)
- 300–500 words

### Platform
- ConvertKit or Revue (simple, integrates with waitlist)

### Metrics
- Open rate (target: 30%+)
- Click rate (target: 5%+)
- Unsubscribe rate (target: <2%)

---

## Channel Prioritization (Resource-Constrained)

If solo founder / limited time, focus on:

**Week 1–2**: GitHub + Reddit + HN (launch velocity)  
**Week 3–4**: Discord (community) + Dev.to (tutorial) + Twitter (ongoing)  
**Month 2+**: YouTube (influencer), Hackathon circuit, LinkedIn (enterprise)

**Do not** spread across all channels simultaneously. Master 2–3 at a time.

---

## Common Pitfalls

| Pitfall | Consequence | Fix |
|---|---|---|
| Posting in Reddit without karma | Shadowbanned, post removed | Build karma first by helping others |
| Ignoring GitHub issues | Reputation for unresponsiveness | SLA <24h; canned responses for common issues |
| Over-promising | User disappointment, churn | Under-promise, over-deliver |
| Inconsistent cadence | Community loses interest | Content calendar, batch-create content |
| No CTA | Traffic without conversion | Every asset ends with star/waitlist/join Discord CTA |

---

## Channel Success Metrics Dashboard

| Channel | Leading Metric | Target (Month 1) | Target (Month 3) |
|---|---|---|---|
| GitHub | Stars/day | 30–50 baseline, 100+ launch | 50–100 sustained |
| Reddit | Post upvotes | 50+ per post | 100+ per post |
| HN | Front page position | Top 20 | Top 10 |
| Discord | Members | 300 | 500 |
| Dev.to | Reads/post | 1K | 5K |
| Twitter | Engagements/tweet | 50 | 200 |
| YouTube | Views/video | 1K | 10K |

---

## Conclusion

Focus on **quality over quantity**. One great GitHub README + one viral Reddit/HN post + one high-quality tutorial beats 10 mediocre assets.

Ensure every channel funnels to:
1. GitHub star (primary)
2. Discord join (community)
3. Waitlist signup (enterprise pipeline)

Track metrics daily during launch week, then weekly. Iterate content based on what resonates.

---

**Last updated**: 2026-04-26  
**Next review**: Post-launch (Day 7)
