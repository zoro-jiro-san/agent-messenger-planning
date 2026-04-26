# AuthZ Gap Analysis — Resource Ownership Validation Pattern

## Pattern: getOwned* Guard Contract

All SpacetimeDB reducers exposing external endpoints MUST:

1. Lookup resource by ID (`*queryById`)
2. IMMEDIATELY call corresponding `getOwned*` guard
3. Proceed only if guard returns non-null; else `403 Forbidden`

### Guard Functions

| Resource | Guard | Error on failure |
|---|---|---|
| `Actor` | `getOwnedActor(ctx, actorId)` | `403 Forbidden` |
| `Device` | `getOwnedDevice(ctx, deviceId)` | `403 Forbidden` |
| `Inbox` | `getOwnedInbox(ctx, inboxId)` | `403 Forbidden` |

### Anti-Pattern (Vulnerable)

```ts
const actor = Actor.queryById(agentDbId);
// ❌ missing ownership check
const bucketKey = `rate_limit:${ctx.sender}:${actor.id}`;
```

### Correct Pattern

```ts
const actor = Actor.queryById(agentDbId);
if (!actor) throw new SenderError(ErrorCode.NotFound, 'Actor not found');

const owned = getOwnedActor(ctx, actor.id);
if (!owned) throw new SenderError(ErrorCode.Forbidden, 'Not your actor');

// safe to use actor.id in security contexts
const bucketKey = `rate_limit:${ctx.sender}:${actor.id}`;
```

---

## Reducer Audit Tracker

| File | Reducer | Guarded? | Notes |
|---|---|---|---|
| `message.ts` | `requestDirectContactWithFirstMessage` | ⚠️ No → fix applied | bucketKey uses actor.id before ownership check |
| `message.ts` | `insertEncryptedMessageIntoThread` | ✅ Yes | Uses runtime `canSendMessage` check |
| `agent-key-bundle.ts` | `rotateAgentKeys` | ✅ Yes | `getOwnedActorWithInbox` first |
| `device-share-request.ts` | `createDeviceShareRequest` | ✅ Yes | `getOwnedDevice` first |
| `thread.ts` | `createDirectThread` | ✅ Yes | `getOwnedActor` first |
| `thread.ts` | `createGroupThread` | ✅ Yes | `getOwnedActor` first |
| `contact-request.ts` | `approveContactRequest` | ✅ Yes | `getOwnedActor` first |
| `contact-request.ts` | `rejectContactRequest` | ✅ Yes | `getOwnedActor` first |
| `contact-request.ts` | `createPendingDirectContactRequest` | ✅ Yes | `getOwnedActor` first |
| `invitation.ts` | `applyInvitationCode` | ✅ Yes | `getOwnedActor` first |
| *(others)* | *(scheduler/internal only)* | N/A | Use `ctx.senderAuth.isInternal` |

---

## Rate Limit Bucket Key Hygiene

Bucket keys should incorporate **only verified ownership IDs**. Never use direct parameters without prior guard.

**Bad**: `bucketKey = `rl:${ctx.sender}:${inputAgentDbId}``
**Good**: `bucketKey = `rl:${ctx.sender}:${ownedActor.id}``

---

## Next Steps

1. Apply fixes from `patches/`
2. Add linter rule to detect missing `getOwned*` calls
3. Expand this doc with new reducers as they're added
