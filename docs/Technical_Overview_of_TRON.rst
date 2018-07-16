==========================
Technical Overview of TRON
==========================

.. contents:: Table of contents
    :depth: 1
    :local:

Structure of TRON Network
-------------------------

Node types
~~~~~~~~~~

There are three types of nodes on Tron’s network, namely witness, FullNode and SolidityNode. A witness is responsible for block production; a FullNode provides APIs, and broadcasts transactions and blocks; a SolidityNode synchronizes irrevocable blocks and provides inquiry APIs.

Network deployment (of exchanges)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Exchanges need to deploy a FullNode and a SolidityNode. The SolidityNode connects to the local FullNode which connects to the mainnet.

Mainnet and Testnet
~~~~~~~~~~~~~~~~~~~

The blockchain explorer of the mainnet is https://tronscan.org.

The blockchain explorer of the testnet is https://test.tronscan.org.

Exchanges should test their code in testnet.

About how to config testnet, please refer to

.. code-block:: shell

    net {
        type = mainnet
    }

    storage {
    # Directory for storing persistent data

    db.directory = "database",
    index.directory = "index",

    # You can custom these 14 databases' configs:

    # account, account-index, asset-issue, block, block-index,
    # block_KDB, peers, properties, recent-block, trans,
    # utxo, votes, witness, witness_schedule.

    # Otherwise, db configs will remain defualt and data will be stored in
    # the path of "output-directory" or which is set by "-d" ("--output-directory").

    # Attention: name is a required field that must be set !!!
    properties = [
    //    {
    //      name = "account",
    //      path = "storage_directory_test",
    //      createIfMissing = true,
    //      paranoidChecks = true,
    //      verifyChecksums = true,
        //      compressionType = 1,        // compressed with snappy
        //      blockSize = 4096,           // 4  KB =         4 * 1024 B
        //      writeBufferSize = 10485760, // 10 MB = 10 * 1024 * 1024 B
        //      cacheSize = 10485760,       // 10 MB = 10 * 1024 * 1024 B
        //      maxOpenFiles = 100
    //    },
    //    {
    //      name = "account-index",
    //      path = "storage_directory_test",
    //      createIfMissing = true,
    //      paranoidChecks = true,
    //      verifyChecksums = true,
        //      compressionType = 1,        // compressed with snappy
        //      blockSize = 4096,           // 4  KB =         4 * 1024 B
        //      writeBufferSize = 10485760, // 10 MB = 10 * 1024 * 1024 B
        //      cacheSize = 10485760,       // 10 MB = 10 * 1024 * 1024 B
        //      maxOpenFiles = 100
        //    },
    ]

    }

    node.discovery = {
        enable = true
        persist = true
        bind.ip = ""
        external.ip = null
    }

    node.backup {
        port = 10001
        priority = 8
        members = [
        ]
    }

    node {
        # trust node for solidity node
        # trustNode = "ip:port"
        trustNode = "127.0.0.1:50051"

    # expose extension api to public or not
    walletExtensionApi = true

    listen.port = 18888

    connection.timeout = 2

    tcpNettyWorkThreadNum = 0

    udpNettyWorkThreadNum = 1

    # Number of validate sign thread, default availableProcessors / 2
    # validateSignThreadNum = 16

    active = [
        # Initial active peers
        # Sample entries:
        # "ip:port",
        # "ip:port"
    ]

    maxActiveNodes = 30

    maxActiveNodesWithSameIp = 5

    minParticipationRate = 0

    p2p {
        version = 20180622
    }

    rpc {
        port = 50051

        # Number of gRPC thread, default availableProcessors / 2
        # thread = 16

        # The maximum number of concurrent calls permitted for each incoming connection
        # maxConcurrentCallsPerConnection =

        # The HTTP/2 flow control window, default 1MB
        # flowControlWindow =

        # Connection being idle for longer than which will be gracefully terminated
        maxConnectionIdleInMillis = 60000

        # Connection lasting longer than which will be gracefully terminated
        # maxConnectionAgeInMillis =

        # The maximum message size allowed to be received on the server, default 4MB
        # maxMessageSize =

        # The maximum size of header list allowed to be received, default 8192
        # maxHeaderListSize =
    }

    }

    active.node = [
        # Active establish connection in any case
        # Sample entries:
        # "ip:port",
        # "ip:port"
    ]

    trust.node = [
        # Passive accept connection in any case
        # Sample entries:
        # "ip:port",
        # "ip:port"
    ]

    seed.node = {
        # List of the seed nodes
        # Seed nodes are stable FullNodes
        # example:
        # ip.list = [
        #   "ip:port",
        #   "ip:port"
        # ]
    ip.list = [
    "47.254.144.25:18888",
    "47.254.146.147:18888",
    "47.254.16.55:18888",
    "47.254.18.49:18888",
    "52.14.86.232:18888"
        ]
    }

    genesis.block = {
    # Reserve balance
        assets = [
    {
      accountName = "Zion"
      accountType = "AssetIssue"
      address = "TNNqZuYhMfQvooC4kJwTsMJEQVU3vWGa5u"
      balance = "95000000000000000"
    },
    {
      accountName = "Sun"
      accountType = "AssetIssue"
      address = "TWsm8HtU2A5eEzoT8ev8yaoFjHsXLLrckb"
      balance = "5000000000000000"
    },
    {
      accountName = "Blackhole"
      accountType = "AssetIssue"
      address = "TSJD5rdu6wZXP7F2m3a3tn8Co3JcMjtBip"
      balance = "-9223372036854775808"
    }
  ]

    witnesses = [
    {
      address: TVdyt1s88BdiCjKt6K2YuoSmpWScZYK1QF,
      url = "http://Alioth.com",
      voteCount = 100027
    },
    {
      address: TCNVmGtkfknHpKSZXepZDXRowHF7kosxcv,
      url = "http://Aries.com",
      voteCount = 100026
    },
    {
      address: TAbzgkG8p3yF5aywKVgq9AaAu6hvF2JrVC,
      url = "http://Cancer.com",
      voteCount = 100025
    },
    {
      address: TMmmvwvkBPBv3Gkw9cGKbZ8PLznYkTu3ep,
      url = "http://Capricorn.com",
      voteCount = 100024
    },
    {
      address: TBJHZu4Sm86aWHtt6VF6KQSzot8vKTuTKx,
      url = "http://Cassiopeia.com",
      voteCount = 100023
    },
    {
      address: TLvCstA93piBhpdvMggJ9r5b793b6rqdGd,
      url = "http://Crux.com",
      voteCount = 100022
    },
    {
      address: TEf2ADumcubtg9NeNi7bNP14KfvYxKzTDu,
      url = "http://Delphinus.com",
      voteCount = 100021
    },
    {
      address: TTqqbNxnqniyeCFi4aYwQQFHtuMwiBLARo,
      url = "http://Dorado.com",
      voteCount = 100020
    },
    {
      address: TWwJwoqAYvUVjmp5odhwZYgKekBqL3Mbcf,
      url = "http://Dubhe.com",
      voteCount = 100019
    },
    {
      address: TCPKsDZCJDzC83KWcAnHo9b46DN9o4s48y,
      url = "http://Eridanus.com",
      voteCount = 100018
    },
    {
      address: TJnd8wF5ScEvuYq4WnJUyGbg6iS7ibnWrY,
      url = "http://Gemini.com",
      voteCount = 100017
    },
    {
      address: TTZDB64rNpdw8rpEKko5FhB7BMUf5y4JMT,
      url = "http://Hercules.com",
      voteCount = 100016
    },
    {
      address: TVWapNccbdFDqdHjFGnJ8ePancR6HjSned,
      url = "http://Leo.com",
      voteCount = 100015
    },
    {
      address: TUVdiR6bYsuDNB5HWPLyK3ueY6225n5AdJ,
      url = "http://Libra.com",
      voteCount = 100014
    },
    {
      address: TRBQFNJrJJzzgqfnbP9WvAjWd2oCNyqanC,
      url = "http://Lupus.com",
      voteCount = 100013
    },
    {
      address: TBSq7zAhyEyVf96tbQmh6SwBGRiQXJf9sx,
      url = "http://Lyra.com",
      voteCount = 100012
    },
    {
      address: TFZhwKPxqadgLGSwkiD1JeFJgfSMn2BD75,
      url = "http://Monoceros.com",
      voteCount = 100011
    },
    {
      address: TZ6PqKSodEW7yQNYSDS8WoDo8t3SfACV3V,
      url = "http://Norma.com",
      voteCount = 100010
    },
    {
      address: TSiyqwmcqsDBXQmWPZhC4Y5zncECMN61Li,
      url = "http://Orion.com",
      voteCount = 100009
    },
    {
      address: TVnWr8bm3b2gDrJDBTfWXuPXiT1cvZUGan,
      url = "http://Pavo.com",
      voteCount = 100008
    },
    {
      address: TNR2BDkX53rFCvkSg89nK7nfeC6hLN7B5o,
      url = "http://Perseus.com",
      voteCount = 100007
    },
    {
      address: TVw2k1pD3n4ErWnr4uWmjVwsdai8vT5wyn,
      url = "http://Phecda.com",
      voteCount = 100006
    },
    {
      address: THtcGdFXoGWNd9PDrhCradfvcdsQAoNVAC,
      url = "http://Phoenix.com",
      voteCount = 100005
    },
    {
      address: TEZ31xxrECtLmsGvQFnh2quQVxKFoHxqqu,
      url = "http://Pyxis.com",
      voteCount = 100004
    },
    {
      address: TA6ztifHZSkQ5F6KMe73rYRgQ5fBKLPomV,
      url = "http://Scutum.com",
      voteCount = 100003
    },
    {
      address: TXuLKjf8J8aCKgDgA5uczwn1yQNYVPLocY,
      url = "http://Taurus.com",
      voteCount = 100002
    },
    {
      address: TAihbgDWBK1QTS5gsk7evWDy2nhpkmkGZJ,
      url = "http://Volans.com",
      voteCount = 100001
    }
  ]

  timestamp = "0" #2017-8-26 12:00:00

  parentHash = "0x9e524e0d6bfbbd25a9bd9cf5c5389f122e2bc2e66a29569d532739a1aa4376ae"
    }

    localwitness = [
    ]

    #localwitnesskeystore = [
    #  "src/main/resources/localwitnesskeystore.json"
    #]

    block = {
        needSyncCheck = true # first node : false, other : true
        maintenanceTimeInterval = 21600000 // 1 day: 86400000(ms), 6 hours: 21600000(ms)
     }

About how to config mainnet, please refer to

