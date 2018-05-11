#################################
Wallet-cli supported command list
#################################

RegisterWallet
==============

RegisterWallet Password.Register a wallet in local.Generate a pair of ecc keys.Derive a AES Key by password and then use the AES algorithm to encrypt and save the private key.The account address is calculated by the public key sha3-256, and taking the last 20 bytes.All subsequent operations that require the use of a private key must enter the password.

ImportWallet
============

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