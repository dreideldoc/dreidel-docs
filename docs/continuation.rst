Continuation and backup
=======================

ReacitvePay sustainability is based on the following principles:

- strong backup policies shall be implemented upon deployment
- fail-over cluster shall be an initial database setup architecture
- we strongly recommend to use Cloud based hosting solutions as hosting facilities
- apply version control along with CI practices
- use external and internal scanners which are intended to identify vulnerabilities in timely manner
- use distributed cluster for smooth Blue/Green deployment scheme

Database failover
-----------------

We deploy external network based solution for PostgreSQL database cluster, based on independent witness server which
identifies primary/standby patterns and switches in case network or data fail.

Personal and sensitive data backups
-----------------------------------

- Personal data is backed-up according general backup policies which include daily incremental and weekly full backup schedule
- Personal data is encrypted and stored separately in areal database (according to local regulations)
- We perform the same backup policies on transaction historical data, payment logs and interaction logs.

Continuous integration and service sustainability
-------------------------------------------------

The system contains the following tests and fully adopted for continuous deployment:

- Web apps Selenium based UI auto-tests
- Intra services API integration tests
- Critical cash flow unit tests
- Public API integration auto-tests
- Stress and system performance tests

Blue/Green deployment strategy
------------------------------

We are using Blue/Green deployment approach for deployment process to avoid critical payment data loss on upgrade or release events.
The system could be installed in two isolated environments with single databases access point and forth and back migration compatibility support.

This pattern allows immediate roll-back-forth by switching between two networks. This approach affects system sustainability overall.
