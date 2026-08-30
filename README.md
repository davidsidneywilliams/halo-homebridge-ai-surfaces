# HALO Homebridge AI Surfaces

HALO is Homebridge Precast's public, machine-readable product discovery and
configuration surface for AI assistants. It provides live Shopify-backed
catalog information for Homebridge's five major architectural product
categories without requiring a customer to install a plugin.

## Public services

- Homebridge AI & Structured Data page: <https://homebridgepc.com/pages/ai>
- Remote MCP endpoint: <https://agent-commerce.homebridgepc.com/mcp-v2>
- Live major-category catalog: <https://agent-commerce.homebridgepc.com/v1/catalog>
- HALO discovery document: <https://agent-commerce.homebridgepc.com/.well-known/halo-agent-commerce.json>
- Shopify-advertised AI index: <https://homebridgepc.com/ai/llms.txt>
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
- Live Shopify-hosted primary images, galleries, and associated video metadata
- Configuration options and required disclosures
- Attributed product links and eligible Shopify cart links
- Buyer-controlled handoff to Shopify Checkout

HALO does not place orders, collect payment, or bypass Shopify Checkout.

Catalog products include a compact primary-media summary and exact variants
include their Shopify-associated featured image when available. The bounded
media-gallery tool returns public Shopify CDN resources, alt text, dimensions,
preview images, hosted-video sources, and approved external-video links. Passing
an exact live SKU resolves its Shopify variant ID and prioritizes the media
associated with that variant. Compatible clients also receive the first
selected image as bounded native MCP image content for inline display. The
tool's text response also supplies an exact Markdown image fallback for clients
that do not visibly render native MCP image content, while the original Shopify
resource link remains available. HALO does not retain or rehost media and does
not claim that a video exists unless Shopify's live product record returns it.
ChatGPT-compatible clients can additionally render the media tool through a
read-only product card supplied by HALO's MCP UI resource.

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
