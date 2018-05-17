===================
Blockchain Explorer
===================

.. contents:: Table of contents
    :depth: 1
    :local:

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/scan.jpg
    :width: 842px
    :height: 212px
    :align: center

Tronscan Super Representative Template
--------------------------------------

Intro
~~~~~

Tronscan provides a way for Super Representatives to publish their information right where the voters are, on Tronscan!

Super Representatives can use this template to build a static page which will be shown on Tronscan. The link will be placed in the voting overview page right next to the name.

By editing files in the repository on Github the Super Representative can manage their own content.

How to use
~~~~~~~~~~

This guide assumes that you already have an account which has Super Representative (candidate) status.

**Step 1: Copy/Fork the template on Github.**

- Go to https://github.com/tronscan/tronsr-template

- Fork the repository

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/fork-repo的副本.png
    :width: 842px
    :height: 539px
    :align: center

After forking the repository you will be navigated to your own `tronsr-template` version of the repository where you can make changes.

**Step 2: Fill in the template.**

The template can now be modified by editing files on Github.

- Click the file you want to edit

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/github-open-file的副本.png
    :width: 842px
    :height: 361px
    :align: center

- Open edit modus

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/github-edit-file的副本.png
    :width: 842px
    :height: 281px
    :align: center

- Add some information to the file

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/edit-team-intro的副本.png
    :width: 842px
    :height: 529px
    :align: center

Files are written in markdown format. An excellent intro can be found at https://guides.github.com/features/mastering-markdown/

- Update the logo.png and banner.png

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/github-upload-files的副本.png
    :width: 842px
    :height: 298px
    :align: center

Then click on "choose your files" and make sure the logo or banner you want to upload is named `logo.png` or `banner.jpg` to overwrite the placeholder images.

After you filled in the template it can now be published on https://tronscan.org

**Step 3: Publish to Tronscan**

- Navigate to https://tronscan.org

- Login to your account. In this example it shows using the private key, but you may use any login method.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/login-with-private-key的副本.png
    :width: 842px
    :height: 557px
    :align: center

- Open account and make sure the "Representative" label is visible

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/open-account的副本.png
    :width: 842px
    :height: 522px
    :align: center

- Scroll to the bottom and click "Set Github Link"

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/set-github-link的副本.png
    :width: 842px
    :height: 382px
    :align: center

- Input your Github username and then press "Link Github"

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/input-username的副本.png
    :width: 842px
    :height: 529px
    :align: center

- View your new Page!

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/view-page的副本.png
    :width: 842px
    :height: 250px
    :align: center

Example
~~~~~~~

The example shows which files are presented where. Whenever the files on Github are modified the page will instantly be updated

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/example-page的副本.png
    :width: 842px
    :height: 250px
    :align: center

FAQ
~~~

- I've modified a file but the changes aren't visible on tronscan.org?

Contents from the repository are served using the Github CDN which uses aggressive caching. It may take a few minutes before the changes are reflected on tronscan.org.

- Why are HTML elements visible on Github but not on tronscan.org?

Tronscan.org will sanitize all HTML tags for security reasons, only standard markdown tags are allowed.

Guide to voting on the new block explorer
-----------------------------------------

Open TRON block explorer or log in to your wallet.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    https://tronscan.org/#/

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/登陆1的副本.png
    :width: 842px
    :height: 314px
    :align: center

Enter your password and download encrypted private key.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Password will encrypt private key. Both password and private key are needed to log in to your wallet.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/输入密码的副本2.png
    :width: 842px
    :height: 314px
    :align: center

Download encrypted private key.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/下载密钥的副本3.png
    :width: 842px
    :height: 460px
    :align: center

Save your private key (by copy-paste or printing). Enter the account page upon successful log-in.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/保存密钥的副本4.png
    :width: 842px
    :height: 460px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/打印保存的副本5.png
    :width: 842px
    :height: 297px
    :align: center

Enter the account page upon successful log-in.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/注册成功的副本6.png
    :width: 842px
    :height: 536px
    :align: center

Only users with TRX are allowed to vote.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

10,000TRX can be claimed at the bottom of the account page to vote and only one claim can be made by every account. Once TRX is successfully claimed, account balance can be viewed in WALLET.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/testnet的副本.png
    :width: 842px
    :height: 536px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/钱包7的副本.png
    :width: 400px
    :height: 481px
    :align: center

An amount of TRX has to be frozen in order to vote for Super Representatives.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To freeze balance, click the FREEZE button in ACCOUNT, enter the amount of TRX you’d like to freeze, check the box to confirm freezing ****TRX for at least 3 days, and click FREEZE BALANCE to complete your freeze.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/冻结8的副本.png
    :width: 842px
    :height: 158px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/9的副本.png
    :width: 842px
    :height: 408px
    :align: center

.. Note:: Only TRX can be frozen. Two things can be obtained through balance freezing: TRON Power and entropy points. TRON Power are used for voting. In the event of unfrozen balance, votes previously casted will no longer be valid, which can be prevented by refreezing balance. Entropy points will not be cleared when balance unfreezes, instead, new entropy points will be accumulated at the next freeze.

Vote for Super Representatives.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Click on VOTES in the navigation bar to enter voting page and then click START VOTING.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/10的副本.png
    :width: 842px
    :height: 539px
    :align: center

Select “Super Representative” to vote.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

On voting page, enter an amount of votes, click SUBMIT VOTES to submit and your will be notified if submission is successful.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/11的副本.png
    :width: 842px
    :height: 462px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/12的副本.png
    :width: 676px
    :height: 524px
    :align: center

Click RESET to reset the amount of votes entered for the current Super Representative.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/13的副本.png
    :width: 842px
    :height: 399px
    :align: center

.. Note:: Once you have submitted the amount of votes, the vote is complete. Voting requires TRON Power, which can be obtained by freezing TRX, one TRON Power for each frozen TRX and one vote for each TRON Power. Previous votes will no longer be valid when TRX is unfrozen, which can be avoided by refreezing. Voting will be successful as long as total votes casted do not exceed total TRON Power. There is no limit to the number of votes casted for a single Super Representative. A successful vote will consume 10^5 entropy points, unless it is more than 10s from the previous contract (vote, transfer, asset migration and balance freeze). When TRON Power are insufficient, user will be alerted on insufficient frozen balance. Only the last vote will be recorded, meaning that the last vote replaces all previous voting records.

.. Voting Guidelines::

+ The maximum votes a user has must be no more than his/her holding of TRX.
+ Every user can vote for multiple candidates for multiple times.
+ The Super Representative list is updated every 6 hours.
+ No TRX will be consumed for voting.



