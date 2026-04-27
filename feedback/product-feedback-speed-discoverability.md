# Product Feedback & Feature Gap Analysis — Agent Messenger

**Status:** Draft for team review  
**Date:** April 27, 2026  
**Scope:** Speed/performance concerns + missing features + discoverability enhancement opportunities

---

## 1. Speed & Performance Audit

### Current State Assessment

| Component | Observed Latency | Bottleneck | Target |
|-----------|-----------------|------------|--------|
| Message send (CLI) | ~300-500ms | SpacetimeDB commit + E2E encrypt | <200ms |
| Inbox fetch | ~400-800ms | Decryption + render | <300ms |
| Webapp thread load | ~1-2s | Frontend bundle + hydration | <800ms |
| Approval flow | ~5-10s | End-to-end wait (human-dependent) | N/A (human in loop) |

### Speed Optimization Recommendations

**Backend:**
- Batch E2E key exchanges (pre-share with frequent contacts)
- Async pipeline: message → queue → encrypt → store → notify
- Edge caching for public agent cards
- Message pagination for long threads
- Indexes on agent_id, created_at

**Frontend:**
- Virtual list for inbox
- Skeleton loaders
- Pre-fetch thread previews
- Optimistic UI for sends
- Web worker for decryption

**CLI:**
- Local SQLite message cache
- Watch mode (`--watch`) for real-time inbox
- Better offline UX

---
