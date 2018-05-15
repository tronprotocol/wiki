==========
Wallet-Cli
==========

.. contents:: Table of contents
    :depth: 1
    :local:

Download java-tron and wallet-cli
---------------------------------

.. code-block:: shell

    git clone https://github.com/tronprotocol/java-tron.git

    git clone https://github.com/tronprotocol/wallet-cli.git

Build and run java-tron
-----------------------

.. code-block:: shell

    cd java-tron

    ./gradlew build

    ./gradlew run -Pwitness

Build and run wallet-cli by command line
----------------------------------------

Create a new command line terminal window.

.. code-block:: shell

    cd wallet-cli

    ./gradlew build

    ./gradlew run -Pcmd

Build and run web wallet
------------------------

.. code-block:: shell

cd wallet-cli

    ./gradlew build

    cd build

    cd libs

    java -jar wallet-1.0-SNAPSHOT.jar

How wallet-cli connects to java-tron
------------------------------------

Wallet-cli connect to java-tron by grpc protocol.

Java-tron nodes can be deployed locally or remotely.

We can set the connected java-tron node IP in config.conf of wallet-cli.

Java-tron provides grpc api list
--------------------------------

Please refer to the link for details.

https://github.com/tronprotocol/Documentation

rpc GetAccount (Account) returns (Account)

rpc CreateTransaction (TransferContract) returns (Transaction)

rpc BroadcastTransaction (Transaction) returns (Return)

rpc ListAccounts (EmptyMessage) returns (AccountList)

rpc CreateAccount (AccountCreateContract) returns (Transaction)

rpc VoteWitnessAccount (VoteWitnessContract) returns (Transaction)

rpc CreateAssetIssue (AssetIssueContract) returns (Transaction)

rpc ListWitnesses (EmptyMessage) returns (WitnessList)

rpc UpdateWitness (WitnessUpdateContract) returns (Transaction)

rpc CreateWitness (WitnessCreateContract) returns (Transaction)

rpc TransferAsset (TransferAssetContract) returns (Transaction)

rpc ParticipateAssetIssue (ParticipateAssetIssueContract) returns (Transaction)

rpc ListNodes (EmptyMessage) returns (NodeList)

rpc GetAssetIssueList (EmptyMessage) returns (AssetIssueList)

rpc GetAssetIssueByAccount (Account) returns (AssetIssueList)

rpc GetAssetIssueByName (BytesMessage) returns (AssetIssueContract)

rpc GetNowBlock (EmptyMessage) returns (Block)

rpc GetBlockByNum (NumberMessage) returns (Block)

rpc FreezeBalance (FreezeBalanceContract) returns (Transaction)

rpc UnfreezeBalance (UnfreezeBalanceContract) returns (Transaction)

rpc WithdrawBalance (WithdrawBalanceContract) returns (Transaction)

Web wallet host
---------------

    127.0.0.0:8088

**Note:** make sure the baseUrl configured in interface.js is what you want, for example 127.0.0.1:8088.

Wallet-cli supported command list
---------------------------------

RegisterWallet
--------------

RegisterWallet Password.Register a wallet in local.Generate a pair of ecc keys.Derive a AES Key by password and then use the AES algorithm to encrypt and save the private key.The account address is calculated by the public key sha3-256, and taking the last 20 bytes.All subsequent operations that require the use of a private key must enter the password.

ImportWallet
------------

ImportwalletByBase64

ChangePassword

Login

Logout

BackupWallet

BackupWallet2Base64

Getaddress

GetBalance

GetAccount

GetAssetissueByAccount

GetAssetIssueByName

SendCoin

TransferAsset

ParticipateAssetissue

Assetissue

CreateWitness

VoteWitness

FreezeBalance

UnfreezeBalance

WithdrawBalance

Listaccounts

Listwitnesses

Listassetissue

listNodes

GetAssetIssueByName

Getblock

Exit or Quit

help

**Input any one of then, you will get more tips.**

How to freeze/unfreeze balance
------------------------------

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

How to vote
-----------

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

How to calculate bandwidth
--------------------------

The bandwidth calculation rule is：
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: shell

    constant * FrozenFunds * days

    Calculation of bandwidth: frozen asset * days * constant.

Suppose 1 TRX is frozen (1,000,000 DROP) for a duration of 3 days, then bandwidth=1,000,00031=3,000,000.

All contracts consume bandwidth, including transfer, migration of asset, voting, freezing balance, etc. Inquiries do not consume bandwidth while for every contract about 100,000 bandwidths is consumed.

If a new operation exceeds a given amount of time (10s) from the last contract, if does not consume any bandwidth.

Bandwith is not removed for balance freezing. New bandwidths will be accumulated upon acts of balance freezing.

How to withdraw block producing reward
---------------------------------------

Upon complete block production, reward will be sent to allowance in user’s account. Withdrawal can be made once every 24 hours, transferring reward from allowance to balance. Asset in allowance cannot be locked or traded.

How to create TRX
-----------------

    You can gen one keypair and address by command line, then modify java-tron config.conf set genesis.block.assets address to yours.

    Now that you have a lot of trx, you can send it to any address.

    With enough trx, you can issue assets, participate in asset, apply for witnesses, and more.



How to create witness
---------------------

It takes 100,000 TRX to become establish a witness account. These TRX will be burnt immediately.

