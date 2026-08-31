# HALO Homebridge AI Surfaces

HALO is Homebridge Precast's zero-install, machine-readable commerce surface for
AI assistants and search agents. It exposes approved, live Shopify-backed
catalog data so an assistant can discover a product category, qualify missing
choices, resolve an exact purchasable variant, show its associated image and
current price, and hand the buyer to the correct Shopify cart or product page.

Customers do **not** need to install a plugin, connect an account, or know that
HALO exists. A remote MCP interface remains available as an optional integration
for clients that support it.

## Zero-install discovery

- Zero-install contract: <https://agent-commerce.homebridgepc.com/.well-known/halo-zero-install.json>
- Discovery overview: <https://agent-commerce.homebridgepc.com/v1/discovery>
- Human- and crawler-readable discovery: <https://agent-commerce.homebridgepc.com/discover>
- Live major-category catalog: <https://agent-commerce.homebridgepc.com/v1/catalog>
- Approved brand and category videos: <https://agent-commerce.homebridgepc.com/v1/videos>
- OpenAPI description: <https://agent-commerce.homebridgepc.com/openapi.json>
- Homebridge AI & Structured Data page: <https://homebridgepc.com/pages/ai>
- AI guidance: <https://homebridgepc.com/agents.md>
- Concise discovery file: <https://homebridgepc.com/llms.txt>
- Extended discovery file: <https://homebridgepc.com/llms-full.txt>

Category discovery pages are available at `/discover/{category}`, and live
catalog data is available at `/v1/catalog/{category}`.

## Shopper flow

HALO supports a conversational path without forcing an assistant to guess:

1. Discover an approved Homebridge category and its live options.
2. Ask only for choices needed to distinguish compatible variants.
3. Resolve the completed selection to an exact Shopify variant and SKU.
4. Return current price, availability, disclosures, and variant-associated
   Shopify media.
5. Offer an attributed product link or eligible Shopify cart link controlled by
   the buyer.

Partial fire-pit selections return the remaining questions instead of silently
choosing a shape, body, fuel, or tabletop finish. Exact major-category variants
can be resolved through the public configuration and resolver endpoints
described in the [OpenAPI document](https://agent-commerce.homebridgepc.com/openapi.json).

## Major-category coverage

- Garden beds
- Fire pits
- Mini greenhouses
- Culvert covers
- Retaining-wall garden beds

Accessories, merchandise, tools, plaques, lighting, and other minor items are
intentionally excluded. Retaining-wall systems require consultation and are not
represented by component or placeholder prices.

## Product media and videos

Exact variants return their Shopify-associated featured image when available.
HALO preserves the Shopify variant ID, SKU, selected options, current price, and
destination URL so the image and commerce action describe the same selection.

HALO also publishes approved Homebridge videos mapped at the brand or major
category level. These associations let an assistant show relevant educational
video for a general Homebridge, garden-bed, fire-pit, greenhouse, culvert-cover,
or retaining-wall question without claiming that a category video documents a
specific SKU. Seasonal material is excluded from the active map unless it is
explicitly enabled.

## Optional MCP interface

- Remote MCP endpoint: <https://agent-commerce.homebridgepc.com/mcp-v2>
- Official MCP Registry name: `com.homebridgepc.agent-commerce/halo-ai-surfaces`
- MCP tool reference: [TOOLS.md](TOOLS.md)

MCP can provide native tool calls and compatible product-card rendering, but it
is an additional distribution path—not a requirement for public discovery.

## Commerce and availability boundaries

HALO can produce attributed product and cart links, but it cannot place an
order, submit payment, or bypass Shopify Checkout. Shopify remains authoritative
for buyer identity, shipping, taxes, discounts, payment, and final order
completion.

Many Homebridge products are made to order. Shopify inventory quantities may be
untracked while a variant remains available for sale. HALO describes these as
**available to order; made to order; lead time applies** rather than treating
untracked inventory as zero stock.

## Documentation-only repository

This repository intentionally contains public metadata and documentation only.
The HALO application source code, infrastructure, credentials, internal business
rules, and operational data are not published here.

See [SECURITY.md](SECURITY.md) and [PRIVACY.md](PRIVACY.md) for the public safety
and data-handling boundaries.
