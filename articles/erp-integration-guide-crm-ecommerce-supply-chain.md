---
layout: article
title: "ERP Integration Guide: CRM, Ecommerce, and Supply Chain Connections"
description: "Complete guide to ERP integration covering API strategies, middleware platforms, CRM connections (Salesforce, HubSpot), ecommerce links (Shopify, Magento), and supply chain systems (WMS, TMS). Includes integration patterns, cost benchmarks, and implementation timelines."
date: 2026-05-18
category: guide
permalink: /guides/erp-integration-crm-ecommerce-supply-chain/
author: B2B ERP Editorial Team
---

A standalone ERP system captures only a fraction of its potential value. The real leverage comes when your ERP exchanges data bidirectionally with CRM, ecommerce, warehouse management, and transportation systems in near-real-time. Yet integration remains the single most underestimated cost driver in ERP projects. A 2025 Panorama Consulting survey found that 67% of ERP implementations exceeded their integration budget, with the average overrun at 38%.

This guide covers the core integration methods, the middleware platforms that broker those connections, and the specific architectural patterns for connecting ERP to Salesforce, HubSpot, Shopify, Magento, WMS, and TMS systems.

## Key Takeaways

- API-first integration is the default strategy in 2026, but file-based EDI still dominates supply chain partner connections. Plan for both.
- Middleware platforms (Dell Boomi, MuleSoft, Celigo, Workato) reduce development time by 40-60% compared to custom code, but add $15K-$150K annually in platform costs.
- Salesforce-to-ERP integration requires careful decisions about which system owns the customer master, quote-to-order handoff, and pricing logic.
- Shopify-to-ERP connections must handle inventory sync at sub-minute latency during peak sales. Batch processing causes overselling.
- WMS integration is the most technically demanding connection due to bin-level inventory requirements and transaction-level accuracy needs.
- Budget 25-40% of your total ERP implementation cost for integration.

## ERP Integration Methods

### REST and SOAP APIs

Every major ERP platform in 2026 exposes REST APIs for programmatic data exchange. SAP S/4HANA provides OData-based APIs with over 400 pre-built endpoints. Oracle Fusion Cloud ERP offers REST APIs across all functional modules. Microsoft Dynamics 365 uses OData v4 endpoints via Dataverse. NetSuite provides both SuiteTalk (SOAP) and RESTlet APIs. Acumatica delivers a contract-based REST API with Swagger documentation.

REST APIs are the right choice for real-time data exchange between cloud-hosted systems at moderate transaction volumes. Rate limiting is the primary constraint. SAP S/4HANA Cloud throttles at roughly 5,000 requests per minute per tenant. NetSuite enforces concurrency limits of 5-25 simultaneous connections depending on license tier.

SOAP APIs still appear in older ERP systems and B2B trading partner connections. NetSuite's SuiteTalk remains more feature-complete than its REST alternative for some modules. Do not dismiss SOAP as legacy; it handles complex data structures that REST sometimes struggles with.

### Webhooks and Event-Driven Integration

Webhooks invert the polling model. Instead of repeatedly asking the ERP whether anything changed, the ERP pushes notifications when events occur. Shopify uses webhooks for order creation, payment capture, and inventory adjustment. Salesforce Platform Events and Change Data Capture provide similar push-based notifications.

Event-driven integration reduces API call volume by 80-95% compared to polling and delivers lower latency for time-sensitive workflows. The tradeoff is reliability: webhooks fail silently if the receiving endpoint is down, so every webhook integration needs a scheduled reconciliation process to catch missed events.

Modern implementations use message queues (Apache Kafka, Amazon SQS, Azure Service Bus) as intermediaries. The source publishes events to the queue; the consumer reads at its own pace. This pattern decouples systems, absorbs traffic spikes, and guarantees delivery even during downtime.

### File-Based and EDI Integration

Flat files and EDI transactions still account for over 60% of supply chain integration volume. Suppliers, 3PLs, and carriers communicate via EDI 850 (purchase orders), EDI 856 (advance ship notices), and EDI 810 (invoices) over AS2 or SFTP. Replacing these channels with API calls is usually impractical because trading partners will not change their systems for you.

ERP platforms handle EDI through built-in modules (SAP IDoc, Oracle EDI Gateway) or dedicated platforms like SPS Commerce, TrueCommerce, or Cleo. CSV and XML file drops over SFTP remain common for smaller partners. Budget for file monitoring, transformation logic, and error handling.

## Middleware and iPaaS Platforms

Point-to-point integrations create an unmaintainable web of custom connections. A five-system landscape has 10 possible connections; a fifteen-system landscape has 105. Middleware centralizes integration logic, provides monitoring, and offers pre-built connectors.

