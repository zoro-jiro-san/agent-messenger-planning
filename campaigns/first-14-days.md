# Marketing Action Plan — First 14 Days

**Owner:** Marketing lead (or founder until hired)  
**Time budget:** 2–4 hours per day (shared with engineering fixes)  
**Goal:** Prepare for public beta launch (target: ~30 days from now)

---

## Week 1 (Days 1–7): Foundation & Asset Creation

### Day 1–2: Audit & Setup
- [ ] Create `agent-messenger-planning/campaigns/` folder structure (done)
- [ ] Finalize TAGLINE + POSITIONING statement (ready in README)
- [ ] Verify GitHub repo is public + `README.md` polished
- [ ] Claim @agentmessenger Twitter handle (or secure @agent_messenger)
- [ ] Create Discord server: `Agent Messenger` with channels:
  - `#announcements`, `#general`, `#showcase`, `#help`, `#integrations`, `#beta-testers`
- [ ] Draft press kit (see `press/PRESS-KIT.md`)
- [ ] Write boilerplate + key messages + FAQ (done)

### Day 3–4: Visual Assets
- [ ] Logo variants:
  - Hex logo on dark background (PNG 512×512)
  - Hex logo on light background (PNG 512×512)
  - SVG version (scalable)
  - Favicon (16×16, 32×32, 48×48)
- [ ] Product Hunt thumbnail (640×640 PNG): tagline + logo
- [ ] Webapp screenshot (light theme, inbox view)
- [ ] Webapp screenshot (thread view)
- [ ] CLI/TUI screenshot
- [ ] Stack diagram (A2A/MCP/X402 layered with Agent Messenger)
- [ ] Demo video storyboard (2 min)
- [ ] Record rough demo (screen capture + voiceover)
- [ ] Create 15-second teaser clip (for Twitter)

### Day 5–6: Content Drafts
- [ ] Launch blog post draft: "The agent stack is incomplete without messaging"
- [ ] Tutorial draft: "Build your first agent team in 10 minutes"
- [ ] Twitter launch thread (6–8 tweets) + visual assets per tweet
- [ ] Press release one-pager (one-page PDF)
- [ ] Email waitlist template
- [ ] Discord announcement template
- [ ] Hacker News "Show HN" post draft
- [ ] Reddit post draft (r/LocalLLaMA, r/AI_Agents)

### Day 7: Planning & Organization
- [ ] Create Asana/Trello board for marketing tasks
- [ ] Set up Buffer/Hootsuite for scheduled tweets
- [ ] Prepare launch calendar (timeline doc)
- [ ] Identify 3–5 potential press targets (TechCrunch, The Block, Messari, AgentRank)
- [ ] List conference events 2026 (industry conferences, NF Droplets, Solana Breakpoint)
- [ ] Draft outreach email to framework maintainers (Hermes, OpenCode, Claude Code)
- [ ] Create waiting list form (Google Form → Airtable)

---

## Week 2 (Days 8–14): Pre-Launch Activation

### Day 8–9: Beta Prep
- [ ] Finalize beta tester application form (Google Form with screening questions)
- [ ] Create private Discord channel `#beta-testers` + role assignment
- [ ] Prepare beta welcome email (with getting started guide)
- [ ] Identify 10–15 beta candidates (friends, early community, friendly projects)
- [ ] Send beta invites
- [ ] Set up GitHub Discussions (if not already)

### Day 10–11: Technical Readiness
- [ ] Finalize `/inboxes` page (functional, not skeleton) in webapp
- [ ] Finalize `/approvals` page (functional)
- [ ] Deploy agent status feature (small but visible)
- [ ] Load test: simulate 100 concurrent agents messaging
- [ ] Smoke test: full user journey from install → message → receipt
- [ ] Fix any showstopper bugs discovered
- [ ] Tag release `v0.1.0-beta` (semver start)

### Day 12–13: Outreach
- [ ] Email press embargo list (TechCrunch, The Block, Messari, AgentRank)
- [ ] Submit PR to Hermes (`agent-messenger` skill integration)
- [ ] Draft/issue OpenCode integration proposal
- [ ] Contact Claude Code team (Anthropic) via proper channels
- [ ] Tweet: "We're launching in 3 days — here's what's coming"
- [ ] Post industry conferences conference track announcement

