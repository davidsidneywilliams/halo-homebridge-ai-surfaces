# Public tool surface

HALO's remote MCP server currently exposes these public discovery and
configuration capabilities:

| Tool | Purpose | Authentication |
|---|---|---|
| `list_homebridge_categories` | Lists Homebridge's approved major categories. | None |
| `get_approved_homebridge_offer` | Reads an enabled controlled exact offer by SKU. | None |
| `configure_homebridge_fire_pit` | Resolves an exact fire-pit configuration against live Shopify data. | None |
| `get_homebridge_major_category_catalog` | Returns approved products and exact live options for a major category. | None |
| `resolve_homebridge_major_variant` | Resolves selected major-category options to a live Shopify variant and eligible links. | None |
| `prepare_homebridge_checkout` | Creates a buyer-controlled Shopify checkout handoff after explicit confirmation. | OAuth |

## Example discovery request

Ask an MCP-capable client to use HALO to configure a round architectural fire
pit with a Corten Steel body, a GFRC Polished Black Granite Finish tabletop, and
propane fuel. Request the exact SKU, current price, availability, disclosures,
and direct link, without creating a checkout.

The live Shopify catalog remains authoritative for price, availability,
shipping, taxes, discounts, and payment.

