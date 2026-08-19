---
name: customer-io-trigger-broadcast
description: >-
  Trigger a Customer.io API-triggered broadcast to a segment or an explicit
  recipient list, then verify who it reached and diagnose per-recipient errors.
api: Customer.io App API
base_url: https://api.customer.io
operations:
  - listBroadcasts
  - getBroadcast
  - triggerBroadcast
  - broadcastStatus
  - broadcastErrors
  - broadcastMetrics
generated: '2026-08-13'
method: generated
source: openapi/_original/customer-io-app-api-openapi.json
---

# Trigger an API-triggered broadcast

A broadcast is a one-time send you build in the Customer.io UI and fire from
code. Unlike a transactional message, it goes to many people at once.

## Steps

1. **Find the broadcast.** `listBroadcasts` — `GET /v1/broadcasts` — then
   `getBroadcast` — `GET /v1/broadcasts/{broadcast_id}` — to confirm the channel
   and state before you fire anything.

2. **Trigger it.** `triggerBroadcast` — `POST /v1/campaigns/{broadcast_id}/triggers`.
   Note the path says `campaigns` even though the id is a broadcast id; that is
   correct and is not a typo in the spec. Supply either a segment, an explicit
   list of recipients, or a data payload for personalization.

   The response carries a **trigger id**. Keep it.

3. **Poll the trigger.** `broadcastStatus` — `GET
   /v1/campaigns/{broadcast_id}/triggers/{trigger_id}` — reports how the trigger
   is progressing. `listBroadcastTriggers` — `GET
   /v1/broadcasts/{broadcast_id}/triggers` — lists past triggers.

4. **Read per-recipient failures.** `broadcastErrors` — `GET
   /v1/campaigns/{broadcast_id}/triggers/{trigger_id}/errors`. This is the only
   place the per-user data errors show up. A `422` on step 2 will tell you
   errors exist and give you the trigger id; it will not tell you which
   recipients failed.

5. **Measure.** `broadcastMetrics` — `GET /v1/broadcasts/{broadcast_id}/metrics`
   — and `broadcastLinks` for click-level detail.

## Rules that will bite you

- **The trigger endpoint is limited to 1 request every 10 seconds.** It is by
  far the most throttled endpoint on the platform. Serialize your triggers.
- **No idempotency key.** A retried trigger fires the broadcast a second time to
  the same audience. If a trigger call times out, call
  `listBroadcastTriggers` and look for a trigger you did not record before you
  retry.
- On `422`, read `errors[].source.pointer` — it names the offending key, for
  example `/data/attributes/per_user_data`.
- On `409`, a linked resource is blocking you; resolve the dependency first.

## Related

- `errors/customer-io-problem-types.yml`
- `rate-limits/customer-io-rate-limits.yml`
- `data-model/customer-io-data-model.yml`
