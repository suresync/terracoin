# ![Terracoin](logo.png) Terracoin Guide

Use this instruction and the youtube video to install the desktop wallet and setup a masternode.
This guide is for the creation of separate Controller Wallet & Masternode.
For Security reasons, THIS IS THE PREFERRED way to run a Masternode. By running your Masternode in this way you are protecting
your coins in your private wallet, and are not required to have your local wallet running after the Masternode has been started successfully.
Your coins will be safe if the masternode server is hacked.

## Table of Content
* [1. Desktop Wallet Preparation](#1-desktop-wallet-preparation-)
	* [1.1 Setting up desktop wallet](#11-setting-up-desktop-wallet)
* [2. Masternode Setup](#2-masternode-setup-)
	* [2.1 Send the coins to your wallet](#21-send-the-coins-to-your-wallet)
	* [2.2 VPS setup](#22-vps-setup)
	* [2.3 Automatic Masternode Setup](#23-automatic-masternode-setup)
	* [2.4 Add masternode on the desktop wallet](#24-add-masternode-on-the-desktop-wallet)
* [3. FAQ](#3-faq)
* [4. The last and the most important step](#4-support)

## Announcement!!
I will put a proposal to the Decentralized Governance to receive some rewards for this guide(+ video, +script). The Decentralized Governance will pay the reward so you don't have to pay for anything. So if you found this guide helpful please run the following command (before end of the month but after the hardfork) on your masternode(s) to accept my proposal.

```NOT READY YET```

Thank you!

## 1. Desktop Wallet Preparation <a href="https://www.youtube.com/watch?v=HAF1NPFsb8Q" target="_blank"><img src="https://i.imgur.com/SY3eO38.png"></a>

### 1.1 Setting up desktop wallet
1. Download wallet. [win-x64](https://github.com/terracoin/terracoin/releases/download/v0.12.1.5/terracoin-qt.exe), [win-x32](https://github.com/terracoin/terracoin/releases/download/v0.12.1.5-32bit/terracoin-qt.exe), [linux-x64](https://github.com/terracoin/terracoin/releases/download/0.12.1.5/terracoin-qt), [github](https://github.com/terracoin/terracoin/releases), [terracoin.io](http://www.terracoin.io/)
1. Start the wallet and select the default data directory. After close the wallet.
1. Optionally download [blockchain.rar](https://transfer.sh/sHxsj/blockchain.rar), [mirror1](https://mega.nz/#!AqZXyCBI!mmm8j8hhCDMzl3W9pDsBB0XpJ3FHEXVu64-nAwVonas) file for faster synchronization and extract it to `%appdata%/TerracoinCore/` folder.
1. Start the wallet again and wait for the sync. (10min to 1h)
	
## 2. Masternode Setup <a href="https://www.youtube.com/watch?v=-Yy3iZsuBK4" target="_blank"><img src="https://i.imgur.com/SY3eO38.png"></a>

### 2.1 Send the coins to your wallet
1. Create and copy a new receiving address. (File => Receiving adresess => New)
1. Send exactly 5000 coins to this address. (One transaction, pay attention to the fee)
1. Wait for the conformation.
1. Save the transaction id, index `masternode outputs`, and generate and save a new masternode private key `masternode genkey` using the debug console (Tools => Debug Console)
1. You can optionaly encrypt the wallet (Settings => Encypt wallet) for security reasons. Do not forget the password or you lose the coins that you have.
1. Backup `%appdata%/TerracoinCore/wallet.dat` file. This contains your coins. DO NOT LOSE IT!

### 2.2 VPS setup
1. Register on [vultr](https://www.vultr.com/?ref=7205683). (or optionaly [DigitalOcean](https://m.do.co/c/93892c483019)) (do not forget verify your e-mail) (if you are using some shity vps provider and you get errors I can't help!)
1. Send some money (10$ is enough for two months) to your account to deploy a server. (1 server cost 5$/mo, you can pay with bitcoin on vultr)
1. Deploy a new server.
    - Server Type: Ubuntu 16.04
    - Server Size: 5$/mo, 1GB memory

### 2.3 Automatic Masternode Setup
1. Download [putty](https://the.earth.li/~sgtatham/putty/latest/w64/putty-64bit-0.70-installer.msi)
1. Start putty and login as root user. (Root password and server ip address is in vultr overview tab)
1. Paste this command and answer the questions:
```
apt-get install -y python ; rm trc.py; wget https://raw.githubusercontent.com/suresync/terracoin/master/trc.py && python trc.py
```

### 2.4 Add masternode on the desktop wallet
1. Open `%appdata%/TerracoinCore/masternode.conf` and add a new line to it. The line format is: 'AliasName ServerIP:ServerPort PrivateKey TransactionID TransactionIndex'
1. Open wallet, wait for sync, unlock wallet
1. Go Masternodes tab (Setting => Options => Wallet => Show Masternode Tab)
1. Click Start All
1. Wait around 1 hour to start receiving coins. Check your the masternode address here: [explorer](https://bchain.info/TRC/) or use your wallet.

## 3. FAQ

1. What if I restart the server?
	- The script setup a cron job so the masternode automaticly starts every time when the vps turns on.
1. How to get masternode profit?
	- Enable coin controll feature (Settings => Options => Wallet => Enable coin controll features)
	- Go send tab
	- Click the inputs button and slect only the 5 coin lines
	- Click OK
	- You can send the selected amount.
	- Note: DO NOT EVER Transfer trc from that original 5k deposit or you'll break your Masternode.
1. What is the password for the mn1 accounts?
	- There is no default password. When you create a user it does not have a password yet, so you cannot login with that username until you create a password. There is one other way to act as a new user without its password. As root type `su - mn1`
	- You need to set a password for the user. Use the passwd command: `passwd mn1`
1. I get the following error: "Could not allocate vin"
	- Make sure your wallet fully synced and UNLOCKED.
	- Make sure the masternode adress contains exactly 5000 coins.
1. How many masternodes can I run using one IP/server?
	- You can only use one masternode per ip address.
1. I got stuck. Can you help me?
	- First of all try to get help from the [community](http://terracoin.io/community.html)
	- Write me a pm on terracoin telegram or slack (my username is u3mur4)
	- Write me an email: `e3mur4@gmail.com`

# 4. Support

### Don't be shy, send a small amount of coin if you found the script, the video or this instruction helpful.

| Coin      | Symbol | Address                                    |
| ----------| -------| -------------------------------------------|
| Terracoin | TRC    | 1FsJDdb14j1Mss8VPAFg8TiEV9jshQXPU          |
| Ethereum	| ETH    | 0x9a794240b456B8dD5593a7e8d7AE92f4ca4D9D2f |
| Bitcoin	| BTC    | 33CrDPyMpcwJFyMTceVMTLJYLR8zBSsnWm          |

	
