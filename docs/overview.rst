System overview
===============

Abstract
--------

Dreidel pay is a simple payment service provider & fund storage (wallets) project with open architecture.

Easy to install, maintain and operate, this project contains only basic and mandatory functions
which could be used/deployed within a payment company.

The system performance is about support 10 TPS with basic (~90 USD worth) cloud web-hosting configuration.


Basic components
----------------

- Account and profile management including multi-level due diligence service
- Funds storage facility (wallet) service
- Core service (financial ledger)
- Fraud prevention and traffic filtering service
- 3d party connector framework
- Public payment API
- Web apps: checkout, wallet app, merchant's backend, management console, reports and analytics

UI and applications
-------------------

1) Checkout:

- Desktop/Mobile friendly payment web-interface (pay-through, pay on wallet top-up)
- Checkout form customization

2) Merchant back-end

- Simple merchant back-end app (transaction history, rates/commissions, settlement options)

3) Wallet app:

- Web Desktop/Mobile wallet interface
- Authentication via mobile/tex code confirmation
- Send/Ask money (p2p transfers)
- Pay merchant's invoice

4) Management console

- Profile and Due diligence customer management
- Reconciliation process
- Account settings
- Chargeback processing

5) Admin/Setting console

- Managing fraud filters
- Managing whitelists
- Business account settings
- Commission settings
- System general settings

6) Analytic/Reporting system

- Customizable reports
- Charts/Graphs
- Alerts and notifications
- Data export (PDF, CSV, etc formats)

Roles
-----

- Busness account (merchant), can use back-end and Public API
- Client service manager, can access management console and Reporting system
- Risk manager, can access Admin console and Reporting system

Architecture and design
-----------------------

1) Tech stack

- Rancher 2.0
- Kubernetes
- Kafka
- Ruby on Rails 4.6
- PostgreSQL

2) Services

- Public API
- Core service
- Settings
- Profile and accounts
- Fraud prevention and traffic filtering

Security and encryption
-----------------------

- Public API requests are optionally secured with RSA-SHA256
- Intra service communication secured by DMZ network architecture and service-to-service authentication
- Sensitive data and customer private data both are encrypted in database and could be stored on dedicated location
  according to local regulatory requirements
- DreidelPay is PCI DSS compatible solution
