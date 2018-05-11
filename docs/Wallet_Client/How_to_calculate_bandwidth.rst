##########################
How to calculate bandwidth
##########################

The bandwidth calculation rule is：
----------------------------------

.. code-block:: shell

    constant * FrozenFunds * days

Calculation of bandwidth: frozen asset * days * constant.

Suppose 1 TRX is frozen (1,000,000 DROP) for a duration of 3 days, then bandwidth=1,000,00031=3,000,000.

All contracts consume bandwidth, including transfer, migration of asset, voting, freezing balance, etc. Inquiries do not consume bandwidth while for every contract about 100,000 bandwidths is consumed.

If a new operation exceeds a given amount of time (10s) from the last contract, if does not consume any bandwidth.

Bandwith is not removed for balance freezing. New bandwidths will be accumulated upon acts of balance freezing.