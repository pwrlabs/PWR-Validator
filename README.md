
### **PWR Chain Validator Node & RPC Node Guide**

### **Validator Node Guide**

**Important Note**: This is the inaugural testnet launch. While we strive for perfection, there might be unforeseen issues. We appreciate all feedback, bug reports, or any other issues reported in our [Discord server](https://discord.gg/DJkcuy9SAg).

#### **Requirements**:
- **CPU**: 1 vCPU
- **Memory**: 1 GB RAM
- **Disk**: 100 GB HDD or higher
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
   wget https://github.com/pwrlabs/PWR-Validator/releases/download/14.0.0/validator.jar
   wget https://github.com/pwrlabs/PWR-Validator/raw/refs/heads/main/config.json
   ```

4. **Run the Node**:

   Replace `<YOUR_SERVER_IP>` with your server's actual IP.
   ```bash
   sudo java --enable-native-access=ALL-UNNAMED -jar validator.jar <YOUR_SERVER_IP>
   ```
   **Note:** V 13.0.0 introduced validator checks before the node starts. Make sure ports 8085 and 8231 are open for TCP and port 7621 is open for UDP.<br>
   **Note:** If port 7621 is open for UDP but the node is saying that it's offline, then just try starting the node over and over agin, because detecting UDP ports can sometimes be hard.<br>

5. **Get Your Address**:
     ```
     curl localhost:8085/address/
     ```

6. **Become a Validator Node**:

   - Initially, your node will synchronize with the blockchain but will not assume validator responsibilities until it possesses staked PWR Coins.
   
   - To obtain sufficient PWR Coins for staking, [apply to become a testnet validator on our Discord server](https://discord.gg/DJkcuy9SAg). Once approved, you can use our discord bot to claim 100k PWR to stake.
   
   - After claiming your coins, your node will initiate a transaction to enlist as a validator.

7. **Running in the Background**:

    If you wish to run the node in the background, ensuring it remains active after closing the terminal, utilize the `nohup` command:
    ```bash
    nohup sudo java --enable-native-access=ALL-UNNAMED -jar validator.jar <YOUR_SERVER_IP> --loop-udp-test &
    ```
    
Congratulations, you've now set up and run a PWR Chain validator node!

