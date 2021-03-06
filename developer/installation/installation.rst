Installation
============

Development environment
-----------------------

This project has full support for running in Docker.

Go to the Docker directory:

.. code-block:: bash

    $ cd docker

Execute below command to run the application:

.. code-block:: bash

    $ docker-compose -f docker-compose.yml -f docker-compose.dev.yml up

Then use another command to setup the database, Elasticsearch and load some demo data:

.. code-block:: bash

    $ docker-compose exec php phing setup

Before start using Open Loyalty, you need to define hosts in your local environment.
Add host ``openloyalty.localhost`` as ``127.0.0.1`` in your system configuration file.
On the Linux it would be ``/etc/hosts``.

If you find any problems using Docker (for example on Windows environments), please try our Vagrant recipe.

After starting Open Loyalty in developer mode, it's exposed services under slightly different URLs:

``http://openloyalty.localhost:8081/admin - the administration panel``
``http://openloyalty.localhost:8081/client - the customer panel``
``http://openloyalty.localhost:8081/pos - the merchant panel``
``http://openloyalty.localhost - RESTful API port``
``http://openloyalty.localhost/app_dev.php/doc - swagger-like API doc``
``http://openloyalty.localhost:8086/ - the MailHog that cachets all e-mails``

.. note::

    After running docker-compose up you may wonder when it’s ready to use because you’ve got a message that keeps
    appearing all the time. It’s perfectly fine to see the message ``open_loyalty_mail | [APIv1] KEEPALIVE /api/v1/events``.
    This message is shown my MailHog which is listening for incoming e-mail messages. Open Loyalty in the development mode
    doesn’t send e-mail to the world. All the e-mails are caught by MailHog. Learn more about
    `MailHog <https://github.com/mailhog/MailHog>`_.

If you don’t want to see messages from running containers run a docker-compose as a daemon ``docker-compose up -d``

Production environment
----------------------

This project has full support for running in Docker.

Go to the Docker directory:

.. code-block:: bash

    $ cd docker

Execute below command to run the application:

.. code-block:: bash

    $ docker-compose up

Then use another command to setup the database, Elasticsearch and load some demo data:

.. code-block:: bash

    $ docker-compose exec php phing setup

Before start using Open Loyalty, you need to define hosts in your local environment.
Add host ``openloyalty.localhost`` as ``127.0.0.1`` in your system configuration file.
On the Linux it would be ``/etc/hosts``.

If you find any problems using Docker (for example on Windows environments) please try our Vagrant recipe.

After starting Open Loyalty it's exposed services under following URLs:

``http://openloyalty.localhost:8182 - the administration panel``
``http://openloyalty.localhost:8183 - the customer panel``
``http://openloyalty.localhost:8184 - the merchant panel``
``http://openloyalty.localhost:8181 - RESTful API port``
``http://openloyalty.localhost:8181/doc - swagger-like API doc``
``http://openloyalty.localhost:8086/ - the MailHog that cachets all e-mails``

Kubernetes
----------

Not described yet.

Quick install with Vagrant
--------------------------

You should have Vagrant and Virtualbox installed prior to executing this recipe.

Then, please execute the following commands:

.. code-block:: bash

    $ vagrant up
    $ vagrant ssh
    $ docker-compose -f docker/docker-compose.yml up -d
    $ docker-compose -f docker/docker-compose.yml exec php phing demo

That's all. Now, you can go to the admin panel ``openloyalty.localhost:8182``.
The default login is admin and password open. You can also go to the customer panel ``openloyalty.localhost:8183``.
