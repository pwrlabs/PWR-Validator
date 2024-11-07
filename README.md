
### **PWR Chain Validator Node & RPC Node Guide**

### **Validator Node Guide**

**Important Note**: This is the inaugural testnet launch. While we strive for perfection, there might be unforeseen issues. We appreciate all feedback, bug reports, or any other issues reported in our [Discord server](https://discord.gg/DJkcuy9SAg).

#### **Requirements**:
- **CPU**: 1 vCPU
- **Memory**: 1 GB RAM
- **Disk**: 50 GB HDD or higher
- **Open TCP Ports**: 8231, 8085
- **Open UDP Port**: 7621

#### **Setup on Ubuntu Server**:

1. **Update OS**: 
   ```bash
   sudo apt update
   ```

2. **Install Java**: 
   ```bash
   sudo apt install default-jdk
   ```

3. **Install the validator node software and config file**:
   ```bash
   wget https://github.com/pwrlabs/PWR-Validator/releases/download/13.2.1/validator.jar
   wget https://github.com/pwrlabs/PWR-Validator/raw/refs/heads/main/config.json
   ```

4. **Set Up your Password**:
   ```bash
   sudo nano password
   ```
   - Enter your desired password.
   - Press `Ctrl + x` to close.
   - Press `Y` to confirm saving the password.
  
5. **Import Your Validator**:

   If you have a private key you want to import then use this command, otherwise skip to the next step.
   ```bash
   sudo java -jar validator.jar --import-key <private key here> password
   ```

6. **Run the Node**:

   Replace `<YOUR_SERVER_IP>` with your server's actual IP.
   ```bash
   sudo java -jar validator.jar password <YOUR_SERVER_IP> --compression-level 0
   ```
   **Note:** V 13.0.0 introduced validator checks before the node starts. Make sure ports 8085 and 8231 are open for TCP and port 7621 is open for UDP.<br>
   **Note:** If port 7621 is open for UDP but the node is saying that it's offline, then just try starting the node over and over agin, because detecting UDP ports can sometimes be hard.<br>
   PWR Chain is the first chain that supports block compression.
   --compression-level sets the level of compression you want your node to use.
   Compression level varies from 0 - 9. 0 disables compression. 9 sets it to maximum.

8. **Get Your Address**:
     ```
     curl localhost:8085/address/
     ```

9. **Become a Validator Node**:

   - Initially, your node will synchronize with the blockchain but will not assume validator responsibilities until it possesses staked PWR Coins.
   
   - To obtain sufficient PWR Coins for staking, [apply to become a testnet validator on our Discord server](https://discord.gg/DJkcuy9SAg). Once approved, you can use our discord bot to claim 100k PWR to stake.
   
   - After claiming your coins, your node will initiate a transaction to enlist as a validator.

10. **Running in the Background**:

    If you wish to run the node in the background, ensuring it remains active after closing the terminal, utilize the `nohup` command:
    ```bash
    nohup sudo java -jar validator.jar password <YOUR_SERVER_IP> --loop-udp-test &
    ```

11. **Getting Your Private Key**:
    ```bash
    nohup sudo java -jar validator.jar get-private-key password
    ```
    A hex string priate key will be returned. This key can be used in the [PWR Browser Wallet](https://chromewebstore.google.com/u/3/detail/pwr-wallet/kennjipeijpeengjlogfdjkiiadhbmjl) 

Congratulations, you've now set up and run a PWR Chain validator node!

