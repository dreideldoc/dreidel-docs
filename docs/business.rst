Public API
==========

ReactivePay public API is designed for interaction between business account and the system.
It allows business account to start accepting payments for its services through various payment methods and in different apps and interfaces.

API use cases
-------------

- Checkout iframe on merchant's web-site
- Direct payment via merchant's apps
- Wallet payments via merchant's apps
- System events async notification
- Reading payment history on business account
- Reverse and refund operations

Payment request flow
--------------------

1. Simple checkout/pay-through

- A merchant (business account) hits API payment endpoint to create charge request (invoice) for a customer
- API response contains payment information along with checkout URL
- A merchant sends customer to checkout URL
- A customer completes payment with his wallet or with the card
- A merchant receives notification with payment status and makes the delivery

2. Direct payment flow

- A merchant sends payment details, such as: card number, wallet authorization info to payment API
- The system processes payment according to the merchant's settings
- A merchant receives notification with payment status and makes the delivery

Request encryption
-------------------

There is an option to encrypt all requests to the API with public/private key based on SHA-512 hash and PKCS standards

This option is strongly recommended to secure your payment execution via API as well as to validate the request origin
and persist this validation throughout request/response interaction chain

If encryption is disabled, then IP filtering is applied.

All communication process between merchant and API is wrapped with SSL/TSL protocol, no unsecured notification URLs are allowed within the system

Payment request snapshot
------------------------

Every API request within the system is logged, system has a complete snapshot for every request including request headers and body.
System use this information for further potential fraud pattern analysis and client claim investigation.
