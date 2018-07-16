===========
TRON Client
===========

.. contents:: Table of contents
    :depth: 1
    :local:

Tronscan
--------

Tronscan Super Representative Template
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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

Guide to Tronscan
~~~~~~~~~~~~~~~~~

Use the block explorer at https://tronscan.org.

**Blockchain module**

**Block search**

Information on all blocks—from the genesis block to all current blocks—can be found on this page, including block height, its previous block and the corresponding byte size. You can also use the search bar to check block height and SR nodes.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/blockchain模块/查看区块.png
    :width: 842px
    :height: 492px
    :align: center

**Transaction search**

You can search for transaction records on this page. Information on the sender and the recipient’s address, the amount of TRX transferred, block height of transaction record, corresponding Hash and production time can all be found. You can also use the search bar to look for a specific transaction by Hash.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/blockchain模块/查询账户.png
    :width: 842px
    :height: 519px
    :align: center

**Check address/transaction statistics**

On the statistics page, we can see figures of the top 25 TRX holders, TRX transferred in the past hour, transactions in the past hour and the trend of average block size. 'The Tronscan will continue to create more data visualizations for the users' convenience.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/blockchain模块/查询交易.png
    :width: 842px
    :height: 536px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/blockchain模块/查看地址交易统计数据.png
    :width: 842px
    :height: 592px
    :align: center

**Check block Live**

Block Live is a special feature of Tronscan, with which users can check the real-time transaction records, votes, token issuance and participation, and nodes. We can also use filters to view only our desired contents.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/blockchain模块/查看地址交易统计数据.png
    :width: 842px
    :height: 592px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/blockchain模块/查看区块直播.png
    :width: 842px
    :height: 216px
    :align: center

**Check node information**

This page shows the number of nodes and the country with most nodes.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/节点信息/数量与分布.png
    :width: 842px
    :height: 135px
    :align: center

This page shows the geographical distribution of TRON’s nodes. From the density of nodes in different regions, users can have a straightforward impression of where they are located. With the embedded Google map, users can zoom in and out of the map to know about the specific details.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/节点信息/地图分布.png
    :width: 842px
    :height: 460px
    :align: center

This page shows the following information on the nodes: IP address, hostname, block height, GPRC, GPRC m/s and time of the last update.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/节点信息/节点信息.png
    :width: 842px
    :height: 489px
    :align: center

**Check SR and SR candidate information**

Users can check out the Super Representative list which includes information on the last block, number of blocks produced, number of blocks missed, productivity and votes.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/SR和SR候选信息/SP信息.png
    :width: 842px
    :height:436px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/SR和SR候选信息/SP候选信息.png
    :width: 842px
    :height: 345px
    :align: center

Users can also check out corresponding links to find out more about the SRs.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/SR和SR候选信息/查看详细信息.png
    :width: 842px
    :height: 404px
    :align: center

**Tokens**

Users can participate in token offerings, get information through token overview or create their own tokens.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/关于代币/三大模块.png
    :width: 842px
    :height: 166px
    :align: center

To participate in token offerings, click on PARTICIPATE and enter an amount to TRX to purchase a certain type of token.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/关于代币/参与代币.png
    :width: 842px
    :height: 438px
    :align: center

Users can also view information on all tokens, including their name, total supply, total amount issued and the registration date.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/关于代币/代币概览.png
    :width: 842px
    :height: 309px
    :align: center

Users can also create their own tokens. Click on CREATE to enter the token creation page, fill in token details, click ISSUE TOKEN and their own token can be successfully issued.

Token creation is very simple in TRON ecosystem. Just set up the required parameters and you are done. The parameters are as follows:

+ Token name
+ Total supply
+ Token description
+ Website URL: to provide users with more information on the token they are purchasing.
+ Token exchange rate with TRX.
+ Participation period: during the participation period, users can exchange TRX for tokens.

A one-time service charge of 1024 TRX is required to create token.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/关于代币/创建代币1.png
    :width: 842px
    :height: 403px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/关于代币/创建代币2.png
    :width: 842px
    :height: 761px
    :align: center