.. code-block:: shell

    net {
      type = mainnet
      # type = testnet
    }

    storage {
      # Directory for storing persistent data

      db.directory = "database",
      index.directory = "index",

      # You can custom these 14 databases' configs:

      # account, account-index, asset-issue, block, block-index,
      # block_KDB, peers, properties, recent-block, trans,
      # utxo, votes, witness, witness_schedule.

      # Otherwise, db configs will remain defualt and data will be stored in
      # the path of "output-directory" or which is set by "-d" ("--output-directory").

      # Attention: name is a required field that must be set !!!
      properties = [
    //    {
    //      name = "account",
    //      path = "storage_directory_test",
    //      createIfMissing = true,
    //      paranoidChecks = true,
    //      verifyChecksums = true,
        //      compressionType = 1,        // compressed with snappy
        //      blockSize = 4096,           // 4  KB =         4 * 1024 B
        //      writeBufferSize = 10485760, // 10 MB = 10 * 1024 * 1024 B
        //      cacheSize = 10485760,       // 10 MB = 10 * 1024 * 1024 B
        //      maxOpenFiles = 100
    //    },
    //    {
    //      name = "account-index",
    //      path = "storage_directory_test",
    //      createIfMissing = true,
    //      paranoidChecks = true,
    //      verifyChecksums = true,
        //      compressionType = 1,        // compressed with snappy
        //      blockSize = 4096,           // 4  KB =         4 * 1024 B
        //      writeBufferSize = 10485760, // 10 MB = 10 * 1024 * 1024 B
        //      cacheSize = 10485760,       // 10 MB = 10 * 1024 * 1024 B
        //      maxOpenFiles = 100
        //    },
      ]

    }

    node.discovery = {
      enable = true
      persist = true
      bind.ip = ""
      external.ip = null
    }

    node.backup {
      port = 10001
      priority = 8
      members = [
      ]
    }

    node {
      # trust node for solidity node
      # trustNode = "ip:port"
      trustNode = "127.0.0.1:50051"

      # expose extension api to public or not
      walletExtensionApi = true

      listen.port = 18888

      connection.timeout = 2

      tcpNettyWorkThreadNum = 0

      udpNettyWorkThreadNum = 1

      # Number of validate sign thread, default availableProcessors / 2
      # validateSignThreadNum = 16

      maxActiveNodes = 30

      maxActiveNodesWithSameIp = 2

      minParticipationRate = 15

      p2p {
        version = 11111 # 11111: mainnet; 20180622: testnet
      }

      active = [
        # Active establish connection in any case
        # Sample entries:
        # "ip:port",
        # "ip:port"
      ]

      passive = [
        # Passive accept connection in any case
        # Sample entries:
        # "ip:port",
        # "ip:port"
      ]

      rpc {
        port = 50051

        # Number of gRPC thread, default availableProcessors / 2
        # thread = 16

        # The maximum number of concurrent calls permitted for each incoming connection
        # maxConcurrentCallsPerConnection =

        # The HTTP/2 flow control window, default 1MB
        # flowControlWindow =

        # Connection being idle for longer than which will be gracefully terminated
        maxConnectionIdleInMillis = 60000

        # Connection lasting longer than which will be gracefully terminated
        # maxConnectionAgeInMillis =

        # The maximum message size allowed to be received on the server, default 4MB
        # maxMessageSize =

        # The maximum size of header list allowed to be received, default 8192
        # maxHeaderListSize =
      }

    }



    seed.node = {
      # List of the seed nodes
      # Seed nodes are stable FullNodes
      # example:
      # ip.list = [
      #   "ip:port",
      #   "ip:port"
      # ]
      ip.list = [
        "54.236.37.243:18888",
        "52.53.189.99:18888",
        "18.196.99.16:18888",
        "34.253.187.192:18888",
        "52.56.56.149:18888",
        "35.180.51.163:18888",
        "54.252.224.209:18888",
        "18.228.15.36:18888",
        "52.15.93.92:18888",
        "34.220.77.106:18888",
        "13.127.47.162:18888",
        "13.124.62.58:18888",
        "13.229.128.108:18888",
        "35.182.37.246:18888",
        "34.200.228.125:18888",
        "18.220.232.201:18888",
        "13.57.30.186:18888",
        "35.165.103.105:18888",
        "18.184.238.21:18888",
        "34.250.140.143:18888",
        "35.176.192.130:18888",
        "52.47.197.188:18888",
        "52.62.210.100:18888",
        "13.231.4.243:18888",
        "18.231.76.29:18888",
        "35.154.90.144:18888",
        "13.125.210.234:18888",
        "13.250.40.82:18888",
        "35.183.101.48:18888"
      ]
    }

    genesis.block = {
      # Reserve balance
      assets = [
        {
          accountName = "Zion"
          accountType = "AssetIssue"
          address = "TLLM21wteSPs4hKjbxgmH1L6poyMjeTbHm"
          balance = "99000000000000000"
        },
        {
          accountName = "Sun"
          accountType = "AssetIssue"
          address = "TXmVpin5vq5gdZsciyyjdZgKRUju4st1wM"
          balance = "0"
        },
        {
          accountName = "Blackhole"
          accountType = "AssetIssue"
          address = "TLsV52sRDL79HXGGm9yzwKibb6BeruhUzy"
          balance = "-9223372036854775808"
        }
      ]

      witnesses = [
        {
          address: THKJYuUmMKKARNf7s2VT51g5uPY6KEqnat,
          url = "http://GR1.com",
          voteCount = 100000026
        },
        {
          address: TVDmPWGYxgi5DNeW8hXrzrhY8Y6zgxPNg4,
          url = "http://GR2.com",
          voteCount = 100000025
        },
        {
          address: TWKZN1JJPFydd5rMgMCV5aZTSiwmoksSZv,
          url = "http://GR3.com",
          voteCount = 100000024
        },
        {
          address: TDarXEG2rAD57oa7JTK785Yb2Et32UzY32,
          url = "http://GR4.com",
          voteCount = 100000023
        },
        {
          address: TAmFfS4Tmm8yKeoqZN8x51ASwdQBdnVizt,
          url = "http://GR5.com",
          voteCount = 100000022
        },
        {
          address: TK6V5Pw2UWQWpySnZyCDZaAvu1y48oRgXN,
          url = "http://GR6.com",
          voteCount = 100000021
        },
        {
          address: TGqFJPFiEqdZx52ZR4QcKHz4Zr3QXA24VL,
          url = "http://GR7.com",
          voteCount = 100000020
        },
        {
          address: TC1ZCj9Ne3j5v3TLx5ZCDLD55MU9g3XqQW,
          url = "http://GR8.com",
          voteCount = 100000019
        },
        {
          address: TWm3id3mrQ42guf7c4oVpYExyTYnEGy3JL,
          url = "http://GR9.com",
          voteCount = 100000018
        },
        {
          address: TCvwc3FV3ssq2rD82rMmjhT4PVXYTsFcKV,
          url = "http://GR10.com",
          voteCount = 100000017
        },
        {
          address: TFuC2Qge4GxA2U9abKxk1pw3YZvGM5XRir,
          url = "http://GR11.com",
          voteCount = 100000016
        },
        {
          address: TNGoca1VHC6Y5Jd2B1VFpFEhizVk92Rz85,
          url = "http://GR12.com",
          voteCount = 100000015
        },
        {
          address: TLCjmH6SqGK8twZ9XrBDWpBbfyvEXihhNS,
          url = "http://GR13.com",
          voteCount = 100000014
        },
        {
          address: TEEzguTtCihbRPfjf1CvW8Euxz1kKuvtR9,
          url = "http://GR14.com",
          voteCount = 100000013
        },
        {
          address: TZHvwiw9cehbMxrtTbmAexm9oPo4eFFvLS,
          url = "http://GR15.com",
          voteCount = 100000012
        },
        {
          address: TGK6iAKgBmHeQyp5hn3imB71EDnFPkXiPR,
          url = "http://GR16.com",
          voteCount = 100000011
        },
        {
          address: TLaqfGrxZ3dykAFps7M2B4gETTX1yixPgN,
          url = "http://GR17.com",
          voteCount = 100000010
        },
        {
          address: TX3ZceVew6yLC5hWTXnjrUFtiFfUDGKGty,
          url = "http://GR18.com",
          voteCount = 100000009
        },
        {
          address: TYednHaV9zXpnPchSywVpnseQxY9Pxw4do,
          url = "http://GR19.com",
          voteCount = 100000008
        },
        {
          address: TCf5cqLffPccEY7hcsabiFnMfdipfyryvr,
          url = "http://GR20.com",
          voteCount = 100000007
        },
        {
          address: TAa14iLEKPAetX49mzaxZmH6saRxcX7dT5,
          url = "http://GR21.com",
          voteCount = 100000006
        },
        {
          address: TBYsHxDmFaRmfCF3jZNmgeJE8sDnTNKHbz,
          url = "http://GR22.com",
          voteCount = 100000005
        },
        {
          address: TEVAq8dmSQyTYK7uP1ZnZpa6MBVR83GsV6,
          url = "http://GR23.com",
          voteCount = 100000004
        },
        {
          address: TRKJzrZxN34YyB8aBqqPDt7g4fv6sieemz,
          url = "http://GR24.com",
          voteCount = 100000003
        },
        {
          address: TRMP6SKeFUt5NtMLzJv8kdpYuHRnEGjGfe,
          url = "http://GR25.com",
          voteCount = 100000002
        },
        {
          address: TDbNE1VajxjpgM5p7FyGNDASt3UVoFbiD3,
          url = "http://GR26.com",
          voteCount = 100000001
        },
        {
          address: TLTDZBcPoJ8tZ6TTEeEqEvwYFk2wgotSfD,
          url = "http://GR27.com",
          voteCount = 100000000
        }
      ]

      timestamp = "0" #2017-8-26 12:00:00

      parentHash = "0xe58f33f9baf9305dc6f82b9f1934ea8f0ade2defb951258d50167028c780351f"
    }

    #localwitness = [
    #]

    localwitnesskeystore = [
      "localwitnesskeystore.json"
    ]

    block = {
      needSyncCheck = true
      maintenanceTimeInterval = 21600000
    }

TRON Testnet
~~~~~~~~~~~~

**Tronscan**

https://test.tronscan.org

**Code version**

Latest master branch

https://test.tronscan.org

**How to connect to the testnet**

1. Modify ``.conf`` file for both FullNode and SolidityNode

2. Delete db directory output-directory for both FullNode and SolidityNode

3. Key modifications:

.. code-block:: shell

    p2p {
        version = 20180622
    }

    parentHash = "0x9e524e0d6bfbbd25a9bd9cf5c5389f122e2bc2e66a29569d532739a1aa4376ae"

**Sample Startup Configuration File**

