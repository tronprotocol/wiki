=============
TRON Protocol
=============

.. contents:: Table of contents
    :depth: 1
    :local:

TRON Protobuf Protocol
----------------------

**The protocol of TRON is defined by Google Protobuf and contains a range of layers, from account, block to transfer.**

**There are 3 types of account—basic account, asset release account and contract account, and attributes included in each account are name, types, address, balance and related asset.**

**A basic account is able to apply to be a validation node, which has serval parameters, including extra attributes, public key, URL, voting statistics, history performance, etc.**

* There are three different ``Account types`` : ``Normal`` , ``AssetIssue`` , ``Contract`` .

    .. code-block:: shell

        enum AccountType {
            Normal = 0;
            AssetIssue = 1;
            Contract = 2;
        }

* An ``Account`` contains 7 parameters:
    
``account_name`` : the name for this account – e.g. *“_BillsAccount_”*.

``type`` : what type of this account is – e.g. *0* stands for type ``Normal`` .

``balance`` : balance of this account – e.g. *4213312*.

``votes`` : received votes on this account – e.g. *{(“0x1b7w…9xj3”,323), (“0x8djq…j12m”,88),…,(“0x82nd…mx6i”,10001)}*.

``asset``: other assets except TRX in this account – e.g. *{<“WishToken”,66666>,<”Dogie”,233>}*.

``latest_operation_time``: the latest operation time of this account.

    .. code-block:: shell

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
    `address`: the address of this witness – e.g. “_0xu82h…7237_”.
`voteCount`: number of received votes on this witness – e.g. _234234_.
    `pubKey`: the public key for this witness – e.g. “_0xu82h…7237_”.
`url`: the url for this witness – e.g. “_https://www.noonetrust.com_”.
    `totalProduced`: the number of blocks this witness produced – e.g. _2434_.
    `totalMissed`: the number of blocks this witness missed – e.g. _7_.
    `latestBlockNum`: the latest height of block – e.g. _4522_.
    `isjobs`: a bool flag.

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

+	A block typically contains transaction data and a blockheader, which is a list of basic block information, including timestamp, signature, parent hash, root of Merkle tree and so on.

    A block contains `transactions` and a `block_header`.
    `transactions`: transaction data of this block.
    `block_header`: one part of a block.

    // block
    message Block {
    repeated Transaction transactions = 1;
    BlockHeader block_header = 2;
}

A `BlockHeader` contains `raw_data` and `witness_signature`.
    `raw_data`: a `raw` message.
    `witness_signature`: signature for this block header from witness node.

    A message `raw` contains 6 parameters:
    `timestamp`: timestamp of this message – e.g. _14356325_.
    `txTrieRoot`: the root of Merkle Tree in this block – e.g. “_7dacsa…3ed_.”
     `parentHash`: the hash of last block – e.g. “_7dacsa…3ed_.”
     `number`: the height of this block – e.g. _13534657_.
    `witness_id`: the id of witness which packed this block – e.g. “_0xu82h…7237_”.
`witness_address`: the adesss of the witness packed this block – e.g. “_0xu82h…7237_”.

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

message `ChainInventory` contains `BlockId` and `remain_num`.
    `BlockId`: the identification of block.
    `remain_num`：the remain number of blocks in the synchronizing process.

    A `BlockId` contains 2 parameters:
    `hash`: the hash of block.
    `number`: the height of block.

    message ChainInventory {
    message BlockId {
        bytes hash = 1;
        int64 number = 2;
    }
    repeated BlockId ids = 1;
    int64 remain_num = 2;
}

+	Transaction contracts mainly includes account create contract, account update contract transfer contract, transfer asset contract, vote asset contract, vote witness contract, witness creation contract, witness update contract, asset issue contract, participate asset issue contract and deploy contract.

    An `AccountCreateContract` contains 3 parameters:
    `type`: What type this account is – e.g. _0_ stands for `Normal`.
                                                                `account_name`: the name for this account – e.g.”_Billsaccount_”.
`owner_address`: the address of contract owner – e.g. “_0xu82h…7237_”.

