Operations
==========

To perform system admin and management functions the following UI web applications are provided:

1. Analytics, transaction history, system performance, wallet monitoring, etc

    `ReactivePay analytics <https://metabase.reactivepay.com/>`_

2. System settings

- Setting up business account parameters such as: 3d party gateway connection params
- Currency conversion rules
- Payment routing strings

    `Settings console <https://settings.reactivepay.com/settings/admin>`_

3. Management console

- Managing customer KYC process
- Adding new business accounts
- Oversee business account finacial performance
- Business account settlements
- Dispute managment

    `Managment console <https://core.reactivepay.com/manage>`_

4. Admin console (only for advanced users)

- Adding new system administrators
- Setting up commission values to an account
- Modifying customer profile data
- Adding/Modifying various system data entities (counrty, currency lists)

    `Admin console <https://core.reactivepay.com/admin>`_

5. Business account backoffice

    `Backoffice console <https://core.reactivepay.com/office>`_

5. Demo-shop demonstrating a simple business account integration

    `Demo-shop for checkout demonstration <https://demo.reactivepay.com/demo>`_

Creating a business account
---------------------------

Login to manage interface following the link:

    `Managment console <https://core.reactivepay.com/manage>`_

.. image:: img/manage_login.png

Navigate to Merchants menu on the left

.. image:: img/manage_merchants.png

Tap add merchant button and fill the form below:

.. image:: img/manage_merchants_add.png

- Email should be a uniqe one withing the system database (can't create 2 merchants with same email)
- Phone number should be in the following format: +8612345678 (+[code][number])
- Settlement info could be filled later, and also accesible on merchant backoffice page
- We reccommend to generate a strong password for an account using strong password gen for example

Find merchant in the list and tap edit icon on the right row menu

* please note that the info like private key and merchant token is a private one, and should be sent directly to a merchant by an account manager, this information should not be disclosed to any 3d parties * 

.. image:: img/manage_merchants_view.png

Adjusting commission 
--------------------

You can adjust commission schedule for any payment type using flexy-commission service.

This service works using flexy-guard rule filtering enging where instead of setting up the rules, you post commissions using
the following JSON format:

.. code-block:: none

        {
            "header": {
                "type": "PayinRequest"
            },
            "body": {
                "self": {
                    "rate": "0.5",
                    "fee": "1"
                },
                "provider": {
                    "rate": "0.4",
                    "fee": "0.3"
                }
            }
        }

Where header section identifies payment request params to fetch commission schedule for and body contains of "self" (commssion charged by the system) and "provider" (commission charged by payment provider) sections
These sections contain commission schedule defined by the following keywords:

**rate** - rate is % based commission fee (like: 0.5%, 0.6%)

**fee** - tand fee is fixed price commission fee (like: 0.1 USD, 0.4 USD)

Please note that no currecny or percentage symbol should be posted along with a float number

To perform initial service setup please follow the steps:

1. Post definition section (defines payment parameters to fetch commission sch. for)

.. image:: img/fl_d.png

.. code-block:: none

    [
    {
        "param": {
        "name": "to_profile",
        "param": {
            "name": "source",
            "param": {
            "name": "type"
            }
        }
        }
    },
    {
        "param": {
        "name": "type"
        }
    },
    {
        "param": {
        "name": "to_profile",
        "param": {
            "name": "source",
            "param": {
            "name": "type",
            "param": {
                "name": "country_bank"
            }
            }
        }
        }
    }
    ]
    
2. Post basic commission schedule

.. image:: img/fl_c.png

.. code-block:: none

    {
    "header": {
        "type": "PayinRequest"
    },
    "body": {
        "self": {
        "rate": "0.5",
        "fee": "1"
        },
        "provider": {
        "rate": "0.4",
        "fee": "0.3"
        }
    }
    }

More commission schedule examples are below:

- commission schedule depends on profile, payment source (channel, type, country of issuer institution)

.. code-block:: none

    {
    "header": {
        "to_profile": "3",
        "source": "default",
        "type": "PayinRequest",
        "country_bank": "RU"
    },
    "body": {
        "self": {
        "rate": "2.2",
        "fee": "10"
        },
        "provider": {
        "rate": "1.1",
        "fee": "5"
        }
    }
    }

- commission schedule depends on profile, payment source (channel, type)

.. code-block:: none

    {
    "header": {
        "to_profile": "3",
        "source": "default",
        "type": "PayinRequest"
    },
    "body": {
        "self": {
        "rate": "2.2",
        "fee": "10"
        },
        "provider": {
        "rate": "1.1",
        "fee": "5"
        }
    }
    }


Handling disputes
-----------------

On-going payment monitoring
---------------------------