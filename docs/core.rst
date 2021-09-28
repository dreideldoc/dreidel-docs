Core service
============

- Core service is a simple transaction ledger which provides basic functions for payment processing.
- The service communicates only with Public API service and 3d party connectors.
- Service should be deployed in DMZ network zone and protected with encryption and Service-to-Service authentication mechanism
- Money stored in cents (atomic currency unit)

Entries or ledger record
------------------------

Ledger structure:

- Operations, represents sufficient customer's operation on the wallet.
- Wallet requests (any request to the service, contains information about initial request: type, amount, currency, etc)
- Entries, an atomic ledger record consists of debit and credit source, type, amount, currency, input/output balance
- Entries are formed accordingly to the wallet request type an account settings (commission, operation type)
- Each entry is linked to: the operation, wallet request, wallet itself

Transaction entry flow
----------------------

1. Classy payment on merchant web-site

- Operation 1 of type 'charge' is created (invoicing a client)
- No entry record created
- Operation 2 of type 'pay' is created (paying the invoice) and linked to Operation 1
- Entry 1 of 'hold' type is created on customer's wallet (funds moved from actual customer's balance to the system designated for holdings wallet)
- Entry 2 created with type 'commission' (commission amount is moved from merchant's wallet to the system designated wallet)
- Request to 3d party gateways is sent and logged
- Entry 3 with type 'pay' (funds are moved from system hold wallet to a merchant's wallet)
- Operation status updated
- Result posted back to Public API which is sending notification to the merchant

2. Money transfer (p2p)

3. Payouts/Settlements

Entry types
-----------

Entries could be of the following types:

- hold
- transfer
- pay
- commission
- payout

Entry direction is defined by Debit (deduct funds) to Credit (fund the account) cash flow concept.

Immutability
------------

Entries are not a subject of any modifications, and meant to be persistent and immutable data.