message AccountCreateContract {
    AccountType type = 1;
    bytes account_name = 2;
    bytes owner_address = 3;
}

A `AccountUpdateContract` contains 2 paremeters:
    `account_name`: the name for this account – e.g.”_Billsaccount_”.
`owner_address`: the address of contract owner – e.g. “_0xu82h…7237_”.

message AccountUpdateContract {
    bytes account_name = 1;
    bytes owner_address = 2;
}

A `TransferContract` contains 3 parameters:
    `amount`: the amount of TRX – e.g. _12534_.
    `to_address`: the receiver address – e.g. “_0xu82h…7237_”.
`owner_address`: the address of contract owner – e.g. “_0xu82h…7237_”.

message TransferContract {
    bytes owner_address = 1;
    bytes to_address = 2;
    int64 amount = 3;
}

A `TransferAssetContract` contains 4 parameters:
    `asset_name`: the name for asset – e.g.”_Billsaccount_”.
`to_address`: the receiver address – e.g. “_0xu82h…7237_”.
`owner_address`: the address of contract owner – e.g. “_0xu82h…7237_”.
`amount`: the amount of target asset - e.g._12353_.

    message TransferAssetContract {
    bytes asset_name = 1;
    bytes owner_address = 2;
    bytes to_address = 3;
    int64 amount = 4;
}

A `VoteAssetContract` contains 4 parameters:
    `vote_address`: the voted address of the asset.
    `support`: is the votes supportive or not – e.g. _true_.
    `owner_address`: the address of contract owner – e.g. “_0xu82h…7237_”.
`count`: the count number of votes- e.g. _2324234_.

    message VoteAssetContract {
    bytes owner_address = 1;
    repeated bytes vote_address = 2;
    bool support = 3;
    int32 count = 5;
}

A `VoteWitnessContract` contains 4 parameters:
    `vote_address`: the addresses of those who voted.
    `support`: is the votes supportive or not - e.g. _true_.
    `owner_address`: the address of contract owner – e.g. “_0xu82h…7237_”.
`count`: - e.g. the count number of vote – e.g. _32632_.

    message VoteWitnessContract {
    bytes owner_address = 1;
    repeated bytes vote_address = 2;
    bool support = 3;
    int32 count = 5;
}

A `WitnessCreateContract` contains 3 parameters:
    `private_key`: the private key of contract– e.g. “_0xu82h…7237_”.
`owner_address`: the address of contract owner – e.g. “_0xu82h…7237_”.
`url`: the url for the witness – e.g. “_https://www.noonetrust.com_”.

    message WitnessCreateContract {
    bytes owner_address = 1;
    bytes private_key = 2;
    bytes url = 12;
}

A `WitnessUpdateContract` contains 2 parameters:
    `owner_address`: the address of contract owner – e.g. “_0xu82h…7237_”.
`update_url`: the url for the witness – e.g. “_https://www.noonetrust.com_”.

    message WitnessUpdateContract {
    bytes owner_address = 1;
    bytes update_url = 12;
}

An `AssetIssueContract` contains 11 parameters:
    `owner_address`: the address for contract owner – e.g. “_0xu82h…7237_”.
`name`: the name for this contract – e.g. “Billscontract”.
`total_supply`: the maximum supply of this asset – e.g. _1000000000_.
    `trx_num`: the number of TRONIX – e.g._232241_.
    `num`: number of corresponding asset.
    `start_time`: the starting date of this contract – e.g._20170312_.
    `end_time`: the expiring date of this contract – e.g. _20170512_.
    `decay_ratio`: decay ratio.
    `vote_score`: the vote score of this contract received – e.g. _12343_.
    `description`: the description of this contract – e.g.”_trondada_”.
`url`: the url of this contract – e.g. “_https://www.noonetrust.com_”.

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

A `ParticipateAssetIssueContract` contains 4 parameters:
    `owner_address`: the address for contract owner – e.g. “_0xu82h…7237_”.
