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
