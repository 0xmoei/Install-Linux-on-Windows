# Install Linux Ubuntu on Windows using WSL

> Certain tasks, such as `Contribute Ceremony` or `Contract Deployments`, sometimes don't require a cloud server (VPS). Instead, installing a Linux distribution like Ubuntu on Windows can be sufficient
>
> In this Guide, I'll tell you how to Install Linux (Ubuntu distribution) on Windows using WSL

## Step 1: Enable WSL

1. Opening Windows Powershell Terminal
![Screenshot_357](https://github.com/user-attachments/assets/42e29c7f-9021-433c-87c4-2f76189b1322)

2. Run the WSL Installation Command:
```
wsl --install
```
* It may ask you to choose a username and password

3. Restart Your Computer:
  
After the installation completes, you may need to restart your computer

## Step 2: Install Ubuntu

1. Open Microsoft Store:

After restarting, open the Microsoft Store from the Start menu.

2. Search for Ubuntu:

In the Store, type "Ubuntu" in the search bar. You’ll see various versions like Ubuntu 20.04 LTS, Ubuntu 22.04 LTS, etc

3. Select and Install:

Click on the version you want to install, then click the Get or Install button

## Step 3: Set Up Ubuntu
1. Launch Ubuntu:

* Once installed, you can launch it directly from the Microsoft Store or by searching for "Ubuntu" in the Start menu
* The first time you launch Ubuntu, it will take a moment to set up. After that, you will be prompted to create a new `user` account and password

### Step 4: Install and Update Packages (aka Drivers)
1. Update and Upgrade default Packages
```
sudo apt update

sudo apt upgrade
```

2. Install more important packages
```
sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```

3. Install Docker
```docker
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Docker version
docker --version
```
***Optional: To install more packages you can check my recent [Linux guide](https://github.com/0xmoei/Linux_Node_Guide/blob/main/linux-config.md)***

#

## Optional: Change user
There are 2 ways to login to ubuntu: 1. You are `root` (administrator with full permissions), or 2. you are an specific `user` with specific permissions

You see by entering `whoami`, I am logged in as user:mirana

![image](https://github.com/user-attachments/assets/f91fd950-9752-430e-90e1-a7759121d928)


If you want to login with root (full permissions):
```
sudo su
```
![image](https://github.com/user-attachments/assets/2fc310f7-c507-41ac-b116-69ca7d3aa677)


* Now you see I am as `root` user, but in `mirana` user **main** directory
* I need to type `cd` to move to the **main** directory of `root`

***To login to a specific user again, Enter this command:*** `su - username`

#

## Access Ubuntu directories in Windows explorer
To go to your Ubuntu directory using Windows explorer, Enter this in Windows Explorer Addressbar
```
\\wsl$
```

* `home`: main directory of your specific user
* `root`: main directory of your `root` user
![image](https://github.com/user-attachments/assets/87f1fef0-ec1d-4de5-a40e-89a990600c4e)


***If you don't have access to root directory,  Enter this command in terminal*** `sudo chmod 755 /root`