`to_address`: the receiver address – e.g. “_0xu82h…7237_”.
`asset_name`: the name of target asset.
    `amount`: the amount of drops.

    message ParticipateAssetIssueContract {
    bytes owner_address = 1;
    bytes to_address = 2;
    bytes asset_name = 3;
    int64 amount = 4;
}

A `DeployContract` contains 2 parameters:
    `script`: the script of this contract.
    `owner_address`: the address for contract owner – e.g. “_0xu82h…7237_”.

message DeployContract {
    bytes owner_address = 1;
    bytes script = 2;
}                       t

+	Each transaction contains several TXInputs, TXOutputs and other related qualities.
    Input, transaction and head block all require signature.

    message `Transaction` contains `raw_data` and `signature`.
    `raw_data`: message `raw`.
    `signature`: signatures form all input nodes.

    `raw` contains 8 parameters:
    `type`: the transaction type of `raw` message.
    `vin`: input values.
    `vout`: output values.
    `expiration`: the expiration date of transaction – e.g._20170312_.
    `data`: data.
    `contract`: contracts in this transaction.
    `scripts`:scripts in the transaction.
    `timestamp`: timestamp of this raw data – e.g. _14356325_.

    message `Contract` contains `type` and `parameter`.
    `type`: what type of the message contract.
    `parameter`: It can be any form.

    There are 8 different of contract types: `AccountCreateContract`, `TransferContract`, `TransferAssetContract`, `VoteAssetContract`, `VoteWitnessContract`,`WitnessCreateContract`, `AssetIssueContract` and `DeployContract`.
    `TransactionType` have two types: `UtxoType` and `ContractType`.

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

message `TXOutputs` contains `outputs`.
    `outputs`: an array of `TXOutput`.

    message TXOutputs {
    repeated TXOutput outputs = 1;
}

message `TXOutput` contains `value` and `pubKeyHash`.
    `value`: output value.
    `pubKeyHash`: Hash of public key

message TXOutput {
    int64 value = 1;
    bytes pubKeyHash = 2;
}

message `TXInput` contains `raw_data` and `signature`.
    `raw_data`: a message `raw`.
    `signature`: signature for this `TXInput`.

                                   message `raw` contains `txID`, `vout` and `pubKey`.
    `txID`: transaction ID.
    `vout`: value of last output.
    `pubKey`: public key.

    message TXInput {
    message raw {
        bytes txID = 1;
        int64 vout = 2;
        bytes pubKey = 3;
    }
    raw raw_data = 1;
    bytes signature = 4;
}

message `Result` contains `fee` and `ret`.
    `ret`: the state of transaction.
    `fee`: the fee for transaction.

                           `code` is the enumerator that defines `ret` property and can be  2 types：`SUCCESS` and `FAILED`.

    message Result {
    enum code {
        SUCESS = 0;
    FAILED = 1;
}
    int64 fee = 1;
    code ret = 2;
}

+	Inventory is mainly used to inform peer nodes the list of items.

    `Inventory` contains `type` and `ids`.
    `type`: what type this `Inventory` is. – e.g. _0_ stands for `TRX`.
                                                                     `ids`: ID of things in this `Inventory`.

    Two `Inventory` types: `TRX` and `BLOCK`.
    `TRX`: transaction.
    `BLOCK`: block.

    // Inventory 
    message Inventory {
    enum InventoryType {
        TRX = 0;
    BLOCK = 1;
}
    InventoryType type = 1;
    repeated bytes ids = 2;
}

message `Items` contains 4 parameters:
    `type`: type of items – e.g. _1_ stands for `TRX`.
                                                    `blocks`: blocks in `Items` if there is any.
    `block_headers`: block headers if there is any.
    `transactions`: transactions if there is any.

    `Items` have four types: `ERR`, `TRX`, `BLOCK` and `BLOCKHEADER`.
    `ERR`: error.
    `TRX`: transaction.
    `BLOCK`: block.
    `BLOCKHEADER`: block header.

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

`InventoryItems` contains `type` and `items`.
    `type`: what type of inventory.
    `items`: the list of inventory.

    message InventoryItems {
    int32 type = 1;
    repeated bytes items = 2;
}

