##Local Wallet Setup

Before you begin installing the MNs onto a single VPS, you will need to setup the MN transaction (tx's) in the local wallet to get a unique masternode private key (the result from the `genkey` command) and a unique `tx id` and `index` (the results from the outputs command).  The following steps should be taken in order for each MN you intend to run before setting up the MN wallets on the VPS.  Commands should be entered into the LOCAL wallet debug console where you plan to keep the 1000 coins required for each MN to operate.

This generates a private key for your masternode.  Make a note of it and keep the information for each MN together.
`masternode genkey`

Make a note of this address and keep it with the `genkey` you just made.  You can also choose any name you wish for your MN, just replace `MN01` with the desired name.
`getaccountaddress MN01`

Now, send EXACTLY 1000 XUEZ to the address you just made in step 2.  Do not attempt to add in fees, just send 1000 exactly to that address.  Wait for 15 confirmations.

First, wait for at least 15 confirmations of the send in your local wallet.  Then enter this command into the debug console.
`masternode outputs`
This will give you 2 important outputs.  The long number is the `tx id` associated with sending the 1000 xuez and the last number by itself (usually 1 or 0) is the `masternode index number`.  

Make a note of these and match them up with the private key and address you just made.  

The private key and outputs must match in the local `masternode.conf` and VPS `xuez.conf` files.

Now open the local `masternode.conf` file.  You can either open it by going into the local xuez wallet and selecting `TOOLS -> Open Masternode Configuration File` or you can navigate to your local xuez wallet folder and open masternode.conf manually.  (For MAC users this is in your hidden library folder)  You will need to enter a single string (all on one line with each item separated by one 1 space) that contains the items seen in the box above.  There should also be an example in the `masternode.conf` itself showing what a proper setup looks like.
`<MN01> VPSipORtor:41798 <MASTERNODE_GENKEY><TXID> <MN_INDEX#>`
Replace MN01 with the name you gave the wallet address in step 2.  Replace the “VPSipORtor” value with the IP address of the VPS where you plan to run the masternode.  If you plan to utilize TOR, we will replace that with the TOR address when we setup the MN on the VPS
