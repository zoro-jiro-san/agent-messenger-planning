# Viral Launch Sequence — Agent Messenger

**Objective**: Trigger algorithmic amplification across platforms in 48h window  
**Success**: 1K GitHub stars, 300 Discord members, demo → star conversion >10%

---

## Timeline Overview (Hour-by-Hour)

```
T-14 days:  Waitlist live (100+ emails collected)
T-7 days:  Demo hosted, GIF final, README ready
T-2 days:  Influencer alerts sent (early access granted)
T=0:       GitHub release + Show HN + Reddit
T+12h:    Twitter launch thread + Discord seeding
T+24h:    Product Hunt launch + waitlist blast
T+36h:    Update 1 (PH) + milestone tweet (500 stars)
T+48h:    Update 2 (PH) + showcase thread + tutorial Teaser
T+72h:    Week 1 recap blog
```

---

## Phase 0: Pre-Launch (T-14 → T-2) — Build the Tinderbox

### Week T-14 → T-10: Foundation
- [ ] Set up waitlist (Paperform/Notion) — embed on placeholder site
- [ ] Create Discord server (channels: #announcements, #get-started, #showcase, #help)
- [ ] Twitter/X account: post 5–10 tweets, follow 100 AI agent devs, get 200+ followers
- [ ] Join Reddit: r/LocalLLaMA, r/programming, r/MachineLearning — start commenting (build karma to 80+)
- [ ] Join LangChain, CrewAI, Hugging Face Discord — answer questions (be helpful)

### Week T-9 → T-7: Content & Assets
- [ ] Finalize demo GIF (3 sec loop, <3MB)
- [ ] Host interactive demo on Vercel/Railway (one-click send message)
- [ ] Add demo → GitHub star → Discord join funnel on demo page
- [ ] Write GitHub README (hero GIF, problem/solution, 5-min quickstart)
- [ ] Draft 3–5 Twitter threads (launch day scheduled)
- [ ] Draft Reddit/HN posts (review by 1–2 beta testers)
- [ ] Prepare Product Hunt listing draft (assets ready, but not live yet)

### Week T-6 → T-2: Warm-up & Coordination
- [ ] Identify 5–10 micro-influencers (5K–50K subs in AI/agent space)
- [ ] DM them: "Early access to Agent Messenger — try it, honest feedback appreciated" (no payment yet)
- [ ] Post 2–3 teaser tweets: "Building something for AI agents to talk to each other" with GIF
- [ ] Waitlist: promote on Twitter (pin tweet), LinkedIn, relevant Discord #promo channels (where allowed)
- [ ] Waitlist goal: 100+ emails by T-2

### Day T-2: Final Countdown
- [ ] Confirm GitHub tag v0.1.0 is ready, CI passing
- [ ] Pre-schedule GitHub release for 12:01 AM PST launch day
- [ ] Prepare real-time response team (you alone, or 1–2 friends on standby)
- [ ] Set up monitoring: GitHub notifications on, Discord bot for @mentions, Twitter alerts
- [ ] Draft canned responses for common Qs: "How is this different from MCP?", "Is this production-ready?", "Why SpacetimeDB?"

---

## Launch Day (T=0) — Coordinated Blast

### 00:00 — GitHub Release (Primary Hub)
**Action**: Push v0.1.0 tag, create release, README live with hero GIF + star CTA

**Checklist**:
- [ ] Release title: "Agent Messenger v0.1.0 — SMS for AI agents"
- [ ] Release notes: What's new, install instructions, quickstart code (copy-paste), known limitations
- [ ] GitHub description updated with demo link
- [ ] Enable Discussions (optional)
- [ ] Tweet immediately: "We just released Agent Messenger v0.1.0 — GitHub ⭐ [link] Demo: [link]"

**Expected**: 10–20 stars in first 15 minutes

---

### 00:05 — Hacker News (Technical Credibility)
**Action**: Post Show HN

**Title**: `Show HN: Agent Messenger — SMS for AI agents`

**Body** (copy from content bank, customized):
```
We've open-sourced Agent Messenger, a protocol + reference implementation for agent-to-agent communication.

Problem: No standard way for agents to exchange messages outside task delegation (A2A) or tool calls (MCP). Building custom message queues per agent is tedious.

Solution: Every agent gets an address. Send encrypted messages to any other agent. Persistent threads. Simple as SMS.

Tech: SpacetimeDB (distributed, pubsub), Python + TypeScript SDKs, 50-line integration.

Demo: [link]
GitHub: [link]
Docs: [link]

We're looking for early adopters and feedback. AMA!
```

**Post-launch**:
- [ ] Pin top comment with context: triple-stack positioning
- [ ] Reply to every comment within 15 minutes (first hour critical)
- [ ] Answer technical questions thoroughly
- [ ] Link to demo in every relevant response

**Expected**: Front page if >50 upvotes in first hour; traffic spike 500–2K visitors

---

### 00:30 — Reddit r/programming (Discovery Engine)
**Action**: Post

**Title**: Open-source: Agent messaging protocol for multi-agent systems

**Body** (copy from content bank)

**After posting**:
- [ ] Reply to first comment within 5 minutes
- [ ] Engage with upvoters who ask questions
- [ ] Do NOT edit title or delete/repost (will trigger spam filter)

**Expected**: 50–100 upvotes, 10+ comments, 200–500 GitHub referrals

---

### 01:00 — Reddit r/LocalLLaMA (High-Relevance)
**Action**: Post (same template, slightly adapted)

**Title**: Agent Messenger — let your LLM agents text each other

**Key difference**: More emphasis on local LLM + LangChain/CrewAI integrations

---

### 06:00 — Twitter/X Launch Thread (Network Amplification)
**Action**: Publish 10-tweet thread

**Thread** (copy from content bank — Thread 1)

**Schedule**:
- [ ] Tweet 1 at 6:00 AM PST (target: 8–10 AM PST engagement window)
- [ ] Replies/replies within 1 hour
- [ ] Quote-tweet early supporters ( HN/Reddit commenters who tweet)
- [ ] Pin thread to profile

**Expected**: 1K+ impressions, 50+ engagements, 20–30 GitHub star referrals

---

### 06:30 — Discord Seeding
**Action**: Share in #show-and-tell channels

**Channels**:
- [ ] LangChain Discord
- [ ] CrewAI Discord  
- [ ] Hugging Face Discord
- [ ] Own Discord (announcements channel)

**Post template**:
```
Hey team — built Agent Messenger, an open protocol for agent-to-agent communication. GitHub: [link] Demo: [link] 

Feedback welcome! (Also looking for early adopters)
```

**Follow-up**:
- [ ] Answer questions in-channel
- [ ] Offer 1:1 onboarding calls to interested devs
- [ ] Pin demo link in Discord

**Expected**: 20–50 new Discord members Day 0

---

## Day 1 (T+24h) — Momentum Maintenance

### 00:00 — Waitlist Email Blast
**Action**: Email all waitlist signups

**Subject**: "Agent Messenger is live — your agents can now text each other"

**Body** (from launch kit templates):
- GitHub link (primary CTA)
- Demo link (secondary)
- Discord invite (community)
- "You were on our waitlist — early access thanks!"

**Expected**: 30–50 email opens, 10–20 GitHub clicks

---

### 00:30 — Comment Monitoring Sprint
**SLA**: All GitHub issues (<2h), HN comments (<15m), Reddit threads (<1h), Twitter mentions (<2h)

**Response strategy**:
- Technical questions: detailed answers with code snippets
- Praise: thank + ask for feedback
- Criticism: acknowledge + promise to improve
- "Is this production-ready?": "v0.1.0 is early but functional; v1.0 stable in 2 months with audit logging"

---

### 12:00 — Milestone Tweet
If >100 stars achieved:
```
100+ stars in 12 hours. Thank you! 🙏

Agent Messenger v0.1.0 is live — try the demo and let us know what you build.

GitHub ⭐: [link]
Demo: [link]
```

**Expected**: Engagement spike, secondary shares

---

## Day 2 (T+48h) — Product Hunt (Social Proof Layer)

### 00:00 — Product Hunt Launch
**Action**: Submit at 12:01 AM PST (Monday optimal)

**Listing**:
- Title: "Agent Messenger — SMS for AI agents"
- Tagline: "Give every AI agent a phone number. Open-source protocol for agent-to-agent messaging."
- Thumbnail: GIF demo or high-contrast branded image
- Maker comment: Vulnerable story (from launch kit)

**Launch sequence**:
- [ ] 23:50 — Final check: all assets uploaded, description proofread
- [ ] 00:01 — Click "Publish"
- [ ] 00:02 — Email waitlist: "Now on Product Hunt! Upvote if useful → [link]"
- [ ] 00:03 — Twitter: "We're on Product Hunt today! Early feedback appreciated → [link]"
- [ ] 00:04 — Discord: ping #announcements with PH link

### Hours 0–2 (Critical Velocity Window)
- [ ] Get 20–30 upvotes from friends/early supporters
- [ ] Reply to every comment within 15 minutes (top 3 comments = 50% of ranking algorithm)
- [ ] Post first update (with user testimonial if available)

**Expected**: Top 20 within 6 hours if first-2-hour velocity maintained

### Hours 2–24
- [ ] Post 2 more updates (new features, user quotes, demo stats)
- [ ] Engage commenters personally (no canned responses)
- [ ] Tweet PH link with #ProductHunt + #AI hashtags

**Success metrics**:
- Top 10 ranking
- 300+ upvotes
- 200–400 new GitHub stars from PH traffic

---

## Day 3–7 (Sustaining the Burst)

### Daily Rhythm:
- [ ] Respond to GitHub issues (<24h SLA)
- [ ] Post 1–2 tweets (milestones, use cases, community spotlights)
- [ ] Share in Discord (#showcase, #help engagement)
- [ ] Cross-post content to Reddit if novel angle

### Week 1 Asset Cadence:
- **Day 4**: Dev.to tutorial published ("Build Multi-Agent Support in 50 Lines")
- **Day 5**: Hashnode cross-post of tutorial
- **Day 6**: YouTube short (60-sec demo) — self-published or micro-influencer
- **Day 7**: Week 1 recap blog post + metrics summary

---

## Burst Amplification Checklist

**Before launch**:
- [ ] GitHub repo public and indexed (test search: `site:github.com agent-messenger`)
- [ ] Demo page loads in <2 seconds (GTMetrix test)
- [ ] All links working (GitHub, demo, docs)
- [ ] README has no markdown errors
- [ ] Twitter account verified (blue check optional but helps)

**Launch day real-time monitoring**:
- [ ] GitHub star count (watch for velocity drop → mobilize network)
- [ ] Demo page traffic (Google Analytics realtime)
- [ ] Twitter impressions/engagements
- [ ] Reddit/HN upvote velocity (if <10 upvotes first 30 min → consider re-post?)
- [ ] Discord member count (target 10–20/hour first 6h)

**Post-launch rapid response**:
- If Day 1 stars < 300 → boost Twitter thread with $50 promotion, email waitlist with "help us reach milestone" plea
- If HN post fails to front page → cross-post to r/programming with stronger headline next day
- If PH ranking flat → mobilize 20 friends for coordinated upvote + comment wave

---

## Velocity Targets (Aggressive but Achievable)

| Hour | Stars | Demo Views | Discord |
|------|-------|------------|---------|
| 0–2  | 50    | 200        | 10      |
| 2–6  | 100   | 500        | 30      |
| 6–12 | 150   | 800        | 50      |
| 12–24| 300   | 1.5K       | 100     |
| 24–48| 500   | 2.5K       | 200     |
| 48–72| 750   | 4K         | 300     |

**Total Week 1**: 1K–1.5K stars, 5K demo views, 500 Discord members

---

## Why This Burst Sequence Works

1. **Algorithmic stacking**: GitHub stars boost HN ranking (social proof in comments), HN traffic boosts GitHub stars, Reddit discovery feeds both.
2. **Demo centrality**: Every channel points to zero-friction demo → instant conversion.
3. **Velocity signaling**: Early spike triggers GitHub Trending, HN front page algorithms.
4. **Network effect**: More stars → more visibility → more stars (flywheel).

---

## Post-Burst (Day 4+)

Once velocity peaks:
- Maintain baseline: 30–50 new stars/day (sustained)
- Weekly content: 1 tutorial or blog post
- Monthly milestone tweet (2K, 5K, 10K stars)
- Community showcase (user projects)
- Influencer videos (if partnerships active)

---

**Last updated**: 2026-04-26  
**Review**: Post-launch Day 3 (adjust velocity targets based on actuals)
