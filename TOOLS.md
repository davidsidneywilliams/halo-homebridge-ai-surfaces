# Public interfaces

HALO is zero-install first. Its public HTTP interfaces can be discovered by
ordinary AI/search agents without an MCP connection, while the remote MCP server
provides an optional native tool surface.

## Zero-install HTTP surface

| Interface | Purpose | Authentication |
|---|---|---|
| `/.well-known/halo-zero-install.json` | Canonical discovery contract and capability links. | None |
| `/v1/discovery` | Machine-readable overview of the public surface. | None |
| `/discover` | Human- and crawler-readable discovery index. | None |
| `/discover/{category}` | Crawlable category landing page with structured product data and actions. | None |
| `/v1/catalog` | Lists approved major categories. | None |
| `/v1/catalog/{category}` | Returns approved live products and options for one category. | None |
| `/v1/configure/fire-pit` | Qualifies a partial fire-pit request or resolves a completed configuration. | None |
| `/v1/resolve` | Resolves exact major-category options to a live Shopify variant. | None |
| `/v1/videos` | Returns approved brand- and category-level video associations. | None |
| `/openapi.json` | Describes the public HTTP contract. | None |

## Optional MCP tool surface

| Tool | Purpose | Authentication |
|---|---|---|
| `get_halo_connection_status` | Reports the live release and available HALO tools. | None |
| `list_homebridge_categories` | Lists approved major categories. | None |
| `get_approved_homebridge_offer` | Reads an enabled controlled exact offer by SKU. | None |
| `configure_homebridge_fire_pit` | Qualifies or resolves a fire-pit configuration against live Shopify data. | None |
| `get_homebridge_major_category_catalog` | Returns approved products and live options for a major category. | None |
| `resolve_homebridge_major_variant` | Resolves selected options to a live variant and eligible commerce links. | None |
| `get_homebridge_product_media` | Returns bounded Shopify media and exact-variant product-card data. | None |
| `display_homebridge_product_media` | Displays the resolved read-only product card in compatible clients. | None |
| `prepare_homebridge_checkout` | Prepares a buyer-controlled Shopify checkout handoff after confirmation. | OAuth |

## Example zero-install request

An agent can inspect the discovery contract, read the fire-pit options, and ask
for any missing body, tabletop finish, fuel, or shape. Once complete, it can
resolve the selection to an exact SKU, price, Shopify-hosted image, availability,
disclosures, product URL, and eligible cart URL.

The live Shopify catalog remains authoritative for price, availability,
shipping, taxes, discounts, and payment.
