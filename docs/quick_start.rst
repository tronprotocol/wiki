===========
Quick Start
===========

.. contents:: Table of contents
    :depth: 1
    :local:

Software Hierarchy
------------------

.. note::  This repository is a IDEA project which you can simply download and import.

**Download and build**

.. code-block:: json

    > git clone https://github.com/tronprotocol/java-tron.git
    > cd java-tron
    > gradle build

**Import project to IDEA**

* [File] -> [New] -> [Project from Existing Sources...]
* Select java-tron/build.gradle
* Dialog [Import Project from Gradle], confirm [Use auto-import] and [Use gradle wrapper task configuration] have been selected，then select Gradle JVM（JDK 1.8）and click [OK]

**Testing**

**Install Kafka and create two topics (block and transaction)**

**Update the configuration**

**Starting program**

**IDEA:**

* [Edit Configurations...] -> [Add New Configuration] -> [Application]
* [Edit Configurations...] -> [Main Class]: org.tron.example.Tron
* [Edit Configurations...] -> [Use classpath of module]: java-tron_main
* [Edit Configurations...] -> [Program arguments]: --type server
* Run

.. image:: /img/commands/default-set.gif

or simply from terminal:

.. code-block:: json

    > ./gradlew run -Pserver=true

**Complete process**

.. image:: /img/commands/process.gif

Other nodes to join need to modify the connection ip.

Commands
--------