.. code-block:: shell

    net {
      type = mainnet
    }

    storage {
      # Directory for storing persistent data

      db.directory = "database",
      index.directory = "index",

      # You can custom these 14 databases' configs:

      # account, account-index, asset-issue, block, block-index,
      # block_KDB, peers, properties, recent-block, trans,
      # utxo, votes, witness, witness_schedule.

      # Otherwise, db configs will remain default and data will be stored in
      # the path of "output-directory" or which is set by "-d" ("--output-directory").

      # Attention: name is a required field that must be set !!!
      properties = [
    //    {
    //      name = "account",
    //      path = "storage_directory_test",
    //      createIfMissing = true,
    //      paranoidChecks = true,
    //      verifyChecksums = true,
        //      compressionType = 1,        // compressed with snappy
        //      blockSize = 4096,           // 4  KB =         4 * 1024 B
        //      writeBufferSize = 10485760, // 10 MB = 10 * 1024 * 1024 B
        //      cacheSize = 10485760,       // 10 MB = 10 * 1024 * 1024 B
        //      maxOpenFiles = 100
    //    },
    //    {
    //      name = "account-index",
    //      path = "storage_directory_test",
    //      createIfMissing = true,
    //      paranoidChecks = true,
    //      verifyChecksums = true,
        //      compressionType = 1,        // compressed with snappy
        //      blockSize = 4096,           // 4  KB =         4 * 1024 B
        //      writeBufferSize = 10485760, // 10 MB = 10 * 1024 * 1024 B
        //      cacheSize = 10485760,       // 10 MB = 10 * 1024 * 1024 B
        //      maxOpenFiles = 100
        //    },
      ]

    }

    node.discovery = {
      enable = true
      persist = true
      bind.ip = ""
      external.ip = null
    }

    node.backup {
      port = 10001
      priority = 8
      members = [
      ]
    }

    node {
      # trust node for solidity node
      # trustNode = "ip:port"
      trustNode = "127.0.0.1:50051"

      # expose extension api to public or not
      walletExtensionApi = true

      listen.port = 18888

      connection.timeout = 2

      tcpNettyWorkThreadNum = 0

      udpNettyWorkThreadNum = 1

      # Number of validate sign thread, default availableProcessors / 2
      # validateSignThreadNum = 16

      active = [
        # Initial active peers
        # Sample entries:
        # "ip:port",
        # "ip:port"
      ]

      maxActiveNodes = 30

      maxActiveNodesWithSameIp = 5

      minParticipationRate = 0

      p2p {
        version = 20180622
      }

      rpc {
        port = 50051

        # Number of gRPC thread, default availableProcessors / 2
        # thread = 16

        # The maximum number of concurrent calls permitted for each incoming connection
        # maxConcurrentCallsPerConnection =

        # The HTTP/2 flow control window, default 1MB
        # flowControlWindow =

        # Connection being idle for longer than which will be gracefully terminated
        maxConnectionIdleInMillis = 60000

        # Connection lasting longer than which will be gracefully terminated
        # maxConnectionAgeInMillis =

        # The maximum message size allowed to be received on the server, default 4MB
        # maxMessageSize =

        # The maximum size of header list allowed to be received, default 8192
        # maxHeaderListSize =
      }

    }

    active.node = [
      # Active establish connection in any case
      # Sample entries:
      # "ip:port",
      # "ip:port"
    ]

    trust.node = [
      # Passive accept connection in any case
      # Sample entries:
      # "ip:port",
      # "ip:port"
    ]

    seed.node = {
      # List of the seed nodes
      # Seed nodes are stable full nodes
      # example:
      # ip.list = [
      #   "ip:port",
      #   "ip:port"
      # ]
      ip.list = [
    "47.254.144.25:18888",
    "47.254.146.147:18888",
    "47.254.16.55:18888",
    "47.254.18.49:18888",
    "52.14.86.232:18888"
      ]
    }

    genesis.block = {
      # Reserve balance
      assets = [
        {
          accountName = "Zion"
          accountType = "AssetIssue"
          address = "TNNqZuYhMfQvooC4kJwTsMJEQVU3vWGa5u"
          balance = "95000000000000000"
        },
        {
          accountName = "Sun"
          accountType = "AssetIssue"
          address = "TWsm8HtU2A5eEzoT8ev8yaoFjHsXLLrckb"
          balance = "5000000000000000"
        },
        {
          accountName = "Blackhole"
          accountType = "AssetIssue"
          address = "TSJD5rdu6wZXP7F2m3a3tn8Co3JcMjtBip"
          balance = "-9223372036854775808"
        }
      ]

      witnesses = [
        {
          address: TVdyt1s88BdiCjKt6K2YuoSmpWScZYK1QF,
          url = "http://Alioth.com",
          voteCount = 100027
        },
        {
          address: TCNVmGtkfknHpKSZXepZDXRowHF7kosxcv,
          url = "http://Aries.com",
          voteCount = 100026
        },
        {
          address: TAbzgkG8p3yF5aywKVgq9AaAu6hvF2JrVC,
          url = "http://Cancer.com",
          voteCount = 100025
        },
        {
          address: TMmmvwvkBPBv3Gkw9cGKbZ8PLznYkTu3ep,
          url = "http://Capricorn.com",
          voteCount = 100024
        },
        {
          address: TBJHZu4Sm86aWHtt6VF6KQSzot8vKTuTKx,
          url = "http://Cassiopeia.com",
          voteCount = 100023
        },
        {
          address: TLvCstA93piBhpdvMggJ9r5b793b6rqdGd,
          url = "http://Crux.com",
          voteCount = 100022
        },
        {
          address: TEf2ADumcubtg9NeNi7bNP14KfvYxKzTDu,
          url = "http://Delphinus.com",
          voteCount = 100021
        },
        {
          address: TTqqbNxnqniyeCFi4aYwQQFHtuMwiBLARo,
          url = "http://Dorado.com",
          voteCount = 100020
        },
        {
          address: TWwJwoqAYvUVjmp5odhwZYgKekBqL3Mbcf,
          url = "http://Dubhe.com",
          voteCount = 100019
        },
        {
          address: TCPKsDZCJDzC83KWcAnHo9b46DN9o4s48y,
          url = "http://Eridanus.com",
          voteCount = 100018
        },
        {
          address: TJnd8wF5ScEvuYq4WnJUyGbg6iS7ibnWrY,
          url = "http://Gemini.com",
          voteCount = 100017
        },
        {
          address: TTZDB64rNpdw8rpEKko5FhB7BMUf5y4JMT,
          url = "http://Hercules.com",
          voteCount = 100016
        },
        {
          address: TVWapNccbdFDqdHjFGnJ8ePancR6HjSned,
          url = "http://Leo.com",
          voteCount = 100015
        },
        {
          address: TUVdiR6bYsuDNB5HWPLyK3ueY6225n5AdJ,
          url = "http://Libra.com",
          voteCount = 100014
        },
        {
          address: TRBQFNJrJJzzgqfnbP9WvAjWd2oCNyqanC,
          url = "http://Lupus.com",
          voteCount = 100013
        },
        {
          address: TBSq7zAhyEyVf96tbQmh6SwBGRiQXJf9sx,
          url = "http://Lyra.com",
          voteCount = 100012
        },
        {
          address: TFZhwKPxqadgLGSwkiD1JeFJgfSMn2BD75,
          url = "http://Monoceros.com",
          voteCount = 100011
        },
        {
          address: TZ6PqKSodEW7yQNYSDS8WoDo8t3SfACV3V,
          url = "http://Norma.com",
          voteCount = 100010
        },
        {
          address: TSiyqwmcqsDBXQmWPZhC4Y5zncECMN61Li,
          url = "http://Orion.com",
          voteCount = 100009
        },
        {
          address: TVnWr8bm3b2gDrJDBTfWXuPXiT1cvZUGan,
          url = "http://Pavo.com",
          voteCount = 100008
        },
        {
          address: TNR2BDkX53rFCvkSg89nK7nfeC6hLN7B5o,
          url = "http://Perseus.com",
          voteCount = 100007
        },
        {
          address: TVw2k1pD3n4ErWnr4uWmjVwsdai8vT5wyn,
          url = "http://Phecda.com",
          voteCount = 100006
        },
        {
          address: THtcGdFXoGWNd9PDrhCradfvcdsQAoNVAC,
          url = "http://Phoenix.com",
          voteCount = 100005
        },
        {
          address: TEZ31xxrECtLmsGvQFnh2quQVxKFoHxqqu,
          url = "http://Pyxis.com",
          voteCount = 100004
        },
        {
          address: TA6ztifHZSkQ5F6KMe73rYRgQ5fBKLPomV,
          url = "http://Scutum.com",
          voteCount = 100003
        },
        {
          address: TXuLKjf8J8aCKgDgA5uczwn1yQNYVPLocY,
          url = "http://Taurus.com",
          voteCount = 100002
        },
        {
          address: TAihbgDWBK1QTS5gsk7evWDy2nhpkmkGZJ,
          url = "http://Volans.com",
          voteCount = 100001
        }
      ]

      timestamp = "0" #2017-8-26 12:00:00

      parentHash = "0x9e524e0d6bfbbd25a9bd9cf5c5389f122e2bc2e66a29569d532739a1aa4376ae"
    }

    localwitness = [
    ]

    #localwitnesskeystore = [
    #  "src/main/resources/localwitnesskeystore.json"
    #]

    block = {
      needSyncCheck = true # first node : false, other : true
      maintenanceTimeInterval = 21600000 // 1 day: 86400000(ms), 6 hours: 21600000(ms)
    }

TRON network versions
~~~~~~~~~~~~~~~~~~~~~

For downloading assets of each version, please follow the link below:

https://github.com/tronprotocol/java-tron/releases

**Odyssey-v2.0.5**

* Feature

1. Add active node and passive node.

2. Leave a message.

**Odyssey-v2.0.4.1**

* Feature

1. Leave message.

**Odyssey-v2.0.4**

**Odyssey-v2.0.3**

* Feature

1. Testnet `Configuration File < https://github.com/tronprotocol/Documentation/blob/master/English_Documentation/TRON_Protocol/Test_Net_of_TRON.md>`_.

**Odyssey-v2.0.2**

* Feature

1. Add backup feature.

**Odyssey-v2.0.1**

* Feature

* Storage

1. Redesign the block storage structure, reduce the disk io to 50% of test net.

2. Add the unconfirmed block rolling back logic.

3. Implement the feature to safe close the node.

* Network

1. Improve the data sync logic, reduce the sync time to 1/3 of test net.

2. Improve the node discover logic.

3. Implement the ddos defend module.

* Architecture

1. Fix the problem of disconnection due to BAD_TX due to certain transaction orders.

2. Fixes the problem that some transactions will be broadcast by nodes when an exception occurs.

3. Fixed the problem that the signed parallel verification counter in the block could not be zeroed.

4. Fix the deadlock problem caused by the log system.

5. Updated seed nodes.

* Mechanism

New Bandwidth Model

1. If the transaction is a token transfer, TRON will try to charge bandwidth points from the token issuer if sufficient.

2. Bandwidth points will be charged from the initiator if sufficient.

3. Complimentary bandwidth points will be charged from the initiator if sufficient.

4. TRX will be charged from and the transaction initiator and burnt.

5. For more information, please view the document.

* Account Creation

In order to create a wallet using this private key, you will need to invoke one of the following three APIs:

1. Directly invoke account creation API.

2. Transfer TRX to the address.

3. Transfer tokens to the address.

* Rewards

1. Candidate reward: 127 candidates updated once every 6 hours will share 115,200 TRX. The reward will be split in accordance to the votes each candidate receives. Each year, candidate reward will total 168,192,000 TRX.

2. Super Representative reward: The TRON Protocol network will generate one block every 3 seconds, with each block awarding 32 TRX to super representatives. A total of 336,384,000 TRX will be awarded annually to twenty-seven super representatives.

* Bug Bounty Program

1. On June 1, TRON Foundation launched Tron Bug Bounty Program with a highest reward of USD$10 million. It is aimed at discovering potential technical vulnerabilities in the mainnet with the help of TRON’s community members, especially those who specialize in global network security, to sustain TRON mainnet as the most secure public blockchain in the industry and to provide secure and stable infrastructure and services to DApps deployed on the mainnet.

2. For more details, please visit https://tron.network/findBug?lng=en

* Community Support

1. We encourage our community to run Tron Odyssey-v2.0.1. If you have some problems on running Tron mainnet, please join our Slacks to get help. You are welcome to ask questions here, we also encourage your answers for other developer’s questions.

* Future Release

1. 6.25 will be Tron Independence Day, at that day we will transfer TRX erc20 token into TRX mainnet token. On 6.26, Tron will hold the first Super Representative election for producing blocks. On 7.31, official Tron Virtual Machine will be released.

* Credits

1. Credits for winners of Tron Program Contest. Rovak, Marius Gill, zx63, TeamGaryTron, Flott, jr, John Savadkuhi, jake Lin are winners of Tron Program Contest for their works of Block Explorer, Android/IOS wallet, Mac wallet, Windows Wallet and Chrome extension wallet.

**Odyssey-v2.0**

* Feature

* Storage

* Network

1. Optimizes handshake logic.

2. Optimizes sending ping message.

3. Optimizes message entities and net log.

4. Solving the problem of disconnection.

5. Solving thread sharing problem: send msg thread & handle msg thread.

6. Solving sync problem chain block inventory msg handle problem.

7. Solving the problem of repeated transaction in network module.

* Architecture

* Mechanism

* New Bandwidth Model

1. If the transaction is a token transfer, TRON will try to charge bandwidth points from the token issuer if sufficient.

2. Bandwidth points will be charged from the initiator if sufficient.

3. Complimentary bandwidth points will be charged from the initiator if sufficient.

4. TRX will be charged from and the transaction initiator and burnt.

For more information, please view the document.

* Account Creation

In order to create a wallet using this private key, you will need to invoke one of the following three APIs:

1. directly invoke account creation API
2. transfer TRX to the address
3. transfer tokens to the address

* Rewards

1.Candidate reward: 127 candidates updated once every 6 hours will share 115,200 TRX. The reward will be split in accordance to the votes each candidate receives. Each year, candidate reward will total 168,192,000 TRX.

2. Super Representative reward: The TRON Protocol network will generate one block every 3 seconds, with each block awarding 32 TRX to super representatives. A total of 336,384,000 TRX will be awarded annually to twenty-seven super representatives.

* Bug Bounty Program

1. On June 1, TRON Foundation launched Tron Bug Bounty Program with a highest reward of USD$10 million. It is aimed at discovering potential technical vulnerabilities in the mainnet with the help of TRON’s community members, especially those who specialize in global network security, to sustain TRON mainnet as the most secure public blockchain in the industry and to provide secure and stable infrastructure and services to DApps deployed on the mainnet.

