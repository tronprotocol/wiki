===========
TRON Client
===========

.. contents:: Table of contents
    :depth: 1
    :local:

Tronscan
--------

Tronscan Super Representative Template
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/scan.jpg
    :width: 842px
    :height: 212px
    :align: center

**Intro**

Tronscan provides a way for Super Representatives to publish their information right where the voters are, on Tronscan!

Super Representatives can use this template to build a static page which will be shown on Tronscan. The link will be placed in the voting overview page right next to the name.

By editing files in the repository on Github the Super Representative can manage their own content.

**How to use**

This guide assumes that you already have an account which has Super Representative (candidate) status.

Step 1: Copy/Fork the template on Github.

- Go to https://github.com/tronscan/tronsr-template

- Fork the repository

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/fork-repo的副本.png
    :width: 842px
    :height: 539px
    :align: center

After forking the repository you will be navigated to your own `tronsr-template` version of the repository where you can make changes.

Step 2: Fill in the template.

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

Step 3: Publish to Tronscan

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

**Example**

The example shows which files are presented where. Whenever the files on Github are modified the page will instantly be updated

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/Tronscan_Template/example-page的副本.png
    :width: 842px
    :height: 250px
    :align: center

**FAQ**

- I've modified a file but the changes aren't visible on tronscan.org?

Contents from the repository are served using the Github CDN which uses aggressive caching. It may take a few minutes before the changes are reflected on tronscan.org.

- Why are HTML elements visible on Github but not on tronscan.org?

Tronscan.org will sanitize all HTML tags for security reasons, only standard markdown tags are allowed.

Guide to voting on the new block explorer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Open TRON block explorer or log in to your wallet.**

    https://tronscan.org/#/

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/登陆1的副本.png
    :width: 842px
    :height: 314px
    :align: center

**Enter your password and download encrypted private key.**

Password will encrypt private key. Both password and private key are needed to log in to your wallet.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/输入密码的副本2.png
    :width: 842px
    :height: 314px
    :align: center

**Download encrypted private key.**

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/下载密钥的副本3.png
    :width: 842px
    :height: 460px
    :align: center

**Save your private key (by copy-paste or printing). Enter the account page upon successful log-in.**

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/保存密钥的副本4.png
    :width: 842px
    :height: 460px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/打印保存的副本5.png
    :width: 842px
    :height: 297px
    :align: center

**Enter the account page upon successful log-in.**

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/注册成功的副本6.png
    :width: 842px
    :height: 536px
    :align: center

**Only users with TRX are allowed to vote.**

10,000TRX can be claimed at the bottom of the account page to vote and only one claim can be made by every account. Once TRX is successfully claimed, account balance can be viewed in WALLET.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/testnet的副本.png
    :width: 842px
    :height: 536px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/钱包7的副本.png
    :width: 400px
    :height: 481px
    :align: center

**An amount of TRX has to be frozen in order to vote for Super Representatives.**

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

**Vote for Super Representatives.**

Click on VOTES in the navigation bar to enter voting page and then click START VOTING.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/10的副本.png
    :width: 842px
    :height: 539px
    :align: center

**Select “Super Representative” to vote.**

On voting page, enter an amount of votes, click SUBMIT VOTES to submit and your will be notified if submission is successful.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/11的副本.png
    :width: 842px
    :height: 462px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/12的副本.png
    :width: 676px
    :height: 524px
    :align: center

**Click RESET to reset the amount of votes entered for the current Super Representative.**

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

Android Wallet
--------------

Introduction
~~~~~~~~~~~~~~

TRON Wallet is a multifunctional Android wallet for the TRON network. It gives you the possibility to interact quickly and easily with your account or to keep your TRX and other account data safe in a cold wallet setup. This app offers you one of the safest ways to protect your private data. The goal in the future is to connect the users even better and easier with the TRON network and thus form a basis for all in the TRON community to strengthen and offer extended possibilities.

**Features**

Create Wallet
+ encrypts private information with a password
+ creates a private/public key pair
+ creates a 24 words recovery phrase (human readable private key recovery phrase) (BIP39)

**Import Wallet**
+ import with private key or 24 words recovery phrase
+ import public address only (watch only setup)

**Wallet Functionalities**
+ check balance (TRX, tokens)
+ toggle market price view
+ check frozen amount
+ send TRX and tokens
+ receive using QR code
+ freeze TRX to get TRON Power and bandwidth
+ submit votes for representatives
+ offline signing mechanism with QR code scanning
+ participate in token distributions
+ manually set your node connection

**Block Explorer**
+ see latest blocks
+ see latest transactions
+ see representative candidates
+ see connected nodes
+ see token distributions
+ see accounts
+ search filter

**Wallet Setups**

Watch only setup
+ import only your public address
+ completely safe because no private information is accessible
+ you have a full overview of your account
+ creates unsigned transactions (used in combination with a cold wallet setup)

Hot Wallet Setup
+ owns public and private key
+ full overview of account
+ full access (sending, freezing, voting, ...)

Cold Wallet Setup
+ minimalistic and safest wallet
+ owns public and private key
+ never connects to the internet (to be completely secure you should never connect your device to the internet)
+ signs transactions (from watch only setup)

