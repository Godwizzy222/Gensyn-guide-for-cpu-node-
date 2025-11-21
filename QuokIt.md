## HOW TO TEST YOUR GPU USING QUOK.IT CLI
<img width="900" height="855" alt="image" src="https://github.com/user-attachments/assets/1195bfba-7dd5-458f-a9c2-c5c280d40359" />

#### Gensyn is patnering with quokit to test GPU CLI. and is on a mission to discover which cloud platforms actually deliver top-tier GPU performance. Rent from Octa, Hyperbolic, Vast, or others? Find out how your provider measures up. If you rent GPUs from clouds like Octa, Hyperbolic, Vast, or others, this is your opportunity to verify that you’re getting the performance you expect.
### STEP 1
#### Register at https://www.quok.it/gensyn fill in your discord username and email and make sure the selected options and click "get early access"
### STEP 2
#### After registering, you'll receive the login details for your account and your 𝐀𝐏𝐈 𝐊𝐄𝐘 (very important) in your email after login, reset your password when prompted to fully access your dashboard.
<img width="900" height="469" alt="image" src="https://github.com/user-attachments/assets/93e3aa63-cf78-4594-b0df-72af6a0e4391" />

### STEP 3
#### I'm testing with my octa GPU for blockassist.
#### Go to your sessions and click on it to reveal the popup modal, then click on "access web ssh" to open the command line screen on a new tab
<img width="861" height="900" alt="image" src="https://github.com/user-attachments/assets/c97592b5-088c-4207-91e4-9b8f1f288171" />

### STEP 4 
####  run the following commands IN ORDER in the command line
```
sudo install -d -m 0755 /etc/apt/keyrings && curl -fsSL https://repo.quok.it/quok.asc | gpg --dearmor | sudo tee /etc/apt/keyrings/quok.gpg >/dev/null && echo 'deb [signed-by=/etc/apt/keyrings/quok.gpg] https://repo.quok.it cross main' | sudo tee /etc/apt/sources.list.d/quok-stable.list >/dev/null && sudo chmod 0644 /etc/apt/keyrings/quok.gpg /etc/apt/sources.list.d/quok-stable.list && sudo apt-get update
sudo apt install quok
quok init
```
#### then input your API KEY (the one sent to your email) when prompted
#### ps: you can also find these commands under the  "get started" tab on your dashboard
<img width="900" height="469" alt="image" src="https://github.com/user-attachments/assets/c9e8c857-bd09-42e9-adb5-63e3e98ee9e9" />

### STEP 5 
#### next you need to install CUDA for the test to work successfully. without CUDA, the test won't work
#### follow these commands IN ORDER to install:
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.0-1_all.deb
```
```
sudo dpkg -i cuda-keyring_1.0-1_all.deb
```
```
 sudo apt-get update
```
```
sudo apt-get install cuda-toolkit-12-6
```
```
export CUDA_HOME=/usr/local/cuda-12.6

```
```
export PATH=$CUDA_HOME/bin:$PATH
```
```
 export LD_LIBRARY_PATH=$CUDA_HOME/lib64:$LD_LIBRARY_PATH
```
```
source ~/.bashrc
```
### STEP 6 
#### Enter the command `quok auditme` to run the analysis on your gpuwhen prompted to enter provider, input "octa" or "octaspace" to begin the testyou can go back to your dashboard on quok to watch the test progress (normally it doesn't take more than 2 mins to complete)so you should see this after completiontheres also a link directing you to your dashboard where you can monitor the progress and resultsif you get an overall grade of B and above you're good, but if you get C, you might need to get another GPU so that you'll get very good results when running your swarm node and also so that your node also won't be crashing all the time
<img width="900" height="173" alt="image" src="https://github.com/user-attachments/assets/2a651847-0b70-4b2e-85ac-b415a8bc62cd" />