### Day 14: Final Checks
- [ ] Verify all launch assets are ready (PH thumbnail, video, images)
- [ ] Finalize Product Hunt listing (draft, don't publish yet)
- [ ] Test waitlist form flow (end-to-end)
- [ ] Schedule all day-of launch tweets (Buffer)
- [ ] Assign day-of support team (3 people on Discord rotation)
- [ ] Prepare first comment for PH (paste into notepad)
- [ ] Final go/no-go decision with core team

---

## Launch Day Checklist

**7am PT:**
- [ ] Publish Product Hunt listing
- [ ] Pin first comment (copy-paste prepared)
- [ ] Tweet launch thread (auto-scheduled or manual)
- [ ] Post Discord announcement
- [ ] Notify waitlist (email blast)
- [ ] Send press embargo email (if embargoed)
- [ ] Verify webapp stability

**Throughout day:**
- [ ] Monitor Discord `#help` — respond to support questions
- [ ] Respond to GitHub issues (create templates if needed)
- [ ] Engage with tweets (reply, like, retweet)
- [ ] Collect feedback internally (notion doc or shared sheet)
- [ ] Log bugs/issues in GitHub (not spam Discord)

**Evening recap:**
- [ ] Tweet "Day 1 metrics" (stars, upvotes, signups)
- [ ] Post Discord recap
- [ ] Compile feedback into "post-launch improvements" doc
- [ ] Celebrate (seriously — team effort)

---

## Post-Launch Week

**Day +1 to +3:**
- [ ] Engage new GitHub stars (thank you tweets)
- [ ] Feature showcase: 1–2 beta projects publicly
- [ ] Follow-up with press for coverage
- [ ] Hacker News post (if not already done Day 0)

**Day +4 to +7:**
- [ ] Blog post: "Our first week: 2000 stars, 100 beta users, what's next"
- [ ] Week 1 metrics dashboard
- [ ] Merge first community PR (if any)
- [ ] Plan conference workshop content

**Day +8 to +14:**
- [ ] Release first minor patch with bug fixes
- [ ] Publish tutorial #2 (deeper dive)
- [ ] Open office hours voice chat (Discord)
- [ ] Announce next milestone (group threads? x402 integration?)

---

## Required Tools & Access

- [ ] GitHub repo owner access (admin)
- [ ] Product Hunt maker account (verified)
- [ ] Twitter/X verified account (blue check helps)
- [ ] Buffer/Hootsuite account (scheduling)
- [ ] Google Workspace (Forms, Docs)
- [ ] Airtable or Notion (waitlist + metrics tracking)
- [ ] Discord server admin
- [ ] Canva (for graphics) or Figma
- [ ] Screen recording tool (OBS, Loom)

---

## "Do Not Launch Until" Checklist

- [ ] `/inboxes` loads real conversations (no redirect or "coming soon")
- [ ] `/approvals` shows pending requests (real UI)
- [ ] Agent status can be set and visible to others
- [ ] Encrypted threads work end-to-end (send + receive)
- [ ] CLI `masumi-agent-messenger` works on fresh install
- [ ] Webapp loads without console errors
- [ ] Documentation site (agentmessenger.io) has at least Getting Started + Tutorial
- [ ] At least 1 external beta tester has used it successfully beyond team
- [ ] Support channel (Discord) is staffed for launch week

---

## Post-Launch Metrics Tracker

Create simple spreadsheet with columns:

| Date | Target Stars | Actual | Waitlist | Discord | Twitter | Messages | Active Agents | Notes |
|------|--------------|--------|-----------|---------|---------|----------|---------------|-------|
| Day 1 | 500 | | 50 | 50 | 50 | 500 | 10 | Launch blitz |
| Day 3 | 1,000 | | 100 | 100 | 100 | 1,500 | 25 | Momentum |
| Day 7 | 2,000 | | 200 | 200 | 200 | 3,000 | 50 | Sustain |
| Day 30 | 5,000 | | 500 | 500 | 300 | 10,000 | 200 | Month 1 |
|------|-------------|----------|-----------------|-------------------|---------------|---------------|-------|

Update daily for first week, then weekly.

---

**Next:** Assign this plan to a person (or yourself) and start Day 1 tasks.
