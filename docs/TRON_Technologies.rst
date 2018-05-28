=================
TRON Technologies
=================

.. contents:: Table of contents
    :depth: 1
    :local:

Protobuf protocol
-----------------

The protocol of TRON is defined by Google Protobuf and contains a range of layers, from account, block to transfer.

+ There are 3 types of account—basic account, asset release account and contract account, and attributes included in each account are name, types, address, balance and related asset.
+ A basic account is able to apply to be a validation node, which has serval parameters, including extra attributes, public key, URL, voting statistics, history performance, etc.

    There are three different ``Account types``: ``Normal``, ``AssetIssue``, ``Contract``.

.. code-block:: shell

      enum AccountType { 
         Normal = 0; 
         AssetIssue = 1; 
         Contract = 2;
       }

An ``Account` contains 7 parameters:

``account_name``: the name for this account – e.g. “*BillsAccount*”.

``type``: what type of this account is – e.g. *0* stands for type ``Normal``.

``balance``: balance of this account – e.g. *4213312*.

``votes``: received votes on this account – e.g. *{(“0x1b7w…9xj3”,323), (“0x8djq…j12m”,88),…,(“0x82nd…mx6i”,10001)}*.

``asset``: other assets except TRX in this account – e.g. *{<“WishToken”,66666>,<”Dogie”,233>}*.

``latest_operation_time``: the latest operation time of this account.

.. code-block:: shell

      // Account 
      message Account { 
        message Vote { 
           bytes vote_address = 1; 
           int64 vote_count = 2;   } 
        bytes accout_name = 1; 
        AccountType type = 2; 
        bytes address = 3; 
        int64 balance = 4; 
        repeated Vote votes = 5; 
        map<string, int64> asset = 6;
        int64 latest_operation_time = 10; 
       }

A ``Witness`` contains 8 parameters:

``address``: the address of this witness – e.g. “*0xu82h…7237*”.

``voteCount``: number of received votes on this witness – e.g. *234234*.

``pubKey``: the public key for this witness – e.g. “*0xu82h…7237*”.

``url``: the url for this witness – e.g. “*https://www.noonetrust.com*”.

``totalProduced``: the number of blocks this witness produced – e.g. *2434*.

``totalMissed``: the number of blocks this witness missed – e.g. *7*.

``latestBlockNum``: the latest height of block – e.g. *4522*.

``isjobs``: a bool flag.

.. code-block:: shell

      // Witness 
      message Witness{ 
        bytes address = 1; 
        int64 voteCount = 2; 
        bytes pubKey = 3; 
        string url = 4; 
        int64 totalProduced = 5; 
        int64 totalMissed = 6; 
        int64 latestBlockNum = 7; 
        bool isJobs = 9;
       }

+ A block typically contains transaction data and a blockheader, which is a list of basic block information, including timestamp, signature, parent hash, root of Merkle tree and so on.

A block contains ``transactions`` and a ``block_header``.

``transactions``: transaction data of this block.

``block_header``: one part of a block.

.. code-block:: shell

      // block
      message Block { 
         repeated Transaction transactions = 1; 
         BlockHeader block_header = 2; 
       }

A ``BlockHeader`` contains ``raw_data`` and ``witness_signature``.

``raw_data``: a ``raw`` message.

``witness_signature``: signature for this block header from witness node.

A message ``raw`` contains 6 parameters:

``timestamp``: timestamp of this message – e.g. *14356325*.

``txTrieRoot``: the root of Merkle Tree in this block – e.g. “*7dacsa…3ed*.”

``parentHash``: the hash of last block – e.g. “*7dacsa…3ed*.”

``number``: the height of this block – e.g. *13534657*.

``witness_id``: the id of witness which packed this block – e.g. “*0xu82h…7237*”.

``witness_address``: the address of the witness packed this block – e.g. “*0xu82h…7237*”.

.. code-block:: shell

      message BlockHeader { 
        message raw { 
          int64 timestamp = 1; 
          bytes txTrieRoot = 2; 
          bytes parentHash = 3; 
          //bytes nonce = 5; 
          //bytes difficulty = 6; 
          uint64 number = 7; 
          uint64 witness_id = 8; 
          bytes witness_address = 9; 
         } 
        raw raw_data = 1; 
        bytes witness_signature = 2; 
       }

message ``ChainInventory`` contains ``BlockId`` and ``remain_num``.

``BlockId``: the identification of block.

``remain_num``：the remaining number of blocks in the synchronizing process.

A ``BlockId`` contains 2 parameters:

``hash``: the hash of block.

``number``: the height of block.

.. code-block:: shell

       message ChainInventory {
            message BlockId {
               bytes hash = 1;
               int64 number = 2;
             }
             repeated BlockId ids = 1;
             int64 remain_num = 2;
          }

+ Transaction contracts mainly includes account create contract, account update contract transfer contract, transfer asset contract, vote asset contract, vote witness contract, witness creation contract, witness update contract, asset issue contract, participate asset issue contract and deploy contract.

An ``AccountCreateContract`` contains 3 parameters:

``type``: What type this account is – e.g. _0_ stands for ``Normal``.

``account_name``: the name for this account – e.g.”*Billsaccount*”.

``owner_address``: the address of contract owner – e.g. “*0xu82h…7237*”.

.. code-block:: shell

         message AccountCreateContract { 
           AccountType type = 1; 
           bytes account_name = 2; 
           bytes owner_address = 3; 
          }

A ``AccountUpdateContract`` contains 2 paremeters:

``account_name``: the name for this account – e.g.”*Billsaccount*”.

``owner_address``: the address of contract owner – e.g. “*0xu82h…7237*”.

.. code-block:: shell

         message AccountUpdateContract {
           bytes account_name = 1;
           bytes owner_address = 2;
          }

A ``TransferContract`` contains 3 parameters:

``amount``: the amount of TRX – e.g. *12534*.

``to_address``: the receiver address – e.g. “*0xu82h…7237*”.

``owner_address``: the address of contract owner – e.g. “*0xu82h…7237*”.

.. code-block:: shell

         message TransferContract { 
           bytes owner_address = 1; 
           bytes to_address = 2; 
           int64 amount = 3;
          }

A ``TransferAssetContract`` contains 4 parameters:

``asset_name``: the name for asset – e.g.”*Billsaccount*”.

``to_address``: the receiver address – e.g. “*0xu82h…7237*”.

``owner_address``: the address of contract owner – e.g. “*0xu82h…7237*”.

``amount``: the amount of target asset - e.g.*12353*.

.. code-block:: shell

         message TransferAssetContract { 
           bytes asset_name = 1; 
           bytes owner_address = 2; 
           bytes to_address = 3; 
           int64 amount = 4; 
          }

A ``VoteAssetContract`` contains 4 parameters:

``vote_address``: the voted address of the asset.

``support``: is the votes supportive or not – e.g. *true*.

``owner_address``: the address of contract owner – e.g. “*0xu82h…7237*”.

``count``: the count number of votes- e.g. *2324234*.

.. code-block:: shell

         message VoteAssetContract { 
           bytes owner_address = 1; 
           repeated bytes vote_address = 2; 
           bool support = 3; 
           int32 count = 5; 
          }

A ``VoteWitnessContract`` contains 4 parameters:

``vote_address``: the addresses of those who voted.

``support``: is the votes supportive or not - e.g. *true*.

``owner_address``: the address of contract owner – e.g. “*0xu82h…7237*”.

``count``: - e.g. the count number of vote – e.g. *32632*.

.. code-block:: shell
         
         message VoteWitnessContract { 
           bytes owner_address = 1; 
           repeated bytes vote_address = 2; 
           bool support = 3; 
           int32 count = 5;
           }

A ``WitnessCreateContract`` contains 3 parameters:

``private_key``: the private key of contract– e.g. “*0xu82h…7237*”.

``owner_address``: the address of contract owner – e.g. “*0xu82h…7237*”.

``url``: the url for the witness – e.g. “*https://www.noonetrust.com*”.

.. code-block:: shell

         message WitnessCreateContract { 
           bytes owner_address = 1; 
           bytes private_key = 2; 
           bytes url = 12; 
          }

A ``WitnessUpdateContract`` contains 2 parameters:

``owner_address``: the address of contract owner – e.g. “*0xu82h…7237*”.

``update_url``: the url for the witness – e.g. “*https://www.noonetrust.com*”.

.. code-block:: shell

         message WitnessUpdateContract {
            bytes owner_address = 1;
            bytes update_url = 12;
          }

An ``AssetIssueContract`` contains 11 parameters:

``owner_address``: the address for contract owner – e.g. “*0xu82h…7237*”.

``name``: the name for this contract – e.g. “Billscontract”.

``total_supply``: the maximum supply of this asset – e.g. *1000000000*.

``trx_num``: the number of TRONIX – e.g.*232241*.

``num``: number of corresponding asset.

``start_time``: the starting date of this contract – e.g.*20170312*.

``end_time``: the expiring date of this contract – e.g. *20170512*.

``decay_ratio``: decay ratio.

``vote_score``: the vote score of this contract received – e.g. *12343*.

``description``: the description of this contract – e.g.”*trondada*”.

``url``: the url of this contract – e.g. “*https://www.noonetrust.com*”.

.. code-block:: shell

         message AssetIssueContract { 
           bytes owner_address = 1; 
           bytes name = 2; 
           int64 total_supply = 4; 
           int32 trx_num = 6; 
           int32 num = 8; 
           int64 start_time = 9; 
           int64 end_time = 10; 
           int32 decay_ratio = 15; 
           int32 vote_score = 16; 
           bytes description = 20; 
           bytes url = 21; 
          }

A ``ParticipateAssetIssueContract`` contains 4 parameters:

``owner_address``: the address for contract owner – e.g. “*0xu82h…7237*”.

``to_address``: the receiver address – e.g. “*0xu82h…7237*”.

``asset_name``: the name of target asset.

``amount``: the amount of suns.

.. code-block:: shell

         message ParticipateAssetIssueContract {
           bytes owner_address = 1;
           bytes to_address = 2;
           bytes asset_name = 3;
           int64 amount = 4;
          }

A ``DeployContract`` contains 2 parameters:

``script``: the script of this contract.

``owner_address``: the address for contract owner – e.g. “*0xu82h…7237*”.

.. code-block:: shell

         message DeployContract { 
           bytes owner_address = 1; 
           bytes script = 2;
           }                       t

+ Each transaction contains several TXInputs, TXOutputs and other related qualities.

Input, transaction and block header all require signature.

message ``Transaction`` contains ``raw_data`` and ``signature``.

``raw_data``: message ``raw``.

``signature``: signatures form all input nodes.

``raw`` contains 8 parameters:

``type``: the transaction type of `raw` message.

``vin``: input values.

``vout``: output values.

``expiration``: the expiration date of transaction – e.g.*20170312*.

``data``: data.

``contract``: contracts in this transaction.

``scripts``:scripts in the transaction.

``timestamp``: timestamp of this raw data – e.g. *14356325*.

message ``Contract` contains ``type`` and ``parameter``.

