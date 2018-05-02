# CheckCash
Shell script to install a [CheckCash Masternode](http://checkcash.info/) on a Linux server running Ubuntu 16.04. Use it on your own risk.
***

## Installation
```
wget -q https://raw.githubusercontent.com/CheckCash/mn-install/master/mn_install.sh
bash mn_install.sh
```
***

## Desktop wallet setup  

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps:  
1. Open the CheckCash Desktop Wallet.  
2. Go to RECEIVE and create a New Address: **MN1**  
3. Send **1000** CKH to **MN1**. You need to send all 1000 coins in one single transaction.
4. Wait for 15 confirmations.  
5. Go to **Help -> "Debug Window - Console"**  
6. Type the following command: **masternode outputs**
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is un
12. Select your MN and click **Start Alias** to start it.
13. Alternatively, open **Debug Console** and type:
```
masternode start-alias "MN1"
```
14. Login to your VPS and check your masternode status by running the following command:.
```
checkcash-cli masternode status
```
***

## Usage:
```
checkcash-cli mnsync status
checkcash-cli masternode status  
checkcash-cli getinfo
```
Also, if you checkcash to check/start/stop **CheckCash**, run one of the following commands as **root**:

```
systemctl status CheckCash #To check if CheckCash service is running  
systemctl start CheckCash #To start CheckCash service  
systemctl stop CheckCash #To stop CheckCash service  
systemctl is-enabled CheckCash #To check if CheckCash service is enabled on boot  
```  
***
