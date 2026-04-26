# Asset Inventory — Agent Messenger Launch

**Launch Version**: v0.1.0  
**Target Completion**: T-7 days before launch  
**Owner**: Marketing lead + design contractor

---

## Digital Assets

### 1. Animated Demo GIF (Hero Asset)
- [ ] Format: MP4 or GIF (GIF preferred for wide compatibility)
- [ ] Duration: 2–3 seconds (loop seamless)
- [ ] Size: <3MB (web-optimized)
- [ ] Content:
  - Frame 1: Two agent icons labeled "Alice" and "Bob"
  - Frame 2: Alice sends "Hey, what's up?" speech bubble
  - Frame 3: Bob receives notification, sees message
  - Frame 4: Bob replies "All good!" speech bubble
- [ ] Color scheme: Brand colors (primary blue #0066FF, secondary gray #333)
- [ ] File location: `assets/gifs/agent-messenger-demo.gif`
- [ ] Also exported: PNG still frame for Product Hunt thumbnail

**Status**: Draft exists, needs polish + compression  
**Owner**: Design  
**Deadline**: T-7 days

---

### 2. Demo Video (30 seconds)
- [ ] Format: MP4 (H.264, 1080p)
- [ ] Duration: Exactly 30 seconds
- [ ] Sound: Silent (auto-play on social platforms)
- [ ] Subtitles: Burned-in text overlays (no audio dependency)
- [ ] Content flow:
  - 0–5s: Problem (agents can't communicate)
  - 5–15s: Solution (Agent Messenger sends message)
  - 15–25s: Code snippet (50 lines max)
  - 25–30s: CTA (GitHub star + demo link)
- [ ] File location: `assets/videos/agent-messenger-demo-30s.mp4`
- [ ] Also: 60-second version for YouTube

**Status**: Not started  
**Owner**: Design/Video contractor  
**Deadline**: T-7 days

---

### 3. Screenshots (4–6 images)

#### Screenshot A: Console Demo (Agent sending message)
- [ ] Terminal window showing Python code
- [ ] Agent output: `>>> Message sent to bob: "Hey"`
- [ ] Both agents' public keys displayed
- [ ] File: `assets/screenshots/01-console-demo.png`

#### Screenshot B: Web Demo (if applicable)
- [ ] Web UI showing message thread
- [ ] Two agent panels with message bubbles
- [ ] File: `assets/screenshots/02-web-ui.png`

#### Screenshot C: Integration Code (50 lines or less)
- [ ] Clean syntax-highlighted code block
- [ ] Shows import + init + send + receive
- [ ] File: `assets/screenshots/03-integration-code.png`

#### Screenshot D: Real Use Case Flow
- [ ] Diagram or photo of multi-agent system (support escalation)
- [ ] Agents A → B → C message flow
- [ ] File: `assets/screenshots/04-use-case-flow.png`

#### Screenshot E (optional): SpacetimeDB CLI
- [ ] SpacetimeDB module logs showing publish/subscribe
- [ ] File: `assets/screenshots/05-spacetime-logs.png`

#### Screenshot F (optional): Discord Community
- [ ] Discord #showcase channel with user project
- [ ] File: `assets/screenshots/06-discord-showcase.png`

**Status**: 2/6 captured (console demo + integration code)  
**Owner**: Product  
**Deadline**: T-3 days

---

### 4. Product Hunt Thumbnail
- [ ] Dimensions: 1024×768 pixels (PNG or GIF)
- [ ] Format: GIF (animated preferred) OR high-contrast PNG
- [ ] Content: 
  - Agent Messenger logo centered
  - Tagline: "SMS for AI agents"
  - CTA: "GitHub → Star" arrow
- [ ] Style: Bright background (neon blue #0066FF), white text
- [ ] File location: `assets/ph/thumbnail.gif`
- [ ] Also: 580×400 thumbnail variant

**Status**: Not started  
**Owner**: Design  
**Deadline**: T-1 day

---

### 5. GitHub Repository Assets
- [ ] `README.md` hero section updated with GIF + star CTA
- [ ] `docs/` folder with:
  - [ ] Quickstart guide
  - [ ] API reference (auto-generated from TypeScript/Python SDK)
  - [ ] Security model explanation
  - [ ] FAQ
- [ ] `examples/` folder with 3 working demos:
  - [ ] `basic-messaging/` (2 agents)
  - [ ] `support-escalation/` (3 agents)
  - [ ] `price-alert-network/` (broadcast pattern)
- [ ] `CONTRIBUTING.md` (guidelines for PRs)
- [ ] `CODE_OF_CONDUCT.md`
- [ ] `LICENSE` (MIT or Apache 2.0)

**Status**: README ~70%, docs partial, examples 1/3  
**Owner**: Engineering  
**Deadline**: Launch Day

---

### 6. Landing / Waitlist Page
- [ ] Platform: Paperform (simple) or Notion (free) or Webflow (custom)
- [ ] Headline: "Agent Messenger — SMS for AI agents"
- [ ] Subhead: "Get early access. First 100 signups get priority support."
- [ ] Email capture field + submit button
- [ ] Demo GIF embedded
- [ ] Link to GitHub (secondary CTA)
- [ ] Confirmation email auto-sent on signup
- [ ] File: N/A (hosted landing page)

**Status**: Not started  
**Owner**: Marketing  
**Deadline**: T-14 days (must capture emails before launch)

---

### 7. Email Onboarding Sequence
- [ ] Email 1: Welcome + GitHub link + Discord invite
- [ ] Email 2: Launch day announcement (live now)
- [ ] Email 3: Week 1 recap + tutorial links
- [ ] Email tool: ConvertKit, MailerLite, or Revue
- [ ] Tracking: UTM parameters on all links

**Status**: Not started  
**Owner**: Marketing  
**Deadline**: T-7 days

---

## Copy & Text Assets

### Git Commit Message Template (for later PRs)
```
fix(authz): verify agentDbId ownership in requestDirectContactWithFirstMessage

Add getOwnedActor check before rate limit bucket composition. Prevents
unauthorized agent linking abuse where caller could exhaust victim's contact
request quota.

- Add ownership guard immediately after Actor.queryById
- Use owned actor.id in bucketKey construction
- Update related unit tests for Forbidden path

Closes #XYZ
```

---

## Asset Pipeline Status (Launcher View)

| Asset | Completion | Next Action | Owner |
|---|---|---|---|
| Demo GIF | 50% | Polish animation + compression | design |
| Demo video | 0% | Script → record → edit | design |
| Screenshots | 33% | Capture UI + use case flow | product |
| PH thumbnail | 0% | Design in Figma/Canva | design |
| README | 70% | Add star CTA + quickstart | eng |
| Examples | 33% | Build support-escalation demo | eng |
| Waitlist page | 0% | Create Paperform form | marketing |
| Email sequence | 0% | Draft 3 emails | marketing |
| Documentation | 40% | Quickstart + FAQ | eng |
| Release notes | 0% | Write v0.1.0 notes | eng |

**Total completion**: ~35% — 2 weeks to 100% at current velocity

---

## Asset File Tree

```
agent-messenger/
├── README.md (hero GIF + star CTA)
├── assets/
│   ├── gifs/
│   │   ├── agent-messenger-demo.gif         ← DRAFT EXISTS
│   │   └── agent-messenger-demo-thumbnail.gif
│   ├── videos/
│   │   ├── agent-messenger-demo-30s.mp4     ← TODO
│   │   └── agent-messenger-demo-60s.mp4     ← TODO
│   ├── screenshots/
│   │   ├── 01-console-demo.png              ← EXISTS
│   │   ├── 02-web-ui.png                    ← TODO
│   │   ├── 03-integration-code.png          ← EXISTS
│   │   ├── 04-use-case-flow.png            ← TODO
│   │   └── ...
│   └── ph/
│       ├── thumbnail.gif                    ← TODO
│       └── thumbnail.png                    ← TODO
├── docs/
│   ├── quickstart.md
│   ├── api/
│   │   ├── python.md
│   │   └── typescript.md
│   └── faq.md
├── examples/
│   ├── basic-messaging/
│   ├── support-escalation/
│   └── price-alert-network/
├── marketing-artifacts/  ← THIS DIRECTORY
│   ├── strategy/
│   ├── content-calendar/
│   ├── launch-kit/
│   └── assets/ (this inventory)
└── CONTRIBUTING.md
```

---

## Asset Sign-off Checklist

Before launch, each asset must pass:

- [ ] **GIF/Video**: Plays smoothly on GitHub README (test in incognito)
- [ ] **Screenshots**: Readable on mobile (small text legible)
- [ ] **README**: Clear problem statement visible without scrolling
- [ ] **Demo link**: Works on mobile + desktop, no auth required
- [ ] **Waitlist form**: Submits successfully, confirmation email arrives
- [ ] **Email sequence**: All 3 emails deliver to Gmail/Outlook (not spam)
- [ ] **Documentation**: Quickstart completes without errors (tested by 2 people)
- [ ] **Examples**: Each runs in <5 minutes (from clone to first message)

---

## Design Guidelines (Brand Identity)

**Colors**:
- Primary: #0066FF (bright blue)
- Secondary: #1A1A2E (dark navy)
- Accent: #00F5D4 (teal green)
- Background: #FFFFFF (white) / #F5F7FA (light gray)
- Error: #FF4757 (red)

**Typography**:
- Headlines: Inter Bold (weight 700)
- Body: Inter Regular (weight 400)
- Code: JetBrains Mono

**Voice**:
- Clear, concise, slightly playful ("SMS for AI agents")
- No hype words like "revolutionary" or "game-changing"
- Developer-first: code examples > marketing copy

---

**Last updated**: 2026-04-26  
**Next review**: Launch Week -1 (final asset check)
