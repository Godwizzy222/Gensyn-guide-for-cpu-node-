##  > RL-SWARM NODE DETAILED GUIDE FOR MAC AND CPU 
### This guide is to help users set up their RL-SWARM node using cpu especially those renting vps


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
##### create a screen 
```
screen -S swarm
```
##### 9 Clone into the `swarm` directory 
```
cd rl-swarm
```
##### 10 Install swarm 
```
docker compose run --rm --build -Pit swarm-cpu
```
##### 11 Login 
##### Duplicate to open a new tab/terminal
