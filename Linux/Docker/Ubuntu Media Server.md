# Ubuntu Media Server Setup

## Installing Ubuntu Server Notes:
- Mount `/home` on a different partition, not the same partition as root directory `/` to easily restore data if the system fails at any point in the future.

## Pre-installation Steps:
### 1- Laptop Lid
If you are using a laptop make sure to enable close lid and screen without putting laptop into sleep by editing `/etc/systemd/logind.conf` and uncomment `HandleSuspendKey`, `HandleLidSwitch` and `HandleLidSwitchDocked` and assign them to `ignore`
```bash
HandleSuspendKey=ignore
HandleLidSwitch=ignore
HandleLidSwitchDocked=ignore
```
then run the following command to restart `systemd`
```bash
sudo systemctl restart systemd-logind
```

### 2- Install monitoring services
- #### Install Neofetch and run it at startup
1. Install neofetch from `apt`:
```bash
sudo apt install neofetch
```
2. Disable all current default MOTD’s daemon scripts:
```bash
sudo chmod -x /etc/update-motd.d/*
```
3. Create a new script, eg. `/etc/update-motd.d/01-custom` with the following [bash script](https://linuxconfig.org/bash-scripting-tutorial-for-beginners):
```bash
#!/bin/sh
echo "GENERAL SYSTEM INFORMATION"
# Show system info using neofetch
neofetch
```
4. Make this script executable
```bash
sudo chmod +x /etc/update-motd.d/01-custom
```
- #### Install `htop` with `libsensors` to monitor the server resources
1. Install services:
```bash
sudo apt install htop libsensors-dev
```
2. Show CPU tempreature by running `htop` command then pressing `F2` to enter the setup, go to `Display options` the activate `Also show CPU tempreature`

### 3- Install Docker ([docs](https://docs.docker.com/engine/install/ubuntu/))
- #### Set up the repository
1. Update the `apt` package index and install packages to allow `apt` to use a repository over HTTPS:
```bash
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
```
2. Add Docker’s official GPG key:
```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
3. Use the following command to set up the repository:
```bash
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
- #### Install Docker Engine
3. Update the `apt` package index:
```bash
sudo apt-get update
```
2. Install Docker Engine, containerd, and Docker Compose (Latest).
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
- #### Add docker users
1. Add your main user to docker group:
```bash
sudo usermod -a -G docker aelzagh
```
2. add user for docker and add it to docker and sudo groups:
```bash
sudo adduser docker --ingroup docker
sudo usermod -a -G sudo docker
```

## Deploy Containers
*Make sure to switch to docker user first*
### 1- Portainer ([docs]([Install Portainer CE with Docker on Linux - Portainer Documentation](https://docs.portainer.io/start/install-ce/server/docker/linux)))
- First, create the volume that Portainer Server will use to store its database:
```bash
docker volume create portainer_data
```
- Then, download and install the Portainer Server container:
```bash
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```
- Open container and import `Sonarr, Radarr, Jackett, qbittorrent, Jellyfin` Images if available

### 2- Sonarr, Radarr, Jackett, qbittorrent, Jellyfin
- Create a folder with name `docker` inside `/home/docker`:
```bash
mkdir ~/docker
```
- Create a `docker-compose.yml` file inside the created folder: [docker-compose.yml]([Dotfiles/docker-compose.yml at main · ahmedelzagh/Dotfiles · GitHub](https://github.com/ahmedelzagh/Dotfiles/blob/main/Linux/docker-compose/Media-Library/docker-compose.yml)) then run `docker compose up -d`

## Setup a share to upload existing Movies/Shows to Library
1- Install samba
```bash
sudo apt install samba
```
2- Add user docker to samba users and set a password:
```bash
sudo smbpasswd -a docker
```
3- Add the samba share by editting `smb.conf`:
```bash
sudo nano /etc/samba/smb.conf
```
add the following at the end:
```bash
[docker]
   comment = docker media amd configs folder
   path = /home/docker/docker
   read only = no
   inherit permission = yes
```
4- Restart samba and allow samba through firewall:
```bash
sudo systemctl restart smbd
sudo ufw allow samba
```