2. For more details, please visit https://tron.network/findBug?lng=en

* Community Support

1. We encourage our community to run Tron Odyssey-v2.0. If you have some problems on running Tron mainnet, please join our Slacks to get help. You are welcome to ask questions here, we also encourage your answers for other developer’s questions.

* Future Release

1. 6.25 will be Tron Independence Day, at that day we will transfer TRX erc20 token into TRX mainnet token. On 6.26, Tron will hold the first Super Representative election for producing blocks. On 7.31, official Tron Virtual Machine will be released.

* Credits

1. Credits for winners of Tron Program Contest. Rovak, Marius Gill, zx63, TeamGaryTron, Flott, jr, John Savadkuhi, jake Lin are winners of Tron Program Contest for their works of Block Explorer, Android/IOS wallet, Mac wallet, Windows Wallet and Chrome extension wallet.

**Odyssey-v1.1.2**

**Odyssey-v1.1.1**

* Feature

1. New bandwidth model

* Improvement

1. More stable sync module.

2. Improve the database performance.

**Odyssey-v1.1**

* Feature

1. Remove the TRONSR minimum balance limit.

2. Token transaction consumes bandwidth of the token issuer.

3. Avoid flood attack

4. Add token frozen

5. When an account issues an asset, it can promise the public to freeze multiple assets. The asset can be unfrozen manually after maturity

* Improvement

1. Remove duplicate verification

2. Improve the message package speed

3. Avoid the dup validate

* Bug Fix

1. Fix the now timestamp bug.

2. Fix the dup trans

3. Fix the dead lock during sync.

**Odyssey with VM**

* Feature

1. Fully support EVM.

2. Implement the vm-adapter.

* Notics

1. This is a test version.

**Odyssey-v1.0.6.3**

* Bug Fix

1. Fix the bandwidth timestamp error.

* Improvement

1. Batch transaction send & receive.

**Odyssey-v1.0.6**

* Feature

1.  Frozen and unfrozen balance for voting and bandwidth.

2.  Transaction bandwidth control to avoid ddos.

3.  Add testNG.

* Improvement

1. Parallel validate signature.

2. Increate the speed of block producing.

3. Reduce the memory usage of index service.

4. Increase the speed of broadcast  block.

5. Improve the  handshake mechanism.

* Bug Fix

1. Out of memory exception.

2. Dup message

**Odyssey-v1.0.5**

* Improvement

1. Add database index module for block explorer

2. Redesign the block id, merge block num in big endian

3. Improve the performance of database.

4. Add tapos support.

* Feature

1. Fix cache transaction exception.

2. Fix dup message .

3. Fix witness disorder exception.

* Other

1. Support the grpc_web_proxy.

**Odyssey-v1.0.4**

* Feature

1. Incorrect disconnection during sync block.

2. A minor error when process fork chain.

3. The inconsistent of witness.

4, Other small bugs.

* Improvement

1. Add more exception.

2. Remove the head in manager.

3. Other improve.

* Other:

1. p2p version -> 51 for testnet

**Odyssey-v1.0.3**

* Feature

1. Transaction executed twice in some condition.

2. Test case break down cause the memory not release.

3. Test other bugs.

* Improvement

1. Performance improvement.

**Odyssey-v1.0.2 for testnet**

* Improvement

1. The block chain

2. Tdp support.

3. Web wallet && explorer support.

**Odyssey-v1.0.1 for testnet**

* Improvement

1. More stable version.

**Odyssey-v1.0 for testnet**

**Exodus-v1.0**

* Features

1.Blockchain basic prototype

2. The multi-node test of the Kafka-based network

* Commands

1. help: Help tips

2. account: Get address

3. getbalance: Get balance

4. send: Send balance to address

5. printblockchain: Print blockchain

6. exit: Exit

Operation of Node
-----------------

Recommended hardware specifications
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: shell

    Minimum specifications for FullNode deployment
    CPU：16-core
    RAM：16G
    Bandwidth：100M
    DISK：10T
    Recommended specifications for FullNode deployment
    CPU：64-core or more
    RAM：64G or more
    Bandwidth：500M and more
    DISK：20T or more

    Minimum specifications for SolidityNode deployment
    CPU：16-core
    RAM：16G
    Bandwidth：100M
    DISK：10T
    Recommended specifications for SolidityNode deployment
    CPU：64-core or more
    RAM：64G or more
    Bandwidth：500M and more
    DISK：20T or more

    DISK capacity depends on the actual transaction volume after deployment, but it’s always better to leave some excess capacity.

Official Public Node
~~~~~~~~~~~~~~~~~~~~

GRPC port: 50051 P2P network port: 18888

**FullNode**

    54.236.37.243

    52.53.189.99

    18.196.99.16

    34.253.187.192

    52.56.56.149

    35.180.51.163

    54.252.224.209

    18.228.15.36

    52.15.93.92

    34.220.77.106

    13.127.47.162

    13.124.62.58

    13.229.128.108

    35.182.37.246

    34.200.228.125

    18.220.232.201

    13.57.30.186

    35.165.103.105

    18.184.238.21

    34.250.140.143

    35.176.192.130

    52.47.197.188

    52.62.210.100

    13.231.4.243

    18.231.76.29

    35.154.90.144

    13.125.210.234

    13.250.40.82

    35.183.101.48

**SolidityNode**

GRPC port: 50051

.. code-block:: shell

    39.105.66.80
    47.254.39.153
    47.89.244.227
    39.105.118.15
    47.75.108.229
    34.234.164.105
    18.221.34.0
    35.178.11.0
    35.180.18.107
    52.63.152.13
    18.231.123.107

How to build
~~~~~~~~~~~~

**1, Getting the code**

Clone/Download the JAVA-TRON Implementation from Github

* Visit the JAVA-TRON github respository

here: https://github.com/tronprotocol/java-tron

* Getting the source code. We use git and Github to maintain the source code. Clone the repository by:

.. code-block:: shell

    git clone https://github.com/tronprotocol/java-tron.git

* To use Git on the command line, you'll need to download, install, and configure Git on your computer. Please check `set up git <https://help.github.com/articles/set-up-git/>`_ and `fork a repo <https://help.github.com/articles/fork-a-repo/>`_.

* If you aren't familiar with using git, you can simply download `the project as a zip <https://github.com/tronprotocol/java-tron/archive/develop.zip>`_ and unpack it somewhere.

* For Mac, you can also install `Github for Mac <https://desktop.github.com/>`_ then `fork and clone our repository <https://guides.github.com/activities/forking/>`_.

**2, Installing dependencies**

* JDK 1.8 is required to be installed in the system.

* `Oracle JDK 8 <https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04>`_ (not Open JDK 8) is required to be installed in Linux Ubuntu system (e.g. Ubuntu 16.04.4 LTS).

**3, Download and Install IntelliJ IDEA**

* Install IDEA and launch the program once the process completes.

* Click through the prompts until you get to the "Welcome to IntelliJ IDEA" screen.

**4, Build in the Terminal**

.. code-block:: shell

    > cd java-tron

    > ./gradlew build

**5, Build an executable JAE**

.. code-block:: shell

    ./gradlew clean shadowJar

**6, Build in IntelliJ IDEA (community version is enough)**

* Start IntelliJ. Select ``File`` -> ``Open`` , then locate to the java-tron folder which you have git cloned to your local drive. Then click ``Open`` button on the right bottom.

* Check on ``Use auto-import`` on the ``Import Project from Gradle`` dialog. Select JDK 1.8 in the ``Gradle JVM`` option. Then click ``OK``.

* IntelliJ will open the project and start gradle syncing, which will take several minutes, depending on your network connection and your IntelliJ configuration

* After the syncing finished, select ``Gradle``  -> ``Tasks`` -> ``build`` , and then double click ``build`` option.

Deployment of SolidityNode and FullNode on the same host
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Create separate directories for FullNode and SolidityNode.**

.. code-block:: shell

    /deploy/fullnode
    /deploy/soliditynode

**Create two folders for FullNode and SolidityNode.**

Clone our latest master branch of https://github.com/tronprotocol/java-tron and extract it to

.. code-block:: shell

    /deploy/java-tron

**Make sure you have the proper dependencies.**

* JDK 1.8 (JDK 1.9+ is not supported yet)
* On Linux Ubuntu system (e.g. Ubuntu 16.04.4 LTS), ensure that the machine has `Oracle JDK 8 < https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04>`_, instead of having ``Open JDK 8`` in the system. If you are building the source code by using ``Open JDK 8``, you will get `Build Failed < https://github.com/tronprotocol/java-tron/issues/337>`_ result.

**Deployment guide**

1. Build the java-tron project

.. code-block:: shell

    cd /deploy/java-tron
    ./gradlew build

2. Copy the FullNode.jar and SolidityNode.jar along with config files into the respective directories.

.. code-block:: shell

    download your needed config file from https://github.com/tronprotocol/TronDeployment.
    main_net_config.conf is the config for mainnet, and test_net_config.conf is the config for testnet.
    please rename the config file to `config.conf` and use this config.conf to start fullnode and soliditynode.

    cp build/libs/FullNode.jar ../fullnode
    cp build/libs/SolidityNode.jar ../soliditynode

3. You can now run your Fullnode using the following command：

.. code-block:: shell

    java -jar FullNode.jar -c config.conf // make sure that your config.conf is downloaded from https://github.com/tronprotocol/TronDeployment

4. Configure the SolidityNode configuration file. You'll need to edit `config.conf` to connect to your local `FullNode`. Change  `trustNode` in `node` to local `127.0.0.1:50051`, which is the default rpc port. Set `listen.port` to any number within the range of 1024-65535. Please don't use any ports between 0-1024 since you'll most likely hit conflicts with other system services. Also change `rpc port` to `50052` or something to avoid conflicts.

.. code-block:: shell

    node {
        trustNode = "127.0.0.1:50051"
        listen.port = 18889 // This needs to be changed.
    }
    rpc {
      port = 50052
    }

5. You can now run your SolidityNode using the following command：

.. code-block:: shell

    java -jar SolidityNode.jar -c config.conf //make sure that your config.conf is downloaded from https://github.com/tronprotocol/TronDeployment


**Logging and network connection verification**

Logs for both nodes are located in ``/deploy/\*/logs/tron.log``. Use ``tail -f /logs/tron.log/`` to follow along with the block syncing.

You should see something similar to this in your logs for block synchronization:

**FullNode**

.. code-block:: shell

    12:00:57.658 INFO  [pool-7-thread-1] [o.t.c.n.n.NodeImpl](NodeImpl.java:830) Success handle block Num:236610,ID:0000000000039c427569efa27cc2493c1fff243cc1515aa6665c617c45d2e1bf

**SolidityNode**

.. code-block:: shell

    12:00:40.691 INFO  [pool-17-thread-1] [o.t.p.SolidityNode](SolidityNode.java:88) sync solidity block, lastSolidityBlockNum:209671, remoteLastSolidityBlockNum:211823

**Stop node gracefully**

Create file stop.sh，use kill -15 to close java-tron.jar（or FullNode.jar、SolidityNode.jar）.

You need to modify pid=``ps -ef |grep java-tron.jar |grep -v grep |awk '{print $2}'`` to find the correct pid.

.. code-block:: shell

    #!/bin/bash
    count=1
    while [ $count -le 60 ]; do
      pid=`ps -ef |grep java-tron.jar |grep -v grep |awk '{print $2}'`
      if [ -n "$pid" ]; then
        kill -15 $pid
        echo "kill -15 java-tron, counter $count"
        sleep 1
      else
        echo "java-tron killed"
        break
      fi
      count=$[$count+1]
      if [ $count -ge 60 ]; then
        kill -9 $pid
      fi
    done

Script to deploy FullNode and SolidityNode
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Download and run script**