``type``: what type of the message contract.

``parameter``: It can be any form.

There are 8 different of contract types: ``AccountCreateContract``, `TransferContract``, ``TransferAssetContract``, ``VoteAssetContract``, ``VoteWitnessContract``,``WitnessCreateContract``, ``AssetIssueContract`` and ``DeployContract``.

``TransactionType`` have two types: ``UtxoType`` and ``ContractType``.

.. code-block:: shell

        message Transaction { 
          enum TranscationType { 
            UtxoType = 0; 
            ContractType = 1; 
           } 
           message Contract { 
             enum ContractType { 
               AccountCreateContract = 0; 
               TransferContract = 1; 
               TransferAssetContract = 2; 
               VoteAssetContract = 3; 
               VoteWitnessContract = 4; 
               WitnessCreateContract = 5; 
               AssetIssueContract = 6; 
               DeployContract = 7; 
               WitnessUpdateContract = 8;
               ParticipateAssetIssueContract = 9
              } 
              ContractType type = 1; 
              google.protobuf.Any parameter = 2; 
            } 
            message raw { 
              TranscationType type = 2; 
              repeated TXInput vin = 5; 
              repeated TXOutput vout = 7; 
              int64 expiration = 8; 
              bytes data = 10; 
              repeated Contract contract = 11; 
              bytes scripts = 16; 
              int64 timestamp = 17;
             } 
             raw raw_data = 1; 
             repeated bytes signature = 5;
          }

message ``TXOutputs`` contains ``outputs``.

``outputs``: an array of ``TXOutput``.

.. code-block:: shell

        message TXOutputs { 
           repeated TXOutput outputs = 1; 
         }

message ``TXOutput`` contains ``value`` and ``pubKeyHash``.

``value``: output value.

``pubKeyHash``: Hash of public key

.. code-block:: shell

        message TXOutput { 
           int64 value = 1; 
           bytes pubKeyHash = 2; 
         }

message ``TXInput`` contains ``raw_data`` and ``signature``.

``raw_data``: a message ``raw``.

``signature``: signature for this ``TXInput``.

message ``raw`` contains ``txID``, ``vout`` and ``pubKey``.

``txID``: transaction ID.

``vout``: value of last output.

``pubKey``: public key.

.. code-block:: shell

        message TXInput { 
           message raw { 
           bytes txID = 1; 
           int64 vout = 2; 
           bytes pubKey = 3; 
         } 
         raw raw_data = 1; 
         bytes signature = 4;
          }

message ``Result`` contains ``fee`` and ``ret``.

``ret``: the state of transaction.

``fee``: the fee for transaction.

``code`` is the enumerator that defines `ret` property and can be  2 types：``SUCCESS`` and ``FAILED``.

.. code-block:: shell

        message Result {
          enum code {
            SUCESS = 0;
            FAILED = 1;
          }
          int64 fee = 1;
          code ret = 2;
        }

+ Inventory is mainly used to inform peer nodes the list of items.

``Inventory`` contains ``type`` and ``ids``.

``type``: what type this ``Inventory`` is. – e.g. *0* stands for ``TRX``.

``ids``: ID of things in this ``Inventory``.

Two ``Inventory`` types: ``TRX`` and ``BLOCK``.

``TRX``: transaction.

``BLOCK``: block.

.. code-block:: shell

        // Inventory 
        message Inventory { 
          enum InventoryType { 
            TRX = 0; 
            BLOCK = 1; 
           } 
           InventoryType type = 1; 
           repeated bytes ids = 2; 
         }

message ``Items`` contains 4 parameters:

``type``: type of items – e.g. *1* stands for ``TRX``.

``blocks``: blocks in ``Items` if there is any.

