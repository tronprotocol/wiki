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

message TransactionInfocontainsid，fee，blockNumber and blockTimeStamp.

`id`：transaction ID.

`fee`： transaction fee

`blockNumber`:the height of the block where the transaction is located.

`blockTimeStamp`:the timestamp of block.

.. code-block:: shell

        message TransactionInfo { 
             bytes id = 1;
             int64 fee = 2;
             int64 blockNumber = 3;
             int64 blockTimeStamp = 4;
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
*GetPaginatedAssetIssueList*

``GetPaginatedAssetIssueList`` takes a parameter of PaginatedMessage, and returns ``AssetIssueList`` object.
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
*GetTransactionInfoById*

``GetTransactionInfoById`` takes a parameter of BytesMessage and returns ``TransactionInfo`` object.

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

``EasyTransferMessage``: TRX easy transfer message.

``passPhrase``: password.

``toAddress``: recipient address.

``amount``: amount of trx to transfer.

.. code-block:: shell

    message EasyTransferMessage{
       bytes passPhrase = 1;
       bytes toAddress = 2;
       int64 amount = 3;
     }

``EasyTransferResponse``: TRX easy transfer response message.

``transaction``: transaction created by transfer.

``result``: result of transaction broadcasting.

.. code-block:: shell

    message EasyTransferResponse{
       Transaction transaction = 1;
       Return result = 2;
     }

``TransactionSign``：the parameter of signature.

``transaction``: transaction to be signed.

``privateKey``: private key for signing.

.. code-block:: shell

    message TransactionSign {
       Transaction transaction = 1;
       bytes privateKey = 2;
     }

Please check detailed protocol document that may change with the iteration of the program at any time. Please refer to the latest version.

TRON Wallet RPC-API
-------------------

For the specific definition of API, please refer to the following link:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
https://github.com/tronprotocol/java-tron/blob/develop/src/main/protos/api/api.proto

Frequently used APIs:
~~~~~~~~~~~~~~~~~~~~

1. Get general info of the wallet (similar to bitcoin getinfo)
GetAccount
2. Get balance of an address (similar to bitcoin getbalance)
GetAccount
3. Create a new address (similar to bitcoin getnewaddress)
You can create an address at the local system.
And you can create a new address on blockchain by calling rpc api createAccount, TransferAsset or CreateTransaction (TransferContract) to make a transfer from an existing account to the new address.
4. Retrieve the list of transaction history by address (similar to bitcoin listtransactions)
GetTransactionsFromThis
GetTransactionsToThis
5. check address is valid or not (regex or API command)
+ Local check--- After decode58check at local, you can get a 21-byte byte array starting with 0x41 (mainnet) or 0xa0 (testnet).
+ If you want to verify whether an address exists on the blockchain, you can call GetAccount.

1. Getting account information

    1.1	Interface statement

    rpc GetAccount (Account) returns (Account) {};

    1.2	Nodes

    FullNode and SolidityNode.

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

4. Creating account

    4.1 Interface statement 

    rpc CreateAccount (AccountCreateContract) returns (Transaction){}; 4.2 Node Fullnode.
     
    4.3 Parameters AccountCreateContract: account type and account address.
 
    4.4 Returns Transaction: returns transaction of account creation. Request broadcasting after obtaining wallet signature.
 
    4.5 Function Account creation. Creating an account (or opting otherwise) when registering a wallet.

5. Account update

    5.1 Interface statement rpc UpdateAccount (AccountUpdateContract) returns (Transaction){}; 

    5.2 Node Fullnode.

     5.3 Parameters AccountUpdateContract: account name and address.
 
    5.4 Returns Transaction: Returns transaction of account update. Request broadcasting after the transaction is signed by wallet. 

    5.5 Function Account name update.

6. Vote

    6.1 Interface statement rpc VoteWitnessAccount (VoteWitnessContract) returns (Transaction){};

     6.2 Node Fullnode.
 
    6.3 Parameters VoteWitnessContract: voter address and list of candidates which includes candidate address and number of votes received.

     6.4 Returns Transaction: returns transaction of votes. Request broadcasting after the transaction is signed by wallet. 

    6.5 Function Vote. Coin holders can only vote for Super Representative candidates, with no more votes than the amount of locked balance (see also 25. Balance freeze).

7. Token issuance

    7.1 Interface statement rpc CreateAssetIssue (AssetIssueContract) returns (Transaction) {};

     7.2 Node Fullnode.

     7.3 Parameters AssetIssueContract: issuer address, token name, total capitalization, exchange rate to TRX, starting date, expiry date, attenuation coefficient, votes, detailed description, url, maximum bandwidth consumption, total bandwidth consumption and frozen token.
 
    7.4 Returns Transaction: returns transaction of token issuance. Request for transaction broadcasting after the transaction is signed by wallet. 

    7.5 Function Token issuance. All users can issue tokens at the cost of 1024 TRX. Following a successful issuance, users can exchange for tokens with TRX before the designated expiry date.

    Sample:

    `assetissue password abc 1000000 1 1 2018-5-31 2018-6-30 abcdef a.com 1000 1000000 200000 180 300000 365`

    With the above command the token named abc is issued with a total capitalization of 1 million tokens at an exchange rate of 1:1 to trx. Its offering is from May 31-June 30, 2018. It is described as abcdef and can be found at a.com.

    A maximum of 1000 bandwidth points can be charged from the issuer’s account per account per day. The maximum bandwidth points to be charged from the issuer per day is 1000,000. 200,000 tokens will be locked for 180 days while another 300,000 tokens will be locked for 365 days.

8. Query of list of Super Representative candidates

    8.1 Interface statement rpc ListWitnesses (EmptyMessage) returns (WitnessList) {}; 

    8.2 Nodes Fullnode and soliditynode. 8.3 parameters EmptyMessage: null. 

    8.4 Returns WitnessList: list of witnesses including detailed information of the candidates.

     8.5 Function Query of all candidates prior to voting returning detailed information on each candidate for users’ reference.

9. Application for Super Representative

    9.1 Interface statement rpc CreateWitness (WitnessCreateContract) returns (Transaction) {}; 

    9.2 Node Fullnode.

     9.3 Parameters WitnessCreateContract: account address and Url.

     9.4 Returns Transaction: Returns a transaction of candidate application. Request broadcasting after the transaction is signed by wallet. 

    9.5 function All users with an account created on the blockchain can apply to become TRON’s Super Representative candidate.

10. Information update of Super Representative candidates

    10.1 Interface statement rpc UpdateWitness (WitnessUpdateContract) returns (Transaction) {};
 
    10.2 Node Fullnode. 10.3 Parameters WitnessUpdateContract: an account address and Url. 

    10.4 Returns Transaction: returns transaction of SR application. Request broadcasting after the transaction is signed by wallet. 

    10.5 Function Updating the url of SRs.

11. Token transfer

    11.1 Interface statement rpc TransferAsset (TransferAssetContract) returns (Transaction){}; 

    11.2 Node Fullnode. 

    11.3 Parameters TransferAssetContract: token name, sender address, recipient address, and the amount of tokens. 

    11.4 Returns Transaction: returns transaction of token transfer. Request broadcasting after the transaction is signed by wallet.

     11.5 Function Token transfer. Creates a transaction of token transfer.

12. Participation in token offering

    12.1 Interface statement rpc ParticipateAssetIssue (ParticipateAssetIssueContract) returns (Transaction){}; 

    12.2 Node Fullnode. 

    12.3 Parameters ParticipateAssetIssueContract: participant address, issuer address, token name, and amount of token (in sun). 

    12.4 Returns Transaction: returns transaction of participation in token offering. Request broadcasting after the transaction is signed by wallet. 

    12.5 Function Participation in token offering.

13. Query of all nodes

    13.1 Interface statement rpc ListNodes (EmptyMessage) returns (NodeList) {}; 

    13.2 Nodes Fullnode and soliditynode. 13.3 Parameters EmptyMessage: null. 

    13.4 Returns NodeList: returns a list of nodes, including their IPs and ports. 

    14.5 Function Listing the IPs and ports of current nodes.

14. Query of list of all tokens

    14.1 Interface statement rpc GetAssetIssueList (EmptyMessage) returns (AssetIssueList) {}; 

    14.2 Node Fullnode and soliditynode. 

    14.3 Parameters EmptyMessage: null. 

    14.4 Returns AssetIssueList: AssetIssueContract list containing information on all issued tokens. 

    14.5 Function List of all issued tokens. Display of all issued tokens for user’s reference.

15. Query of tokens issued by a given account

    15.1 Interface statement rpc GetAssetIssueByAccount (Account) returns (AssetIssueList) {}; 

    15.2 Nodes Fullnode and soliditynode. 15.3 Parameters Account: address. 

    15.4 Returns AssetIssueList: AssetIssueContract list containing information on all issued tokens. 

    15.5 Function Query of all tokens issued by a given account.

16. Query of token information by token name

    16.1 Interface statement rpc GetAssetIssueByName (BytesMessage) returns (AssetIssueContract) {};
 
    16.2 Nodes Fullnode and soliditynode. 16.3 Parameters BytesMessage: token name.
 
    16.4 Returns AssetIssueContract: information on the token.

     17.5 Function Query of token information with the name. The exclusiveness of token name is ensured on TRON’s network.

17. Query of current tokens by timestamp

    17.1 Interface statement rpc GetAssetIssueListByTimestamp (NumberMessage) returns (AssetIssueList){};

    17.2 Node Soliditynode. 

    17.3 Parameters NumberMessage: current timestamp (the number of milliseconds since 1970) .

    17.4 Returns AssetIssueList: AssetIssueContract list including detailed information of the tokens. 

    17.5 Function List of issued tokens by timestamp. Display of current nodes for users’ reference.

18. Get current block

    18.1 Interface statement rpc GetNowBlock (EmptyMessage) returns (Block) {}; 

    18.2 Nodes Fullnode and soliditynode. 18.3 Parameters EmptyMessage: null. 

    18.4 Returns Block: information on current block. 

    18.5 Function Inquire the latest block.

19. Get block by block height

    19.1 Interface statement rpc GetBlockByNum (NumberMessage) returns (Block) {}; 

    19.2 nodes Fullnode and soliditynode. 

    19.3 parameters NumberMessage: block height.
 
    19.4 Returns Block: block information. 

    19.5 function Accessing the block at designated height, otherwise returning to the genesis block.

20. Get total number of transactions

    20.1 Interface statement rpc TotalTransaction (EmptyMessage) returns (NumberMessage) {}; 

    20.2 Nodes Fullnode and soliditynode.

     20.3 Parameters EmptyMessage: null. 

    20.4 Returns NumberMessage: Total number of transactions. 

    20.5 Function Inquiring the total number of transactions.

21. Query of transaction by ID

    21.1 Interface statement rpc getTransactionById (BytesMessage) returns (Transaction) {}; 

    21.2 Node Soliditynode. 

    21.3 Parameters BytesMessage: transaction ID or Hash.
 

    21.4 Returns Transaction: Queried transaction. 

    21.5 Function Query of transaction details by ID which is the Hash of transaction.

22. Query of transaction by timestamp

    22.1 Interface statement rpc getTransactionsByTimestamp (TimeMessage) returns (TransactionList) {};

     22.2 Node Soliditynode.
 
    22.3 Parameters TimeMessage: starting time and ending time. 

    22.4 Returns TransactionList: transaction list.

     22.5 Function Query of transactions by starting and ending time.

23. Query of transaction initiations by address

    23.1 Interface statement rpc getTransactionsFromThis (Account) returns (TransactionList) {}; 

    23.2 Node Soliditynode. 

    23.3 Parameters Account: initiator‘s account (address). 

    23.4 Returns TransactionList: transaction list. 

    23.5 Function Query of transaction initiations by account address.

24. Query of transaction receptions by address

    24.1 Interface statement rpc getTransactionsToThis (Account) returns (NumberMessage) {};
 
    24.2 Node Soliditynode. 

    24.3 Parameters Account: Recipient account (address). 

    24.4 Returns TransactionList: transaction list. 

    24.5 Function Query of all transactions accepted by one given account.

25. Freeze Balance

    25.1 Interface statement rpc FreezeBalance (FreezeBalanceContract) returns (Transaction) {}; 

    25.2 Node Full Node. 

    25.3 Parameters FreezeBalanceContract: address, amount of trx to freeze and frozen duration. Currently balance can only be frozen for 3 days. 

    25.4 Returns Transaction: Return includes a transaction of balance. Request transaction broadcasting after signed by wallet.
 
    25.5 Function

    Two things can be gained through freezing balance:

    a. Bandwidth Points.
 
    b. Power to vote.

26. Unfreeze Balance

    26.1 Interface statement rpc UnfreezeBalance (UnfreezeBalanceContract) returns (Transaction) {}; 

    26.2 Node Full Node. 

    26.3 Parameters UnfreezeBalanceContract: address. 

    26.4 Returns Transaction: returns transaction. Request transaction broadcasting after signed by wallet.
 
    26.5 Function Balance can be unfrozen only 3 days after the latest freeze. Voting records will be cleared upon unfrozen balance, while bandwidth points won’t be. Frozen balance will not be automatically unfrozen after 3 days’ duration.

27. Block-production reward redemption

    27.1 Interface statement rpc WithdrawBalance (WithdrawBalanceContract) returns (Transaction) {};
 
    27.2 Node Full Node. 

    27.3 Parameters WithdrawBalanceContract: address. 

    27.4 Returns Transaction: returns transaction. Request transaction broadcasting after signed by wallet. 

    27.5 Function This interface is only accessible to Super Representatives. Super Representative can obtain reward after successful account keeping. Instead of saved to account balance, rewards will be held independently in account allowance, with 1 permitted withdrawal to account balance every 24 hours.

28. Unfreeze balance

    28.1 Interface statement

    rpc UnfreezeAsset (UnfreezeAssetContract) returns (Transaction) {};

    28.2 Node

    Fullnode.

    28.3 Parameters

    UnfreezeAssetContract:: address.

    28.4 Returns

    Transaction: returns the transaction; request broadcasting after the transaction is signed by wallet.

    28.5 Function

    Token issuers can unfreeze locked supply during issuance.

29. Query of the next maintenance time

    29.1 Interface statement

    rpc GetNextMaintenanceTime (EmptyMessage) returns (NumberMessage) {};

    29.2 Node

    Fullnode.

    29.3 Parameters

    EmptyMessage: no parameter needed.

    29.4 Returns

    NumberMessage: the next maintenance time.

    29.5 Function

    Get the next maintenance time.

30. Query of transaction information

    30.1 Interface statement

    rpc GetTransactionInfoById (BytesMessage) returns (TransactionInfo) {};

    30.2 Node

    Soliditynode.

    30.3 Parameters

    BytesMessage: transaction ID

    30.4 Returns

    TransactionInfo: transaction information.

    30.5 Function

    Query of transaction fee, block location and the timestamp of the block.

31. Query block by ID

    31.1 Interface statement

    rpc GetBlockById (BytesMessage) returns (Block) {};

    31.2 Node

    Fullnode.

    31.3 Parameter

    BytesMessage: block ID.

    31.4 Returns

    Block: the block.

    31.5 Function

    Query of block by block ID.

32. Token update

    32.1 Interface statement

    rpc UpdateAsset (UpdateAssetContract) returns (Transaction) {};

    32.2 Node

    Fullnode.

    32.3 Parameters

    UpdateAssetContract: issuer address, token description, token url, maximum bandwidth consumption by each account and total bandwidth consumption.

    32.4 Returns

    Transaction: returns transaction; request broadcasting after the transaction is signed by wallet.

    32.5 Function

    Token update can only be initiated by the token issuer to update token description, url, maximum bandwidth consumption by each account and total bandwidth consumption.

33. Paginated query of token list

    33.1 Interface statement

    rpc GetPaginatedAssetIssueList (PaginatedMessage) returns (AssetIssueList) {};

    33.2 Nodes

    Fullnode and soliditynode.

    33.3 Parameters

    PaginatedMessage: starting index (0) and the number of tokens displayed on each page.

    33.4 Returns

    AssetIssueList: a paginated list of AssetIssueContract containing detailed information of tokens.

    33.5 Function

    Paginated list of tokens displaying tokens information for users’ reference.

34. Transaction signing

    34.1 Interface statement

    rpc GetTransactionSign (TransactionSign) returns (Transaction) {};

    34.2 Node

    Fullnode.

    34.3 Parameters

    TransactionSign: Transaction to be signed and the private key to sign with.

    34.4 Returns

    Transaction: transaction to be signed.

35. Address and private key creation

    35.1 Interface statement

    rpc CreateAdresss (BytesMessage) returns (BytesMessage) {};

    35.2 Node

    Fullnode.

    35.3 Parameters

    BytesMessage: Passphrase

    35.4 Returns

    BytesMessage: address.

36. TRX easy transfer

    36.1 Interface statement

    rpc EasyTransfer (EasyTransferMessage) returns (EasyTransferResponse) {};

    36.2 Node

    Fullnode.

    36.3 Parameters:

    EasyTransferMessage: password for transfer, toAddress and the amount of tokens to transfer.

    36.4 Returns

    EasyTransferResponse: the transaction of a transfer and the result of broadcasting.