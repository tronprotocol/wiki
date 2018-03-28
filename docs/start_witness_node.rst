===========
Start Witness Node
===========

.. contents:: Table of contents
  :depth: 1
  :local:

Witness node, join the testnet. Get block information from the testnet and execute it as a booker.

**Steps**

1. create an account using wallet-api, and apply to become a witness;

  1. Create an account using wallet-api;
  2. Transfer at least 100 assets from the existing account to the new account.(Account applying for a witness requires at least 100 assets);
  3. Apply as a witness;
  4. Voting to the witness, when the number of votes cast is in the top 21, it will become the witness at the next maintenance (interval 24h):

After the account is applied for as the witness, the service node can be started. Before the next maintenance period, the node will only synchronize the blocks and not producing block.

2. Start the service node.

  1. ``seed.node.ip.list``. The default is the seed node of the public test chain, which is not modified here;
  2. ``genesis.block.witnesses``, which is not modified here;
  3. ``genesis.block.timestamp``, which is not modified here;
  4. ``localWitness``. Configure the private key of the newly applied account;
  5. Add ``--witness`` to the startup parameter to specify this node as the witness node;
  6. Start the service(``./gradlew run -Pwitness``).