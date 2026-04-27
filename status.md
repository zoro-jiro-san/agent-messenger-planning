# Status — Agent Messenger Marketing & GTM

**Last updated:** 2026-04-26  
**Phase:** 0 — Pre-Launch / Planning  
**Overall health:** 🟡 Planning complete, execution pending  

---

## Quick Summary

| Area | Status | Notes |
|------|--------|-------|
| Marketing strategy | ✅ Complete | Full GTM plan written (MARKETING-PLAN.md) |
| Campaign briefs | ✅ Complete | PH launch, content calendar, 14-day checklist |
| Tactical templates | ✅ Complete | Social post templates, email scripts, Discord bots |
| Press kit | ✅ Complete | Boilerplate, FAQ, assets list (press/PRESS-KIT.md) |
| Visual assets | ⬜ Not started | Logo, screenshots, PH thumbnail, demo video |
| Documentation site | ⬜ Not started | agentmessenger.io domain + GitHub Pages setup |
| Discord server | ⬜ Not started | Need to create + set up channels |
| Beta program | ⬜ Not started | Waitlist form, invite list, onboarding flow |
| Technical readiness | ⬜ In progress | `/inboxes` and `/approvals` need to be functional |
| First 10 beta testers | ⬜ Not started | Dependent on tech readiness + Discord |

---

## Milestone Progress

### Phase 0: Pre-Launch Planning (Target: complete 2026-04-26)
- [x] Competitive research (A2A, MCP, ADMP, UAM, OpenFused)
- [x] Positioning finalized ("SMS for AI agents")
- [x] Audience segmentation (frameworks, builders, enterprises, Masumi ecosystem)
- [x] Campaign structure defined (4 phases)
- [x] Platform strategy mapped (6 primary channels)
- [x] Content calendar drafted (Q2–Q3)
- [x] Social media templates created
- [x] Press kit drafted
- [x] Decision log started
- [ ] **Build: assets (logo, screenshots, video)**
- [ ] **Build: docs site + webapp fixes**
- [ ] **Build: Discord server + waitlist form**

---

### Phase 1: Soft Launch / Private Beta (Target: 2026-05-10 to 2026-05-24)

**Prerequisites:**
- [ ] Webapp `/inboxes` page functional (real data)
- [ ] `/approvals` page functional
- [ ] Agent status field implemented
- [ ] E2E encryption verified end-to-end
- [ ] CLI installs cleanly on fresh machine
- [ ] Documentation: Getting Started + 1 tutorial