Tronscan Introduction
~~~~~~~~~~~~~~~~~~~~~

**View latest TRX market information**

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/市场资讯/市场资讯.png
    :width: 842px
    :height: 423px
    :align: center

**Open Tronscan and log in to your wallet.**

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
    :height: 130px
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

Super Representative
~~~~~~~~~~~~~~~~~~~~~

Token holders in the TRON community fall into the following categories:

1. Token holder: Individual holding any amount of TRX.
2. Super Representative candidates: 127 individuals elected through voting by the entire token holder community. Votes are updated once every 6 hours.
3. Super Representatives: top 27 individuals among the 127 candidates, voted once every 6 hours. Super Representatives play a key role in governing the TRON community by ensuring basic functions, e.g. block generation and bookkeeping, and obtain corresponding earnings.

**Super Representative**

Users can get SR information from TRON blockchain explorer, the detailed information shown as below:

+ The account address of the delegate.
+ The total votes that the delegate received.
+ The url of personal website.
+ The total of blocks produced by the delegate.
+ The total missed blocks of delegate.

**Super Representative Recommendations**

Every token holder has the opportunity to become a TRON Super Representative. However, for the network and community to operate more smoothly and effectively, we have created a set of standards and regulations for eligible candidates to become recommended Super Representatives. We will promote recommended SRs to increase their chances of being elected.

New recommended Super Representatives are updated and posted once a week.

How to apply for SR candidate.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Open TRON Blockchain explorer:  https://tronscan.org

Click "Account" button.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/申请成为超级代表/点击账户.jpg
    :width: 842px
    :height: 1170px
    :align: center

Click "APPLY TO BE A SUPER REPRESENTATIVE CANDIDATE" button.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/申请成为超级代表/申请成为超级代表候选.jpg
    :width: 842px
    :height: 242px
    :align: center

Write your personal website address and check information below website address.

.. image:: https://raw.githubusercontent.com/ybhgenius/wiki/master/docs/img/Blockchain_Explorer/申请成为超级代表/填写网站地址并勾选.jpg
    :width: 842px
    :height: 565px
    :align: center

.. Note:: 9999 TRX will be paid when users apply to be a SR candidate.

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

+ individual connection (connect to any node, e.g. private net)
+ check balance (TRX, tokens)
+ toggle market price view
+ check frozen amount
+ send TRX and tokens
+ receive using QR code
+ freeze TRX to get votes and bandwidth
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

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/查看相关信息/区块和交易信息.png
    :width: 842px
    :height: 1496px
    :align: center

Check SR candidate information
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/查看相关信息/查看SP候选信息.png
    :width: 842px
    :height: 1496px
    :align: center

Check node information
~~~~~~~~~~~~~~~~~~~~~~

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/查看相关信息/查看节点信息.png
    :width: 842px
    :height: 1496px
    :align: center

Participate in token offerings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ select the token you’d like to buy
+ select quantity of purchase

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/查看相关信息/查看token信息.png
    :width: 842px
    :height: 1496px
    :align: center

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/查看相关信息/选择购买数量.png
    :width: 842px
    :height: 1496px
    :align: center

Check account information
~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/查看相关信息/查看账户信息.png
    :width: 842px
    :height: 1496px
    :align: center

Import wallet
~~~~~~~~~~~~~
+ import public address only (watch-only setup)
+ or import with private key or 24-word recovery phrase

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/倒入钱包/导入钱包.png
    :width: 842px
    :height: 1496px
    :align: center

Create account
~~~~~~~~~~~~~~

1. Cellphone screen display.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/创建钱包账户/1.桌面显示.png
    :width: 842px
    :height: 1496px
    :align: center

2. Account creation page in app.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/创建钱包账户/2.点击app之后的界面.jpg
    :width: 842px
    :height: 1496px
    :align: center

3. Tap CREATE WALLET.

+ Cold wallet creation: toggle COLD WALLET SETUP, tick I AM AWARE OF THE RISKS and set the name and password.
+ Hot wallet creation: don’t toggle COLD WALLET SETUP, tick I AM AWARE OF THE RISKS and set the name and password.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/创建钱包账户/3.设置用户名和密码.png
    :width: 842px
    :height: 1496px
    :align: center

