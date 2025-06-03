# ✅ Gensyn Node Setup Guide (Google Cloud VPS)

> **Important for Existing Users:**  
> 🔐 *Ensure you have backed up your `.pem` file before proceeding.*

---

## 🧹 Optional: Clean Previous Installations

```bash
cd ~
sudo apt update
sudo apt remove --purge nodejs npm -y 2>/dev/null
sudo apt autoremove -y
rm -rf rl-swarm gensyn-testnet .nvm .npm .ngrok*
```

---

## 🆕 New User Setup Instructions

### 1️⃣ Run the Setup Script

```bash
curl https://raw.githubusercontent.com/imysryasir/Gsnyn-1-Click-Solutions/refs/heads/main/gensyn_setup.sh | bash
```

---

### 2️⃣ Navigate to `rl-swarm` and Checkout Required Version

```bash
cd rl-swarm
git reset --hard
git pull origin main
git checkout tags/v0.4.3
```

---

### 3️⃣ Import Your `.pem` File

Transfer your existing `.pem` file into the `rl-swarm` directory using **SFTP** (e.g., via **Termius**) or your preferred method.

---

### 4️⃣ Start a Screen Session

```bash
screen -S gensyn
```

---

### 5️⃣ Navigate to Project Directory

```bash
cd $HOME/rl-swarm/
```

---

### 6️⃣ Fix Gensyn Script (Run **Twice**)

```bash
curl https://raw.githubusercontent.com/imysryasir/Gsnyn-1-Click-Solutions/refs/heads/main/fixgensyn.sh | bash
# Run again
curl https://raw.githubusercontent.com/imysryasir/Gsnyn-1-Click-Solutions/refs/heads/main/fixgensyn.sh | bash
```

---

### 7️⃣ Activate Virtual Environment and Start Node

```bash
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
```

- **Select Option:** `MATH-A`  
- **Input Value:** `0.5`

---

## 🔐 Login Instructions (IMPORTANT)

Open a **new terminal tab/session**, then run:

```cloudflared tunnel --url http://localhost:3000
```

Use the generated link in your browser to log in with **Gmail** and complete **OTP verification**.

---

## ❌ If Your Node Terminates Automatically

Apply this fix **twice**:

```bash
sed -i -r 's|(dht = hivemind.DHT\(start=True, startup_timeout=30, *)(.*)|\1ensure_bootstrap_success=False, \2|' ~/rl-swarm/hivemind_exp/runner/grpo_runner.py
```

---

## ✅ You're Done!

After approximately **1–2 hours**, you’ll see an option on screen:  
**Enter `3` and press Enter** to finalize the setup.

🎉 Your Gensyn node should now be running **smoothly** and participating in the network!

---

## 📢 Stay Connected

- **Twitter (X):** [@AR74622](https://x.com/AR74622)  
- **Reward Check Bot (Telegram):** [@Gensyn_track_bot](https://t.me/Gensyn_track_bot)
