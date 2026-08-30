# HALO Homebridge AI Surfaces

HALO is Homebridge Precast's public, machine-readable product discovery and
configuration surface for AI assistants. It provides live Shopify-backed
catalog information for Homebridge's five major architectural product
categories without requiring a customer to install a plugin.

## Public services

- Remote MCP endpoint: <https://agent-commerce.homebridgepc.com/mcp-v2>
- Live major-category catalog: <https://agent-commerce.homebridgepc.com/v1/catalog>
- AI guidance: <https://homebridgepc.com/agents.md>
- Concise discovery file: <https://homebridgepc.com/llms.txt>
- Extended discovery file: <https://homebridgepc.com/llms-full.txt>
- Official MCP Registry name: `com.homebridgepc.agent-commerce/halo-ai-surfaces`

## Major-category coverage

- Garden beds
- Fire pits
- Mini greenhouses
- Culvert covers
- Retaining-wall garden beds

Accessories, merchandise, tools, plaques, lighting, and other minor items are
intentionally excluded. Retaining-wall systems require consultation and are not
represented by component or placeholder prices.

## What HALO provides

- Approved Homebridge category and product data
- Exact live Shopify variants and SKUs where applicable
- Current Shopify prices and availability
- Configuration options and required disclosures
- Attributed product links and eligible Shopify cart links
- Buyer-controlled handoff to Shopify Checkout

HALO does not place orders, collect payment, or bypass Shopify Checkout.

## Availability semantics

Many Homebridge products are made to order. Shopify inventory quantities may be
untracked while a variant remains available for sale. HALO describes these
products as **available to order; made to order; lead time applies**. It does
not interpret untracked inventory as zero stock.

## Authentication boundary

Public catalog discovery and configuration tools do not require a customer
account. The separate checkout-session action is OAuth-protected, scoped, and
merchant controlled. Product links and cart links never submit an order or
payment.

## Documentation-only repository

This repository intentionally contains public metadata and documentation only.
The HALO application source code, infrastructure, credentials, internal business
rules, and operational data are not published here.

See [SECURITY.md](SECURITY.md) and [PRIVACY.md](PRIVACY.md) for the public safety
and data-handling boundaries.

