# Security

HALO's public discovery, catalog, configuration, media, video, and resolver
interfaces expose approved product information. They can generate attributed
product and eligible Shopify cart URLs, but they cannot place orders, submit a
checkout, or collect payment.

Any protected checkout-session action is separately governed by OAuth scopes,
explicit buyer confirmation, merchant controls, quantity limits, and a global
kill switch. Shopify Checkout remains authoritative for buyer identity,
shipping, taxes, discounts, payment, and order completion.

Do not submit credentials, payment information, customer personal information,
or confidential business data to this documentation repository.

To report a security issue privately, use Homebridge's contact information at
<https://homebridgepc.com/pages/contact-us> and do not open a public issue that
contains exploit details, credentials, or personal information.