.. code-block:: shell

    wget https://raw.githubusercontent.com/tronprotocol/TronDeployment/master/deploy_tron.sh -O deploy_tron.sh

**Parameter Illustration**

.. code-block:: shell

    bash start_tron.sh --app [FullNode|SolidityNode] --net [mainnet|testnet] --db [keep|remove|backup]

    --app	Running application. The default node is Fullnode and it could be FullNode or SolidityNode.
    --net	Connecting network. The default network is mainnet and it could be mainnet or testnet.
    --db	The way of data processing could be keep, remove and backup. If you launch two different networks, like from mainnet to testnet or from testnet to mainnet, you need to delete database.
    --trust-node	It only works when deploying SolidityNode. The specified gRPC service of Fullnode, like 127.0.0.1:50051 or 13.125.249.129:50051.
    --rpc-port	Port of grp. If you deploy SolidityNode and FullNode on the same host，you need to configure different ports.
    --commit	Optional， commitid of project.
    --branch	Optional，branch of project.

**Examples**

Deployment of FullNode on the one host.

.. code-block:: shell

    wget https://raw.githubusercontent.com/tronprotocol/TronDeployment/master/deploy_tron.sh -O deploy_tron.sh
    bash deploy_tron.sh --app FullNode --net mainnet

Deployment of SolidityNode on the one host.

.. code-block::

    wget https://raw.githubusercontent.com/tronprotocol/TronDeployment/master/deploy_tron.sh -O deploy_tron.sh
    #User can self-configure the IP and Port of GRPC service in the turst-node field of SolidityNode.
    bash deploy_tron.sh --app SolidityNode --net mainnet --trust-node <grpc-ip:grpc-port>


Deployment of FullNode and SolidityNode on the same host.

.. code-block:: shell
    wget https://raw.githubusercontent.com/tronprotocol/TronDeployment/master/deploy_tron.sh -O deploy_tron.sh
    bash deploy_tron.sh --app FullNode --net mainnet
    # You need to configure different gRPC ports on the same host because gRPC port is available on SolidityNode and FullNodeConfigure and it cannot be set as default value 50051. In this case the default value of rpc port is set as 50041.
    sh deploy_tron.sh --app SolidityNode --net mainnet --trust-node 127.0.0.1:50051 --rpc-port 50041

**Deployment of grpc gateway**

Summary

This script helps you download the code from https://github.com/tronprotocol/grpc-gateway and deploy the code on your environment.

Pre-requests

Please follow the guide on https://github.com/tronprotocol/grpc-gateway

Install Golang, Protoc, and set $GOPATH environment variable according to your requirement.

Download and run script

.. code-block:: shell

    wget https://raw.githubusercontent.com/tronprotocol/TronDeployment/master/deploy_grpc_gateway.sh -O deploy_grpc_gateway.sh

Parameter Illustration

.. code-block:: shell

    bash deploy_grpc_gateway.sh --rpchost [rpc host ip] --rpcport [rpc port number] --httpport [http port number]

    --rpchost The FullNode or SolidityNode IP where the grpc service is provided. Default value is "localhost".
    --rpcport The Fullnode or SolidityNode port number grpc service is consuming. Default value is 50051.
    --httpport The port intends to provide http service provided by grpc gateway. Default value is 18890.

Example

Use default configuration：

.. code-block:: shell

    bash deploy_grpc_gateway.sh

Use customized configuration：

.. code-block:: shell

    bash deploy_grpc_gateway.sh --rpchost 127.0.0.1 --rpcport 50052 --httpport 18891

Demand-based development
~~~~~~~~~~~~~~~~~~~~~~~~

Depending on the needs of your system, build a GRPC implementation to connect to the full node and solidity nodes. A guide to Tron’s APIs can be found at https://github.com/tronprotocol/Documentation/blob/master/TRX/Tron-overview.md#4-tron-api.

A starter guide to GRPC is available here: https://grpc.io/

We also have a fork of https://github.com/tronprotocol/grpc-gateway which provides a HTTP interface to GRPC. We do not recommend using this for exchanges.

Testing
~~~~~~~

We highly recommend that exchanges run a test to TRON’s mainnet as soon as possible.

For any other information, please refer to: https://github.com/tronprotocol/Documentation/blob/master/TRX/Tron-overview.md

TRON API
--------

Currently TRON only supports gRPC interfaces and not http interfaces. The grpc-gateway is for the use of debugging only and we strongly suggest that developers do not use it for development.

Definition of API
~~~~~~~~~~~~~~~~~

For the definition of API, see also: https://github.com/tronprotocol/protocol/blob/master/api/api.proto

Explanation of APIs
~~~~~~~~~~~~~~~~~~~

For the full introduction of API, please refer https://github.com/tronprotocol/Documentation/blob/master/English_Documentation/TRON_Protocol/TRON_Wallet_RPC-API.md

APIs under wallet service are provided by the FullNode. APIs under walletSolidity and walletExtension services are provided by the SolidityNode. APIs under the walletExtension service, whose processing time is long, are provided by the SolidityNode. The FullNode provides APIs for operations on the blockchain and for data inquiry, while the SolidityNode only provides APIs for the latter. The difference between these two nodes is that data of the FullNode could be revoked due to forking, whereas the solidified data of the solidity one is irrevocable.

.. code-block:: shell

    wallet/GetAccount
    Function:Returns account information.

    wallet/CreateTransaction
    Function: Creates a transaction of transfer. If the recipient address does not exist, a corresponding account will be created on the blockchain.

    wallet/ BroadcastTransaction
    Function: Broadcasts transaction. Transaction has to be signed before being broadcasted.

    wallet/ UpdateAccount
    Function: Updates account name. Account name can only be updated once for each account.

    wallet/ VoteWitnessAccount
    Function:Users can vote for witnesses.

    wallet/ CreateAssetIssue
    Function: Creates token. Users can issue their own token on Tron’s public blockchain, which can be used for reciprocal transfers and be bought with TRX. Users can chose to freeze a certain portion of the token supply during token issuance.

    wallet/ UpdateWitness
    Function: Updates witness information.

    wallet/ CreateAccount
    Function: Created account. Existent accounts can revoke this API to create a new account with an address.

    wallet/ CreateWitness
    Function: Users can apply to become Super Representatives, which costs 9,999 TRX.

    wallet/ TransferAsset
    Function: Token transfer.

    wallet/ ParticipateAssetIssue
    Function: Token participation. Users can participate in token offerings with their TRX.

    wallet/ FreezeBalance
    Function: Freeze TRX. Freezing TRX gives users bandwidth points and Tron Power, which are used for transactions and voting for witnesses respectively.

    wallet/ UnfreezeBalance
    Function: Unfreezes TRX. Frozen TRX can only be unfrozen 3 days afterwards. Unfreezing TRX also takes away corresponding bandwidth points, Tron power and the votes.

    wallet/ UnfreezeAsset
    Function: Unfreezes tokens.

    wallet/ WithdrawBalance
    Function: SRs and SR candidates can withdraw block reward and witness reward for the top 127 candidates to their account balance. One withdrawal can be made by each account every 24 hours.

    wallet/ UpdateAsset
    Function: Updates information of an issued token.

    wallet/ ListNodes
    Function: Returns a list of all nodes.

    wallet/ GetAssetIssueByAccount
    Function: Get information on a token by account.

    wallet/ GetAccountNet
    Function: Get bandwidth information on an account, including complimentary bandwidth points and bandwidth points obtained from balance freeze.

    wallet/ GetAssetIssueByName
    Function: Inquire token by token name.

    wallet/ GetNowBlock
    Function: Returns the latest block.

    wallet/ GetBlockByNum
    Function: Inquire block by block height.

    wallet/ GetBlockById
    Function: Inquire block by block ID. The ID of a block is the hash of the blockheader’s Raw data.

    wallet/ GetBlockByLimitNext index
    Function: Returns blocks indexed between the startNum and the endNum (including both ends).

    wallet/ GetBlockByLatestNum
    Function: Get the latest N blocks. N is defined in the parameter.

    wallet/ GetTransactionById
    Function: Get transaction by ID, which is the hash of the Raw data of the transaction.

    wallet/ ListWitnesses
    Function: Get a list of all witnesses.

    wallet/ GetAssetIssueList
    Function: Get a list of all issued tokens.

    wallet/ TotalTransaction
    Function: Get the total amount of transactions on the blockchain.

    wallet/ GetNextMaintenanceTime
    Function: Get the next maintenance time, namely the next update of witness votes count.

    WalletSolidity/ GetAccount
    Function:

    WalletSolidity/ ListWitnesses
    Function:

    WalletSolidity/ GetAssetIssueList
    Function:

    WalletSolidity/ GetNowBlock
    Function:

    WalletSolidity/ GetBlockByNum
    Function:

    WalletExtension/ GetTransactionsFromThis
    Function: Get the record of all outbound transactions from a certain account.

    WalletExtension/ GetTransactionsToThis
    Function: Get the record of all incoming transactions of a certain account.

HTTP RPC Interface
~~~~~~~~~~~~~~~~~~~

Available in the lastest build of java-tron master.

Please add to the configuration files for both nodes:

.. code-block:: shell

  node {
  ...
    http {
      fullNodePort = 8090
      solidityPort = 8091
    }

**SolidityNode Interface**

The default http port on solidityNode is 8091.

.. code-block:: shell

/walletsolidity/getaccount
Function：Query information about an account
demo: curl -X POST  http://127.0.0.1:8091/walletsolidity/getaccount -d '{"address": "41E552F6487585C2B58BC2C9BB4492BC1F17132CD0"}'
Parameters：address should be converted to a hex string
Return value：Account Object

/walletsolidity/listwitnesses
Function：Query the list of super representatives
demo: curl -X POST  http://127.0.0.1:8091/walletsolidity/listwitnesses
Parameters：None
Return value：List of all super representatives

/walletsolidity/getassetissuelist
Function：Query the list of Tokens
demo: curl -X POST  http://127.0.0.1:8091/walletsolidity/getassetissuelist
Parameters：None
Return value：List of all Tokens

/walletsolidity/getpaginatedassetissuelist
Function：Query the list of Tokens with pagination
demo: curl -X POST  http://127.0.0.1:8091/walletsolidity/getpaginatedassetissuelist -d '{"offset": 0, "limit":10}'
Parameters：Offset is the index of the starting Token, and limit is the number of Tokens expected to be returned.
Return value：List of Tokens

/walletsolidity/getnowblock
Function：Query the latest block
demo: curl -X POST  http://127.0.0.1:8091/walletsolidity/getnowblock
Parameters：None
Return value：Latest block on solidityNode

/walletsolidity/getblockbynum
Function：Query block by height
demo: curl -X POST  http://127.0.0.1:8091/walletsolidity/getblockbynum -d '{"num" : 100}'
Parameters：Num is the height of the block
Return value：specified Block object

/walletsolidity/gettransactionbyid
Function：Query transaction based on id
demo: curl -X POST  http://127.0.0.1:8091/walletsolidity/gettransactionbyid -d '{"value" : "309b6fa3d01353e46f57dd8a8f27611f98e392b50d035cef213f2c55225a8bd2"}'
Parameters：value is the transaction id，converted to a hex string
Return value：specified Transaction object

/walletsolidity/gettransactioninfobyid
Function：Query transaction fee based on id
demo: curl -X POST  http://127.0.0.1:8091/walletsolidity/gettransactioninfobyid -d '{"value" : "309b6fa3d01353e46f57dd8a8f27611f98e392b50d035cef213f2c55225a8bd2"}'
Parameters：value is the transaction id，converted to a hex string
Return value：Transaction fee，block height and block creation time

/walletextension/gettransactionsfromthis
Function：Query the list of transactions sent by an address
demo: curl -X POST  http://127.0.0.1:8091/walletextension/gettransactionsfromthis -d '{"account" : {"address" : "41E552F6487585C2B58BC2C9BB4492BC1F17132CD0"}, "offset": 0, "limit": 10}'
Parameters：Address is the account address, converted to a hex string; offset is the index of the starting transaction; limit is the number of transactions expected to be returned
Return value：Transactions list

/walletextension/gettransactionstothis
Function：Query the list of transactions received by an address
demo: curl -X POST  http://127.0.0.1:8091/walletextension/gettransactionstothis -d '{"account" : {"address" : "41E552F6487585C2B58BC2C9BB4492BC1F17132CD0"}, "offset": 0, "limit": 10}'
Parameters：Address is the account address, converted to a hex string; offset is the index of the starting transaction; limit is the number of transactions expected to be returned
Return value：Transactions list

**FullNode Interface**

.. code-block:: shell

The default http port on FullNode is 8090.

wallet/createtransaction
Function：Creates a transaction of transfer. If the recipient address does not exist, a corresponding account will be created on the blockchain.
demo: curl -X POST  http://127.0.0.1:8090/wallet/createtransaction -d '{"to_address": "41e9d79cc47518930bc322d9bf7cddd260a0260a8d", "owner_address": "41D1E7A6BC354106CB410E65FF8B181C600FF14292", "amount": 1000 }'
Parameters：To_address is the transfer transfer address, converted to a hex string; owner_address is the transfer transfer address, converted to  a hex string; amount is the transfer amount
Return value：Transaction contract data

/wallet/gettransactionsign
Function：Sign the transaction, the api has the risk of leaking the private key, please make sure to call the api in a secure environment
demo: curl -X POST  http://127.0.0.1:8090/wallet/gettransactionsign -d '{
"transation" : {"txID":"454f156bf1256587ff6ccdbc56e64ad0c51e4f8efea5490dcbc720ee606bc7b8","raw_data":{"contract":[{"parameter":{"value":{"amount":1000,"owner_address":"41e552f6487585c2b58bc2c9bb4492bc1f17132cd0","to_address":"41d1e7a6bc354106cb410e65ff8b181c600ff14292"},"type_url":"type.googleapis.com/protocol.TransferContract"},"type":"TransferContract"}],"ref_block_bytes":"267e","ref_block_hash":"9a447d222e8de9f2","expiration":1530893064000,"timestamp":1530893006233}}
"privateKey" : "your private key"}
}'
Parameters：Transaction is a contract created by http api, privateKey is the user private key
Return value：Signed Transaction contract data

