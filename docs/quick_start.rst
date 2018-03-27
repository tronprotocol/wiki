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

How to Build
------------

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

* The building will normally finish in less than one minute.

*Build an executable JAE

.. code-block:: shell

    ./gradlew clean shadowJar
    Build in IntelliJ IDEA (community version is enough):

* Start IntelliJ Idea. Select File -> Open, then locate to the java-tron folder which you have git cloned to your local drive. Then click Open button on the right bottom.
* Check on Use auto-import on the Import Project from Gradle dialog. Select JDK 1.8 in the Gradle JVM option. Then click OK.
* IntelliJ will open the project and start gradle syncing, which will take several minutes, depending on your network connection and your IntelliJ configuration.
* After the syncing finished, select Gradle -> Tasks -> build, and then double click build option. The project will start building, which will normally take less than one minute to finish.

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

    > # Witness node will generate blocks
    > java -jar java-tron.jar --witness true/false
    > # Private key
    > tron.jar --private-key YourPrivateKey
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

    > ./gradlew run -Pwitness

**Complete process**

.. image:: /img/commands/process.gif
:width: 100%

Other nodes to join need to modify the connection ip.

**DOCKER:**