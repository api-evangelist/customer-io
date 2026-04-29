# Customer.io (customer-io)
Customer.io is a marketing automation and customer engagement platform that enables businesses to send targeted messages based on real-time behavioral data. Their developer platform provides APIs for ingesting customer data and events, managing campaigns, segments, and broadcasts, and sending transactional and automated messages across email, push, SMS, and in-app channels.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/customer-io/refs/heads/main/apis.yml)

## Scope

- **Type:** Contract
- **Position:** Consuming
- **Access:** 3rd-Party

## Tags:

 - Messaging, Marketing Automation, Customer Data, Customer Engagement, CDP, Transactional Email

## Timestamps

- **Created:** 2025-03-01
- **Modified:** 2026-03-20

## APIs

### Customer.io Track API
The Customer.io Track API allows developers to send behavioral data and customer profile information into Customer.io. It provides endpoints for identifying customers, tracking events, managing devices for push notifications, and sending anonymous events. The API uses basic authentication with a Site ID and API key, and accepts JSON request bodies. It is commonly used to build custom integrations that feed customer activity data into Customer.io for use in messaging campaigns and automation workflows.

**Human URL:** [https://docs.customer.io/integrations/api/track/](https://docs.customer.io/integrations/api/track/)


#### Tags:

 - Messaging, Marketing Automation, Customer Data, Event Tracking, Behavioral Data

#### Properties

- [Documentation](https://docs.customer.io/integrations/api/track/)
- [OpenAPI](openapi/customer-io-track-api-openapi.yml)

### Customer.io App API
The Customer.io App API enables developers to manage workspace resources and send messages programmatically. It provides endpoints for sending transactional messages, triggering broadcasts, managing customers and segments, retrieving campaign and newsletter data, and exporting customer information. The API uses bearer token authentication with an App API key and is designed for operations that go beyond data ingestion, such as retrieving metrics, managing message templates, and automating outbound communications from Customer.io.

**Human URL:** [https://docs.customer.io/integrations/api/app/](https://docs.customer.io/integrations/api/app/)


#### Tags:

 - Messaging, Marketing Automation, Campaigns, Transactional Email, Segments, Broadcasts

#### Properties

- [Documentation](https://docs.customer.io/integrations/api/app/)
- [OpenAPI](openapi/customer-io-app-api-openapi.yml)

### Customer.io Pipelines API
The Customer.io Pipelines API is the newer data ingestion interface for getting customer and event data into Customer.io. It follows the Segment spec and supports identify, track, page, screen, group, and alias calls. Customer.io recommends the Pipelines API for new integrations because it is easier to use, supports outbound data integrations and transformations, and is the focus of ongoing development. It uses a CDP API key for authentication and provides a modern alternative to the legacy Track API.

**Human URL:** [https://docs.customer.io/integrations/data-in/connections/http-api/](https://docs.customer.io/integrations/data-in/connections/http-api/)


#### Tags:

 - Messaging, Customer Data Platform, Data Ingestion, Marketing Automation, CDP

#### Properties

- [Documentation](https://docs.customer.io/integrations/data-in/connections/http-api/)
- [OpenAPI](openapi/customer-io-pipelines-api-openapi.yml)

## Common Properties

- [Website](https://customer.io/)
- [Documentation](https://docs.customer.io/)
- [Privacy Policy](https://customer.io/legal/privacy-policy/)
- [Terms of Service](https://customer.io/legal/terms-of-service/)
- [Support](https://customer.io/contact/)
- [Blog](https://customer.io/blog/)
- [Login](https://fly.customer.io/login)
- [AsyncAPI - Reporting Webhooks](asyncapi/customer-io-reporting-webhooks-asyncapi.yml)
- [JSON Schema - Customer](json-schema/customer-io-customer-schema.json)
- [JSON Schema - Event](json-schema/customer-io-event-schema.json)
- [JSON Schema - Webhook Payload](json-schema/customer-io-webhook-payload-schema.json)
- [JSON-LD Context](json-ld/customer-io-context.jsonld)
- [Vocabulary](vocabulary/customer-io-vocabulary.yml)
- [Rules](rules/customer-io-rules.yml)
- [Capabilities](capabilities/customer-io-capabilities.yml)

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