``block_headers``: block headers if there is any.

``transactions``: transactions if there is any.

``Items`` have four types: ``ERR``, ``TRX``, ``BLOCK`` and ``BLOCKHEADER``.

``ERR``: error.

``TRX``: transaction.

``BLOCK``: block.

``BLOCKHEADER``: block header.

.. code-block:: shell

        message Items { 
          enum ItemType { 
            ERR = 0; 
            TRX = 1; 
            BLOCK = 2; 
            BLOCKHEADER = 3; 
           } 
           ItemType type = 1; 
           repeated Block blocks = 2; 
           repeated BlockHeader
           block_headers = 3; 
           repeated Transaction transactions = 4;
         }

``InventoryItems`` contains ``type`` and ``items``.

``type``: what type of inventory.

`items`: the list of inventory.

.. code-block:: shell

        message InventoryItems { 
          int32 type = 1; 
          repeated bytes items = 2;
          }

message ``BlockInventory`` contains ``type``.

``type``: what type of inventory.

There are 3 types:``SYNC``, ``ADVTISE``, ``FETCH``.

.. code-block:: shell

        // Inventory
         message BlockInventory {
           enum Type {
             SYNC = 0;
             ADVTISE = 1;
             FETCH = 2;
           }

message ``BlockId`` contains ``ids`` and ``type``.

``ids``: the identification of block.

``type``: what type of the block.

``ids`` contains 2 parameters:

``hash``: the hash of block.

``number``: the height of block.

.. code-block:: shell

         message BlockId {
            bytes hash = 1;
            int64 number = 2;
          }
          repeated BlockId ids = 1;
          Type type = 2;
         }

``ReasonCode``: the type of reason.

``ReasonCode`` contains 15 types of disconnect reasons:

``REQUESTED``

``TCP_ERROR``

``BAD_PROTOCOL``

``USELESS_PEER``

``TOO_MANY_PEERS``

``DUPLICATE_PEER``

``INCOMPATIBLE_PROTOCOL``

``NULL_IDENTITY``

``PEER_QUITING``

``UNEXPECTED_IDENTITY``

``LOCAL_IDENTITY``

``PING_TIMEOUT``

``USER_REASON``

``RESET``

``UNKNOWN``

.. code-block:: shell

        enum ReasonCode {
          REQUESTED = 0;
          TCP_ERROR = 1;
          BAD_PROTOCOL = 2;
          USELESS_PEER = 3;
          TOO_MANY_PEERS = 4;
          DUPLICATE_PEER = 5;
          INCOMPATIBLE_PROTOCOL = 6;
          NULL_IDENTITY = 7;
          PEER_QUITING = 8;
          UNEXPECTED_IDENTITY = 9;
          LOCAL_IDENTITY = 10;
          PING_TIMEOUT = 11;
          USER_REASON = 12;
          RESET = 16;
          UNKNOWN = 255;
        }

message ``DisconnectMessage`` contains ``reason``:

``DisconnectMessage``: the message when disconnection occurs.

``reason``: the reason for disconnecting.

message ``HelloMessage`` contains 3 parameters:

``HelloMessage``: the message for building connection.

``from``: the nodes that request for building connection.

 ``version``: the version when connection is built.

+ Wallet Service RPC and blockchain explorer

``Wallet`` service contains several RPCs.

*GetBalance* :
``GetBlance`` takes a parameter of Account, and returns an ``Account``object.

*CreateTransaction* ：
``CreateTransaction``takes a parameter of TransferContract, and returns an ``Transaction``object.

*BroadcastTransaction* :
``BroadcastTransaction``takes a parameter of Transaction, and returns an ``Return``object.

*CreateAccount* :
``CreateAccount``takes a parameter of AccountCreateContract, and returns an ``Transaction``object.

*CreateAssetIssue* :
``CreateAssetIssue``takes a parameter of AssetIssueContract, and returns an ``Transaction``object.

*ListAccounts*:
``ListAccounts`` takes a parameter of EmptyMessage, and returns an ``AccountList`` object.

*UpdateAccount*:
``UpdateAccount`` takes a parameter of AccountUpdateContract, and returns an ``Transaction`` object.

*VoteWitnessAccount*:
``VoteWitnessAccount`` takes a parameter of VoteWitnessContract, and returns an ``Transaction`` object.

*WitnessList*:
``WitnessList`` takes a parameter of WitnessUpdateContract, and returns an ``WitnessList`` object.

*UpdateWitness*:
``UpdateWitness`` takes a parameter of WitnessUpdateContract, and returns an ``Transaction`` object.

*CreateWitness*:
``CreateWitness`` takes a parameter of WitnessCreateContract, and returns an ``Transaction``object.

*TransferAsset*:
``TransferAsset`` takes a parameter of TransferAssetContract, and returns an ``Transaction`` object.

*ParticipateAssetIssue*:
``ParticipateAssetIssue`` takes a parameter of ParticipateAssetIssueContract, and returns an ``Transaction`` object.

*ListNodes*:
``ListNodes`` takes a parameter of EmptyMessage, and returns an ``NodeList`` object.