**Dell Boomi** leads in mid-market ERP integration with connectors for SAP, Oracle, NetSuite, Dynamics 365, Salesforce, and Shopify. Starts around $50K annually. Strong low-code interface and EDI support, though complex transformations sometimes require custom scripting.

**MuleSoft** is the enterprise-grade choice for Salesforce-heavy organizations. Anypoint Platform provides API lifecycle management alongside integration. Starts at $75K-$150K annually. Deep governance controls but steep learning curve.

**Celigo** targets NetSuite-centric organizations with pre-built flows for NetSuite-to-Shopify, NetSuite-to-Salesforce, and NetSuite-to-Amazon. Starts around $20K annually. Fast time-to-value for NetSuite shops.

**Workato** combines integration with workflow automation via a recipe-based approach. Starts around $30K annually. Intuitive for business analysts but complex error handling can be difficult to debug.

**Microsoft Power Automate** is the budget option for Dynamics 365 environments. Included in many Microsoft 365 licenses but insufficient for high-volume transactional integration.

Custom-coded integration makes sense when middleware connectors cannot support your business logic or when you need sub-second latency. Cost ranges from $30K-$200K per connection. Middleware makes sense for everything else when running three or more integrations.

## CRM Integration: Salesforce and HubSpot

### Salesforce-to-ERP Architecture

The Salesforce-to-ERP connection is the most common enterprise integration. The fundamental question is system-of-record ownership: which system owns the customer master, pricing, and the quote-to-cash handoff?

**Pattern 1: Salesforce owns lead-to-opportunity; ERP owns post-order.** Salesforce manages leads, accounts, opportunities, and quotes. When a deal closes, the integration creates a sales order in the ERP. From that point, the ERP handles fulfillment, invoicing, and revenue recognition. Salesforce receives status updates for visibility but does not modify order data. This is the most common and stable approach.

**Pattern 2: ERP owns pricing and inventory; Salesforce consumes via API.** Necessary when pricing depends on real-time inventory, customer-specific discounts, or complex configuration rules. Salesforce CPQ calls the ERP pricing engine during quote creation. This adds 200-800ms latency per call but eliminates quote-to-order discrepancies from stale pricing data.

**Key mappings:** Salesforce Accounts to ERP Customer Master. Opportunities (closed-won) to Sales Orders. Products to Item Master. Price Book Entries to Price Lists. Customer master data should sync in near-real-time (within 2 minutes). Pricing data syncs daily unless using real-time lookups. Order status syncs hourly or via webhook.

### HubSpot-to-ERP Integration

HubSpot follows similar patterns at lower complexity. Its marketplace includes connectors for NetSuite, QuickBooks, Dynamics 365, and SAP Business One. Operations Hub and platforms like Celigo provide additional sync capabilities. HubSpot's less restrictive rate limits (100 requests per 10 seconds) make it faster to implement, though it typically acts as the junior partner, consuming ERP data rather than driving complex logic.

## Ecommerce Integration: Shopify and Magento

### Shopify-to-ERP Integration

Shopify dominates ecommerce for B2B companies with a DTC channel and is growing in B2B wholesale via Shopify Plus. The integration covers five data flows.

**Product and pricing sync.** The ERP masters product data (SKU, description, weight, cost) and pricing, pushing to Shopify via the Products API. Sync daily for catalog changes, real-time for promotional price updates.

**Inventory sync.** The highest-stakes integration point. Shopify's Inventory API accepts location-level quantities. Normal operations need 5-15 minute syncs; flash sales and Black Friday need sub-minute sync to prevent overselling. The ERP must push available-to-promise quantities (on-hand minus allocated minus safety stock), not raw on-hand counts. Getting this calculation wrong is the top cause of overselling.

**Order flow.** Orders flow to the ERP via webhooks (orders/create, orders/paid). The integration must handle edits, cancellations, partial fulfillments, and refunds, each triggering a different ERP transaction type.

**Fulfillment feedback.** Tracking numbers and carrier info push back to Shopify via the Fulfillment API, triggering customer notifications. This loop must close within minutes of shipment.

### Magento (Adobe Commerce) Integration

Magento mirrors Shopify's patterns but adds complexity from its multi-store architecture. Its REST and GraphQL APIs are comprehensive but slower under load. Magento 2's message queue framework (RabbitMQ or MySQL) supports event-driven integration for high-volume scenarios.

The key difference is Magento allows custom modules that embed ERP logic directly into the platform. This is powerful but creates maintenance burden during major version updates. Treat ERP integration as a dedicated software project, not a configuration task.

## Supply Chain Integration: WMS and TMS

### Warehouse Management System (WMS) Integration

