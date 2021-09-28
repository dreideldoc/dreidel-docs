Installation
============

To learn more about submodules check out the [following link](https://github.blog/2016-02-01-working-with-submodules/)

To clone all repos at once just run:

.. code-block:: bash

    git clone --recurse-submodules -j8 git@gitlab.com:reactive-pay/rpay-compose.git

Put an `.env` file for each service folder. It will allow to easily setup ENV variables for each service in further.

Docker install
--------------

Install docker on your local machine: https://www.docker.com/community-edition#/download

Then start building your services:

.. code-block:: bash

    docker-compose build

Once it finished we need to setup some basic data.
Each service has the same name as project's folder name, it's very useful when you enter docker containers.

Setup rpay-business
--------------------
.. code-block:: bash

    docker-compose run --rm rpay-business bash
    rake db:create
    rake db:migrate
    rake db:seed
    rake rpay:setup_db_data
    exit

If something went wrong with development data, you can try to clean the database using the following rake task:

.. prompt:: bash $

    rake db:clear

It clears all data but does not drop the database, so you can start over `rake db:migrate` again.

Setup rpay-core
----------------

.. code-block:: bash

    docker-compose run --rm rpay-core bash
    rake db:create
    rake db:migrate
    rake db:seed
    rake rpay:setup_db_data
    rake rpay:add_demo_business_account
    exit

And again here, if something went wrong with development data, try again with `rake db:clear`.

Setup rpay-settings
--------------------

.. code-block:: bash

    docker-compose run --rm rpay-settings bash
    rake db:create
    rake db:migrate
    rake db:seed
    exit

Setup rpay-guard
-----------------

For guard service there is no specific setup procedure.

Get services up and running
----------------------------

.. code-block:: bash

    docker-compose up

Final checks
------------

Check that services are reachable for each other.
To do that, enter into each container and try to reach other service via `RestClient`

.. warning:: you should get services up and running in the first place to be able reaching out multiple services from separate console


Install ReactivePay cluster
---------------------------

Requirements:

- Subdomain name, ready to attached to the cloud infrastructure
- Account to a cloud data hosting services (AWS/AliCloud/VMSphere)
- Define "Ansible" settings for network environment setup

Run:

.. code-block:: bash

    {{ ansible_root }}/\!_stand-recreate.sh {{ ansible_environment }} {{ product_name }} USERNAME PASS {{ NOWAIT }} {{ TYPE_OF_RUN }} {{ cloud_type }}

Managing docker containers
--------------------------

Minimal hosting requirements
----------------------------
