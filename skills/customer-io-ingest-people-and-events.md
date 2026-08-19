---
name: customer-io-ingest-people-and-events
description: >-
  Get people, events, objects and relationships into Customer.io through the
  Pipelines (CDP) API, and know when to reach for the Track API instead.
api: Customer.io Pipelines API
base_url: https://cdp.customer.io/v1
operations:
  - identify
  - track
  - page
  - screen
  - group
  - alias
  - batch
generated: '2026-08-13'
method: generated
source: openapi/_original/customer-io-pipelines-api-openapi.json
---

# Ingest people and events

Customer.io has **two** ingest APIs. Pick once, deliberately.

- **Pipelines API** (`https://cdp.customer.io/v1`) — the Segment-spec interface.
  This is what Customer.io recommends for new integrations and where its
  development is focused. Every mobile SDK and most integrations sit on it.
- **Track API** (`https://track.customer.io`) — the older Customer.io-specific
  interface. Still fully supported, easier to read if you only ever talk to
  Customer.io, harder to troubleshoot if you also fan out to other destinations.

Both use HTTP basic auth, but with **different credentials**: Pipelines takes
the CDP API key as the username with a blank password (`API_key:`); Track takes
`site_id:api_key`.

## Steps (Pipelines)

1. **Identify the person.** `identify` — `POST /identify`. Requires at least one
   of `userId` or `anonymousId`. Traits become profile attributes. This is an
   upsert, so repeating it converges rather than duplicating.

2. **Track behaviour.** `track` — `POST /track`, with an event `name` and
   optional `properties`. Page and screen views have their own calls: `page` —
   `POST /page`, `screen` — `POST /screen`.

3. **Associate to an object.** `group` — `POST /group`. This is how a person
   joins a company, account or course. Objects and relationships are native here
   and largely absent from Track v1.

4. **Merge identities.** `alias` — `POST /alias`, linking a new identity to an
   existing one.

5. **Batch.** `batch` — `POST /batch` for throughput.

## The thing that surprises everybody

**The Pipelines API only has POST.** There is no `DELETE`. Deletes and other
state changes are expressed as `track` events with a reserved `name` — send a
`track` event named `Delete Person` to delete, `Suppress Person` to suppress.
Customer.io calls these *semantic events*, and the same pattern carries the
eCommerce and CRM vocabularies (`Add to Cart`, `Purchase`, `Update Customer`).

If you reason about this API from HTTP verbs alone you will conclude it cannot
delete. The capability lives in the event vocabulary, not the method.

## Limits

- Single request payload: **64 KB**. Batch request: **1 MB**.
- Track API fair-use limit: **100 requests/second**, live and backfill, v1 and v2.
- No `RateLimit-*` headers anywhere. Back off on `429`.

## When to use Track instead

Use the Track API when you need something Pipelines does not express as a call:
device registration (`add_device`, `delete_device`), suppression toggles
(`suppress`, `unsuppress`), manual segment membership (`add_to_segment`,
`remove_from_segment`), profile merges (`merge`), or the v2 unified `entity` and
`batch` shapes.

## Related

- `conventions/customer-io-conventions.yml`
- `data-model/customer-io-data-model.yml`
- `authentication/customer-io-authentication.yml`
