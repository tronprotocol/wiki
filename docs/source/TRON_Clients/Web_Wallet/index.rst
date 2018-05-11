##########
Web_Wallet
##########

Quick Start
================================================================================

How to use
----------

**Requirements**

- Node v9.8.0
- Yarn

**Running**

.. code-block:: shell

    > yarn install

    > yarn start


The wallet should then be running on http://localhost:3000

**Changing the default API URL**

By default the Explorer will connect to http://localhost:3000 for its data.

When developing locally the url can be changed by defining the ``API_URL`` environment variable

.. code-block:: shell

    > API_URL=http://127.0.0.0:8088 yarn start

This should change the API_URL to point to your local ``wallet-cli`` server

Details
================================================================================

.. toctree::
    :hidden:

    What_is_a_Super_Representative.rst
    How_to_run_a_Super_Representative.rst
    How_to_vote.rst
    How_to_create_token.rst


