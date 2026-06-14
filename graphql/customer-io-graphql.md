# Customer.io GraphQL Schema

## Overview

This conceptual GraphQL schema represents the Customer.io messaging and marketing automation platform. Customer.io provides APIs for tracking behavioral data, managing customer profiles and segments, sending transactional messages, triggering campaigns and broadcasts, and retrieving delivery metrics. The schema covers the full breadth of the Customer.io App API and Track API surface.

## Source APIs

- Track API: https://docs.customer.io/integrations/api/track/
- App API: https://docs.customer.io/integrations/api/app/
- Pipelines API: https://docs.customer.io/integrations/data-in/connections/http-api/
- Documentation: https://docs.customer.io
- GitHub: https://github.com/customerio

## Schema File

See `customer-io-schema.graphql` for the full type definitions.

## Type Summary

### Customer Types
- `Customer` — top-level customer profile with identifier and attributes
- `CustomerDetails` — extended customer record including segment memberships and devices
- `CustomerAttributes` — key-value attribute map associated with a customer
- `CustomerIdentifier` — unique identifier used to look up or reference a customer
- `CustomerSegment` — association between a customer and a segment

### Segment Types
- `Segment` — a named group of customers
- `SegmentDetails` — extended segment information including type and conditions
- `SegmentType` — enum distinguishing manual vs automatic segments
- `ManualSegment` — segment populated by explicit customer additions
- `AutomaticSegment` — segment driven by conditions evaluated against customer data
- `SegmentCondition` — a single condition clause used in automatic segment logic
- `SegmentMetric` — aggregate counts and rates for a segment

### Attribute Types
- `Attribute` — a single named attribute with a typed value
- `AttributeType` — enum for string, number, boolean, datetime, array
- `AttributeValue` — union-like wrapper around an attribute's raw value

### Event Types
- `Event` — base event with timestamp and type
- `EventDetails` — extended event record including arbitrary data payload
- `EventData` — key-value payload carried by an event
- `EventType` — enum for page, custom, anonymous, and screen event kinds
- `PageView` — specialised event capturing a page URL and title
- `CustomEvent` — a named event sent via the Track API
- `AnonymousEvent` — event not associated with a known customer identity

### Campaign Types
- `Campaign` — a messaging campaign definition
- `CampaignDetails` — extended campaign record with trigger, schedule, and metrics
- `CampaignStatus` — enum for draft, running, paused, stopped
- `TriggerType` — enum for event-triggered, segment-triggered, and date-triggered campaigns
- `MessageSchedule` — timing configuration for a campaign or broadcast
- `CampaignMetric` — aggregate delivery and engagement statistics for a campaign

### Message Types
- `Message` — base message with type and delivery status
- `MessageType` — enum covering email, push, SMS, slack, webhook, in-app
- `EmailMessage` — message delivered via email channel
- `PushMessage` — message delivered via push notification
- `SMSMessage` — message delivered via SMS channel
- `SlackMessage` — message delivered to a Slack channel
- `WebhookMessage` — outbound webhook call treated as a message delivery
- `InAppMessage` — message displayed inside a mobile or web app
- `MessageContent` — rendered body and subject of a message
- `MessageTemplate` — reference to the template used to render a message

### Template Types
- `Template` — a reusable message template
- `TemplateDetails` — extended template record with content and type
- `TemplateType` — enum for email, push, SMS, in-app, and webhook templates

### Delivery Types
- `Deliveries` — paginated list of delivery records
- `DeliveryStatus` — enum for sent, delivered, opened, clicked, bounced, failed, unsubscribed
- `DeliveryEvent` — a lifecycle event emitted during message delivery
- `OpenEvent` — delivery event recording a message open
- `ClickEvent` — delivery event recording a link click
- `ConvertEvent` — delivery event recording a conversion goal completion

### Broadcast Types
- `Broadcast` — a one-time send to a segment or list
- `BroadcastDetails` — extended broadcast record with schedule and status
- `NewsletterCampaign` — a broadcast newsletter send

### Transactional Types
- `TransactionalMessage` — a programmatically triggered message sent to a specific customer

### Automation Types
- `AutomationWorkflow` — a multi-step automation sequence
- `WorkflowTrigger` — the entry condition that starts a workflow
- `WorkflowStep` — a single action step within a workflow
- `WorkflowDelay` — a timed wait step within a workflow
- `WorkflowCondition` — a branch condition evaluated within a workflow

### Metric Types
- `Metric` — a generic named metric with a numeric value

### Auth Types
- `APIKey` — an API key used to authenticate against Customer.io APIs
- `Token` — a short-lived bearer token

### Webhook Types
- `Webhook` — a registered outbound webhook endpoint for reporting events

## Key Relationships

- A `Customer` belongs to zero or more `Segment` objects via `CustomerSegment`
- `Campaign` targets a `Segment` and uses a `MessageTemplate`
- `Broadcast` sends a `Message` derived from a `Template` to a `Segment`
- `DeliveryEvent` subtypes (`OpenEvent`, `ClickEvent`, `ConvertEvent`) are emitted per `Message` delivery
- `AutomationWorkflow` is composed of ordered `WorkflowStep`, `WorkflowDelay`, and `WorkflowCondition` nodes
- `TransactionalMessage` is independent of campaigns and sends directly to a `Customer`

## Usage Notes

Customer.io does not expose a native public GraphQL endpoint. This schema is a conceptual representation derived from the REST API surface and is intended for integration modeling, tooling generation, and documentation purposes. The types map closely to the request and response bodies of the App API and Track API.
