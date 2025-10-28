##  > RL-SWARM NODE DETAILED GUIDE FOR MAC AND CPU 
<img width="1697" height="549" alt="Screenshot 2025-10-28 143217" src="https://github.com/user-attachments/assets/8dcdd1cf-cd9c-441f-8c57-479875db6835" />

### This guide is to help users set up their RL-SWARM node using cpu(ununtu) and macOS


## Requirements;
##### arm64 or x86 cpu with min 16gb ram 
##### 8cores cpu
##### min 600gbssd storage 
##### huggingface token, get it from https://huggingface.co/ create an account and create access token with write and save it 
##### if you're running on vps then rent from contabo or https://my.hostbrr.com/order/forms/

##### PS: some softwares dosen't requires `sudo` cmd so always confirm


### 1 Update system packages 
```bash
sudo apt update && sudo apt upgrade -y
```
### 2 Install essential tools 
```
sudo apt install screen curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```
### 3 Install python
```
sudo apt install python3 python3-pip python3-venv python3-dev -y
```
### 4 Install Node 
```
sudo apt update
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo bash -
sudo apt install -y nodejs
node -v
npm install -g yarn
yarn -v
```
### 5 Install yarn 
#### for ubuntu 
```
sudo apt install -y yarn
```
##### verify
```
yarn --version
```
#### for macOS 
```
npm install -g corepack && corepack enable
corepack prepare yarn@stable --activate
yarn --version
```
### 6 Install Docker
#### for ubuntu
```console
# install required dependencies
sudo apt install ca-certificates curl gnupg lsb-release -y

# Add Docker’s official GPG key
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Set up Docker repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker Engine
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

# Start and enable Docker
sudo systemctl start docker
sudo systemctl enable docker

# Verify installation
docker --version

# You should see something like:
# Docker version 27.0.3, build xxxxxxx

```
#### For mac users, download the docker desktop (https://www.docker.com/products/docker-desktop/ incase you haven't downloaded it yet) and verify docker on your terminal using
```
docker --version
```
### 7 Clone the Gensyn Repository
```
git clone https://github.com/gensyn-ai/rl-swarm/
```
### 8 Run the swarm 
##### > create a screen 
```
screen -S swarm
```
### 9 Clone into the `swarm` directory 
```
cd rl-swarm
```
### 10 Install swarm 
```
docker compose run --rm --build -Pit swarm-cpu
```
### 11 Install cloudfared and login 
## Duplicate tab(open a new terminal) and run cloudfared so you can gen login website 
##### for ubuntu/linux vps on the dupicated tab
```
sudo apt update && sudo apt install -y wget
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
```
##### for macOS on the duplicated tab
```
brew install cloudflared
```
##### verify cloudfared 
```
cloudflared --version
```
### Login 
##### After installing and verifying on the duplicated tab run
```
cloudflared tunnel --url http://localhost:3000
```
#### Go to the web in the box just like shown in the image below and copy the link and load in your browser 
<img width="1122" height="189" alt="Screenshot 2025-10-28 140639" src="https://github.com/user-attachments/assets/1d62c1b0-1bd2-488d-88d9-679530db7641" />
input your email and login then go back to the previous tab on your terminal then wait for it to load and ask some questions which have the following answers

 > `Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N]` = press `N` and enter

> `Enter the name of the model you want to use in huggingface repo/name format, or press [Enter] to use the default model` 

 Join Judge 
 
 to participate on Ai predictions and place bets you wil be asked 
 > `Would you like to participate in the AI Prediction Market? (Y/n)` = Press `Y` and enter 
 you'll see welcome to Gensyn testnet. Good luck 
 You can now close screen with `Ctrl+A+D` and you're done!
