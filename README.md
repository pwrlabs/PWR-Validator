
### **PWR Chain Validator Node & RPC Node Guide**

### **Validator Node Guide**

**Important Note**: This is the inaugural testnet launch. While we strive for perfection, there might be unforeseen issues. We appreciate all feedback, bug reports, or any other issues reported in our [Discord server](https://discord.gg/DJkcuy9SAg).

#### **Requirements**:
- **CPU**: 2 vCPU
- **Memory**: 2 GB RAM
- **Disk**: 100 GB HDD or higher
- **Open TCP Ports**: 8231, 8085

#### **Setup on Ubuntu Server**:

1. **Update OS**: 
   ```bash
   sudo apt update
   ```

2. **Install Java**: 
   ```bash
   sudo apt install default-jdk
   ```

3. **Open Required Ports**:
   For UFW (Uncomplicated Firewall)
      ```bash
   sudo ufw allow 8231/tcp
   sudo ufw allow 8085/tcp
   sudo ufw reload
      ```
      
   For iptables
      ```bash
   sudo iptables -A INPUT -p tcp --dport 8231 -j ACCEPT
   sudo iptables -A INPUT -p tcp --dport 8085 -j ACCEPT
   sudo netfilter-persistent save
   ```
   Note: If you're using a cloud provider, you may also need to configure the ports in their firewall/security group settings.


5. **Install the validator node software and config file**:
   ```bash
   wget https://github.com/pwrlabs/PWR-Validator/releases/download/15.19.0/validator.jar
   wget https://github.com/pwrlabs/PWR-Validator/raw/refs/heads/main/config.json
   ```

6. **Setup your password**:
   ```bash
   echo "your password here" > password 
   ```

7. **Run the Node**:

   Replace `<YOUR_SERVER_IP>` with your server's actual IP.
   ```bash
   nohup sudo java --enable-native-access=ALL-UNNAMED -jar validator.jar --ip <your nodes ip here> --password password & 
   ```
   **Note:** Make sure ports 8085 and 8231 are open for TCP.

8. **Get Your Address**:
     ```
     java -jar validator.jar get-address password
     ```

9. **Become a Validator Node**:

   - Initially, your node will synchronize with the blockchain but will not assume validator responsibilities until it possesses staked PWR Coins.
   
   - To obtain sufficient PWR Coins for staking, [apply to become a testnet validator on our Discord server](https://discord.gg/DJkcuy9SAg). Once approved, you can use our discord bot to claim 100k PWR to stake.
   
   - After claiming your coins, your node will initiate a transaction to enlist as a validator.

10. **Checking your nodes log**:

    If you wish to check your nodes log, you can do so using the following command:
    ```bash
    tail -n 1000 nohup.out -f 
    ```
    
Congratulations, you've now set up and run a PWR Chain validator node!

