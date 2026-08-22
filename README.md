# Customer.io (customer-io)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Customer.io is a customer engagement platform that combines a customer data platform, marketing automation, and messaging delivery to send behavior-triggered email, push, SMS, and in-app messages. Its API surface includes the Track API for sending behavioral data and customer profile updates, the App API for managing workspace resources and sending transactional and broadcast messages, the Pipelines API which is a Segment-spec data ingestion interface, and outbound reporting webhooks that deliver message lifecycle events.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/customer-io/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/customer-io/refs/heads/main/apis.yml)

## Tags

- Behavioral Data
- Broadcasts
- Campaigns
- CDP
- Customer Data
- Customer Data Platform
- Data Ingestion
- Email
- Event Tracking
- Marketing Automation
- Messaging
- Push Notifications
- Segments
- SMS
- Transactional Email

## Timestamps

- **Created:** 2024-01-01
- **Modified:** 2026-05-19

## APIs

### Customer.io Track API

The Customer.io Track API allows developers to send behavioral data and customer profile information into Customer.io. It provides endpoints for identifying customers, tracking events, managing devices for push notifications, and sending anonymous events. The API uses basic authentication with a Site ID and API key, and accepts JSON request bodies.

- **Human URL:** [https://docs.customer.io/integrations/api/track/](https://docs.customer.io/integrations/api/track/)
- **Base URL:** `https://track.customer.io`

#### Tags

- Behavioral Data
- Customer Data
- Event Tracking
- Marketing Automation
- Messaging

#### Properties

- [Documentation](https://docs.customer.io/integrations/api/track/)
- [OpenAPI](openapi/customer-io-track-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/customer-io-track-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/customer-io-track-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Customer.io App API

The Customer.io App API enables developers to manage workspace resources and send messages programmatically. It provides endpoints for sending transactional messages, triggering broadcasts, managing customers and segments, retrieving campaign and newsletter data, and exporting customer information.

- **Human URL:** [https://docs.customer.io/integrations/api/app/](https://docs.customer.io/integrations/api/app/)
- **Base URL:** `https://api.customer.io`

#### Tags

- Broadcasts
- Campaigns
- Marketing Automation
- Messaging
- Segments
- Transactional Email

#### Properties

- [Documentation](https://docs.customer.io/integrations/api/app/)
- [OpenAPI](openapi/customer-io-app-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/customer-io-app-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/customer-io-app-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Customer.io Pipelines API

The Customer.io Pipelines API is the newer data ingestion interface for getting customer and event data into Customer.io. It follows the Segment spec and supports identify, track, page, screen, group, and alias calls. Customer.io recommends the Pipelines API for new integrations because it is easier to use, supports outbound data integrations and transformations, and is the focus of ongoing development.

- **Human URL:** [https://docs.customer.io/integrations/data-in/connections/http-api/](https://docs.customer.io/integrations/data-in/connections/http-api/)
- **Base URL:** `https://cdp.customer.io`

#### Tags

- CDP
- Customer Data Platform
- Data Ingestion
- Marketing Automation
- Messaging

#### Properties

- [Documentation](https://docs.customer.io/integrations/data-in/connections/http-api/)
- [OpenAPI](openapi/customer-io-pipelines-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/customer-io-pipelines-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/customer-io-pipelines-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/customerio)
- [LinkedIn](https://www.linkedin.com/company/customer-io)
- [Website](https://customer.io)
- [Documentation](https://docs.customer.io)
- [AsyncAPI](asyncapi/customer-io-reporting-webhooks-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)
- [JSON Schema](json-schema/customer-io-customer-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/customer-io-event-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/customer-io-webhook-payload-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/customer-io-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Vocabulary](vocabulary/customer-io-vocabulary.yml)
- [Rules](rules/customer-io-rules.yml)
- [Capabilities](capabilities/customer-io-capabilities.yml)
- [Integrations](https://customer.io/integrations)
- [L L Ms Txt](https://docs.customer.io/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
