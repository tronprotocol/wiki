============
TRON Clients
============

.. contents:: Table of contents
    :depth: 1
    :local:

Choosing a client
-----------------

Why should I choose Java develop clients?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

TRON enables JAVA development—a programming language that owns the highest number of community members and is highly commercialized. The natural support capability of JAVA’s community is incomparable to others. In order to accomplish the construction of decentralized platform with a more decentralized development model, TRON hopes to effectively mobilize the strength of the community.

Multi-Language Support TRON Client in the future
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

TRON will support other development languages in the future, including Scala. C++, Python, Go, etc.

How should I install on my desktop/laptop?( PC)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Java-Tron
---------

Server
^^^^^^

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

Set up the environment
^^^^^^^^^^^^^^^^^^^^^^

**Supported Operating System**

Tron currently supports the following operating systems:

* Centos 7.
* Fedora 25 and higher (Fedora 27 recommended).
* Mint 18.
* Ubuntu 16.04 (Ubuntu 16.10 recommended).
* MacOS Darwin 10.12 and higher (MacOS 10.13.x recommended).

How to Build
^^^^^^^^^^^^

**Getting the code**

* Use Git from the Terminal, see the Setting up Git and Fork a Repo articles. In the shell command, type:

.. code-block:: shell

    git clone https://github.com/tronprotocol/java-tron.git

* For Mac, you can also install GitHub for Mac then fork and clone our repository.
* If you'd rather not use Git, use the Download ZIP button on the right to get the source directly.

**Prepare dependencies**

* JDK 1.8 (do not use JDK 1.9 please)

**Building source code**

* Build in the Terminal

.. code-block:: shell

    cd java-tron
    ./gradlew build

The building will normally finish in less than one minute.

* Build an executable JAE

.. code-block:: shell

    ./gradlew clean shadowJar

Build in IntelliJ IDEA (community version is enough):

1.Start IntelliJ Idea. Select File -> Open, then locate to the java-tron folder which you have git cloned to your local drive. Then click Open button on the right bottom.

2.Check on Use auto-import on the Import Project from Gradle dialog. Select JDK 1.8 in the Gradle JVM option. Then click OK.

3.IntelliJ will open the project and start gradle syncing, which will take several minutes, depending on your network connection and your IntelliJ configuration.

4.After the syncing finished, select Gradle -> Tasks -> build, and then double click build option. The project will start building, which will normally take less than one minute to finish.

Running
^^^^^^^

**Running a private testnet**

* Running a full node

In the Terminal

.. code-block:: shell

    ./gradlew run

Use the executable JAE

.. code-block:: shell

    cd build/libs
    java -jar java-tron.jar

In IntelliJ IDEA

1.After the building finishes, locate FullNode in the project structure view panel, which is on the path java-tron/src/main/java/org.tron/program/FullNode.

2.Select FullNode, right click on it, and select Run 'FullNode.main()', then FullNode starts running.


Wallet-CLI
----------