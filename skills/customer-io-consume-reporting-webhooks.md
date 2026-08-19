---
name: customer-io-consume-reporting-webhooks
description: >-
  Register a Customer.io reporting webhook, verify its HMAC signature, and
  reconcile message lifecycle events back to the delivery that caused them.
api: Customer.io App API
base_url: https://api.customer.io
operations:
  - createWebhook
  - listWebhooks
  - getWebhook
  - updateWebhook
  - deleteWebhook
  - getMessage
generated: '2026-08-13'
method: generated
source: >-
  openapi/_original/customer-io-app-api-openapi.json,
  openapi/_original/customer-io-reporting-webhooks-openapi.json
---

# Consume reporting webhooks

Reporting webhooks are Customer.io's outbound event stream: everything that
happens to a message after you send it.

## Steps

1. **Register the endpoint.** `createWebhook` — `POST /v1/reporting_webhooks` —
   with your HTTPS URL and the event types you want. `listWebhooks`,
   `getWebhook`, `updateWebhook` and `deleteWebhook` manage it afterwards.

2. **Verify every request before you trust it.** Each POST carries two headers:

   - `x-cio-timestamp` — a Unix timestamp of when the request was sent.
   - `x-cio-signature` — an **HMAC-SHA256** of the request body keyed with your
     webhook signing key.

   Compute the HMAC over the raw body and compare in constant time. Reject a
   request whose `x-cio-timestamp` is outside your replay window. **Do not parse
   the body before you verify it.**

3. **Branch on `object_type` then `metric`.** Every event carries `event_id` (a
   ULID), `object_type`, `metric`, `timestamp` and a `data` object. The eight
   object types are `customer`, `email`, `sms`, `whatsapp`, `push`, `in_app`,
   `slack` and `webhook`. Metrics include `drafted`, `attempted`, `sent`,
   `delivered`, `opened`, `clicked`, `converted`, `bounced`, `dropped`,
   `spammed`, `failed`, `undeliverable`, `unsubscribed` and `replied`. Not every
   metric exists for every type — `spammed` is email-only, `replied` is SMS and
   WhatsApp only.

4. **Reconcile on `delivery_id`.** Every message event replays the
   `delivery_id` you got back from the send call. That is the join key. The
   event also carries `campaign_id`, `broadcast_id`, `newsletter_id`,
   `transactional_message_id`, `action_id`, `content_id`, `journey_id`,
   `trigger_id`, `customer_id` and `cio_id`, so you can attribute any event to
   its sending construct without a second API call.

5. **Trace causality.** `trigger_event_id` on a delivery event points back at
   the customer event that started the journey — behaviour to message, in one
   hop.

## Rules that will bite you

- **Deduplicate on `event_id`.** Webhook delivery is at-least-once; the same
  ULID can arrive twice.
- Events are ordered per delivery only by `timestamp`, and `timestamp` is a Unix
  integer in seconds — two events in the same second are not orderable from the
  payload. Use the metric lifecycle, not the clock, to order them.
- `link_id` appears only on `*_clicked` events; `device_id` only on push events.

## Related

- `asyncapi/customer-io-reporting-webhooks-asyncapi.yml`
- `openapi/_original/customer-io-reporting-webhooks-openapi.json`
- `data-model/customer-io-data-model.yml`