**Deliverables:**
- [ ] Discord server + channels + rules
- [ ] Waitlist form live (100+ signups target)
- [ ] 10–15 beta testers invited
- [ ] Beta support infrastructure (#beta-testers channel, office hours schedule)
- [ ] Feedback collection (Google Form) active
- [ ] Issue template + Discussions enabled on GitHub

**Success criteria:**
- ≥ 10 active beta users (send ≥ 10 messages each)
- Good-first-issue labels help attract contributors
- No P0 bugs unfixed
- At least 1 external user completes onboarding without 1:1 help

---

### Phase 2: Public Beta Launch (Target: ~2026-05-31)

**Trigger:** All Phase 1 criteria met + tech readiness confirmed.

**Day 0 assets needed:**
- [ ] Product Hunt listing (thumbnail, gallery, first comment)
- [ ] Demo video (2 min + 15s teaser)
- [ ] Launch blog post ("The agent stack is incomplete without messaging")
- [ ] Twitter launch thread (6–8 tweets, pinned)
- [ ] Email to waitlist + beta
- [ ] Press embargo list notified
- [ ] Discord announcement ready
- [ ] HN + Reddit posts prepared
- [ ] Social media scheduling set (Buffer/Hootsuite)

**Day 0 sequence:**
- 07:00 PT: PH go live
- 07:05: Twitter launch thread
- 07:10: Discord announcement
- 07:30: Waitlist email blast
- 08:00: Press embargo lift
- 09:00: Blog publish
- 12:00: Discord AMA (voice)
- 16:00: Reddit + HN
- 18:00: Twitter Spaces
- 20:00: Recap tweet

**Day 1–7 sustain:**
- Daily monitoring (Discord, GitHub issues, Twitter)
- Community spotlights
- Milestone tweets (stars, messages sent)
- Follow-up PRs (Hermes, OpenCode)
- Week 1 retrospective blog (Day 7)

**Day 30 targets:**
- 1,000 GitHub stars
- 500 waitlist signups
- 500 Discord members
- 200 registered agents
- 1 framework integration merged

---

## Blockers & Open Tasks

### High Priority (Block launch)

| Task | Owner | Status | Notes |
|------|-------|--------|-------|
| Fix `/inboxes` page (real UI) | Eng team | ⬜ | Currently redirect/skeleton |
| Fix `/approvals` page | Eng team | ⬜ | Currently skeleton |
| Implement agent status (send+receive) | Eng team | ⬜ | PRD exists, needs implementation |
| Verify E2E encryption end-to-end | Eng team | ⬜ | Encryption test, plaintext never hits server |
| Deploy demo agent (`hello-agent`) | Eng team | ⬜ | Always-available auto-reply agent for onboarding |
| Documentation site (agentmessenger.io) | Eng + Design | ⬜ | GitHub Pages + domain + 5 core pages |
| Logo + brand assets | Designer | ⬜ | Hex logo dark/light, favicon, PH thumbnail |
| Demo video (2 min) | Video editor | ⬜ | Build → demo → outreach assets |

---

### Medium Priority (Pre-launch nice-to-have)

- [ ] Mobile CSS polish
- [ ] CLI `--help` examples screenshotted for docs
- [ ] HTTP status code error messages improved
- [ ] `good-first-issue` label on GitHub
- [ ] PR template + issue template
- [ ] GitHub Discussions categories set
- [ ] Welcome bot for Discord (auto-DM new members)
- [ ] GitHub bot (notify releases → Discord)

---

### Low Priority (Post-launch)

- [ ] T-Shirt design for top contributors
- [ ] Swag store (TBD)
- [ ] Advanced analytics (mixpanel, posthog)
- [ ] A/B test PH thumbnail variants
- [ ] Ambassador program

---

## Resource Gaps

| Resource | Need | Status |
|----------|------|--------|
| Marketing lead FTE | 0.5–1.0 | ❌ Unassigned (currently founder time) |
| Community manager | 0.5 | ❌ Unassigned (founder/mods) |
| Designer FTE | 0.2 | ❌ Not engaged yet |
| Video editor | contract | ❌ Not engaged yet |
| Discord mods | 3–5 people | ❌ Not recruited |
| X/Twitter API credentials | Optional for posting | ⬜ Not set up |
| Buffer/Hootsuite account | Optional for scheduling | ⬜ Not set up |

**Note:** Core team currently: Sarthi (founder) + possibly Patrick/Albina/Elena as advisors. Need to assign explicit campaign ownership.

---

## Known Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| Webapp blockers not fixed in time | Medium | High | Prioritize `/inboxes` + `/approvals` over polish; 2-week sprint |
| Launch day low engagement | Medium | Medium | Pre-seed with 50–100 beta users asking questions; schedule 20+ launch-day posts |
| "Not needed" pushback on HN/Reddit | High | Low | Prepare A2A/MCP comparison threads; show real use cases; engage constructively |
| Spam/abuse at scale | Medium | High | First-contact approval built from day 1; block/allowlist UI; rate limits |
| Community neglect (slow replies) | Medium | Medium | Set up mod rotation schedule; auto-responders for common questions |
| Framework maintainers uninterested | Medium | Medium | Build direct integration ourselves (SDKs), show traction, then re-approach |

---

## Metrics Dashboard (Targets)

| Metric | Baseline (0) | Day 7 | Day 30 | Month 3 |
|--------|--------------|-------|--------|---------|
| GitHub stars | 0 | 500 | 1,000 | 2,500 |
| Waitlist signups | 0 | 200 | 500 | 1,000 |
| Discord members | 0 | 200 | 500 | 800 |
| Twitter followers | 0 | +100 | +300 | +800 |
| Messages sent (cumulative) | 0 | 1k | 5k | 20k |
| Active agents (DAU) | 0 | 50 | 200 | 500 |
| Framework integrations | 0 | 0 | 1 | 3+ |
| Beta projects showcased | 0 | 2 | 5 | 15+ |

---

## Immediate Next Actions

**This week (Apr 26 – May 2):**
1. [ ] Create Discord server (channels + rules + roles)
2. [ ] Claim @agent_messenger Twitter handle (or @agentmessenger)
3. [ ] Designer: start logo + PH thumbnail
4. [ ] Eng: start `/inboxes` + `/approvals` fixes
5. [ ] Set up waitlist form (Google Form → Airtable sheet)
6. [ ] Draft launch blog post (Week 1 content)
7. [ ] Identify 10 beta candidates (DM on Twitter/Discord)
8. [ ] Verify domain `agentmessenger.io` points to GitHub Pages repo (or set up)

**Next week (May 3 – May 9):**
- Assets delivery (logo, thumbnail)
- Demo video recording
- Docs site scaffolding
- Beta invites sent (first 5)
- Monitor tech progress; adjust launch date if blockers remain

---

**Status updated:** 2026-04-26 — Planning complete, moving to execution phase.
