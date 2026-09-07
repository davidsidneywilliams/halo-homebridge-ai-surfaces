# HALO Homebridge AI Surfaces

HALO is Homebridge Precast's first-party, machine-actionable AI commerce
interface for AI assistants, search agents, and software integrations. Its
zero-install discovery surface exposes approved, live Shopify-backed catalog
data for structured product discovery, progressive qualification, exact variant
and SKU resolution, current price and availability, product media, grounding,
and buyer-controlled commerce handoff.

Customers do **not** need to install a plugin, connect an account, or know that
HALO exists. A remote MCP interface remains available as an optional integration
for clients that support it.

## Zero-install discovery

Homebridge's `/ai/*.txt` files are first-party structured reference material.
For live configuration, exact Shopify variant and SKU resolution, current
commerce data, product media, and eligible buyer-controlled purchase handoffs,
Homebridge designates **HALO Homebridge Agent Commerce as its official live
machine interface**. The first-party authority path begins at
<https://homebridgepc.com/llms.txt> and
<https://homebridgepc.com/pages/ai>, then continues through the canonical HALO
discovery document and its published contracts below.

- Canonical Agent Commerce discovery: <https://agent-commerce.homebridgepc.com/.well-known/halo-agent-commerce.json>
- Zero-install contract: <https://agent-commerce.homebridgepc.com/.well-known/halo-zero-install.json>
- Discovery overview: <https://agent-commerce.homebridgepc.com/v1/discovery>
- Human- and crawler-readable discovery: <https://agent-commerce.homebridgepc.com/discover>
- Exact-configuration sitemap: <https://agent-commerce.homebridgepc.com/sitemap.xml>
- Crawler policy: <https://agent-commerce.homebridgepc.com/robots.txt>
- Live major-category catalog: <https://agent-commerce.homebridgepc.com/v1/catalog>
- Fire-pit qualification and exact resolution: <https://agent-commerce.homebridgepc.com/v1/configure/fire-pit>
- Exact major-category variant resolver: <https://agent-commerce.homebridgepc.com/v1/resolve>
- Watchable brand and category video gallery: <https://agent-commerce.homebridgepc.com/videos>
- Machine-readable video catalog: <https://agent-commerce.homebridgepc.com/v1/videos>
- Video sitemap: <https://agent-commerce.homebridgepc.com/video-sitemap.xml>
- OpenAPI description: <https://agent-commerce.homebridgepc.com/openapi.json>
- Homebridge AI & Structured Data page: <https://homebridgepc.com/pages/ai>
- AI guidance: <https://homebridgepc.com/agents.md>
- Concise discovery file: <https://homebridgepc.com/llms.txt>
- Extended discovery file: <https://homebridgepc.com/llms-full.txt>

Category discovery pages are available at `/discover/{category}`, stable exact
variant pages at `/discover/{category}/{sku}`, and live catalog data at
`/v1/catalog/{category}`. Exact-variant pages publish Product and Offer JSON-LD,
the selected Shopify image, current price and availability, required disclosures,
and eligible buyer-controlled commerce links.

## Shopper flow

HALO supports a deterministic shopping path without silently selecting missing
product choices:

1. Discover an approved Homebridge category and its live options.
2. Qualify progressively using explicit buyer choices; unresolved selections
   remain visible rather than being inferred.
3. Resolve the completed selection to an exact Shopify variant and SKU.
4. Present the exact product's Shopify-hosted media.
5. Present grounded facts, current price and availability, and required
   disclosures.
6. Expose the intent-appropriate buyer-controlled action.