wallet/broadcasttransaction
Function：Broadcast the signed transaction
demo：curl -X POST  http://127.0.0.1:8090/wallet/broadcasttransaction -d '{"signature":["97c825b41c77de2a8bd65b3df55cd4c0df59c307c0187e42321dcc1cc455ddba583dd9502e17cfec5945b34cad0511985a6165999092a6dec84c2bdd97e649fc01"],"txID":"454f156bf1256587ff6ccdbc56e64ad0c51e4f8efea5490dcbc720ee606bc7b8","raw_data":{"contract":[{"parameter":{"value":{"amount":1000,"owner_address":"41e552f6487585c2b58bc2c9bb4492bc1f17132cd0","to_address":"41d1e7a6bc354106cb410e65ff8b181c600ff14292"},"type_url":"type.googleapis.com/protocol.TransferContract"},"type":"TransferContract"}],"ref_block_bytes":"267e","ref_block_hash":"9a447d222e8de9f2","expiration":1530893064000,"timestamp":1530893006233}}'
Parameters：Signed Transaction contract data
Return value：broadcast success or faiilure

wallet/updateaccount
Function：Modify account name
demo：curl -X POST  http://127.0.0.1:8090/wallet/updateaccount -d '{"account_name": "0x7570646174654e616d6531353330383933343635353139" ,"owner_address":"41d1e7a6bc354106cb410e65ff8b181c600ff14292"}'
Parameters：account_name is the name of the account, converted into a hex string；owner_address is the account address of the name to be modified, converted to a hex string.
Return value：modification Transaction Object

wallet/votewitnessaccount
Function：Vote on the super representative
demo：curl -X POST  http://127.0.0.1:8090/wallet/votewitnessaccount -d '{
"owner_address":"41d1e7a6bc354106cb410e65ff8b181c600ff14292",
"votes": [{"vote_address": "41e552f6487585c2b58bc2c9bb4492bc1f17132cd0", "vote_count": 5}]
}'
Parameters：Owner_address is the voter address, converted to a hex string; votes.vote_address is the address of the super delegate being voted, converted to a hex string; vote_count is the number of votes

wallet/createassetissue
Function：Issue Token
demo：curl -X POST  http://127.0.0.1:8090/wallet/createassetissue -d '{
"owner_address":"",
"name":"{{assetIssueName}}",
"abbr": "{{abbrName}}",
"total_supply" :4321,
"trx_num":1,
"num":1,
"start_time" :{{startTime}},
"end_time":{{endTime}},
"vote_score":2,
"description":"007570646174654e616d6531353330363038383733343633",
"url":"007570646174654e616d6531353330363038383733343633",
"free_asset_net_limit":10000,
"public_free_asset_net_limit":10000,
"frozen_supply":{"frozen_amount":1, "frozen_days":2}
}'


wallet/createaccount
Function：Create an account. Uses an already activated account to create a new account
demo：curl -X POST  http://127.0.0.1:8090/wallet/createaccount -d '{"owner_address":"41d1e7a6bc354106cb410e65ff8b181c600ff14292", "account_address": "41e552f6487585c2b58bc2c9bb4492bc1f17132cd0"}'
Parameters：Owner_address is an activated account，converted to a hex String; account_address is the address of the new account, converted to a hex string, this address needs to be calculated in advance
Return value：Create account Transaction raw data

wallet/createwitness
Function：Apply to become a super representative
demo：curl -X POST  http://127.0.0.1:8090/wallet/createwitness -d '{"owner_address":"41d1e7a6bc354106cb410e65ff8b181c600ff14292", "url": "007570646174654e616d6531353330363038383733343633"}'
Parameters：owner_address is the account address of the applicant，converted to a hex string；url is the official website address，converted to a hex string
Return value：Super Representative application Transaction raw data

wallet/transferasset
Function：Transfer Token
demo：curl -X POST  http://127.0.0.1:8090/wallet/transferasset -d '{"owner_address":"41d1e7a6bc354106cb410e65ff8b181c600ff14292", "to_address": "41e552f6487585c2b58bc2c9bb4492bc1f17132cd0", "asset_name": "0x6173736574497373756531353330383934333132313538", "amount": 100}'
Parameters：Owner_address is the address of the withdrawal account, converted to a hex string；To_address is the recipient address，converted to a hex string；asset_name is the token contract address，converted to a hex string；Amount is the amount of token to transfer
Return value：Token transfer Transaction raw data

wallet/easytransfer
Function: Easily transfer from an address using the password string. Only works with accounts created from createAddress
Demo: curl -X POST http://127.0.0.1:8090/wallet/easytransfer -d '{"passPhrase": "7465737470617373776f7264","toAddress": "41D1E7A6BC354106CB410E65FF8B181C600FF14292", "amount":10}'
Parameters: passPhrase is the password, converted from ascii to hex. toAddress is the recipient address, converted into a hex string; amount is the amount of TRX to transfer in SUN.
Warning: Please control risks when using this API. To ensure environmental security, please do not invoke APIs provided by other or invoke this very API on a public network.

wallet/easytransferbyprivate
Function：Easily transfer from an address using the private key.
demo: curl -X POST  http://127.0.0.1:8090/wallet/easytransferbyprivate -d '{"privateKey": "D95611A9AF2A2A45359106222ED1AFED48853D9A44DEFF8DC7913F5CBA727366", "toAddress":"4112E621D5577311998708F4D7B9F71F86DAE138B5","amount":10000}'
Parameters：passPhrase is the private key in hex string format. toAddress is the recipient address, converted into a hex string; amount is the amount of TRX to transfer in SUN.
Return value： transaction, including execution results.
Warning: Please control risks when using this API. To ensure environmental security, please do not invoke APIs provided by other or invoke this very API on a public network.

wallet/createaddress
Function: Create address from a specified password string (NOT PRIVATE KEY)
Demo: curl -X POST http://127.0.0.1:8090/wallet/createaddress -d '{"value": "7465737470617373776f7264" }'
Parameters: value is the password, converted from ascii to hex
Return value：value is the corresponding address for the password, encoded in hex. Convert it to base58 to use as the address.
Warning: Please control risks when using this API. To ensure environmental security, please do not invoke APIs provided by other or invoke this very API on a public network.

wallet/generateaddress
Function: Generates a random private key and address pair
demo：curl -X POST -k http://127.0.0.1:8090/wallet/generateaddress
Parameters: no parameters.
Return value：value is the corresponding address for the password, encoded in hex. Convert it to base58 to use as the address.
Warning: Please control risks when using this API. To ensure environmental security, please do not invoke APIs provided by other or invoke this very API on a public network.


wallet/participateassetissue
Function：Create a new Token
demo：curl -X POST http://127.0.0.1:8090/wallet/participateassetissue -d '{
"to_address": "41e552f6487585c2b58bc2c9bb4492bc1f17132cd0",
"owner_address":"41e472f387585c2b58bc2c9bb4492bc1f17342cd1",
"amount":100,
"asset_name":"3230313271756265696a696e67"
}'
Parameters：
to_address is the address of the Token issuer，converted to a hex string
owner_address is the address of the Token owner，converted to a hex string
amount is the number of tokens created
asset_name is the name of the token，converted to a hex string
Return value：Token creation Transaction raw data

wallet/freezebalance
Function：Freezes an amount of TRX. Will give bandwidth and TRON Power(voting rights) to the owner of the frozen tokens.
demo：curl -X POST http://127.0.0.1:8090/wallet/freezebalance -d '{
"owner_address":"41D1E7A6BC354106CB410E65FF8B181C600FF14294",
"frozen_balance": 10000,
"frozen_duration": 3
}'
Parameters：
owner_address is the address that is freezing trx account，converted to a hex string
frozen_balance is the number of frozen trx
frozen_duration is the duration in days to be frozem
Return value：Freeze trx transaction raw data

wallet/unfreezebalance
Function：Unfreeze TRX that has passed the minimum freeze duration. Unfreezing will remove bandwidth and TRON Power.
demo：curl -X POST http://127.0.0.1:8090/wallet/unfreezebalance -d '{
"owner_address":"41e472f387585c2b58bc2c9bb4492bc1f17342cd1",
}'
Parameters：
owner_address address to unfreeze TRX for，converted to a hex string
Return value：Unfreeze TRX transaction raw data

wallet/unfreezeasset
Function：Unfreeze a token that has passed the minimum freeze duration.
demo：curl -X POST http://127.0.0.1:8090/wallet/unfreezeasset -d '{
"owner_address":"41e472f387585c2b58bc2c9bb4492bc1f17342cd1",
}'
Parameters：
owner_address address to unfreeze Tokens for，converted to a hex string
Return value：Unfreeze Token transaction raw data

wallet/withdrawbalance
Function：Withdraw Super Representative rewards, useable every 24 hours.
demo：curl -X POST http://127.0.0.1:8090/wallet/withdrawbalance -d '{
"owner_address":"41e472f387585c2b58bc2c9bb4492bc1f17342cd1",
}'
Parameters：
owner_address is the address to withdraw from，converted to a hex string
Return value：Withdraw TRX transaction raw data

wallet/updateasset
Function：Update a Token's information
demo：curl -X POST http://127.0.0.1:8090/wallet/updateasset -d '{
"owner_address":"41e472f387585c2b58bc2c9bb4492bc1f17342cd1",
"description": ""，
"url": "",
"new_limit" : 1000000,
"new_public_limit" : 100
}'
Parameters：
Owner_address is the address of the token issuer, converted to a hex string
Description is a description of the token, converted to a hex string
Url is the official website address of the token issuer, converted to a hex string
New_limit is the free bandwidth that each token can use for each holder.
New_public_limit is the free bandwidth of the token
Return value: Token update transaction raw data


wallet/listnodes
Function：List the nodes which the api fullnode is connecting on the network
demo: curl -X POST  http://127.0.0.1:8090/wallet/listnodes
Parameters：None
Return value：List of nodes