message `BlockInventory` contains `type`.
    `type`: what type of inventory.

    There are 3 types:`SYNC`, `ADVTISE`, `FETCH`.

    // Inventory
    message BlockInventory {
    enum Type {
        SYNC = 0;
    ADVTISE = 1;
    FETCH = 2;
}

    message `BlockId` contains `ids` and `type`.
        `ids`: the identification of block.
        `type`: what type of the block.

        `ids` contains 2 parameters:
        `hash`: the hash of block.
        `number`: the height of block.

        message BlockId {
        bytes hash = 1;
        int64 number = 2;
    }
    repeated BlockId ids = 1;
    Type type = 2;
}

`ReasonCode`: the type of reason.

    `ReasonCode` contains 15 types of disconnect reasons:
    `REQUESTED`
        `TCP_ERROR`
        `BAD_PROTOCOL`
        `USELESS_PEER`
        `TOO_MANY_PEERS`
        `DUPLICATE_PEER`
        `INCOMPATIBLE_PROTOCOL`
        `NULL_IDENTITY`
        `PEER_QUITING`
        `UNEXPECTED_IDENTITY`
        `LOCAL_IDENTITY`
        `PING_TIMEOUT`
        `USER_REASON`
        `RESET`
        `UNKNOWN`

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

message`DisconnectMessage` contains `reason`.
    `DisconnectMessage`: the message when disconnection occurs.
    `reason`: the reason for disconnecting.

                                 message`HelloMessage` contains 2 parameters:
    `HelloMessage`: the message for building connection.
    `from`: the nodes that request for building connection.
    `version`: the version when connection is built.



