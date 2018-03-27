===========
Quick Start
===========

.. contents:: Table of contents
:depth: 1
    :local:

Set up the environment
----------------------

**Supported Operating System**

Tron currently supports the following operating systems:

* Centos 7.
* Fedora 25 and higher (Fedora 27 recommended).
* Mint 18.
* Ubuntu 16.04 (Ubuntu 16.10 recommended).
* MacOS Darwin 10.12 and higher (MacOS 10.13.x recommended).


Download and build
------------------

.. code-block:: json

    > git clone https://github.com/tronprotocol/java-tron.git
    > cd java-tron
    > gradle build

**Building an executable JAE**

.. code-block:: json

    > git clone https://github.com/tronprotocol/java-tron.git
    > cd java-tron
    > ./gradlew clean shadowJar
    > java -jar java-tron/build/libs/java-tron.jar

**Optional samples**

.. code-block:: shell

    > # Normal node
    > java -jar java-tron.jar
    > # Witness node will generate blocks
    > java -jar java-tron.jar --witness
    > # Private key
    > java -jar java-exit
                     ^^^^
                     **Exit**

                     .. code-block:: json
                         > exit

                     .. image:: /img/commands/exit.gif
:width: 100%
tron.jar --private-key YourPrivateKey
    > # Store data directory
    > java -jar java-tron.jar --output-directory OutputDirectory
    # Addresses of seed nodes
    > java -jar java-tron.jar --seed-nodes 127.0.0.1:7080,127.0.0.1:7081
    # Port of node
    > java -jar java-tron.jar --overlay-port 7080

.. note::  This repository is a IDEA project which you can simply download and import.

**Import project to IDEA**

* [File] -> [New] -> [Project from Existing Sources...]
* Select java-tron/build.gradle
* Dialog [Import Project from Gradle], confirm [Use auto-import] and [Use gradle wrapper task configuration] have been selected，then select Gradle JVM（JDK 1.8）and click [OK]

**Testing**

**Update the configuration**

**Starting program**

**IDEA:**

* [Edit Configurations...] -> [Add New Configuration] -> [Application]
* [Edit Configurations...] -> [Main Class]: org.tron.example.Tron
* [Edit Configurations...] -> [Use classpath of module]: java-tron_main
* [Edit Configurations...] -> [Program arguments]: --type server
* Run

.. image:: /img/commands/default-set.gif
:width: 100%

or simply from terminal:

.. code-block:: json

    > ./gradlew run -Pserver=true

**Complete process**

.. image:: /img/commands/process.gif
:width: 100%

Other nodes to join need to modify the connection ip.
