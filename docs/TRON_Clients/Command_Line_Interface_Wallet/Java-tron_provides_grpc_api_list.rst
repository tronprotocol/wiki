Java-tron provides grpc api list:
------------------------------------

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