+	Wallet Service RPC and blockchain explorer

    `Wallet` service contains several RPCs.
    __`GetBalance`__ :
    Return balance of an `Account`.
    __`CreateTransaction`__ ：
    Create a transaction by giving a `TransferContract`. A Transaction containing a transaction creation will be returned.
    __`BroadcastTransaction`__ :
    Broadcast a `Transaction`. A `Return` will be returned indicating if broadcast is success of not.
    __`CreateAccount`__ :
    Create an account by giving a `AccountCreateContract`.
    __`CreatAssetIssue`__ :
    Issue an asset by giving a `AssetIssueContract`.
    __`ListAccounts`__:
    Check out the list of accounts by giving a `ListAccounts`.
    __`UpdateAccount`__:
    Issue an asset by giving a `UpdateAccountContract`.
    __`VoteWitnessAccount`__:
    Issue an asset by giving a `VoteWitnessContract`.
    __`WitnessList`__:
    Check out the list of witnesses by giving a `WitnessList`.
    __`UpdateWitness`__:
    Issue an asset by giving a `WitnessUpdateContract`.
    __`CreateWitness`__:
    Issue an asset by giving a `WitnessCreateContract`.
    __`TransferAsset`__:
    Issue an asset by giving a `TransferAssetContract`.
    __`ParticipateAssetIssue`__:
    Issue an asset by giving a `ParticipateAssetIssueContract`.
    __`ListNodes`__:
    Check out the list of nodes by giving a `ListNodes`.
    __`GetAssetIssueList`__:
    Get the list of issue asset by giving a `GetAssetIssueList`.
    __`GetAssetIssueByAccount`__:
    Get issue asset by giving a `Account`.
    __`GetAssetIssueByName`__:
    Get issue asset by giving a`Name`.
    __`GetNowBlock`__:
    Get block.
    __`GetBlockByNum`__:
    Get block by block number.
    __`TotalTransaction`__:
    Check out the total transaction.

    service Wallet {

    rpc GetAccount (Account) returns (Account) {
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

`WalletSolidity` service contains several RPCs.
    __`GetAccount`__ :
    `GetAccount` takes a parameter of Account, and returns an `Account` object.
    __`ListAccounts`__:
    `listAccounts` takes a parameter of EmptyMessage , and returns `listAccounts` object.
    __`ListWitness`__:
    `LitWitness` takes a parameter of EmptyMessage, and returns `WitnessList` object.
    __`ListNodes`__:
    `ListNodes` takes a parameter of EmptyMessage, and returns `NodeList` object.
    __`GetAssetIssueList`__:
    `GetAssetIssueList` takes a parameter of EmptyMessage, and returns `AssetIssueList` object.
    __`GetAssetIssueListByTimeStamp`__:
    `GetAssetIssueListByTimeStamp` takes a parameter of EmptyMessage, and returns `AsssetIssueList` object.
    __`GetAssetIssueByAccount`__:
    `GetAssetIssueByAccount` takes a parameter of `Account`, and returns `AssetIssueList` object.
    _`GetAssetIssueByName`__:
    `GetAssetIssueByName` takes a parameter of `BytesMessage`, and returns `AssetIssueContract`.
    __`GetNowBlock`__:
    `GetNowBlock` takes a parameter of `EmptyMessage`, and returns `Block`.
    __`GetBlockByNum`__:
    `GetBlockByNumber` takes a parameter of `NumberMessage`, and returns `Block`.
    __`TotalTransaction`__:
    `TotalTransaction` takes a parameter of `EmptyMessage`, and returns `NumberMessage`.
    __`getTransactionById`__:
    `getTransactionById` takes a parameter of `BytesMessage`, and returns `Transaction`.
    __`getTransactionsByTimeStamp`__:
    `getTransactionsByTimeStamp` takes a parameter of `TimeMessage`, and returns `TransactionList`.
    __`getTransactionsFromThis`__:
    `getTransactionsFromThis` takes a parameter of `Account`, and returns `TransactionList`.
    __`getTransactionsToThis`__:
    `getTransactionsToThis` takes a parameter of `Account`, and returns ` NumberMessage`.

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

    Get transaction.

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

`AccountList`: the list of acounts in the blockchain explorer.
    message `AccountList` contains one parameter:
    `account`:

message AccountList {
    repeated Account accounts = 1;
}

`WitnessList`: the list of witnesses in the blockchain explorer.
    message `WitnessList` contains one parameter:
    `witnesses`:

message WitnessList {
    repeated Witness witnesses = 1;
}

`AssetIssueList`: the list of issue asset in the blockchain explorer.
    message `AssetIssueList` contains one parameter:
    `assetIssue`:

message AssetIssueList {
    repeated AssetIssueContract assetIssue = 1;
}

`NodeList`: the list of nodes in the node distribution map.
    message `NodeList` contains one parameter:
    `nodes`:

message NodeList {
    repeated Node nodes = 1;
}

`Address`: the address  of nodes.
    message`Address` contains 2 parameters:
    `host`: the host of nodes.
    `port`: the port number of nodes.

    message Address {
    bytes host = 1;
    int32 port = 2;
}

message `Return` has only one parameter:
    `result`: a bool flag.

    message `Return` {
    bool result = 1;
}

+ The message structure of UDP.

    `Endpoint`: the storage structure of nodes' information.
message`Endpoint` contains 3 parameters:
    `address`: the address of nodes.
    `port`: the port number.
    `nodeId`:the ID of nodes.


    message Endpoint {
    bytes address = 1;
    int32 port = 2;
    bytes nodeId = 3;
}

`PingMessage`: the message sent from one node to another in the connecting process.
    message`PingMessage` contains 4 parameters:
    `from`: which node does the message send from.
    `to`: which node will the message send to.
    `version`: the version of the Internet.
    `timestamp`: the timestamp of message.

    message PingMessage {
    Endpoint from = 1;
    Endpoint to = 2;
    int32 version = 3;
    int64 timestamp = 4;
}

`PongMessage`: the message implies that nodes are connected.
    message`PongMessage` contains 3 parameters:
    `from`: which node does the message send from.
    `echo`:
`timestamp`: the timestamp of message.

    message PongMessage {
    Endpoint from = 1;
    int32 echo = 2;
    int64 timestamp = 3;
}

`FindNeighbours`: the message sent from one node to find another one.
    message`FindNeighbours` contains 3 parameters:
    `from`: which node does the message send from.
    `targetId`: the ID of targeted node.
    `timestamp`: the timestamp of message.

    message FindNeighbours {
    Endpoint from = 1;
    bytes targetId = 2;
    int64 timestamp = 3;
}

`FindNeighbour`: the message replied by the neighbour node.
    message`Neighbours` contains 3 parameters:
    `from`: which node does the message send from.
    `neighbours`: the neighbour node.
    `timestamp`: the timestamp of message.

    message Neighbours {
    Endpoint from = 1;
    repeated Endpoint neighbours = 2;
    int64 timestamp = 3;
}



# Please check detailed protocol document that may change with the iteration of the program at any time. Please refer to the latest version.




    #TRON Wallet RPC-API

## 1. Getting account information

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

## 2. TRX transfer

2.1	Interface statement
rpc CreateTransaction (TransferContract) returns (Transaction)　{};
2.2	Node
Fullnode.
2.3	Parameters
TransferContract: addresses of the sender and the recipient, and amount of transfer (in drop).
2.4	Returns
Transaction: returns transaction of transfer contract; request transaction after acquisition of wallet signature.
2.5	Function
Transfer. Creation of a transaction of transfer.

## 3. Transaction broadcasting

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

## 4. Query of account list

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

## 5. Creating account

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

## 6. Account update (to be realized)

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

## 7. Vote

7.1	Interface statement
rpc VoteWitnessAccount (VoteWitnessContract) returns (Transaction){};
7.2	Node
Fullnode.
7.3	Parameters
VoteWitnessContract: voter address and list of votes; candidate address and number of votes received.
7.4	Returns
Transaction: returns transaction of votes
7.5	Function
Vote. Coin holders can only vote for Super Representative candidates, with no more votes than the amount of holding of TRX.

## 8. Token issuance

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

## 9. Query of list of Super Representative candidates

9.1	Interface statement
rpc ListWitnesses (EmptyMessage) returns (WitnessList) {};
9.2	Nodes
Fullnode and soliditynode.
9.3	parameters
EmptyMessage: null.
9.4	Returns
WitnessList: list of witnesses and detailed information of the candidates.
9.5	Function
Query of all candidates prior to voting. Display

## 10. Application for Super Representative (to be realized)

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

## 11. Information update of Super Representative candidate (to be realized)

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

## 12. Token transfer

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

## 13. Participation in token offering

13.1 Interface statement
rpc ParticipateAssetIssue (ParticipateAssetIssueContract) returns (Transaction){};
13.2 Node
Fullnode.
13.3 Parameters
ParticipateAssetIssueContract: participant address, issuer address, token name, and amount of token (in drop).
13.4 Returns
Transaction: returns transaction of participation in token offering.
13.5 Function
Participation in toke offering.

## 14. Query of nodes

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

#3 15. Query of tokens

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

## 16. Query of tokens issued by a given account

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

## 17. Query of token information with token name

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

## 18. Query of current tokens by timestamp (to be realized)

18.1 Interface statement
rpc GetAssetIssueListByTimestamp (NumberMessage) returns (AssetIssueList){};
18.2 Node
Soliditynode.
18.3 Parameters
NumberMessage: current timestamp (the number of milliseconds since 1970)
18.4 Returns
AssetIssueList: AssetIssueContract list and detailed information
18.5 Function
List of all nodes. Display of current nodes for users’ reference.

## 19. Get current block

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


## 20. Get block by block height

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

## 21. Get total number of transactions

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

## 22. Query of transaction by ID (to be realized)

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

## 23. Query of transaction by timestamp (to be realized)

23.1 Interface statement
rpc getTransactionsByTimestamp (TimeMessage) returns (TransactionList) {};
23.2 Node
Soliditynod.
23.3 Parameters
TimeMessage: starting time and ending time.
23.4 Returns
TransactionList: transaction list.
23.5 Function
Query of transactions by starting and ending time.

## 24. Query of transaction initiations by address (to be realized)

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

## 25. Query of transaction receptions by address (to be realized)

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


