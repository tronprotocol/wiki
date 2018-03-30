===========
Quick Start
===========

.. contents:: Table of contents
  :depth: 1
  :local:

**Current Testnet p2p version: 31（resources/config.conf:node.p2p.verson = 31）**

**Supported Operating System**

Tron supports any operating systems that can run JDK 1.8.

**Prepare dependencies**

* JDK 1.8 (do not use JDK 1.9 please)

**Getting the code**

1. Use Git from the Terminal, see the `Setting up Git <https://help.github.com/articles/set-up-git/>`_ and `Fork a Repo <https://help.github.com/articles/fork-a-repo/>`_ articles. In the shell command, type:

.. code-block:: shell

    git clone https://github.com/tronprotocol/java-tron.git

2. For Mac, you can also install `GitHub for Mac <https://desktop.github.com/>`_ then `fork and clone our repository <https://guides.github.com/activities/forking/>`_;

3. If you’d rather not use Git, use the `Download ZIP <https://github.com/tronprotocol/java-tron/archive/develop.zip>`_ button on the right to get the source directly.

**Importing java-tron to IntelliJ IDEA**

1. Terminal:

.. code-block:: shell

    > cd java-tron
    > ./gradlew build

2. IntelliJ IDEA:

* ``File`` -> ``New`` -> ``Project from existing sources...``;
* Select ``java-tron/build.gradle``;
* Check on ``Use auto-import`` on the ``Import Project from Gradle`` dialog. Select JDK 1.8 in the ``Gradle JVM`` option. Press ``OK``;
* After the syncing finished, install ``Lombok Plugin``, and set ``Enable annotation processing``, then you can execute ```./gradlew run`` and start a full node.

**Build an executable Jar**

.. code-block:: shell

    > cd java-tron
    > ./gradlew clean shadowJar
    > cd build/libs/
    > java -jar java-tron.jar

**JUnit**

.. code-block:: shell

    > cd java-tron
    > ./gradlew test

**Contribution**

Contributions are welcomed and greatly appreciated. Please see `CONTRIBUTING.md <https://github.com/tronprotocol/java-tron/blob/develop/CONTRIBUTING.md>`_ for details on submitting patches and the contribution workflow.

**Servers**

+----------------+-----------------+---------------------+
| IP             | Location        | Description         |
+================+=================+=====================+
| 47.254.16.55   | Silicon Valley  | Witness Node        |
+----------------+-----------------+---------------------+
| 47.254.18.49   | Silicon Valley  | Witness Node        |
+----------------+-----------------+---------------------+
| 18.188.111.53  | Ohio            | Witness Node        |
+----------------+-----------------+---------------------+
| 54.219.41.56   | California      | Witness Node        |
+----------------+-----------------+---------------------+
| 35.169.113.187 | Virginia        | Witness Node        |
+----------------+-----------------+---------------------+
| 34.214.241.188 | Oregon          | Witness Node        |
+----------------+-----------------+---------------------+
| 47.254.146.147 | Frankfurt       | Witness Node        |
+----------------+-----------------+---------------------+
| 47.254.144.25  | Frankfurt       | Witness Node        |
+----------------+-----------------+---------------------+
| 47.91.246.252  | Hongkong        | Witness Node        |
+----------------+-----------------+---------------------+
| 47.91.216.69   | Hongkong        | Witness Node        |
+----------------+-----------------+---------------------+
| 39.106.220.120 | Beijing         | Witness Node        |
+----------------+-----------------+---------------------+
| 47.95.14.107   | Beijing         | Blockchain Explorer |
+----------------+-----------------+---------------------+

**Links**

* TRON Website: https://tron.network/
* GitHub: https://github.com/tronprotocol/java-tron/
* Community Telegram Group: https://t.me/tronnetworkEN/
* Slack Workspace: https://tronfoundation.slack.com/