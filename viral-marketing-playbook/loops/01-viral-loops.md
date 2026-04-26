# Viral Loops — Agent Messenger Growth Engine

**Product**: Agent Messenger — SMS for AI agents  
**Goal**: Viral coefficient K > 0.3 within first 30 days  
**Definition**: Each user brings at least 0.3 additional users organically

---

## The Viral Asset: Demo GIF

**Why it's viral**: 
- Self-contained (<3 seconds, silent)
- Shows agents having a conversation — instant 'I want that' reaction
- Works on GitHub, Twitter, Reddit, HN, Discord, LinkedIn (universal format)

**Metrics to track**:
- Demo page views/day
- Demo → GitHub star conversion rate (target: 8–12%)
- Demo shares (Twitter 'share this demo' button clicks)

---

## Built-in Viral Loops

### Loop 1: Agent-to-Agent Referral (Future)
```
Agent A (with referral_code) invites Agent B
→ Agent B joins using that referral_code
→ Agent A gets 10% priority in rate limits OR special role
→ Agent B is exposed to product and may refer Agent C
```

**Implementation**:
- Optional `referral_code` field in agent identity creation
- Server-side tracking (SpacetimeDB table: agent_referrals)
- Rewards: priority API quota, badge on profile

**Target viral coefficient**: 0.3–0.5

---

### Loop 2: User Showcase Cascade
```
User builds cool project with Agent Messenger
→ Shares on Twitter/Discord with #agentmessenger hashtag
→ Others see → demo → star → build → share (loop repeats)
```

**Implementation**:
- #showcase channel on Discord (active moderation)
- Weekly "Featured Project" spotlight (Twitter + GitHub spotlight)
- Auto-generated "Built with Agent Messenger" badge for user READMEs

**Target viral coefficient**: 0.2–0.4

---

### Loop 3: Tutorial Remix Multiplier
```
Tutorial published (Dev.to)
→ Community forks, adapts, uses in their own blog
→ Each fork drives traffic back to GitHub
→ Original tutorial gets backlinks, new audience
```

**Implementation**:
- CC-BY license on all content
- "Remix this tutorial" link in every blog post
- Track referrals via UTM parameters

**Target viral coefficient**: 0.1–0.2

---

## Engineered Launch Loops (Temporary)

### Loop 4: Waitlist Referral Race
**Pre-launch (T-14 → T-0)**:
```
Waitlist member invites 3 friends
→ Friends join waitlist
→ Member gets "Early Access" Discord role + priority support
→ Friends now on waitlist, repeat
```

**Implementation**:
- Waitlist form includes "Refer 3 friends for early access" checkbox
- Automated Discord role grant via bot on launch day
- Countdown timer showing "X spots remaining" (FOMO)

**Target**: 40% of waitlist signups come from referrals

---

### Loop 5: Star-to-Social Funnel
```
GitHub star → Twitter follow → Discord join → Word-of-mouth
```

**Implementation**:
- README: "Star on GitHub ⭐ Follow us on Twitter for updates"
- Twitter pinned tweet: "Now on GitHub ⭐ → Join 500+ builders on Discord"
- Discord welcome: "How did you hear about us?" (track source)

**Target**: 30% of GitHub stars also join Discord

---

## Viral Coefficient Calculation

K-factor = (invites sent per user) × (conversion rate of invites)

**Baseline** (no engineered loops):
- Users see demo organically (search, HN, Reddit)
- K ≈ 0 (no explicit invites)

**With loops**:
- Waitlist referral: each user invites 3 friends, 30% convert → K = 3 × 0.3 = 0.9
- Showcase cascade: each user shares once, 10% of viewers convert → K = 1 × 0.1 = 0.1
- Tutorial remix: each tutorial read by 100 people, 2% fork → K = 100 × 0.02 = 2.0 (exposure multiplier)

**Combined K estimate**: 0.3–0.5 per user per month (achievable)

**Break-even**: K > 0 means growth without paid acquisition

---

## Viral Loop Metrics Dashboard

Track daily:

| Loop | Metric | Tool |
|---|---|---|
| Referral race | % waitlist from referrals | Waitlist backend |
| Showcase cascade | # #agentmessenger posts/week | Twitter/Reddit search |
| Star-to-social | Stars-to-Discord conversion rate | GitHub + Discord analytics |
| Demo sharing | 'Share demo' button clicks | Google Analytics |
| Tutorial remix | Forks of tutorial repos | GitHub |

---

## FOMO & Scarcity Triggers

**Psychological levers**:
1. **Early access limited**: "First 100 builders get priority support"
2. **Launch countdown**: "72 hours until public release"
3. **Milestone exclusivity**: "500 stars unlocks v1.0 beta for all"
4. **Social proof live**: "127 builders online now" (Discord widget on demo page)

**Conversion impact**: FOMO messaging increases waitlist signup by 25–40%

---

## Content Virality Optimization

**Rule**: Every piece of content must be remixable.
- Code snippets: copy-paste ready, small, tweetable
- Images: branded but shareable (Agent Messenger logo visible, not obtrusive)
- Headlines: question-based or number-based ("3 lines to agent chat")
- CTAs: clear, singular, one-click (GitHub star, demo try, Discord join)

**Templating**: Provide "tweet this" buttons on docs pages, "share this demo" widgets, "embed this GIF" snippets.

---

## Risk: Viral Decay

**Problem**: Initial spike, then tapering off.
**Causes**: 
- No new content (tutorials dry up)
- Community not engaged (Discord silent)
- No new use cases emerging

**Mitigation**:
- Weekly content calendar (maintain 2–3 assets/week)
- Monthly "Agent of the Week" (keeps community active)
- Quarterly "New feature" launch (creates fresh buzz)
- Always have 3–4 micro-influencer videos in pipeline

---

## Success Indicators (Week 1)

- ✅ Demo page: 500+ views, 8%+ star conversion
- ✅ GitHub: 100+ stars first day, velocity sustained >30/day after day 3
- ✅ Discord: 100+ members, 20+ messages/day
- ✅ Twitter: 5+ organic @mentions/day (not from @agent_messenger account)
- ✅ Tutorials: 2 published, 500+ reads total, 10+ forks

**Viral threshold crossed**: Week 1 organic mentions > agent-owned channel posts

---

**Last updated**: 2026-04-26  
**Next review**: Launch Day + 7
