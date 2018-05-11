Command line operation flow example
-----------------------------------

.. code-block:: shell

    cd wallet-cli

    ./gradlew build

    ./gradlew run -Pcmd

    RegisterWallet 123456      (password = 123456)

    login 123456

    getAddress                 (Print ``address = f286522619d962e6f93235ca27b2cb67a9e5c27b``, backup it)

    BackupWallet 123456        (Print ``priKey = 22be575f19b9ac6e94c7646a19a4c89e06fe99e2c054bd242c0af2b6282a65e9``, backup it) (BackupWallet2Base64 option)

    getbalance                 (Print 'Balance = 0')

    //set genesis.block.assets address to yours. restart java-tron.

    getbalance

    assetIssue 123456 testAssetIssue00001 10000000000000000 1 100 2018-4-1 2018-4-30 1 just-test https://github.com/tronprotocol/wallet-cli/

    getaccount  f286522619d962e6f93235ca27b2cb67a9e5c27b

    (Print balance: 9999900000

    asset {

    key: "testAssetIssue00001"

    value: 10000000000000000

    })

    (cost trx 1000 trx for assetIssue)

    (You can query the trx balance and other asset balances for any account )

    TransferAsset 123456 649DDB4AB82D558AD6809C7AB2BA43D1D1054B3F testAssetIssue00001 10000
