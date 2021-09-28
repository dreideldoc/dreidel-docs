Client account and profile
==========================

Basic principles
----------------

Every payment request which is identified with unique parameters considered to be a separate account/profile entity within the system.
Accounts and profile data are initially collected from payment request headers and body parameters.

If account already exists in database then decision based on payment flow settings is made and a customer goes
through pay-through flow or through wallet funding first process.

Each transaction/payment processing flow is tagged/marked with designated to this flow account.

Each account includes profile date (phone number, name, email, supportive documents, date of birth, etc)


Client due diligence
--------------------

- Client requires to perform due diligence within the system once overall turn-over on its wallet exceeds pre-defined threshold
- By due diligence we mean verification and validation of customer personal data
- Client verification includes: phone number, email, name, date of birth
- Client validation includes: person identification (id document), proof of address, proof of funds, proof of card possession.
- Client validation is automatically performed using authorized 3d party service providers (Face recognition, MRZ recognition, Address validation services)
- Risk management team tracks validation performance using dedicated web interface and have an option manually chang validation statuses for specific customers.
- Client due diligence is applied to individuals, business representative and commercial entities

Account types
-------------

1) Pale account

  a) Pale account type is assigned to an account in case of pay-through payment mode enabled,
     where no information for comprehensive verification process is collected
  b) Client due diligence procedure is not applicable to this type of accounts
  c) Pale account profile information depends on payment method choice
    (ex. if classic credit/debit card is chosen then cardholder name will be collected and assigned to the profile name field)
  d) Pale account type could be converted to any account type by collecting additional info from the client
  e) Pale account type describes an account as the weakest related to risk and fraud protection of its type

2) Personal account

  a) Personal account type requires phone number, email and client name verification to be accomplished
  b) Client due diligence procedure is applicable and presented by simplified process of phone number validation with a text code
  c) Personal accounts considered to be verified and partially validated
  d) Personal account type has a pre-defined lifetime turn-over limit, breaching which triggering Green account upgrade process

3) Green account

  a) Green account is a personal account which has been fully verified and validated
  b) Green account type has a pre-defined lifetime turn-over limit

4) Business account

  a) Assigned to a commercial clients, traders, merchants
  b) Enhanced due diligence process including beneficiary identification and legitimacy of operations
     is performed on each account of this type
  c) Business accounts have access to API endpoints to process payments
  d) Business accounts are the subject of merchant fraud prevention system and shall be framed with number of limits
     (transaction amount, average ticket size, allowed countries, etc)
