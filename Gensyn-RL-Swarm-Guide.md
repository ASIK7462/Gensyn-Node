# 🚀 GENSYN RL-SWARM 0.5.1 — Step-by-Step Setup Guide

A simple and clean guide to install and run a Gensyn RL-Swarm node on your Ubuntu VPS (22.04+).  
Includes system setup, model selection, and tunnel access via Cloudflare.

---

## ✅ Prerequisites

- A fresh Ubuntu VPS (recommended 22.04 or later)
- 32GB RAM
- 250 GB SSD

---

## 🧩 1. Update System & Install Dependencies

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl wget git screen build-essential python3 python3-pip python3-venv ufw
```

---

## 📦 2. Install Node.js, npm & Yarn

```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
npm install -g yarn
```

---

## 🖥️ 3. Create Gensyn Screen Session

```bash
screen -S gensyn
```

---

## 🔗 4. Clone the RL-Swarm Repository

```bash
git clone https://github.com/gensyn-ai/rl-swarm
cd rl-swarm
```

> ⚠️ **Note:** Import your `.pem` file here if required.

---

## 🧪 5. Set Up Python Virtual Environment & Run

```bash
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
```

- Select a model based on your system specs  
- Or simply press `Enter` to continue with the **default model**

---

## 🔐 6. Open New VPS Tab & Configure UFW Firewall

```bash
sudo apt install ufw -y
sudo ufw allow 22
sudo ufw allow 3000/tcp
sudo ufw --force enable
```

---

## 🌐 7. Install & Setup Cloudflare Tunnel

```bash
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
```

Once installed, run the tunnel:

```bash
cloudflared tunnel --url http://localhost:3000
```

> 🌍 This will generate a public link — use it to access your dashboard.

---

## 📌 Notes

- Detach from any screen session with: `Ctrl + A`, then `D`
- To reattach a screen: `screen -r gensyn`
- Official Repo: [Gensyn RL-Swarm](https://github.com/gensyn-ai/rl-swarm)

---

## ✅ Done!

You're now running Gensyn RL-Swarm 0.5.1 with full tunnel access.  
Happy Swarming! 🧠⚙️
