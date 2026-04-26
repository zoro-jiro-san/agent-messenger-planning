# Implementation Checklist — AuthZ Hardening + Quality Sprint

> Sprint goal: Close critical authZ gap, add test coverage, establish patterns for EF+RLS migration

---

## Phase 0 — Prep (Done)

- [x] Clone masumi-agent-messenger latest main
- [x] Scan all SpacetimeDB reducers in `spacetimedb/src/operations/*.ts`
- [x] Identify unguarded `Actor/Device/Inbox` lookups
- [x] Document findings in planning repo

---

## Phase 1 — Critical Patch (Day 1)

**Objective**: Fix the single critical authZ gap

- [ ] **T1.1** — Apply `patches/message-authz-fix.diff` to `message.ts`:
  - Insert `getOwnedActor(ctx, actor.id)` call
  - Verify throw uses `ErrorCode.Forbidden`
- [ ] **T1.2** — Run TypeScript build to ensure no type errors:
  ```bash
  cd /path/to/masumi-agent-messenger
  ./scripts/build-spacetime.sh
  ```
- [ ] **T1.3** — Run existing integration tests:
  ```bash
  cd webapp && npm test tests/security/live/
  ```
- [ ] **T1.4** — Commit with conventional commit:
  ```bash
  git add spacetimedb/src/operations/message.ts
  git commit -m "fix(authz): verify agentDbId ownership in requestDirectContactWithFirstMessage"
  ```
- [ ] **T1.5** — Push branch `security-hardening/2026-04-authz-gaps` to origin
- [ ] **T1.6** — Open draft PR with template from `docs/security-audit-findings.md`

---

## Phase 2 — Test Coverage Expansion (Day 2)

**Objective**: Prevent regression with unit tests

- [ ] **T2.1** — Set up test scaffold for SpacetimeDB reducers (if not present)
- [ ] **T2.2** — Write `requestDirectContactWithFirstMessage` authZ violation test:
  - Setup: two identities (alice, bob); bob owns actor X
  - Action: alice calls with bob's `agentDbId` for X
  - Expect: `403 Forbidden` (not `404` or `429`)
- [ ] **T2.3** — Write rate limit success test (owned actor → limit enforced)
- [ ] **T2.4** — Add similar tests for `rotateAgentKeys` and `createDeviceShareRequest`
- [ ] **T2.5** — Run full test suite in CI; confirm ≥80% reducer branch coverage
- [ ] **T2.6** — Commit tests; update PR

---

## Phase 3 — Infrastructure Patterns (Week 2)

**Objective**: Lay groundwork for Supabase EF+RLS migration (FundWise-aligned)

- [ ] **T3.1** — Catalog all client-facing Supabase mutations in `webapp/lib/supabase/`
- [ ] **T3.2** — Draft Edge Function template (`supabase/functions/_shared/authenticate.ts`)
- [ ] **T3.3** — Draft RLS policies per table (see `plan/rls-policy-templates.md`)
- [ ] **T3.4** — Implement one pilot EF (e.g., `create-agent-key`) end-to-end
- [ ] **T3.5** — Update client to call EF instead of direct Supabase client
- [ ] **T3.6** -- Document migration steps in `plan/ef-migration-guide.md`

---

## Phase 4 — Audit Logging (Week 3)

**Objective**: Immutable record of sensitive actions

- [ ] **T4.1** — Create `audit_log` table migration
- [ ] **T4.2** — Add `logAuditEvent(actorId, action, resourceType, resourceId, metadata)` helper
- [ ] **T4.3** — Instrument `rotateAgentKeys`, `createDeviceShareRequest`, message send
- [ ] **T4.4** — Verify pg_notify → webhook delivery
- [ ] **T4.5** — Document log schema & query patterns

---

## Phase 5 — Documentation & Closeout

- [ ] Merge PR after review
- [ ] Update `SECURITY.md` with new authZ expectations
- [ ] Record sprint retrospective in `docs/quality-sprint-2026-04.md`
- [ ] Archive this plan; incubate new skill from learnings

---

## Dependencies & Blockers

| Task | Blocker | Owner |
|---|---|---|
| T1.1 (patch) | None | self |
| T2.2 (tests) | SpacetimeDB test harness setup | devops |
| T3.2 (EF template) | Supabase Edge Functions enabled on project | platform |
| T4.1 (audit table) | DB migration window | db-owner |

---

## Success Metrics

- Zero unguarded `queryById` → `getOwned*` gaps in new reducers
- Unit test coverage ≥ 80% for reducers
- All PR checks green (lint, typecheck, tests)
- EF migration pilot completed with no client-breaking changes