wallet/getassetissuebyaccount
Function：List the tokens issued by an account.
demo: curl -X POST  http://127.0.0.1:8090/wallet/getassetissuebyaccount -d '{"address": "41F9395ED64A6E1D4ED37CD17C75A1D247223CAF2D"}'
Parameters：Token issuer account address，converted to a hex string
Return value：List of tokens issued by the account

wallet/getaccountnet
Function：Query bandwidth information.
demo: curl -X POST  http://127.0.0.1:8090/wallet/getaccountnet -d '{"address": "4112E621D5577311998708F4D7B9F71F86DAE138B5"}'
Parameters：Account address，converted to a hex string
Return value：Bandwidth information for the account. If a field doesn't appear, then the corresponding value is 0. {"freeNetUsed": 557,"freeNetLimit": 5000,"NetUsed": 353,"NetLimit": 5239157853,"TotalNetLimit": 43200000000,"TotalNetWeight": 41228}

wallet/getassetissuebyname
Function：Query token by name.
demo: curl -X POST  http://127.0.0.1:8090/wallet/getassetissuebyname -d '{"value": "44756354616E"}'
Parameters：The name of the token, converted to a hex string
Return value：token.

/wallet/getnowblock
Function：Query the latest block
demo: curl -X POST  http://127.0.0.1:8090/wallet/getnowblock
Parameters：None
Return value：Latest block on full node

/wallet/getblockbynum
Function：Query block by height
demo: curl -X POST  http://127.0.0.1:8090/wallet/getblockbynum -d '{"num" : 100}'
Parameters：Num is the height of the block
Return value：specified Block object

wallet/getblockbyid
Function：Query block by ID
demo: curl -X POST  http://127.0.0.1:8090/wallet/getblockbyid -d '{"value": "0000000000038809c59ee8409a3b6c051e369ef1096603c7ee723c16e2376c73"}'
Parameters：Block ID.
Return value：Block Object

wallet/getblockbylimitnext
Function：Query a range of blocks by block height
demo: curl -X POST  http://127.0.0.1:8090/wallet/getblockbylimitnext -d '{"startNum": 1, "endNum": 2}'
Parameters：
   startNum：Starting block height, including this block
   endNum：Ending block height, excluding that block
Return value：A list of Block Objects

wallet/getblockbylatestnum
Function：Query the latest blocks
demo: curl -X POST  http://127.0.0.1:8090/wallet/getblockbylatestnum -d '{"num": 5}'
Parameters：The number of blocks to query
Return value：A list of Block Objects

wallet/gettransactionbyid
Function：Query transaction by ID
demo: curl -X POST  http://127.0.0.1:8090/wallet/gettransactionbyid -d '{"value": "d5ec749ecc2a615399d8a6c864ea4c74ff9f523c2be0e341ac9be5d47d7c2d62"}'
Parameters：Transaction ID.
Return value：Transaction information.

wallet/listwitnesses
Function：Query the list of super representatives
demo: curl -X POST  http://127.0.0.1:8090/wallet/listwitnesses
Parameters：None
Return value：List of all super representatives

wallet/getassetissuelist
Function：Query the list of Tokens
demo: curl -X POST  http://127.0.0.1:8090/wallet/getassetissuelist
Parameters：None
Return value：List of all Tokens

wallet/getpaginatedassetissuelist
Function：Query the list of Tokens with pagination
demo: curl -X POST  http://127.0.0.1:8090/wallet/getpaginatedassetissuelist -d '{"offset": 0, "limit": 10}'
Parameters：Offset is the index of the starting Token, and limit is the number of Tokens expected to be returned.
Return value：List of Tokens

wallet/totaltransaction
Function：Count all transactions on the network
demo: curl -X POST  http://127.0.0.1:8090/wallet/totaltransaction
Parameters：None
Return value：Total number of transactions.

wallet/getnextmaintenancetime
Function：Get the time of the next Super Representative vote
demo: curl -X POST  http://127.0.0.1:8090/wallet/getnextmaintenancetime
Parameters：None
Return value: number of milliseconds until the next voting time.

wallet/validateaddress
Function：validate address
demo: curl -X POST  http://127.0.0.1:8090/wallet/validateaddress -d '{"address": "4189139CB1387AF85E3D24E212A008AC974967E561"}'
Parameters：The address, should be in base58checksum, hexString or base64 format.
Return value: ture or false

API code generation
~~~~~~~~~~~~~~~~~~~

APIs are based on the gRPC protocol, see https://grpc.io/docs/ for more information.

API demo
~~~~~~~~

Please refer to the following two classes for a GRPC example in Java.

.. code-block:: shell

    https://github.com/tronprotocol/wallet-cli/blob/master/src/main/java/org/tron/walletserver/WalletClient.java

    https://github.com/tronprotocol/wallet-cli/blob/master/src/main/java/org/tron/walletserver/GrpcClient.java

Mechanism
---------

Account creation
~~~~~~~~~~~~~~~~

You can generate an offline keypair, which includes an address and a private key, that will not be recorded by TRON.

In order to create a wallet using this private key, you will need to invoke one of the following three APIs:

+ directly invoke account creation API
+ transfer TRX to the address
+ transfer tokens to the address

Once the transaction is confirmed, you can find corresponding information of the account in TRON network.

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

Once the balance is frozen, the user will receive a proportionate amount of TRON Power(TP) and bandwidth. TRON Power(TP) represents voting power whereas bandwidth points are used to pay for transactions. Their usage and means of calculation will be introduced in following sections.

Frozen assets are held in your frozen account and cannot be used for trading.

More TP and bandwidth points can be obtained by freezing more balance. The balance can be unfrozen after 3 days from the latest freezing.

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
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Each time a Super Representative finishes block production, reward will be sent to the subaccount in the superledger. Super Representatives can check but not directly make use of this asset. A withdrawal can be made once every 24 hours, transferring the reward from the subaccount to the Super Representative’s account.

Super Representative Election
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Every account in TRON’s network is entitled to vote for the Super Representatives they support. Voting requires TP, which is determined by users’ current amount of frozen balance.

Calculation of TP: 1 TP for 1 frozen TRX.

Once you unfreeze your balance, an equivalent amount of TP is also lost, meaning that previous votes casted may no longer be valid. You can refreeze your balance to regain validity of votes.

.. Note:: TRON network only keeps record of the latest votes, meaning that every new allocation of votes you make will replace all previous records.

+ e.g.

.. code-block:: shell

    freezebalance password 10_000_000 3    // 10 TP for 10 frozen TRX
    votewitness password witness1 4 witness2 6    //4 votes for witness1 and 6 votes for witness2
    vote witness password witness1 3 witness2 7    // 3 votes for witness1 and 7 votes for witness2

The final result of the above commands is 3 votes for witness1 and 7 votes for witness2.

Bandwidth Points
~~~~~~~~~~~~~~~~

Having too many transactions will clog our network like Ethereum and may incur delays on transaction confirmation. To keep the network operating smoothly, TRON network only allows every account to initiate a limited number of transactions for free every once every 10 seconds. To engage in transactions more frequently requires bandwidth. Like TRON Power(TP), bandwidth can be obtained through freezing TRX.

1. Definition of bandwidth points

Transactions are transmitted and stored in the network in byte arrays. Bandwidth points consumed in a transaction equals the size of its byte array.

If the length of a byte array is 200 then the transaction consumes 200 bandwidth points.

2. Calculation of bandwidth points

Bandwidth points are the number of usable bytes for an account per day.

Within a given period of time, the entire network could only handle a fixed amount of bandwidth.

The ratio of bandwidth points in an account to the bandwidth capacity of TRON’s network equals the ratio of frozen balance in an account to frozen balance on the entire network.

e.g If frozen asset on the entire network totals 1,000,000 TRX and one given account froze 1,000 TRX, or 0.1% of total TRX frozen, then the account can perform about 300 transactions per day.

.. Note:: Since the amount of frozen asset on the entire network and for a certain account are subject to change, bandwidth points held by an account isn’t always fixed.

3. Complimentary bandwidth points

There are 5000 bandwidth points for free per account per day. When an account hasn’t frozen any balance, or when its bandwidth points have run out, complimentary bandwidth points can be used.

Each transaction in Tron’ network is about 200 bytes, so each account enjoys about 25 transactions for free each day.

4. Token transfer

For transactions of token transfer, bandwidth points will first be charged from the token issuer.

When issuing tokens, the issuer can configure a limit to maximum bandwidth consumption, namely the maximal bandwidth points which can be charged from him/her for a token holder’s token transfers within 24 hours and the maximal total of bandwidth points.

These two parameters can be configured through updateAsset interface.

5. Consumption of bandwidth points

Aside from inquiries, any other type of transaction consumes bandwidth points. The bandwidth consumption procedure is as follows:

    + If the transaction isn’t a token transfer, skip to step 2. If the transaction is a token transfer, TRON will try to charge bandwidth points from the token issuer. If the issuer does not have sufficient bandwidth points or the charge is beyond the issuer’s maximal threshold, go to step 2.
    + Charge bandwidth points from the initiator. If bandwidth points are insufficient:
      (1) If the transaction creates a new account, skip to step 4.
      (2) If the transaction does not create a new account, go to step 3.
    + Charge free bandwidth points from the initiator. If there is insufficient free bandwidth points, go to step 4.
    + TRX will be charged from and the transaction initiator and burnt.
      (1) For a normal transfer, it costs about 0.002 TRX.
      (2) If a new account is created by the transaction, it costs about 0.1 TRX.
    .. Note:: When balance unfreezes, bandwidth points will be cleared since there is no more frozen TRX.

6. Account creation

Complimentary bandwidth points cannot be used for account creation. Bandwidth points gained from balance freezing or 0.1 TRX is needed.

Users can create account by directly invoking account creation API, TRX transfer and token transfer.

Token issuance
~~~~~~~~~~~~~~

In TRON’s network, every account is capable of issuing tokens at the expense of 1024 TRX. Users can lock their tokens in separately.

To issue token, issuer needs to set up token name, total capitalization, exchange rate to TRX, circulation duration, description, website, maximum bandwidth consumption per account, total bandwidth consumption and token freeze.

+ e.g.

assetissue password abc 1000000 1 1 2018-5-31 2018-6-30 abcdef a.com 1000 1000000 200000 180 300000 365

Tokens named abc are issued with the above command, with a capitalization totaling 1 million. The exchange rate of abc to TRX is 1:1. The duration of circulation is May 31-June 30, 2018. It is described as abcdef. The provided website is a.com.

A maximum of 1000 bandwidth points can be charged from the issuer’s account per account per day. A maximum of 1,000,000 bandwidth points can be charged from the issuer’s account for all token holders’ transactions each day. in total capitalization, 200,000 tokens are locked for 180 days and 300,000 tokens are locked for 365 days.

**SR Rewards**

1.	Candidate reward: 127 candidates updated once every 6 hours will share 115200 TRX. The reward will be split in accordance to the votes each candidate receives. Each year, candidate reward will total 168,192,000 TRX.
2.	Super Representative reward: The TRON Protocol network will generate one block every 3 seconds, with each block awarding 32 TRX to super representatives. A total of 336,384,000 TRX will be awarded annually to twenty-seven super representatives.
3.	There will be no inflation on the TRON network before January 1, 2021, and the TRON Foundation will award all block rewards and candidate rewards prior to that date.

Relevant expenses
~~~~~~~~~~~~~~~~~

When there are sufficient bandwidth points, no TRX is charged. If a transaction fee is charged, it will be recorded in the fee field in the transaction results. If no transaction fee is charged, meaning that corresponding bandwidth points have been deducted, the fee field will read “0”. There will only be a service charge after a transaction has been written into the blockchain. For more information on the fee field, please see also Transaction.Result.fee, with the corresponding proto file at https://github.com/tronprotocol/protocol/blob/master/core/Tron.proto.

See also: https://github.com/tronprotocol/Documentation/blob/master/English_Documentation/TRON_Protocol/Mechanism_Introduction.md