Check information on blocks and recent transactions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/9的副本.png
    :width: 842px
    :height: 408px
    :align: center

![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/查看相关信息/区块和交易信息.png)

Check SR candidate information
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/查看相关信息/查看SP候选信息.png)

Check node information
~~~~~~~~~~~~~~~~~~~~~~
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/查看相关信息/查看节点信息.png)

Participate in token offerings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ select the token you’d like to buy
+ select quantity of purchase
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/查看相关信息/查看token信息.png)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/查看相关信息/选择购买数量.png)

Check account information
~~~~~~~~~~~~~~~~~~~~~~~~~
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/查看相关信息/查看账户信息.png)

Import wallet
~~~~~~~~~~~~~
+ import public address only (watch-only setup)
+ or import with private key or 24-word recovery phrase
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/倒入钱包/导入钱包.png)

Create account
~~~~~~~~~~~~~~

1. Cellphone screen display.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/创建钱包账户/1桌面显示.png)
2. Account creation page in app.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/创建钱包账户/2.点击app之后的界面.jpg)
3. Tap CREATE WALLET.
+ Cold wallet creation: toggle COLD WALLET SETUP and tick I AM AWARE OF THE RISKS.
+ Hot wallet creation: don’t toggle COLD WALLET SETUP and tick I AM AWARE OF THE RISKS.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/创建钱包账户/3.设置密码.jpg)
4. Tap GENERATE ADDRESS AND PRIVATE KEY and tap OK after reading the information page.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/创建钱包账户/4.png)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/创建钱包账户/6.png)
5. Make sure to save your private key and 24-word recovery phrase.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/创建钱包账户/7.钱包创建好之后的页面%20now%20we%20see%20here%20is%20a%20public%20address%20%2Cprivate%20key%20and%2024%20words%20recovery%20phrase.jpg)
6. Tap continue and enter wallet page.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/创建钱包账户/8.创建号钱包之后下滑页面找到continue按钮.jpg)

Voting
~~~~~~

Users can vote in hot wallet setup.

1.	Enter wallet page.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/1.当前的余额显示页面.jpg)
2. Enter transfer page.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/2.点击余额右侧的转账页面.png)
3. Select freeze and enter freeze page.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/3.点击FREEZE进入TRX冻结页面.jpg)
4. Type in freeze amount.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/4.在freeze%20amount%20输入栏中键入希望冻结的TRX数量，然后点击freeze按钮，注，拥有多少冻结TRX就拥有多少投票权.jpg)
5. Enter your password and confirm the freeze.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/5冻结TRX需要输入账户密码进行确认.jpg)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/6.键入账户密码.jpg)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/7.png)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/8.进行100TRX冻结之后的页面显示.jpg)
6. Return to balance page and click the vote button on the left-hand side.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/9.回到余额显示页面，然后点击余额左侧的投票按钮.jpg)
7. Enter SR candidate page.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/10.点击投票按钮之后进入超级代表候选人list页面，candidates一栏下显示的是所有待投票竞选的SR候选人.jpg)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/11.此为your%20votes页面下的显示情况，因为我们还没有对任何一个SR候选节点进行投票，所以列表中空空如也.png)
8. Select a SR candidate and enter the amount of votes.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/12.我们回到candidates一栏，任意选择一个SR候选人进行投票演示，以list中首个系节点为例，注，candidates%20list%20的排列是以票数多少为顺序.jpg)
9. Tap SUBMIT, enter the amount of votes and your password and submit votes.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/13.输入希望为此节点投出的票数.jpg)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/14.点击submit%20votes之后要求输入账户密码进行确认投票.jpg)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/16.png)
10. You can check your votes in the candidates tab and in the votes tab.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/17.为此候选人投过票后此候选人右侧显示你为其透过的票数.jpg)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/投票/18.这个时候我们可以看到在your%20votes一栏中与投票前不同的是出现了我们为其投过票的SR候选人信息.jpg)

Initiate transfer
~~~~~~~~~~~~~~~~~

1. Enter account page.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/转出和转入/转入/1.账户中有余额时候的余额显示界面.png)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/转出和转入/转入/2.点击余额数字可转换成美元的等值额度.png)
2. Enter your address or scan QR-code to extract address. Enter the amount of TRX for transfer and tap SEND.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/转出和转入/转入/3.点击右侧转账按钮后出现的界面（默认停留在send也就是转出TRX时的操作页面）可以通过在to一栏输入转入地址也可以点击右侧的二维码小标志，打开二维码扫描页面.png)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/转出和转入/转入/4.点击receive后显示自己的钱包地址和二维码性质的地址，可供转出账户进行输入和scan，待转出账户操作完毕后，点击左上角返回箭头进行余额查看.jpg)
![](https://github.com/ybhgenius/Documentation/blob/master/images/Wallet_for_Android/转出和转入/转出/6.输入希望转入的额度点击send.png)
3. Enter account password and tap SEND, and you will see the message of SENT SUCCESSFULLY.
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/转出和转入/转出/7.点击send之后需要输入账户密码进行确认.png)
![](https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/转出和转入/转出/9.png)