*GetAssetIssueList*:
``GetAssetIssueList`` takes a parameter of EmptyMessage, and returns an ``GetIssueList`` object.

*GetAssetIssueByAccount*:
``GetAssetIssueByAccount`` takes a parameter of Account, and returns an ``AssetIssueList`` object.

*GetAssetIssueByName*:
``GetAssetIssueByName`` takes a parameter of BytesMessage, and returns an ``AssetIssueContract`` object.

*GetNowBlock*:
``GetNowBlock`` takes a parameter of EmptyMessage, and returns an ``Block`` object.

*GetBlockByNum*:
``GetBlockByNum`` takes a parameter of NumberMessage, and returns an ``Block`` object.

*TotalTransaction*:
``TotalTransaction`` takes a parameter of EmptyMessage, and returns an ``NumberMessage`` object.

.. code-block:: shell

      service Wallet {
      returns (Account) {
          option (google.api.http) = {
            post: "/wallet/getaccount"
            body: "*"
          };

        };

        rpc CreateTransaction (TransferContract) returns (Transaction) {
          option (google.api.http) = {
            post: "/wallet/createtransaction"
            body: "*"
          };
        };

        rpc BroadcastTransaction (Transaction) returns (Return) {
          option (google.api.http) = {
            post: "/wallet/broadcasttransaction"
            body: "*"
          };
        };

        rpc GetAccount (Account)
        rpc ListAccounts (EmptyMessage) returns (AccountList) {
          option (google.api.http) = {
                post: "/wallet/listaccount"
                body: "*"
            };

        };

        rpc UpdateAccount (AccountUpdateContract) returns (Transaction) {
          option (google.api.http) = {
            post: "/wallet/updateaccount"
            body: "*"
          };
        };

        rpc CreateAccount (AccountCreateContract) returns (Transaction) {
          option (google.api.http) = {
            post: "/wallet/createaccount"
            body: "*"
          };
        };

        rpc VoteWitnessAccount (VoteWitnessContract) returns (Transaction) {
          option (google.api.http) = {
            post: "/wallet/votewitnessaccount"
            body: "*"
          };
        };

        rpc CreateAssetIssue (AssetIssueContract) returns (Transaction) {
          option (google.api.http) = {
            post: "/wallet/createassetissue"
            body: "*"
          };
        };

        rpc ListWitnesses (EmptyMessage) returns (WitnessList) {
          option (google.api.http) = {
            post: "/wallet/listwitnesses"
            body: "*"
          };
        };

        rpc UpdateWitness (WitnessUpdateContract) returns (Transaction) {
          option (google.api.http) = {
            post: "/wallet/updatewitness"
            body: "*"
          };
        };

        rpc CreateWitness (WitnessCreateContract) returns (Transaction) {
          option (google.api.http) = {
            post: "/wallet/createwitness"
            body: "*"
          };
        };

        rpc TransferAsset (TransferAssetContract) returns (Transaction) {
          option (google.api.http) = {
            post: "/wallet/transferasset"
            body: "*"
          };
        }

        rpc ParticipateAssetIssue (ParticipateAssetIssueContract) returns (Transaction) {
          option (google.api.http) = {
            post: "/wallet/participateassetissue"
            body: "*"
          };
        }

        rpc ListNodes (EmptyMessage) returns (NodeList) {
          option (google.api.http) = {
            post: "/wallet/listnodes"
            body: "*"
          };
        }
        rpc GetAssetIssueList (EmptyMessage) returns (AssetIssueList) {
          option (google.api.http) = {
            post: "/wallet/getassetissuelist"
            body: "*"
          };
        }
        rpc GetAssetIssueByAccount (Account) returns (AssetIssueList) {
          option (google.api.http) = {
            post: "/wallet/getassetissuebyaccount"
            body: "*"
          };
        }
        rpc GetAssetIssueByName (BytesMessage) returns (AssetIssueContract) {
          option (google.api.http) = {
            post: "/wallet/getassetissuebyname"
            body: "*"
          };
        }
        rpc GetNowBlock (EmptyMessage) returns (Block) {
          option (google.api.http) = {
            post: "/wallet/getnowblock"
            body: "*"
          };
        }
        rpc GetBlockByNum (NumberMessage) returns (Block) {
          option (google.api.http) = {
            post: "/wallet/getblockbynum"
            body: "*"
          };
        }
        rpc TotalTransaction (EmptyMessage) returns (NumberMessage) {
          option (google.api.http) = {
            post: "/wallet/totaltransaction"
            body: "*"
          };
        }
      };

``WalletSolidity`` service contains several RPCs.
*GetAccount* :

``GetAccount`` takes a parameter of Account, and returns an ``Account`` object.
*ListAccounts*:

``listAccounts`` takes a parameter of EmptyMessage , and returns ``listAccounts`` object.
*ListWitness*:

``LitWitness`` takes a parameter of EmptyMessage, and returns ``WitnessList`` object.
*ListNodes*:

``ListNodes`` takes a parameter of EmptyMessage, and returns ``NodeList`` object.
*GetAssetIssueList*:

``GetAssetIssueList`` takes a parameter of EmptyMessage, and returns ``AssetIssueList`` object.
*GetAssetIssueListByTimeStamp*:

``GetAssetIssueListByTimeStamp`` takes a parameter of EmptyMessage, and returns ``AsssetIssueList`` object.
*GetAssetIssueByAccount*:

``GetAssetIssueByAccount`` takes a parameter of Account, and returns ``AssetIssueList`` object.
*GetAssetIssueByName*:

``GetAssetIssueByName`` takes a parameter of BytesMessage, and returns ``AssetIssueContract`` object.
*GetNowBlock*:

``GetNowBlock`` takes a parameter of EmptyMessage, and returns ``Block`` object.
*GetBlockByNum*:

``GetBlockByNumber`` takes a parameter of NumberMessage, and returns ``Block`` object.
*TotalTransaction*:

``TotalTransaction`` takes a parameter of EmptyMessage, and returns ``NumberMessage`` object.
*getTransactionById*:

``getTransactionById`` takes a parameter of BytesMessage, and returns ``Transaction`` object.
*getTransactionsByTimeStamp*:

``getTransactionsByTimeStamp`` takes a parameter of TimeMessage, and returns ``TransactionList`` object.
*getTransactionsFromThis*:

``getTransactionsFromThis`` takes a parameter of Account, and returns ``TransactionList`` object.
*getTransactionsToThis*:

``getTransactionsToThis`` takes a parameter of Account, and returns ``NumberMessage`` object.

