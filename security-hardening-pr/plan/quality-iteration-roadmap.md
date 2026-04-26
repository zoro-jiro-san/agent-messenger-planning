# Quality Iteration Roadmap — Security & Infrastructure

Phase  | Focus | ETA | Owner
-------|-------|-----|------
Phase 1 | AuthZ critical gap fix | Day 1 | self
Phase 2 | Unit test coverage expansion | Day 2 | self
Phase 3 | Supabase EF+RLS migration prep | Week 2 | devops
Phase 4 | Audit logging infrastructure | Week 3 | platform
Phase 5 | Documentation & handoff | Week 4 | all

---

## Phase 1 Deliverables

- `security-hardening-pr/patches/message-authz-fix.diff` applied
- PR opened with security advisory context
- CI green (typecheck, lint, tests)

---

## Phase 3 Alignment with FundWise

This sprint's EF+RLS work maps directly to FundWise Phase 2 (backend hardening):

| FundWise Phase | Agent-Messenger Task | Outcome |
|---|---|---|
| Phase 2 — Supabase Edge Functions | T3.2–T3.5: EF template + pilot migration | Pattern established for all client mutations |
| Phase 2 — Row-Level Security | T3.3: RLS policy templates | Proven policy set for user isolation |
| Phase 2 — Audit Log | Phase 4: audit_log infrastructure | Compliant event trail |

---

## Quality Metrics

| Metric | Baseline | Target |
|---|---|---|
| Unauthorized access test failures | 1 (critical) found | 0 |
| Unit test coverage (reducers) | ~0% | ≥80% |
| AuthZ guard compliance | 94% | 100% |
| Security docs coverage | partial | complete |

---
