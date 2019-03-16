BTK Masternode Setup Guide
==========================

## Introduction

This guide is for a single masternode, on a Ubuntu 18.04 64-bit server (VPS) running headless and will be controlled from the wallet on your local computer (Control wallet). The wallet on the the VPS will be referred to as the Remote wallet.

You will need your server details for progressing through this guide including the public IP address.

First the basic requirements:

1. 20,000,000 BTK
1. A main computer (your everyday computer) – This will run the control wallet, hold your collateral 20,000,000 BTK and can be turned on and off without affecting the masternode.
1. Masternode Server (VPS – The computer that will be on 24/7).
1. A unique IP address for your VPS / Remote wallet.

For security reasons, you’re are going to need a different IP for each masternode you plan to host.

## Configuration

Note: The auto zBTK minter should be disabled during this setup to prevent autominting of your masternode collateral. BEFORE unlocking your wallet, you can disable auto-minting in the control wallet option menu.

**Step 1:** Using the control wallet, enter the debug console (Tools > Debug console) and type the following command:

```
masternode genkey (This will be the masternode’s privkey. We’ll use this later…)
```

**Step 2:** Using the control wallet still, enter the following command:

```
getaccountaddress chooseAnyNameForYourMasternode
```

**Step 3:** Still in the control wallet, send 20,000,000 BTK to the address you generated in step 2. (Be 100% sure that you entered the address correctly. You can verify this when you paste the address into the **“Pay To:”** field, the label will auto populate with the name you chose”, also make sure this is exactly 20,000,000 BTK; No less, no more.)

**Be absolutely 100% sure that send to address is copied correctly and then check it again. We cannot help you, if you send 20,000,000 BTK to an incorrect address.**

**Step 4:** Still in the control wallet, enter the command into the console:

```
masternode outputs
```

*This gets the proof of transaction of sending 20,000,000 BTK*

**Step 5:** Still on the main computer, go into the BTK data directory:

OS | Path to BTK
------------ | -------------
Windows | `%Appdata%/BTK/`
macOS | `~/Library/Application\ Support/BTK/`
Linux | `~/.btk/`

Find masternode.conf and add the following line to it:
```
<Name of Masternode(Use the name you entered earlier for simplicity)> <Unique VPS Public IP address>:61472 <The result of Step 1> <Result of Step 4> <The number after the long line in Step 4>
```

Example:
```
MN1 31.14.135.27:61472 892WPpkqbr7sr6Si4fdsfssjjapuFzAXwETCrpPJubnrmU6aKzh c8f4965ea57a68d0e6dd384324dfd28cfbe0c801015b973e7331db8ce018716999 1
```

Substitute it with your own values and without the “<>”s.

## VPS Remote Wallet Install

Install the latest version of the BTK wallet onto your masternode. The latest version can be found here: [BTK Releases](https://github.com/bitcoin-token/Bitcoin-Turbo-Koin-Core/releases).

**Step 1:** Log in to your VPS:

```
cd ~
```

**Step 2:** From your home directory, download the latest version from the BTK GitHub repository:

```
wget https://github.com/bitcoin-token/Bitcoin-Turbo-Koin-Core/releases/download/v1.0.0/btk-x86_64-linux-gnu.tar.gz
```