.. code-block:: shell

      service WalletSolidity {

        rpc GetAccount (Account) returns (Account) {

        };

        rpc ListAccounts (EmptyMessage) returns (AccountList) {

        };

        rpc ListWitnesses (EmptyMessage) returns (WitnessList) {

        };

        rpc ListNodes (EmptyMessage) returns (NodeList) {

        }
        rpc GetAssetIssueList (EmptyMessage) returns (AssetIssueList) {

        }
        rpc GetAssetIssueListByTimestamp (NumberMessage) returns (AssetIssueList) {

        }
        rpc GetAssetIssueByAccount (Account) returns (AssetIssueList) {

        }
        rpc GetAssetIssueByName (BytesMessage) returns (AssetIssueContract) {

        }
        rpc GetNowBlock (EmptyMessage) returns (Block) {

        }
        rpc GetBlockByNum (NumberMessage) returns (Block) {

        }

        //Get transaction.

        rpc TotalTransaction (EmptyMessage) returns (NumberMessage) {

        }
        rpc getTransactionById (BytesMessage) returns (Transaction) {

        }
        rpc getTransactionsByTimestamp (TimeMessage) returns (TransactionList) {

        }
        rpc getTransactionsFromThis (Account) returns (TransactionList) {

        }
        rpc getTransactionsToThis (Account) returns (NumberMessage) {

        }
      };

``AccountList``: the list of accounts in the blockchain explorer.

message ``AccountList`` contains one parameter:

``account``:

.. code-block:: shell

       message AccountList {
         repeated Account accounts = 1;
       }

``WitnessList``: the list of witnesses in the blockchain explorer.

message ``WitnessList`` contains one parameter:

``witnesses``:

.. code-block:: shell

        message WitnessList {
          repeated Witness witnesses = 1;
        }

``AssetIssueList``: the list of issue asset in the blockchain explorer.

message ``AssetIssueList`` contains one parameter:

``assetIssue``:

.. code-block:: shell

        message AssetIssueList {
          repeated AssetIssueContract assetIssue = 1;
        }

``NodeList``: the list of nodes in the node distribution map.

message ``NodeList`` contains one parameter:

``nodes``:

.. code-block:: shell

         message NodeList {
           repeated Node nodes = 1;
         }

``Address``: the address  of nodes.

message ``Address`` contains 2 parameters:

``host``: the host of nodes.

``port``: the port number of nodes.

.. code-block:: shell

          message Address {
            bytes host = 1;
            int32 port = 2;
          }

message ``Return`` has only one parameter:

``result``: a bool flag.

.. code-block:: shell

          message Return { 
            bool result = 1;
           }

+ The message structure of UDP.

``Endpoint``: the storage structure of nodes' information.

message ``Endpoint`` contains 3 parameters:

``address``: the address of nodes.

``port``: the port number.

``nodeId``:the ID of nodes.

.. code-block:: shell

      message Endpoint {
         bytes address = 1;
         int32 port = 2;
         bytes nodeId = 3;
       }

``PingMessage``: the message sent from one node to another in the connecting process.

