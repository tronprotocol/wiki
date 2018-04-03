===========
Running a delegate.
===========

.. contents:: Table of contents
  :depth: 1
  :local:

The following steps serve as an introduction on how to become an actively delegate through our TRON blockchain explorer.

**Steps**

1. A registered account is required in TRON blockchain explorer.

* In order to use TRON blockchain explorer, you will need to register an account, please visit our website:

  http://git.razko.nl/wallet-web/#/login

2. A certain sum of TRX is required to be transferred to your new account.

* TRX for testing will be sent to your testing acoount once you successfully apply through account management.

3. You can get started to apply to be a delegate.

* Click the button “ Apply_for_delegate” first.

* Provide your personal website address. The type of address is including but not limited to: website, blog, social media account, etc.

4. After approval voting, the top 21 delegates by total approval are selected. The state of active delegates is updated once every maintenance interval (1 day).

* Build in the Terminal

.. code-block:: shell

    ./gradlew run -Pwitness=true

* Use the executable JAE

.. code-block:: shell

    cd build/libs

    java -jar java-tron.jar --witness true

* In IntelliJ IDEA

Open the configuration panel:

In the Program arguments option, fill in --witness:

Then, run FullNode::main() again.





