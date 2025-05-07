# Gensyn Node (RL-SWARM) - Complete Setup Guide

This guide helps you run a Gensyn RL-SWARM node on your VPS or local machine.

---

## **Step 1: Install Python and Essential Tools**
```bash
# Update system and install tools
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof

# Check Python version
python3 --version
```

---

## **Step 2: Install Node.js, npm, and Yarn**
```bash
# Install Node.js v20.x
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt update && sudo apt install -y nodejs

# Install Yarn
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list > /dev/null
sudo apt update && sudo apt install -y yarn

# Check versions
node -v
npm -v
yarn -v
```

---

## **Step 3: Clone RL-SWARM Repo and Set Up Environment**
```bash
# Clone the repository
git clone https://github.com/gensyn-ai/rl-swarm.git

# Enter the repo
cd rl-swarm

# Create and activate Python virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Go to modal-login folder
cd modal-login

# Install dependencies
yarn install
yarn upgrade
yarn add next@latest viem@latest
```

---

## **Step 4: Start a Screen Session (Optional for VPS)**
```bash
# Start screen session to keep process running
screen -S gensyn
```

---

## **Step 5: Pull the Latest Release**
```bash
# If no local changes:
git pull

# If you made changes:
git reset --hard HEAD
git pull
```

---

## **Step 6: Run the Swarm Node**
```bash
# Navigate to the root folder
cd ..

# Run the node script
./run_rl_swarm.sh
```

---

## **(Optional) Expose Localhost using Ngrok**
```bash
# Download and install Ngrok
wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-amd64.tgz
tar -xvzf ngrok-v3-stable-linux-amd64.tgz
sudo mv ngrok /usr/local/bin/

# Start ngrok on port 3000
ngrok http 3000
```

---

## **Tips**
- Use `screen -r gensyn` to reattach your screen session.
- Use `Ctrl+A + D` to detach from the screen without stopping the process.
