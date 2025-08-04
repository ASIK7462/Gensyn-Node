# 🚀 GENSYN RL-SWARM — CLEAN INSTALLATION & SETUP GUIDE (0.5.1)

## 🔄 Step 1: Clean Up Old Setup

```bash
cd ~
sudo apt update
sudo apt remove --purge nodejs npm -y 2>/dev/null
sudo apt autoremove -y
rm -rf rl-swarm gensyn-testnet .nvm .npm .ngrok*
```

---

## 📦 Step 2: System Update

```bash
sudo apt update && sudo apt upgrade -y
```

---

## 🖥️ Step 3: Start a Screen Session

```bash
screen -S gensyn
```

---

## 🔁 Step 4: Clone the Repository

```bash
git clone https://github.com/gensyn-ai/rl-swarm
cd rl-swarm
```

---

## 🔐 Step 5: Import Your `.pem` File

*(Make sure your PEM file is placed in the correct directory as needed)*

---

## 🧪 Step 6: Create and Activate Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
```

---

## 🌐 Step 7: Open a New Tab & Set Up Tunnel Access

```bash
sudo apt install ufw -y
sudo ufw allow 22
sudo ufw allow 3000/tcp
sudo ufw --force enable

wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb

cloudflared tunnel --url http://localhost:3000
```

---

## ⚠️ [Optional] Crash Fix — Node Keeps Crashing?

If your node is crashing, run the following command to increase the timeout:

```bash
pip install --force-reinstall transformers==4.51.3 trl==0.19.1
pip freeze
bash run_rl_swarm.sh
```

---

## 📢 Stay Connected

- 🔗 **Follow me for more**: [https://x.com/AR74622](https://x.com/AR74622)  
- 🤖 **Telegram Bot (Reward Updates)**: [@GensynReward_Bot](https://t.me/GensynReward_Bot)  
- 📊 **Official Dashboard**: [https://dashboard.gensyn.ai/](https://dashboard.gensyn.ai/)
