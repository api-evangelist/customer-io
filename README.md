# Customer.io (customer-io)

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