message ``PingMessage` contains 4 parameters:

``from``: which node does the message send from.

``to``: which node will the message send to.

``version``: version of the message sending node.

``timestamp``: the timestamp of message.

.. code-block:: shell

       message PingMessage {
          Endpoint from = 1;
          Endpoint to = 2;
         int32 version = 3;
         int64 timestamp = 4;
        }

``PongMessage``: the message implies that nodes are connected.

message ``PongMessage`` contains 3 parameters:

``from``: which node does the message send from.

``echo``:

``timestamp``: the timestamp of message.

.. code-block:: shell

        message PongMessage {
          Endpoint from = 1;
          int32 echo = 2;
          int64 timestamp = 3;
         }

``FindNeighbours``: the message sent from one node to find another one.

message ``FindNeighbours`` contains 3 parameters:

``from``: which node does the message send from.

``targetId``: the ID of targeted node.

``timestamp``: the timestamp of message.

.. code-block:: shell

        message FindNeighbours {
          Endpoint from = 1;
          bytes targetId = 2;
          int64 timestamp = 3;
         }

``FindNeighbour``: the message replied by the neighbour node.

message ``Neighbours`` contains 3 parameters:

``from``: which node does the message send from.

``neighbours``: the neighbour node.

``timestamp``: the timestamp of message.

.. code-block:: shell

        message Neighbours {
          Endpoint from = 1;
          repeated Endpoint neighbours = 2;
          int64 timestamp = 3;
         }

Please check detailed protocol document that may change with the iteration of the program at any time. Please refer to the latest version.

TRON Wallet RPC-API
-------------------

1. Getting account information

    1.1	Interface statement

    rpc GetAccount (Account) returns (Account) {};

    1.2	Nodes

    Fullnode and soliditynode.

    1.3	Parameters

    Account: type in the address.

    1.4	Returns

    Account: returns all account information.

    1.5	Functions

    Query of balance list. Display of all asset information in account return.

2. TRX transfer

    2.1	Interface statement

    rpc CreateTransaction (TransferContract) returns (Transaction)　{};

    2.2	Node

    Fullnode.

    2.3	Parameters

    TransferContract: addresses of the sender and the recipient, and amount of transfer (in sun).

    2.4	Returns

    Transaction: returns transaction of transfer contract; request transaction after acquisition of wallet signature.

    2.5	Function

    Transfer. Creation of a transaction of transfer.

3. Transaction broadcasting

    3.1	Interface statement

    rpc BroadcastTransaction (Transaction) returns (Return) {};

    3.2	Node

    Fullnode.

    3.3	Parameters

    Transaction: transaction signed by wallet. In TRON network, operations entailing change of blockchain status are sealed in the transaction.

    3.4	Returns

    Return: success or failure. Transaction will be initiated and returned with feedback before broadcasting takes place. Note: return of success doesn’t necessarily mean completion of transaction.

    3.5	Function

    Transfer, vote, issuance of token, or participation in token offering. Sending signed transaction information to node, and broadcasting it to the entire network after witness verification.

4. Query of account list

    4.1	Interface statement

    rpc ListAccounts (EmptyMessage) returns (AccountList);

    4.2	Node

    Fullnode and soliditynode.

    4.3	Parameters

    EmptyMessage: null.

    4.4	Returns

    AccountList: Account list.

    4.5	Function

    Query of all account information currently stored in the blockchain.

5. Creating account (deleted, no longer available)

    5.1	Interface statement

    rpc CreateAccount (AccountCreateContract) returns (Transaction){};

    5.2	Node

    Fullnode.

    5.3	Parameters

    AccountCreateContract: account type, account name and account address.

    5.4	Returns

    Transaction: returns transaction of account creation. Request broadcasting after acquisition of wallet signature.

    5.5	Function

    Account creation. Creating an account (or opting otherwise) when registering a wallet.

    6. Account update (to be realized)

    6.1	Interface statement

    rpc UpdateAccount (AccountUpdateContract) returns (Transaction){};

    6.2	Node

    Fullnode.

    6.3	Parameters

    AccountUpdateContract: account name and address.

    6.4	Returns

    Transaction: Returns transaction of account creation.

    6.5	Function

    Account name update.

7. Vote

    7.1	Interface statement

    rpc VoteWitnessAccount (VoteWitnessContract) returns (Transaction){};

    7.2	Node

    Fullnode.

    7.3	Parameters

    VoteWitnessContract: voter address and list of votes; candidate address and number of votes received.

    7.4	Returns

    Transaction: returns transaction of votes

    7.5	Function

    Vote. Coin holders can only vote for Super Representative candidates, with no more votes than the amount of locked balance (see also 26. Balance freeze).

8. TRON wallet RPC-API for token issuance

    8.1	Interface statement

    rpc CreateAssetIssue (AssetIssueContract) returns (Transaction) {};

    8.2	Node

    Fullnode.

    8.3	Parameters

    AssetIssueContract: issuer address, token name, total capitalization, exchange rate to TRX, starting date, expiry date, attenuation coefficient, votes, detailed description, url, etc.

    8.4	Returns

    Transaction: returns transaction of token issuance. Request for transaction broadcasting after acquiring wallet signature.

    8.5	Function

    Token issuance. All users can issue tokens at the cost of 1024 TRX. Following successful issuance, users can exchange for the token with TRX before the designated expiry date.

9. Query of list of Super Representative candidates

    9.1	Interface statement

    rpc ListWitnesses (EmptyMessage) returns (WitnessList) {};

    9.2	Nodes

    Fullnode and soliditynode.

    9.3	parameters

    EmptyMessage: null.

    9.4	Returns

    WitnessList: list of witnesses and detailed information of the candidates.

    9.5	Function

    Query of all candidates prior to voting.

10. Application for Super Representative (to be realized)

    10.1 Interface statement

    rpc CreateWitness (WitnessCreateContract) returns (Transaction) {};

    10.2 Node

    Fullnode.

    10.3 Parameters

    WitnessCreateContract: account address and Url.

    10.4 Returns

    Transaction: Returns

    10.5 function

    All users with an account created on the blockchain can apply to become TRON’s Super Representative candidate.

11. Information update of Super Representative candidate (to be realized)

    11.1 Interface statement

    rpc UpdateWitness (WitnessUpdateContract) returns (Transaction) {};

    11.2 Node

    Fullnode.

    11.3 Parameters

    WitnessUpdateContract: an account address and Url.

    11.4 Returns

    Transaction: returns transaction of SR application. Request broadcasting after acquiring wallet signature.

    11.5 Function

    Updating the url of SRs.

12. Token transfer

    12.1 Interface statement

    rpc TransferAsset (TransferAssetContract) returns (Transaction){};

    12.2 Node

    Fullnode.

    12.3 Parameters

    TransferAssetContract: token name, sender’s address, recipient address, and the amount of tokens.

    12.4 Returns

    Transaction: returns transaction of token transfer. Request to broadcast after acquiring wallet signature.

    12.5 Function

    Token transfer. Create a transaction of token transfer.

13. Participation in token offering

    13.1 Interface statement

    rpc ParticipateAssetIssue (ParticipateAssetIssueContract) returns (Transaction){};

    13.2 Node

    Fullnode.

    13.3 Parameters

    ParticipateAssetIssueContract: participant address, issuer address, token name, and amount of token (in sun).

    13.4 Returns

    Transaction: returns transaction of participation in token offering.

    13.5 Function

    Participation in token offering.

14. Query of nodes

    14.1 Interface statement

    rpc ListNodes (EmptyMessage) returns (NodeList) {};

    14.2 Nodes

    Fullnode and soliditynode.

    14.3 Parameters

    EmptyMessage: null.

    14.4 Returns

    NodeList: returns a list of nodes, including their IPs and ports.

    14.5 Function

    Listing the IPs and ports of current nodes.

15. Query of tokens

    15.1 Interface statement

    rpc GetAssetIssueList (EmptyMessage) returns (AssetIssueList) {};

    15.2 Node

    Fullnode and soliditynode.

    15.3 Parameters

    EmptyMessage: null.

    15.4 Returns

    AssetIssueList: AssetIssueContract list and information on issued tokens.

    15.5 Function

    List of all issued tokens. Display of all issued tokens for user’s reference.

16. Query of tokens issued by a given account

    16.1 Interface statement

    rpc GetAssetIssueByAccount (Account) returns (AssetIssueList) {};

    16.2 Nodes

    Fullnode and soliditynode.

    16.3 Parameters

    Account: address.

    16.4 Returns

    AssetIssueList: AssetIssueContract list.

    16.5 Function

    Query of all tokens issued by a given account.

17. Query of token information with token name

    17.1 Interface statement

    rpc GetAssetIssueByName (BytesMessage) returns (AssetIssueContract) {};

    17.2 Nodes

    Fullnode and soliditynode.

    17.3 Parameters

    BytesMessage: token name.

    17.4 Returns

    AssetIssueContract: information on the token.

    17.5 Function

    Query of token information with the name. The exclusiveness of token name is ensured on TRON’s network.

18. Query of current tokens by timestamp

    18.1 Interface statement

    rpc GetAssetIssueListByTimestamp (NumberMessage) returns (AssetIssueList){};

    18.2 Node

    Soliditynode.

    18.3 Parameters

    NumberMessage: current timestamp (the number of milliseconds since 1970)

    18.4 Returns

    AssetIssueList: AssetIssueContract list and detailed information

    18.5 Function

    List of issued tokens by timestamp. Display of current nodes for users’ reference.

19. Get current block

    19.1 Interface statement

    rpc GetNowBlock (EmptyMessage) returns (Block) {};

    19.2 Nodes

    Fullnode and soliditynode.

    19.3 Parameters

    EmptyMessage: null.

    19.4 Returns

    Block: information on current block.

    19.5 Function

    Access the latest block.

20. Get block by block height

    20.1 Interface statement

    rpc GetBlockByNum (NumberMessage) returns (Block) {};

    20.2 nodes

    Fullnode and soliditynode.

    20.3 parameters

    NumberMessage: block height.

    20.4 Returns

    Block: block information.

    20.5 function

    Accessing the block at designated height, otherwise returning to the genesis block.

21. Get total number of transactions

    21.1 Interface statement

    rpc TotalTransaction (EmptyMessage) returns (NumberMessage) {};

    21.2 nodes

    Fullnode and soliditynode.

    21.3 Parameters

    EmptyMessage: null.

    21.4 Returns

    NumberMessage: Total number of transactions.

    21.5 Function

    Accessing the total number of transactions.

22. Query of transaction by ID

    22.1 Interface statement

    rpc getTransactionById (BytesMessage) returns (Transaction) {};

    22.2 Node

    Soliditynode.

    22.3 Parameters

    BytesMessage: transaction ID or Hash.

    22.4 Returns

    Transaction:  Queried transaction.

    22.5 Function

    Query of transaction details by ID which is the Hash of transaction.

23. Query of transaction by timestamp

    23.1 Interface statement

    rpc getTransactionsByTimestamp (TimeMessage) returns (TransactionList) {};

    23.2 Node

    Soliditynode.

    23.3 Parameters

    TimeMessage: starting time and ending time.

    23.4 Returns

    TransactionList: transaction list.

    23.5 Function

    Query of transactions by starting and ending time.

24. Query of transaction initiations by address (to be realized)

    24.1 Interface statement

    rpc getTransactionsFromThis (Account) returns (TransactionList) {};

    24.2 Node

    Soliditynode.

    24.3 Parameters

    Account: initiator account (address).

    24.4 Returns

    TransactionList: transaction list.

    24.5 Function

    Query of transaction initiations by account address.

25. Query of transaction receptions by address (to be realized)

    25.1 Interface statement

    rpc getTransactionsToThis (Account) returns (NumberMessage) {};

    25.2 Node

    Soliditynode.

    25.3 Parameters

    Account: Recipient account (address).

    25.4 Returns

    TransactionList: transaction list.

    25.5 Function

    Query of all transactions accepted by one given account.

26. Freeze Balance

    26.1 Interface statement

    rpc FreezeBalance (FreezeBalanceContract) returns (Transaction) {};

    26.2 Node

    Full Node.

    26.3 Parameters

    FreezeBalanceContract: address, balance to freeze and frozen duration. Currently balance can only be frozen for 3 days.

    26.4 Returns

    Transaction: Return includes a transaction of balance. Request transaction broadcasting after signed by wallet.

    26.5 Function

    Two things can be gained through freezing balance:

    a.	Bandwidth  points. Each update of blockchain transaction consumes bandwidth  points (if more than 10s from the previous transaction, the current transaction does not consume any points). Bandwidth  points obtained=suns*frozen duration. Each transaction (all operations altering blockchain accounts) consumes 100,000 bandwidth  points.
    b.	Votes. The amount of votes gained equals to the amount of frozen TRX.

27. Unfreeze Balance

    27.1 Interface statement

    rpc UnfreezeBalance (UnfreezeBalanceContract) returns (Transaction) {};

    27.2 Node

    Full Node.

    27.3 Parameters

    UnfreezeBalanceContract: address.

    27.4 Returns

    Transaction: returns transaction. Request transaction broadcasting after signed by wallet.

    27.5 Function

    Balance can be unfrozen only 3 days after the latest freeze. Voting records will be cleared upon unfrozen balance, while bandwidth  points won’t be. Frozen balance will not be automatically unfrozen after 3 days’ duration.

28. Block-production reward redemption

    28.1 Interface statement

    rpc WithdrawBalance (WithdrawBalanceContract) returns (Transaction) {};

    28.2 Node

    Full Node.

    28.3 Parameters

    WithdrawBalanceContract: address.

    28.4 Returns

    Transaction: returns transaction. Request transaction broadcasting after signed by wallet.

    28.5 Function

    This interface is only accessible to Super Representatives. Super Representative can obtain reward after successful account keeping. Instead of saved to account balance, rewards will be held independently in account allowance, with 1 permitted withdrawal to account balance every 24 hours.

Procedures of transaction signature generation
----------------------------------------------

Procedures
~~~~~~~~~~
1.	Convert the format of the transaction’s raw data to byte[].
2.	Conduct sha256 calculation on raw data.
3.	Sign the results of sha256 with the private key in correspondence with the address of each contract (1 contract and 1 private key for now).
4.	Add the signed result to transaction.

Signature algorithm
~~~~~~~~~~~~~~~~~~~~
1,	ECDSA algorithm, SECP256K.
2,	Example of signature data
   
.. code-block:: shell

    priKey:::8e812436a0e3323166e1f0e8ba79e19e217b2c4a53c970d4cca0cfb1078979df        
    pubKey::04a5bb3b28466f578e6e93fbfd5f75cee1ae86033aa4bbea690e3312c087181eb366f9a1d1d6a437a9bf9fc65ec853b9fd60fa322be3997c47144eb20da658b3d1        
    hash:::159817a085f113d099d3d93c051410e9bfe043cc5c20e43aa9a083bf73660145        
    r:::38b7dac5ee932ac1bf2bc62c05b792cd93c3b4af61dc02dbb4b93dacb758123f        
    s:::08bf123eabe77480787d664ca280dc1f20d9205725320658c39c6c143fd5642d        
    v:::0 

.. Note:: the signed result should be 65 byte in size—r 32 bytes, s 32 bytes and v 1 byte.

3,	Signature verification

When a full node receives transaction, it will verify signature, comparing an address calculated with hash, r, s and v with the address of the contract. Signature is successfully verified if the two addresses match.

Example of code
~~~~~~~~~~~~~~~

.. code-block:: shell

   java
    public static Transaction sign(Transaction transaction, ECKey myKey) {

        Transaction.Builder transactionBuilderSigned = transaction.toBuilder();
        byte[] hash = sha256(transaction.getRawData().toByteArray());
        List<Contract> listContract = transaction.getRawData().getContractList();

            for (int i = 0; i < listContract.size(); i++) {

                ECDSASignature signature = myKey.sign(hash);
                ByteString bsSign = ByteString.copyFrom(signature.toByteArray());
                //Each contract may be signed with a different private key in the future.
                transactionBuilderSigned.addSignature( bsSign );
                 
                }

Mechanism
---------

Account creation
~~~~~~~~~~~~~~~~

You can generate an offline keypair, which includes an address and a private key, that will not be recorded by TRON. In order to create a wallet using this private key, you will need to make a transfer (either in TRX or any other token) to the new address from an existing TRON's wallet. If the transfer is successful, you will have created a new wallet with the corresponding address.

Guidelines for Super Representative application
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

All willing users can apply to become Super Representatives, but to prevent malicious attacks, we have set up a threshold for admittance—to run for Super Representative, 9999 TRX in the applicants’ account will be burnt. After successful application, users can run for Super Representatives.

Freezing/unfreezing balance
~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Why tokens are frozen?**

The balance freezing mechanism is set up out of two considerations:
+ To prevent malicious spam transactions from clogging the network and causing delayed transaction confirmation.
+ To prevent malicious voting.

**Freeze/unfreeze mechanism**

Once the balance is frozen, the user will receive a proportionate amount of TRON Power(TP) and bandwidth. TRON Power(TP) represents voting power whereas bandwidth is used to pay for transactions. Their usage and means of calculation will be introduced in following sections.

Frozen assets are held in your frozen account and cannot be used for trading.

The fixed frozen duration is 3 days, after which you can unfreeze your balance any time you like manually. Balance unfrozen will be transferred back into your current account.

More TP and bandwidth can be obtained by freezing more balance. The balance can be unfrozen after 3 days from the latest freezing.

The fixed frozen duration is 3 days, after which you can unfreeze your balance any time you like manually. Balance unfrozen will be transferred back into your current account.

+ The freezing command is as follows:

.. code-block:: shell

    freezebalance password amount time
    amount: the unit of frozen balance is sun. The minimum balance frozen is 1,000,000 sun, or 1 TRX.
    time: frozen duration lasting from date of freeze and date to unfreeze is 3 days.

+ e.g.

.. code-block:: shell

    freezebalance password 10_000_000 3

+ Unfreezing command:

.. code-block:: shell

    unfreezebalance password

Block-production reward for Super Representatives
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Each time a Super Representative finishes block production, reward will be sent to the subaccount in the superledger. Super Representatives can check but not directly make use of this asset. A withdrawal can be made once every 24 hours, transferring the reward from the subaccount to the Super Representative’s account.

Super Representative Election
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Every account in TRON’s network is entitled to vote for the Super Representatives they support. Voting requires TP, which is determined by users’ current amount of frozen balance.

Calculation of TP: 1 TP for 1 frozen TRX.

Once you unfreeze your balance, an equivalent amount of TP is also lost, meaning that previous votes casted may no longer be valid. You can refreeze your balance to regain validity of votes.

.. Note:: TRON network only keeps record of the latest votes, meaning that every new allocation of votes you make will replace all previous records.

+ e.g.

.. code-block:: shell

    freezebalance password 10_000_000 3// 10 bandwidths for 10 frozen TRX
    votewitness password witness1 4 witness2 6//4 votes for witness1 and 6 votes for witness2
    vote witness password witness1 3 witness2 7// 3 votes for witness1 and 7 votes for witness2

The final result of the above commands is 3 votes for witness1 and 7 votes for witness2.

Bandwidth Points
~~~~~~~~~~~~~~~~

Having too many transactions will clog our network like Ethereum and may incur delays on transaction confirmation. To keep the network operating smoothly, TRON network only allows every account to initiate a limited number of transactions for free every once every 10 seconds. To engage in transactions more frequently requires bandwidth. Like TRON Power(TP), bandwidth can be obtained through freezing TRX.

1. Definition of bandwidth points

Transactions are transmitted and stored in the network in byte arrays. Bandwidth points consumed in a transaction equals the size of its byte array.

If the length of a byte array is 100 then the transaction consumes 100 bandwidth points.

2. Calculation of bandwidth points

Bandwidth points are the number of usable bytes for an account per day.

Within a given period of time, the entire network could only handle a fixed amount of bandwidth. To TRON’ network, the daily capacity is approximately 54G.

The ratio of bandwidth points in an account to the bandwidth capacity of TRON’s network equals the ratio of frozen balance in an account to frozen balance on the entire network.

e.g If frozen asset on the entire network totals 1,000,000 TRX and one given account froze 1,000 TRX, or 0.1% of total TRX frozen, then the account has 0.1%*54GB=54MB bandwidth points for its transactions.

.. Note:: Since the amount of frozen asset on the entire network and for a certain account are subject to change, bandwidth points held by an account isn’t always fixed.

3. Complimentary bandwidth points

There are 1K bandwidth points for free per account per day. When an account hasn’t frozen any balance, or when its bandwidth points have run out, complimentary bandwidth points can be used.

Each transaction in Tron’ network is about 200 bytes, so each account enjoys about 5 transactions for free each day.

.. Note:: total complimentary bandwidth takes up 1/4 of total bandwidth on the network, amounting to 13.5 GB. When total complimentary bandwidth used exceeds that threshold (meaning too many accounts have used complimentary bandwidth points), even if there are sufficient complimentary bandwidth points in an account, they cannot be used for transaction.

4. Token transfer

For transactions of token transfer, bandwidth points will first be charged from the token issuer.

When issuing tokens, the issuer can configure a limit to maximum bandwidth consumption, namely the maximal bandwidth points which can be charged from him/her for a token holder’s token transfers within 24 hours and the maximal total of bandwidth points.

These two parameters can be configured through updateAsset interface.

5. Consumption of bandwidth points

Aside from inquiries, any other type of transaction consumes bandwidth points. The bandwidth consumption procedure is as follows:
    + If the transaction isn’t a token transfer, skip to step 2. If the transaction is a token transfer, TRON will try to charge bandwidth points from the token issuer. If the issuer does not have sufficient bandwidth points or the charge is beyond the issuer’s maximal threshold, go to step 2.
    + Bandwidth points will be charged from the initiator. If insufficient, go to step 3.
    + Complimentary bandwidth points will be charged from the initiator. If again insufficient, transaction fails.

.. Note:: When balance unfreezes, bandwidth points will be cleared since there is no more frozen TRX.

6. Account creation

Account creation costs transaction initiator 10,000 bandwidth points.

Users can create new accounts for token transfer.

Token issuance
~~~~~~~~~~~~~~

In TRON’s network, every account is capable of issuing tokens. Users can lock their tokens in separately.

To issue token, issuer needs to set up token name, total capitalization, exchange rate to TRX, circulation duration, description, website, maximal bandwidth consumption per account, total bandwidth consumption and token freeze.

+ e.g.

.. code-block:: shell

    assetissue password abc 1000000 1 1 2018-5-31 2018-6-30 abcdef a.com 1000 1000000 200000 180 300000 365

Tokens named abc are issued with the above command, with a capitalization totaling 1 million. The exchange rate of abc to TRX is 1:1. The duration of circulation is May 31-June 30, 2018. It is described as abcdef. The provided website is a.com.

A maximum of 1000 bandwidth points can be charged from the issuer’s account per account per day. A maximum of 1,000,000 bandwidth points can be charged from the issuer’s account for all token holders’ transactions each day. in total capitalization, 200,000 tokens are locked for 180 days and 300,000 are locked for 365 days.

