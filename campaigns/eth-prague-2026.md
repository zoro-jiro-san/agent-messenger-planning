# Campaign Brief: ETH Prague 2026 — The Production Agent Track

**Track name:** "From Demo to Deployment: Agent Infrastructure That Lasts"
**Rationale:** ETH Prague 2026 theme emphasizes *real-world impact*. We shift from "build something cool" to "build something *deployable*." Judges value sustainability, privacy, and governance — aligns perfectly with Agent Messenger's production-readiness messaging.

**Track prizes (total $5,000 — increased from $3K to attract serious teams):**
1. **Best Production-Ready Integration** — $2,500
   - Criteria: Code quality, documentation, error handling, deployability
   - Must include: Dockerfile, README with setup steps, integration test suite
   - Bonus: Published to npm/PyPI or merged into upstream framework
2. **Best Real-World Impact Use Case** — $1,500
   - Criteria: Solves actual user problem, not just tech demo
   - Examples: DAO governance assistant, DeFi risk agent coordination, NFT community management
   - Must include: User story, problem statement, impact metrics
3. **Best Privacy-Preserving Design** — $1,000 (NEW)
   - **Aligned with ETHPrague "Future Society" track**
   - Criteria: GDPR-compliant data handling, minimal data retention, encryption-at-rest
   - Must include: Data flow diagram, privacy policy snippet, consent mechanism

**Pre-hackathon prep (April–May 2026):**

| Date | Action | Owner |
|------|--------|-------|
| Apr 30 | Publish "Production-Ready Starter Kit" repo: Docker-compose deployment, monitoring setup, test suite scaffold | Eng |
| May 7 | Release "Agent Messenger Compliance Guide": GDPR considerations, data retention defaults, audit logging how-to | Docs |
| May 14 | Blog post: "What Makes an Agent System Production-Ready? 5 Lessons from 12 Months of Deployments" (leak Viqus/Mindra production lessons) | Content |
| May 21 | Contact ETH Prague organizers: propose panel talk "Infrastructure for Sustainable Agent Ecosystems" (position as thought leader, not just sponsor) | Founder |
| May 28 | Discord #eth-prague channel opens; weekly office hours begin (recorded for remote participants) | Community |

**Hackathon weekend (June 2026) — revised structure:**

**Friday:**
- Workshop 1 (90 min): "Building Production Agents — Error Handling, Observability, and Deployability"
  - Live coding: build a CI/CD agent squad with retries, status reporting, human escalation
  - Emphasize: structured logging, health checks, graceful degradation
- Workshop 2 (60 min): "Privacy by Design for Agent Communication"
  - GDPR principles applied to agent messaging
  - Data minimization: what to log vs. what to encrypt
  - User consent flows for human-in-the-loop approvals

**Saturday:**
- Judge Meet & Greet (informal) — focus on "real-world impact" criteria
- Technical office hours: monitoring setup (Prometheus metrics), alert configuration, chaos testing (agent failure scenarios)

**Sunday (Demo Day):**
- **Judging rubric weights** (align with ETHPrague values):
  - Innovation (20%)
  - **Production-readiness (30%)** — NEW PRIORITY
  - Real-world impact (30%)
  - Privacy/ethics (20%) — aligns with "Future Society" track
- Demo requirement: **deploy to Railway/Render/Fly.io and show live dashboard** (not just localhost)

**Post-hackathon:**
- Publish all projects to GitHub with "eth-prague-2026" tag
- Offer winning teams: 3-month free enterprise tier + security audit
- Publish winner case studies with **deployment metrics** (uptime, messages sent, human escalations)
- Invite top 2 teams to contribute to Agent Messenger documentation as "hackathon alumni"

**Success metrics (revised):**
- **≥ 5 projects deployed to public hosting** (not just GitHub repos)
- **≥ 2 PRs submitted to upstream frameworks** (Hermes, OpenCode) demonstrating integration
- **≥ 3 teams complete security checklist** (encryption, audit logging, data minimization)
- **Media coverage** highlighting Agent Messenger as "infrastructure for sustainable agent economies"

---

**Owner:** Marketing lead + community team
**Collaborators:** Masumi core team, ETH Prague organizers, Sokosumi (co-sponsor)
