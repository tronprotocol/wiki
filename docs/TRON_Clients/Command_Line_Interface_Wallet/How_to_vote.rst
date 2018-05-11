How to vote
----------------------------------

Voting requires shares, which can be obtained through balance freezing.

- Calculation of shares: 1 share for 1 frozen TRX. 
- Once unfrozen, previous votes casted will be invalid, which can be prevented by refreezing balance.

**Note:** TRON network only keeps record of the latest votes, meaning that every new vote you make will replace all previous records.

Example：

.. code-block:: shell

    freezebalance 123455 10_000_000 3// 10 shares for 10 frozen TRX

    votewitness123455 witness1 4 witness2 6//4 votes for witness1 and 6 votes for witness2

    vote witness 123455 witness1 10// 10 votes for witness1

The final result of the above commands is 10 votes for witness1 and no vote for witness2.
