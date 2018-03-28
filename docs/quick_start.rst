===========
Quick Start
===========

.. contents:: Table of contents
  :depth: 1
  :local:

**Supported Operating System**

Tron currently supports the following operating systems:

* Centos 7;
* Fedora 25 and higher (Fedora 27 recommended);
* Mint 18;
* Ubuntu 16.04 (Ubuntu 16.10 recommended);
* MacOS Darwin 10.12 and higher (MacOS 10.13.x recommended).

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

* [File] -> [New] -> [Project from existing sources...];
* Select java-tron/build.gradle;
* Check on Use auto-import on the Import Project from Gradle dialog. Select JDK 1.8 in the Gradle JVM option. Press [OK];
* After the syncing finished, you can execute ./gradlew run and start a full node.

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

**Links**

* TRON Website: https://tron.network/
* GitHub: https://github.com/tronprotocol/java-tron/
* Community Telegram Group: https://t.me/tronnetworkEN/
* Slack Workspace: https://tronfoundation.slack.com/