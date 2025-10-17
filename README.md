# PART 1:: gensyn-setup

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


# PART 2::  SWARM Role & Telegram Bot Setup Guide 🐝

- Get your SWARM role and Telegram bot up and running in no time. This guide walks you through every step, so even if you’re new, you’ll be good to go..  

- Step 1: Run your RL-Swarm Node

Before you can get your SWARM role, make sure your RL-Swarm node is up and running.
Check out the setup PART 1:: ABOVE

---

## Use a screen session to ensure the bot stays online even if you disconnect:

```bash
screen -S swarm-bot
```


## 2 Install Gswarm

```bash
# Install Go:
sudo rm -rf /usr/local/go
curl -L https://go.dev/dl/go1.22.4.linux-amd64.tar.gz | sudo tar -xzf - -C /usr/local
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> $HOME/.bash_profile
source .bash_profile
go version
```
```
go install github.com/Deep-Commit/gswarm/cmd/gswarm@latest
```
## Verify Installation
```
gswarm --version
```


## 3 Telegram Bot Set-Up 🤖


**1️⃣ Create a Telegram Bot**

- Open Telegram and chat with @BotFather
-  Send the command:

```bash
/newbot
```
Follow the instructions:

- Choose a name for your bot
- Choose a username (must end with “bot”)
- Save the bot token provided — you’ll need it later.
- Start a chat with your new bot and send some messages to it

**2. Get Your Chat ID:**

- Open Telegram and search for @chat_id_echo_bot

- Send any message to the bot.

- The bot will reply with your chat ID — save it for later use.


<img width="1290" height="1757" alt="image" src="https://github.com/user-attachments/assets/72a4111c-853d-4e5b-b6d2-c4d75f3b6c06" />
<img width="952" height="360" alt="image" src="https://github.com/user-attachments/assets/2e8deacc-8822-41fc-b67a-b0833890641a" />


## 3 Run Gswarm Bot
```
gswarm
```

Run `gswarm` in your terminal now and follow the prompts to enter your bot token, chat ID, and EOA address

- You'll find EOA address by logging in the https://dashboard.gensyn.ai/

<img width="545" height="358" alt="image" src="https://github.com/user-attachments/assets/2a8b69d1-b61f-4b54-bacc-f4cb837d215a" />




## 4 Linking Discord and Telegram

To link your Discord and Telegram accounts, follow these steps:

1. Get your verification code

Open Discord and go to the #|swarm-link channel

Type:

```bash
/link-telegram
```
You will receive a verification code.

2. Verify the code on Telegram

Open your Telegram bot

Type:

```bash
/verify <code>
```
Replace <code> with the code you received from Discord.

Once verified, your Discord and Telegram accounts are linked, and you’ll earn The Swarm role.

<img width="624" height="378" alt="image" src="https://github.com/user-attachments/assets/b23c1602-5e72-4203-83d3-435f26e6e007" />







**See you in the Swarm! 🚀**


📌 **Follow for updates:** [ALEXSZ](https://twitter.com/alexsz_onchain)  
<img width="760" height="363" alt="Screenshot 2025-10-13 163033" src="https://github.com/user-attachments/assets/06b8fe37-4d6d-48d7-b318-8c5c72e15c08" />


# PART 3::  BLOCK Role

-- First sign up on Hugging Face https://huggingface.co/
-- Create new access Token and save token for further use: https://huggingface.co/settings/tokens
--- ALSO SAVE YOUR Blockassit url: https://huggingface.co/<YOUR_USERNAME_HERE>/blockassist

FOLLOW BELOW VIDEO TO SETUP BLOCK NODE: https://x.com/colonydrops/status/1977382444375359652

### ** CLAIMING ROLES ON DISCORD **
goto the #Link-For-Access channel : https://discord.com/channels/852932483691577395/1397909075685146804

>> Hugging Face
Use the command /verify-huggingface to register your Hugging Face profile

>> The Swarm 
Follow the guideS Above
Return there to get your linking code by running /link-telegram and follow the instructions.
Get the @The Swarm role

>> The Block 
Once you have both of the above roles, go to ⁠︱🐝︱the-swarm
Use the command /verify-block
Register your uploaded BlockAssist model
get your @Block


<img width="353" height="237" alt="image" src="https://github.com/user-attachments/assets/549752e1-dfda-4002-b1c4-757abced8e26" />



