##############################
How to freeze/unfreeze balance
##############################

Once balance is frozen, users will received a proportionate amount of shares and bandwidth.

The shares are your votes and bandwidth is used for transactions.

Their usage and means of calculation will be introduced in following sections.

**The freeze command is as follows:**

.. code-block:: shell

    freezebalance password amount time

``amount``: freeze balance in drops, with a minimum of 1_000_000drops, equivalent to 1 TRX.


``time``: frozen time, the interval between freezing asset and unfreezing is at least 3 days.

For example：

.. code-block:: shell

    freezebalance 123455 10000000 3


Frozen assets will transfer from account Balance to Frozen, which will be reversed once balance unfreezes. Frozen assets cannot be used for transactions.

When in need of more shares or bandwidth, users can freeze more balance to obtain more shares and bandwidth. Date to unfreeze balance will be renewed to 3 days after the latest freeze.

Assets can be unfrozen after the date to unfreeze.


**Unfreeze command is as follows:：**

.. code-block:: shell

    unfreezebalance password
