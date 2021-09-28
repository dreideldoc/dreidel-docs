
Web apps
========

Web apps include a set of UI connected to system API endpoints to facilitate its customers with:

- Checkout payment app (wallet, pay-through options)
- Wallet web-application for fund storing and transferring
- Back-end app for business accounts with transaction history and settlement request form
- Admin app and analytics

Business account app
--------------------

Business account app is a checkout payment form with the following settings:

- Pay-through mode, customer payment information posts directly to the payment provider, specified for the business account (Visa/MasterCard/CUP ...)
- Top-up mode (staged), a customer tops up his wallet (first stage) then using stored funds pays business account's bill (charge request)
- One-tap, pre-conditions: a customer logged-in in its wallet (cookie installed to customer's browser or session persisted with mobile app)
  and has enough stored values to pay the bill. If pre-conditions fulfilled, then customer pays the bill with one tap in the app, being redirected to his wallet right away.

Checkout form rendering and visualization depend on which payment providers are connected (applied) to a business account.


Business account backend
------------------------

Back-end is a simple web-app where business account owner can track its transaction history, rate, request settlement, interact with support team

Management/Financial console
----------------------------

Management app is aimed to automate and help with day-to-day operations by providing the following functions:

- Account and profile review along with due diligence information, with blocking and approval options per account.
- Business account review and profiling, making manual corrections and updating account statuses (blocked, active, suspended).
- Settlement processing and reconciliation procedure support
- Charge back and customer claim management

Account settings and fraud filter management console
----------------------------------------------------

Web-app fully designated to support system critical settings and recommended for risk manage use only. The app provides system supervisor with the following options:

- Business account settings: Profile information, MCC code, available payment methods, checkout settings
- Overall system limits and thresholds
- Fraud prevention filtering rules: daily, monthly, lifetime limits
- Available/Disabled countries
- Bank (BIN) filters and blacklists
- Rate/Commission setting per account

Analytics and reporting system
------------------------------

Dynamic report builder with:

- Table rendering reports
- Graphs/Charts
- Alerts/Pulses

System used as day-to-day monitoring and alerting system as well as for management level periodic and analytical reports
