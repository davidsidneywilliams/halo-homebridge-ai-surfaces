# Security

HALO's public read tools expose approved product and configuration information.
They cannot place orders or collect payment.

Checkout-session creation is separately protected by OAuth scopes, explicit
buyer confirmation, merchant controls, quantity limits, and a global kill
switch. Shopify Checkout remains authoritative for buyer identity, shipping,
taxes, payment, and order completion.

Do not submit credentials, payment information, customer personal information,
or confidential business data to this documentation repository.

To report a security issue privately, use Homebridge's contact information at
<https://homebridgepc.com/pages/contact-us> and do not open a public issue that
contains exploit details, credentials, or personal information.

