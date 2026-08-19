# Quarantined scaffold OpenAPIs — NOT published by Customer.io

The two files in this directory were **written by the API Evangelist pipeline**, not by
Customer.io. They were hand-authored summaries of the App API and Pipelines API, and they
were previously stored in `openapi/_original/` where they read as harvested upstream
source. They are not.

On **2026-08-13** contract discovery found the **real, first-party OpenAPI 3.1.0 documents**
that Customer.io publishes from its own documentation host, indexed in
<https://docs.customer.io/llms.txt> and <https://customer.io/.well-known/api-catalog>:

| Published spec | Operations | Now stored at |
|---|---|---|
| <https://docs.customer.io/files/journeys-app.json> | 166 | `openapi/_original/customer-io-app-api-openapi.json` |
| <https://docs.customer.io/files/journeys-track.json> | 18 | `openapi/_original/customer-io-track-api-openapi.json` |
| <https://docs.customer.io/files/pipelines.json> | 7 | `openapi/_original/customer-io-pipelines-api-openapi.json` |
| <https://docs.customer.io/files/journeys-webhooks.json> | 1 webhook | `openapi/_original/customer-io-reporting-webhooks-openapi.json` |

The scaffolds described **52 operations across all three surfaces**; the published App API
alone has **166**. They are kept here for provenance, not for use.

## Open follow-up

The per-tag documents in `openapi/*.yml` were split from these scaffolds by an earlier
`refine-openapis` run, so they inherit the scaffold's coverage gaps and its incorrect
`servers[]` (every one of them names `https://api.customer.io/v1`, including the Track and
Pipelines tags, whose real bases are `https://track.customer.io` and
`https://cdp.customer.io/v1`). **They should be re-refined from `openapi/_original/`.**
Until that happens, treat `openapi/_original/*.json` as the authority for this provider.

Two further defects to fix in the same pass:

- `customer-io-batch-api-openapi.yml` and `customer-io-entity-api-openapi.yml` declare
  the path `../v2/batch` and `../v2/entity` — a relative traversal, not a valid OpenAPI
  path. The real paths are `/api/v2/batch` and `/api/v2/entity` on `track.customer.io`.
- `customer-io-customers-api-openapi.yml` mixes App API paths (`/customers`,
  `/customers/{identifier}/attributes`) with Track API paths
  (`/customers/{identifier}/suppress`) in one document under one `servers[]` block, so
  no single base URL can be correct for it. Its `apis.yml` `baseURL` was left on
  `https://track.customer.io` in the 2026-08-13 enrichment pass rather than guessed at.