4. Tap GENERATE ADDRESS AND PRIVATE KEY and tap OK after reading the information page.

.. image:: (https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/创建钱包账户/4.png
    :width: 842px
    :height: 1496px
    :align: center

.. image:: https://raw.githubusercontent.com/ybhgenius/Documentation/master/images/Wallet_for_Android/创建钱包账户/6.png
    :width: 842px
    :height: 1496px
    :align: center

5. Make sure to save your private key and 24-word recovery phrase.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/创建钱包账户/7.钱包创建好之后的页面%20now%20we%20see%20here%20is%20a%20public%20address%20%2Cprivate%20key%20and%2024%20words%20recovery%20phrase.jpg
    :width: 842px
    :height: 1496px
    :align: center

6. Tap continue and enter wallet page.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/创建钱包账户/8.创建号钱包之后下滑页面找到continue按钮.jpg
    :width: 842px
    :height: 1496px
    :align: center

Voting
~~~~~~

Users can vote in hot wallet setup.

1.	Enter wallet page.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/1.余额TP带宽显示界面.png
    :width: 842px
    :height: 1496px
    :align: center

2. Enter transfer page.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/2.点击右侧的转账界面.png
    :width: 842px
    :height: 1496px
    :align: center

3. Select freeze and enter freeze page.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/3.freeze页面.png
    :width: 842px
    :height: 1496px
    :align: center

4. Type in freeze amount.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/4.在freeze%20amount%20输入栏中键入希望冻结的TRX数量，然后点击freeze按钮，注，拥有多少冻结TRX就拥有多少投票权.jpg
    :width: 842px
    :height: 1496px
    :align: center

5. Enter your password，click send button and confirm the freeze.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/5.确认合约.png
    :width: 842px
    :height: 1496px
    :align: center

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/6输入密码点击发送.png
    :width: 842px
    :height: 1496px
    :align: center

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/7.发送成功.png
    :width: 842px
    :height: 1496px
    :align: center

6. Return to balance page and click the vote button on the left-hand side.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/9.点击投票按钮.png
    :width: 842px
    :height: 1496px
    :align: center

7. Enter SR candidate page.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/10.点击投票按钮之后进入超级代表候选人list页面，candidates一栏下显示的是所有待投票竞选的SR候选人.jpg
    :width: 842px
    :height: 1496px
    :align: center

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/11.此为your%20votes页面下的显示情况，因为我们还没有对任何一个SR候选节点进行投票，所以列表中空空如也.png
    :width: 842px
    :height: 1496px
    :align: center

8. Select a SR candidate and enter the amount of votes.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/12.我们回到candidates一栏，任意选择一个SR候选人进行投票演示，以list中首个系节点为例，注，candidates%20list%20的排列是以票数多少为顺序.jpg
    :width: 842px
    :height: 1496px
    :align: center

9. Tap SUBMIT, enter the amount of votes and your password and submit votes.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/13.输入希望为此节点投出的票数.jpg
    :width: 842px
    :height: 1496px
    :align: center

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/14.点击submit%20votes之后要求输入账户密码进行确认投票.jpg
    :width: 842px
    :height: 1496px
    :align: center

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/16.png
    :width: 842px
    :height: 1496px
    :align: center

10. You can check your votes in the candidates tab and in the votes tab.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/17.为此候选人投过票后此候选人右侧显示你为其透过的票数.jpg
    :width: 842px
    :height: 1496px
    :align: center

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/投票/18.这个时候我们可以看到在your%20votes一栏中与投票前不同的是出现了我们为其投过票的SR候选人信息.jpg
    :width: 842px
    :height: 1496px
    :align: center

Initiate transfer
~~~~~~~~~~~~~~~~~

1. Enter account page.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/转出和转入/转入/1.显示余额界面.png
    :width: 842px
    :height: 1496px
    :align: center

2. Enter your address or scan QR-code to extract address. Enter the amount of TRX for transfer and tap SEND.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/转出和转入/转入/3.点击右侧转账按钮后出现的界面（默认停留在send也就是转出TRX时的操作页面）可以通过在to一栏输入转入地址也可以点击右侧的二维码小标志，打开二维码扫描页面.png
    :width: 842px
    :height: 1496px
    :align: center

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/转出和转入/转入/4.点击receive后显示自己的钱包地址和二维码性质的地址，可供转出账户进行输入和scan，待转出账户操作完毕后，点击左上角返回箭头进行余额查看.jpg
    :width: 842px
    :height: 1496px
    :align: center

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/转出和转入/转出/6.输入希望转入的额度点击send.png
    :width: 842px
    :height: 1496px
    :align: center

3. Enter account password and tap SEND, and you will see the message of SENT SUCCESSFULLY.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/转出和转入/转出/7.点击send之后需要输入账户密码进行确认.png
    :width: 842px
    :height: 1496px
    :align: center

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/转出和转入/转出/9.png
    :width: 842px
    :height: 1496px
    :align: center

Check history
~~~~~~~~~~~~~

1. Enter history page.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/历史记录/1.进入历史记录界面.png
    :width: 842px
    :height: 1496px
    :align: center

2. Check each transaction information.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/历史记录/2.查看单笔交易信息.png
    :width: 842px
    :height: 1496px
    :align: center

3. Check transaction information on Tronscan.

.. image:: https://raw.githubusercontent.com/tronprotocol/Documentation/master/images/Wallet_for_Android/历史记录/3.tronscan上查看记录.png
    :width: 842px
    :height: 1496px
    :align: center

Wallet-Cli
----------

# wallet-cli [![Build Status](https://travis-ci.org/tronprotocol/wallet-cli.svg?branch=master)](https://travis-ci.org/tronprotocol/wallet-cli)
Wallet CLI


Download wallet-cli
---------------------------------
    git clone https://github.com/tronprotocol/wallet-cli.git


    Edit config.conf in src/main/resources
----------------------------------------
    ```
net {
 type = mainnet
 #type = testnet 
}

fullnode = {
  ip.list = [
    "fullnode ip : port"
  ]
}

soliditynode = {
  ip.list = [
    "solidity ip : port"
  ]
}//note: solidity node is optional

```
Build and run wallet-cli by command line
----------------------------------------
    Create a new command line terminal window.

    ```
cd wallet-cli  
./gradlew build      
./gradlew run
```

Build and run web wallet
----------------------------------------
    ```
cd wallet-cli  
./gradlew build
cd build/libs
java -jar wallet-cli.jar
```


How wallet-cli connects to java-tron :
--------------------------------------
    Wallet-cli connect to java-tron by grpc protocol.
    Java-tron nodes can be deployed locally or remotely.
    We can set the connected java-tron node IP in config.conf of wallet-cli.


    Wallet-cli supported command list:
    ----------------------------------

        RegisterWallet
RegisterWallet Password
Register a wallet in local.
    Generate a pair of ecc keys.
    Derive a AES Key by password and then use the AES algorithm to encrypt and save the private key.
    The account address is calculated by the public key sha3-256, and taking the last 20 bytes.
    All subsequent operations that require the use of a private key must enter the password.

    ImportWallet
ImportwalletByBase64
ChangePassword
Login
Logout
BackupWallet
BackupWallet2Base64
Getaddress
GetBalance
GetAccount
GetAssetissueByAccount
GetAssetIssueByName
SendCoin
TransferAsset
ParticipateAssetissue
Assetissue
CreateWitness
VoteWitness
FreezeBalance
UnfreezeBalance
WithdrawBalance
Listaccounts
Listwitnesses
Listassetissue
listNodes
GetAssetIssueByName
Getblock
UpdateAccount
Exit or Quit
help

Input any one of then, you will get more tips.


    How to freeze/unfreeze balance
----------------------------------

    After the funds are frozen, the corresponding number of shares and bandwidth will be obtained.
    Shares can be used for voting and bandwidth can be used for trading.
                                                                    The rules for the use and calculation of share and bandwidth are described later in this article.


**Freeze operation is as follows：**

```
freezebalance password amount time
```

*amount:The amount of frozen funds，the unit is drop.
    The minimum value is **1000000 drop(1TRX)**.*

*time：Freeze time, this value is currently only allowed for **3 days***


For example：
```
freezebalance 123455 10000000 3
```


After the freeze operation,frozen funds will be transferred from Account Balance to Frozen,
    You can view frozen funds from your account information.
    After being unfrozen, it is transferred back to Balance by Frozen, and the frozen funds cannot be used for trading.


                                                                                                                   When more share or bandwidth is needed temporarily, additional funds may be frozen to obtain additional share and bandwidth.
    The unfrozen time is postponed until 3 days after the last freeze operation

After the freezing time expires, funds can be unfroze.


**Unfreeze operation is as follows：**
```
unfreezebalance password 
```



How to vote
----------------------------------

    Voting requires share. Share can be obtained by freezing funds.

- The share calculation method is: **1** unit of share can be obtained for every **1TRX** frozen.
- After unfreezing, previous vote will expire. You can avoid the invalidation of the vote by re-freezing and voting.

**Note:** The Tron Network only records the status of your last vote, which means that each of your votes will cover all previous voting results.

    For example：

```
freezebalance 123455 10000000 3   // Freeze 10TRX and acquire 10 units of shares

votewitness 123455 witness1 4 witness2 6   // Cast 4 votes for witness1 and 6 votes for witness2 at the same time.

votewitness 123455 witness1 10   // Voted 10 votes for witness1.
```

The final result of the above command was 10 votes for witness1 and 0 votes for witness2.



                                                                                    How to calculate bandwidth
----------------------------------

    The bandwidth calculation rule is：
```
constant * FrozenFunds * days
```
Assuming freeze 1TRX（1_000_000 DROP），3 days，bandwidth obtained = 1* 1_000_000 * 3 = 3_000_000.

    Any contract needs to consume bandwidth, including transfer, transfer of assets, voting, freezing, etc.
    The query does not consume bandwidth, and each contract needs to consume **100_000 bandwidth**.

If the previous contract exceeds a certain time (**10s**), this operation does not consume bandwidth.

    When the unfreezing operation occurs, the bandwidth is not cleared.
    The next time the freeze is performed, the newly added bandwidth is accumulated.


    How to withdraw balance
----------------------------------

    After each block is produced, the block award is sent to the account's allowance,
and an withdraw operation is allowed every **24 hours** from allowance to balance.
    The funds in allowance cannot be locked or traded.


    How to create witness
----------------------------------
    Applying to become a witness account needs to consume **100_000TRX**.
This part of the funds will be burned directly.


    How to create account
----------------------------------
    It is not allowed to create accounts directly. You can only create accounts by transferring funds to non-existing accounts.
    Transfer to a non-existent account with a minimum transfer amount of **1TRX**.

Command line operation flow example
-----------------------------------

    cd wallet-cli
    ./gradlew build
    ./gradlew run
RegisterWallet 123456      (password = 123456)
login 123456
getAddress                 (Print 'address = f286522619d962e6f93235ca27b2cb67a9e5c27b', backup it)
BackupWallet 123456        (Print 'priKey = 22be575f19b9ac6e94c7646a19a4c89e06fe99e2c054bd242c0af2b6282a65e9', backup it) (BackupWallet2Base64 option)
getbalance                 (Print 'Balance = 0')

getbalance

assetIssue 123456 testAssetIssue00001 10000000000000000 1 100 2018-4-1 2018-4-30 1 just-test https://github.com/tronprotocol/wallet-cli/
    getaccount  f286522619d962e6f93235ca27b2cb67a9e5c27b
(Print balance: 9999900000
asset {
    key: "testAssetIssue00001"
    value: 10000000000000000
})
(cost trx 1000 trx for assetIssue)
    (You can query the trx balance and other asset balances for any account )
TransferAsset 123456 649DDB4AB82D558AD6809C7AB2BA43D1D1054B3F testAssetIssue00001 10000