User address generation
-----------------------

Algorithm description
~~~~~~~~~~~~~~~~~~~~~

1. First generate a key pair and extract the public key (a 64-byte byte array representing its x,y coordinates).
2. Hash the public key using sha3-256 function and extract the last 20 bytes of the result.
3. Add 41 to the beginning of the byte array. Length of the initial address should be 21 bytes.
4. Hash the address twice using sha256 function and take the first 4 bytes as verification code.
5. Add the verification code to the end of the initial address and get an address in base58check format through base58 encoding.
6. An encoded mainnet address begins with T and is 34 bytes in length.

.. code-block:: shell

    Please note that the sha3 protocol we adopt is KECCAK-256.

Mainnet addresses begin with 41
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: shell

    address = 41||sha3[12,32): 415a523b449890854c8fc460ab602df9f31fe4293f
    sha256_0 = sha256(address): 06672d677b33045c16d53dbfb1abda1902125cb3a7519dc2a6c202e3d38d3322
    sha256_1 = sha256(sha256_0): 9b07d5619882ac91dbe59910499b6948eb3019fafc4f5d05d9ed589bb932a1b4
    checkSum = sha256_1[0, 4): 9b07d561
    addchecksum = address || checkSum: 415a523b449890854c8fc460ab602df9f31fe4293f9b07d561
    base58Address = Base58(addchecksum): TJCnKsPa7y5okkXvQAidZBzqx3QyQ6sxMW

Java code demo
~~~~~~~~~~~~~~

.. code-block:: shell

    package org.tron.demo;

    import static java.util.Arrays.copyOfRange;

    import java.math.BigInteger;
    import java.util.Arrays;
    import org.spongycastle.math.ec.ECPoint;
    import org.springframework.util.StringUtils;
    import org.tron.common.crypto.ECKey;
    import org.tron.common.crypto.Hash;
    import org.tron.common.crypto.Sha256Hash;
    import org.tron.common.utils.Base58;
    import org.tron.common.utils.ByteArray;
    import org.tron.common.utils.Utils;
    import org.tron.core.exception.CipherException;
    import org.tron.walletserver.WalletClient;

    public class ECKeyDemo {

      private static byte[] private2PublicDemo(byte[] privateKey) {
        BigInteger privKey = new BigInteger(1, privateKey);
        ECPoint point = ECKey.CURVE.getG().multiply(privKey);
        return point.getEncoded(false);
      }

      private static byte[] public2AddressDemo(byte[] publicKey) {
        byte[] hash = Hash.sha3(copyOfRange(publicKey, 1, publicKey.length));
        System.out.println("sha3 = " + ByteArray.toHexString(hash));
        byte[] address = copyOfRange(hash, 11, hash.length);
        address[0] = WalletClient.getAddressPreFixByte();
        return address;
      }

      public static String address2Encode58CheckDemo(byte[] input) {
        byte[] hash0 = Sha256Hash.hash(input);
        System.out.println("sha256_0: " + ByteArray.toHexString(hash0));

        byte[] hash1 = Sha256Hash.hash(hash0);
        System.out.println("sha256_1: " + ByteArray.toHexString(hash1));

        byte[] inputCheck = new byte[input.length + 4];
        System.out.println("checkSum: " + ByteArray.toHexString(copyOfRange(hash1, 0, 4)));

        System.arraycopy(input, 0, inputCheck, 0, input.length);
        System.arraycopy(hash1, 0, inputCheck, input.length, 4);
        System.out.println("addchecksum: " + ByteArray.toHexString(inputCheck));

        return Base58.encode(inputCheck);
      }

      private static String private2Address(byte[] privateKey) throws CipherException {
        ECKey eCkey;
        if (StringUtils.isEmpty(privateKey)) {
          eCkey = new ECKey(Utils.getRandom());  //Gen new Keypair
        } else {
          eCkey = ECKey.fromPrivate(privateKey);
        }
        System.out.println("Private Key: " + ByteArray.toHexString(eCkey.getPrivKeyBytes()));

        byte[] publicKey0 = eCkey.getPubKey();
        byte[] publicKey1 = private2PublicDemo(eCkey.getPrivKeyBytes());
        if (!Arrays.equals(publicKey0, publicKey1)){
          throw new CipherException("publickey error");
        }
        System.out.println("Public Key: " + ByteArray.toHexString(publicKey0));

        byte[] address0 = eCkey.getAddress();
        byte[] address1 = public2AddressDemo(publicKey0);
        if (!Arrays.equals(address0, address1)){
          throw new CipherException("address error");
        }
        System.out.println("Address: " + ByteArray.toHexString(address0));

        String base58checkAddress0 = WalletClient.encode58Check(address0);
        String base58checkAddress1 = address2Encode58CheckDemo(address0);
        if (!base58checkAddress0.equals(base58checkAddress1)){
          throw new CipherException("base58checkAddress error");
        }

        return base58checkAddress1;
      }

      public static void main(String[] args) throws CipherException {
        String privateKey = "F43EBCC94E6C257EDBE559183D1A8778B2D5A08040902C0F0A77A3343A1D0EA5";
        String address = private2Address(ByteArray.fromHexString(privateKey));
        System.out.println("base58Address: " + address);

        System.out.println("================================================================\r\n");

        address = private2Address(null);
        System.out.println("base58Address: " + address);

      }
    }

Construction and signature of transaction
-----------------------------------------

There are two ways to construct a transaction.

Invoke APIs on the FullNode
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Based on your own needs, construct a corresponding local Contract and construct transactions with corresponding APIs. For the contract, please refer to https://github.com/tronprotocol/protocol/blob/master/core/Contract.proto.

Local construction
~~~~~~~~~~~~~~~~~~

Based on the definition of a transaction, you will need to fill in all fields of a transaction to construct a transaction at your local. Please note that you will need to configure the details of reference block and expiration, so you will need to connect to the mainnet during transaction construction. We advise that you set the latest block on the full node as your reference block and production time of the latest block+N minutes as your expiration time. N could be any number you find fit. The backstage condition is (Expiration > production time of the latest block and Expiration < production time of the latest block + 24 hours). If the condition is fulfilled, then the transaction is legit, and if not, the transaction is expired and will not be received by the mainnet. method of setting refference block: set RefBlockHash as subarray of newest block's hash from 8 to 16, set BlockBytes as subarray of newest block's height from 6 to 8. The code is as follows:

.. code-block:: shell

    public static Transaction setReference(Transaction transaction, Block newestBlock) {
        long blockHeight = newestBlock.getBlockHeader().getRawData().getNumber();
        byte[] blockHash = getBlockHash(newestBlock).getBytes();
        byte[] refBlockNum = ByteArray.fromLong(blockHeight);
        Transaction.raw rawData = transaction.getRawData().toBuilder()
            .setRefBlockHash(ByteString.copyFrom(ByteArray.subArray(blockHash, 8, 16)))
            .setRefBlockBytes(ByteString.copyFrom(ByteArray.subArray(refBlockNum, 6, 8)))
            .build();
        return transaction.toBuilder().setRawData(rawData).build();
      }

Method of setting Expiration and transaction timestamp
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: shell

    public static Transaction createTransaction(byte[] from, byte[] to, long amount) {
    Transaction.Builder transactionBuilder = Transaction.newBuilder();
    Block newestBlock = WalletClient.getBlock(-1);

    Transaction.Contract.Builder contractBuilder = Transaction.Contract.newBuilder();
    Contract.TransferContract.Builder transferContractBuilder = Contract.TransferContract
        .newBuilder();
    transferContractBuilder.setAmount(amount);
    ByteString bsTo = ByteString.copyFrom(to);
    ByteString bsOwner = ByteString.copyFrom(from);
    transferContractBuilder.setToAddress(bsTo);
    transferContractBuilder.setOwnerAddress(bsOwner);
    try {
      Any any = Any.pack(transferContractBuilder.build());
      contractBuilder.setParameter(any);
    } catch (Exception e) {
      return null;
    }
    contractBuilder.setType(Transaction.Contract.ContractType.TransferContract);
    transactionBuilder.getRawDataBuilder().addContract(contractBuilder)
        .setTimestamp(System.currentTimeMillis())//timestamp should be in millisecond format
        .setExpiration(newestBlock.getBlockHeader().getRawData().getTimestamp() + 10 * 60 * 60 * 1000);//exchange can set Expiration by needs
    Transaction transaction = transactionBuilder.build();
    Transaction refTransaction = setReference(transaction, newestBlock);
    return refTransaction;
  }

Procedures of transaction signature generation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After a transaction is constructed, it can be signed using the ECDSA algorithm. For security reasons, we suggest all exchanges to adopt offline signatures.

**Procedures**

1.	Convert the format of the transaction’s raw data to byte[].
2.	Conduct sha256 calculation on raw data.
3.	Sign the results of sha256 with the private key in correspondence with the address of each contract (1 contract and 1 private key for now).
4.	Add the signed result to transaction.

**Signature algorithm**

1. ECDSA algorithm, SECP256K.

2. Example of signature data

.. code-block:: shell

    priKey:::8e812436a0e3323166e1f0e8ba79e19e217b2c4a53c970d4cca0cfb1078979df
    pubKey::04a5bb3b28466f578e6e93fbfd5f75cee1ae86033aa4bbea690e3312c087181eb366f9a1d1d6a437a9bf9fc65ec853b9fd60fa322be3997c47144eb20da658b3d1
    hash:::159817a085f113d099d3d93c051410e9bfe043cc5c20e43aa9a083bf73660145
    r:::38b7dac5ee932ac1bf2bc62c05b792cd93c3b4af61dc02dbb4b93dacb758123f
    s:::08bf123eabe77480787d664ca280dc1f20d9205725320658c39c6c143fd5642d
    v:::0

.. Note:: the signed result should be 65 byte in size—r 32 bytes, s 32 bytes and v 1 byte.

3. Signature verification

When a full node receives transaction, it will verify signature, comparing an address calculated with hash, r, s and v with the address of the contract. Signature is successfully verified if the two addresses match.

**Example of code**

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

**Calculation of transaction ID**

Hash the Raw data of the transaction.

.. code-block:: shell

    Hash.sha256(transaction.getRawData().toByteArray())

**Calculation of block ID**

Block ID is a combination of block height and the hash of the blockheader’s raw data. To get block ID, first hash the raw data of the blockheader and replace the first 8 bytes of the hash with the blockheight, as the following:

.. code-block:: shell

    private byte[] generateBlockId(long blockNum, byte[] blockHash) { 
     byte[] numBytes = Longs.toByteArray(blockNum); 
     byte[] hash = blockHash; 
     System.arraycopy(numBytes, 0, hash, 0, 8); 
     return hash;
     }

BlockHash is the hash of the raw data of the blockheader, which can be calculated as the following:

.. code-block:: shell

    Sha256Hash.of(this.block.getBlockHeader().getRawData().toByteArray())

Demo
~~~~

The demo for local transaction construction and signing can be found at: https://github.com/tronprotocol/wallet-cli/blob/master/src/main/java/org/tron/demo/TransactionSignDemo.java.

Nodejs demo
-----------

We have provided nodejs demo, please refer https://github.com/tronprotocol/tron-demo/tree/master/demo/nodejs

Migration plan
--------------

Token migration from ERC20 TRX to Mainnet TRX will occur between June 21st – June 25th (GMT+8). If your TRX is held on an exchange, no action is required. If your TRX is held in a wallet, you must deposit your TRX to an exchange before June 24, 2018 to avoid any losses. From June 21st– 25th, TRX withdrawals on exchanges will be suspended. On June 25th, both TRX deposits and withdraws on exchanges will be suspended. Deposits and withdraws will resume on June 26th. During this period, TRX trading will not be affected. If your TRX is held in a wallet and you were not aware of the migration notice, or saw the migration notice after June 25th, please visit our permanent token-exchange counter to exchange your tokens for mainnet TRX.

Relevant files
--------------

See also: https://github.com/tronprotocol/Documentation#documentation-guide