Partial fire-pit selections return the remaining questions instead of silently
choosing a shape, body, fuel, or tabletop finish. Exact major-category variants
can be resolved through the public configuration and resolver endpoints
described in the [OpenAPI document](https://agent-commerce.homebridgepc.com/openapi.json).

## Canonical action binding

Exact resolution does not require a consuming application to choose among a
collection of peer URLs. HALO exposes three canonical top-level action objects
and an explicit mapping from user intent to those objects:

| Intent | Canonical object | Role |
|---|---|---|
| Inspect the exact configured product | `inspectionAction` | Shopper-facing exact Shopify variant destination. It preserves the resolved configuration and does not place an order. |
| Express purchase intent | `shopperAction` | Buyer-controlled commerce handoff. For a `purchase_ready` product, its type is `open_cart` and its URL is the exact attributed Shopify cart permalink. Opening it prepares the selected configuration but does not place an order or collect payment. |
| Inspect the machine-readable evidence | `referenceAction` | HALO grounding and evidence resource. It is explicitly not a shopper destination. |

The corresponding `actionBindings` object identifies these relationships
structurally:

```json
{
  "actionBindings": {
    "inspectExactProduct": "inspectionAction",
    "explicitPurchaseIntent": "shopperAction",
    "inspectEvidence": "referenceAction"
  }
}
```

Compatibility fields such as `commerceLinks`, `urlRoles`, and `shopperActions`
remain available for existing consumers. The canonical action abstraction makes
their intended use explicit.

## Exact-resolution example

A completed fire-pit selection of **Square**, **Stackstone**, **Natural Gas**,
and **GFRC Polished Black Granite Finish** currently resolves to:

- SKU: `HB-FP-STK-BG-GAS-SQ`
- Shopify variant: `44680376287277`
- Price: `$4,332 USD`
- Availability: `available`

An abbreviated result has this shape:

```json
{
  "purchaseState": "purchase_ready",
  "actionBindings": {
    "inspectExactProduct": "inspectionAction",
    "explicitPurchaseIntent": "shopperAction",
    "inspectEvidence": "referenceAction"
  },
  "inspectionAction": {
    "type": "view_exact_product",
    "shopperFacing": true,
    "placesOrder": false,
    "url": "<exact attributed Shopify variant URL>"
  },
  "shopperAction": {
    "type": "open_cart",
    "shopperFacing": true,
    "buyerControlled": true,
    "placesOrder": false,
    "collectsPayment": false,
    "url": "<exact attributed Shopify cart permalink>"
  },
  "referenceAction": {
    "type": "inspect_evidence",
    "shopperFacing": false,
    "url": "<HALO exact-configuration evidence URL>"
  }
}
```

This is a protocol example, not a second catalog. Product identity, price,
availability, media, and action URLs remain subject to the live Shopify-backed
HALO result.

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
For an exact purchase-ready result, the durable presentation sequence is:

**product media → grounded facts and disclosures → eligible shopper handoff**

Product media is part of the resolved product presentation rather than optional
decorative metadata. When a compatible client cannot render native media, HALO
provides fallback presentation data so the grounded product identity and media
reference remain available. A cart link is not a substitute for product
presentation.

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

## Client capabilities and graceful degradation

HALO supports several consumption paths without assuming that every AI client
has the same retrieval, rendering, or tool-execution capabilities:

- **Native callable interface:** a compatible client can use HALO's structured
  tools for progressive qualification, exact resolution, Shopify-hosted media,
  live commerce data, and buyer-controlled handoff.
- **Zero-install web consumption:** a web-capable agent can discover Homebridge's
  first-party resources and consume HALO's public structured representations
  without establishing a native callable connection.
- **Ordinary storefront or search fallback:** conventional product pages remain
  available, but this path does not carry HALO's deterministic qualification and
  exact-resolution guarantees.

Client capabilities, retrieval behavior, and rendering support can change
independently of HALO. The public contracts describe available semantics without
claiming universal support from any particular AI vendor.

## Public and trusted interface boundary

HALO deliberately separates public discovery content from trusted callable
interface metadata.

Public web and discovery surfaces describe Homebridge's first-party merchant
authority, capabilities, field meanings, product and media provenance, evidence
roles, and buyer-handoff semantics. They do not purport to override a consuming
application's system or developer instructions, safety policies, or
prompt-injection protections.

Trusted MCP tool descriptions and structured callable contracts can apply
stricter operational safeguards: missing selections are not inferred,
buyer-confirmed choices are preserved, exact resolution precedes exact SKU and
price presentation, resolved media remains part of the result, grounding
boundaries are retained, and purchase intent maps to the appropriate exact
buyer-controlled handoff. This separation is intended to cooperate with client
security boundaries, not circumvent them.

## Commerce and availability boundaries

HALO can produce attributed product and cart links, but it cannot place an
order, submit payment, or bypass Shopify Checkout. Shopify remains authoritative
for buyer identity, shipping, taxes, discounts, payment, and final order
completion.

Many Homebridge products are made to order. Shopify inventory quantities may be
untracked while a variant remains available for sale. HALO describes these as
**available to order; made to order; lead time applies** rather than treating
untracked inventory as zero stock.

## Grounding and product-truth boundaries

Exact product claims originate from approved merchant sources and live
Shopify-backed records. General storefront prose or facts about similar products
do not establish configuration-specific truth. Missing or unconfirmed details
remain unknown rather than being inferred.

This boundary is particularly important for details such as burner inclusion or
manufacturer, BTU output, CSA status, exact warranty coverage, gas-installation
requirements, and other configuration-specific claims that lack an approved
exact-product source.

## Documentation-only repository

This repository intentionally contains public metadata and documentation only.
The HALO application source code, infrastructure, credentials, internal business
rules, and operational data are not published here.

See [SECURITY.md](SECURITY.md) and [PRIVACY.md](PRIVACY.md) for the public safety
and data-handling boundaries.


## Portable media contract — 2026-09-07

Exact SKU resolution keeps live Shopify identity, price, availability, primary media, and the buyer-controlled cart handoff together. Every media item exposes `url`, nullable `mimeType`, `width`, `height`, `relationship`, `association`, `associatedVariantIds`, `exactVariantDepictionVerified`, and `fidelityNote`. Existing `sources` and `previewImage` fields remain compatible.

A Shopify variant assignment is not proof that every selected option is visibly depicted. Variant-associated imagery is conservatively `representative`; unassociated gallery media is `product_family`. Preserve the fidelity note, including that staging accessories need not be included. No image is labeled an independently verified exact depiction.

Use the [bounded JSON gallery](https://agent-commerce.homebridgepc.com/v1/media?category=fire_pits&productHandle=homebridge-gfrc-concrete-fire-pit&sku=HB-FP-STK-BG-GAS-SQ&limit=6) or the [ordinary browser gallery](https://agent-commerce.homebridgepc.com/v1/media?category=fire_pits&productHandle=homebridge-gfrc-concrete-fire-pit&sku=HB-FP-STK-BG-GAS-SQ&limit=6&format=html). Both are anonymous read-only projections of Shopify. OpenAPI documents the request and shared media schema.

`get_homebridge_product_media` returns JSON/text HTTPS references without MCP resource links or embedded gallery image files. A second display call is unnecessary. `display_homebridge_product_media` remains an optional compatibility widget for clients that support it. Exact resolvers retain their existing optional single inline-image enhancement.

Remote rendering depends on the client. Never claim an image, gallery, card, or cart control is shown without actual client confirmation. Provide visible ordinary image/gallery links when rich rendering is unavailable, and always provide the eligible exact cart URL as a visible ordinary link. No universal ChatGPT, Gemini, Claude, or Perplexity rendering support is claimed.

Release identifier: `2026-09-07-portable-media-v1`. See [client acceptance tests](MEDIA_CLIENT_TESTS.md) for the exact external validation protocol and remaining limitations.
