# gensyn-setup

# Gensyn Node  (RL-Swarm)

Easily set up and run your Gensyn RL-Swarm node on any Linux VPS or server — no Docker required.
This guide handles all installs, configs, and secure access via Ngrok.

## 🧠 System Requirements

| Component | Minimum      | Recommended   |
|------------|--------------|---------------|
| **CPU**    | AMD64 or ARM | 4+ cores      |
| **RAM**    | 16GB         | 25GB+         |
| **Storage**| 20GB         | SSD preferred |


## ⚙️ Setup Steps

### 🔧 1. Update System

```bash
apt update && apt upgrade -y
```

### 📦 2. Install Dependencies

```bash
apt install screen curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev -y
```

### 🐍 3. Install Python

```bash
apt install python3 python3-pip python3-venv python3-dev -y
```

### 📱 4. Install Node.js and Yarn

```bash
# Install Node.js
apt update
curl -fsSL https://deb.nodesource.com/setup_22.x | bash -
apt install -y nodejs
node -v

# Install Yarn
npm install -g yarn
yarn -v
```

### 🖥️ 5. Create Screen Session

```bash
screen -S gensyn
```
---

### 🆕 6. **Clone Repository**

```bash
git clone git clone https://github.com/gensyn-ai/rl-swarm
cd rl-swarm
```

## ⚡ 7. Set Up Python Environment and Install vLLM

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install vllm
```

---

## ⚡ 8. Run RL-Swarm

```bash
./run_rl_swarm.sh
```

### 🧩 Next Step

You’ll see something like this:

```bash
Please open http://localhost:3000 in your host browser.
>> Waiting for modal userData.json to be created..
```
<img width="651" height="250" alt="image" src="https://github.com/user-attachments/assets/79a90d90-c8a6-4ea7-89ef-22058ac5d9ef" />


## 🌐 9. Expose Your Localhostt Using Ngrok

## **NGROK INSTALLATION**  

### **AMD64 Machines**  
```bash
wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-amd64.tgz
tar -xvzf ngrok-v3-stable-linux-amd64.tgz
sudo mv ngrok /usr/local/bin/
```  

### **ARM Machines**  
```bash
wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-arm64.tgz
tar -xvzf ngrok-v3-stable-linux-arm64.tgz
sudo mv ngrok /usr/local/bin/
```  


### 2. Configure Ngrok
1. Visit [ngrok.com](https://ngrok.com)
2. Sign up using your email
3. Go to `Your Authtoken` section
4. Click "Show Authtoken" and copy the command
5. On your VPS terminal, paste the authtoken command:
```bash
ngrok config add-authtoken YOUR_TOKEN_HERE
```
6. Start Ngrok tunnel:
```bash
ngrok http 3000
```
7. Use the generated Ngrok URL (e.g., `https://abc123.ngrok.io`) to:
   - Access the Gynsyn page
   - Authorize with your Google account

## 🎯 What's Next?  

If you see `"Hello, [Your Node Name]"`, your node is active!  

✅ **Enjoy running your Swarm Node effortlessly!** 

## 🎯 Quick Commands

```bash
# Start RL-Swarm
cd gensyn-testnet && ./run_rl_swarm.sh

# Reconnect to screen
screen -r gensyn
```

---

**See you in the Swarm! 🚀**


📌 **Follow for updates:** [ALEXSZ](https://twitter.com/alexsz_onchain)  
<img width="760" height="363" alt="Screenshot 2025-10-13 163033" src="https://github.com/user-attachments/assets/06b8fe37-4d6d-48d7-b318-8c5c72e15c08" />