WMS integration is the most technically demanding ERP connection. While other integrations deal with orders and customers, WMS integration operates at bin locations, pick paths, lot numbers, and serial numbers.

**Inbound:** The ERP sends purchase orders to the WMS, which directs receiving and putaway. Receipt confirmations flow back to update inventory and trigger AP matching.

**Outbound:** The ERP sends sales orders for fulfillment. The WMS optimizes picking and packing. Ship confirmations with quantities, lot/serial numbers, and tracking data flow back to trigger revenue recognition and customer notification.

**Inventory reconciliation:** The WMS owns physical inventory truth at the bin level. The ERP owns financial inventory at the item level. Cycle count adjustments from the WMS must post to the ERP. Inventory holds in the ERP must flow to the WMS to prevent picking restricted stock.

Many WMS platforms (Manhattan Associates, Blue Yonder) still rely on flat-file integration. Modern platforms (Logiwa, ShipHero) offer REST APIs. Hybrid approaches using APIs for real-time events and files for bulk transfers are common.

### TMS Integration

TMS integration connects ERP shipping requirements to carrier rate shopping, route optimization, and tracking. EDI dominates: EDI 204 (load tender), EDI 214 (shipment status), and EDI 210 (freight invoice) are standard. Even API-first organizations use EDI for carrier communication because that is what carriers support.

## Integration Architecture Patterns

**Hub-and-Spoke.** All systems connect to a central middleware platform that handles transformation, routing, and error management. Recommended for organizations with 5-15 integrated systems. The hub provides centralized monitoring, consistent error handling, and a single place to troubleshoot failures. The tradeoff is a potential bottleneck at the hub during peak processing, mitigated by the redundancy that enterprise middleware platforms provide. Most mid-market ERP integration projects start here.

**Publish-Subscribe (Event-Driven).** Systems publish events to a message broker (Kafka, RabbitMQ, Amazon SNS/SQS). Consuming systems subscribe to relevant event topics and process messages independently. This pattern excels when multiple systems must react to the same business event. A single "order shipped" event from the WMS can simultaneously update the ERP financial ledger, notify the ecommerce storefront, trigger a customer email, and log the shipment in the TMS. Advantages include loose coupling between systems, horizontal scalability, and guaranteed message delivery. The disadvantage is increased architectural complexity and the need for event schema governance across teams.

**Orchestration vs. Choreography.** Orchestration uses a central controller that directs the sequence of integration steps: call System A, wait for a response, transform the data, call System B, handle errors, and retry failed steps. This provides clear visibility into end-to-end process status. Use orchestration for complex multi-step workflows like order-to-cash where sequence and error handling are critical. Choreography lets each system react independently to events without a central controller. Each system publishes its own events after completing its work, triggering downstream processes organically. This scales better and eliminates the controller bottleneck but makes end-to-end visibility harder. Use choreography for high-volume, loosely coupled processes like inventory position updates across channels.

## Implementation Timeline and Budget

A mid-market integration project covering CRM, ecommerce, and WMS typically requires 12-20 weeks and $75K-$300K.

**Weeks 1-3:** Discovery and mapping. Document data flows, field mappings, system-of-record decisions, and exception handling. This phase determines project success. **Weeks 4-8:** Development and unit testing. Build flows, configure connectors, test each connection independently. **Weeks 9-14:** Integration testing. End-to-end scenarios including edge cases like partial shipments, cancellations, and price overrides. **Weeks 15-18:** UAT and cutover planning. **Weeks 19-20:** Go-live and stabilization with 4-6 weeks of hypercare.

Budget breakdown for a $200K project: middleware licensing 20%, development labor 45%, testing 20%, project management 15%. Add 15-20% contingency.

## Common Pitfalls

**Underestimating data quality.** Integration exposes every data problem: duplicate customers, inconsistent SKUs, missing addresses, conflicting units of measure. Budget 15-20% of effort for data cleanup.

**Ignoring error handling.** Every integration will fail. Design with retry logic, exponential backoff, dead letter queues, and alerting that notifies the right people within minutes.

**Over-syncing data.** Sync the minimum data each system needs. Over-syncing increases maintenance burden and triggers unnecessary update cascades.

**Skipping performance testing.** An integration handling 50 daily orders may collapse at 5,000. Load test at 3-5x expected peak volume.

## Next Steps

Start with discovery before selecting middleware. Document current data flows, identify system-of-record ownership for every entity, and catalog known data quality issues. This groundwork reduces your timeline by 20-30%.

For vendor-specific guidance, see our comparisons of [cloud vs. on-premise ERP](/guides/cloud-vs-on-premise-erp/) and [best ERP for retail and ecommerce](/articles/best-erp-for-retail-and-ecommerce-2026/).
