---
name: customer-io-send-transactional-email
description: >-
  Send a Customer.io transactional email from a stored template and confirm it
  was queued, without double-sending on a retry.
api: Customer.io App API
base_url: https://api.customer.io
operations:
  - listTransactional
  - getTransactional
  - sendEmail
  - getMessage
generated: '2026-08-13'
method: generated
source: openapi/_original/customer-io-app-api-openapi.json
---

# Send a transactional email

Transactional messages are the receipts, password resets and 2FA codes a person
implicitly opted into. They are sent one at a time against a stored template.

## Before you start

- Base URL: `https://api.customer.io` (US) or `https://api-eu.customer.io` (EU).
  Credentials do not cross regions. If you are unsure which region a workspace
  lives in, call `getRegion` on `https://track.customer.io/api/v1/accounts/region`.
- Authorization: `Authorization: Bearer <App API Key>`.
- If you are using a service-account token (`sa_live_`) instead, you must also
  send `X-Workspace-Id: <workspace id>` on every request, because
  service-account tokens are not workspace-scoped. Customer.io's own guidance is
  to use an App API Key for production and reserve `sa_live_` for testing.

## Steps

1. **Find the template.** `listTransactional` — `GET /v1/transactional` — returns
   the transactional messages in the workspace. Read the one you want and note
   its id. `getTransactional` — `GET /v1/transactional/{transactional_id}` —
   returns its detail if you need to confirm the channel and variants.

2. **Send.** `sendEmail` — `POST /v1/send/email`. Provide
   `transactional_message_id`, the recipient `to`, and an `identifiers` object
   naming the person by `id`, `email` or `cio_id`. Put template variables in
   `message_data`.

3. **Record the delivery id.** A 200 returns a `delivery_id` and `queued_at`.
   **Persist the `delivery_id` before you do anything else** — see the retry
   rule below.

4. **Confirm.** `getMessage` — `GET /v1/messages/{message_id}` — returns the
   delivery state and engagement for that message. For a push/streaming view,
   register a reporting webhook instead; every lifecycle event replays the same
   `delivery_id`.

## Rules that will bite you

- **There is no idempotency key.** Customer.io publishes no `Idempotency-Key`
  header and no `idempotency_key` field. A retried `sendEmail` sends a second
  email. If the call times out, do **not** blind-retry: look the person up with
  `getPersonMessages` (`GET /v1/customers/{customer_id}/messages`) and check
  whether the message already exists before sending again.
- **Rate limit: 100 requests/second** on the transactional send endpoints, and
  the API returns **no** `RateLimit-*` or `Retry-After` headers. Back off
  exponentially with jitter on `429`; you cannot read remaining budget.
- **403 means entitlement, not credentials.** `{"meta":{"error":"Account is not
  authorized for transactional messaging..."}}` is a plan/account state. Do not
  rotate the key; escalate.
- **Percent-encode anything you put in a URL.** An unencoded `+` in an email
  address returns `200` with an empty result, not an error.
- Error shape on these endpoints is `{"meta":{"error": "..."}}`, which is
  **different** from the rest of the App API's `{"errors":[{"detail","status"}]}`.
  Handle both.

## Related

- `conventions/customer-io-conventions.yml`
- `errors/customer-io-problem-types.yml`
- `rate-limits/customer-io-rate-limits.yml`
