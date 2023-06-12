# Debian
---
Debian is a reliable, secure, and open-source operating system with key features including:
1. Stability: Debian focuses on providing a stable operating system through rigorous testing and careful package selection.
2. Security: Regular security updates are released to address vulnerabilities and ensure the safety of the system.
3. Package Management: Debian's Advanced Packaging Tool (APT) simplifies software installation, updates, and removal, with a vast repository of thousands of software packages.
4. Free Software Philosophy: Debian strictly adheres to the principles of free and open-source software, promoting user freedom and transparency.
5. Multiple Desktop Environments: Debian supports various desktop environments, allowing users to choose the interface that best suits their preferences.
6. Documentation: Debian provides extensive documentation, including installation guides, administration manuals, and package-specific documentation, making it easier for users to understand and utilize the system.
7. Versatility: Debian is designed to work on a wide range of devices, from personal computers to servers, catering to diverse user needs.

With these features, Debian stands as a popular choice for individuals, organizations, and other Linux distributions seeking a stable, secure, and customizable operating system.

Project Homepage: [Debian -- The Universal Operating System](https://www.debian.org/)
Documentation: [Debian -- Documentation](https://www.debian.org/doc/)

---
## Post Install Steps (12.0.0)
*Desktop Environment*

### 1- Configure Repositories
- Update `sources.list` file: Open the `sources.list` file using a text editor with root privileges. For example:
```bash
sudo nano /etc/apt/sources.list
```

- Replace the contents of the file with the following lines, which provide the correct repository URLs for Debian 12 "Bookworm":
```bash
deb http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware
deb-src http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware

deb http://security.debian.org/debian-security bookworm-security main contrib non-free
deb-src http://security.debian.org/debian-security bookworm-security main contrib non-free
```

- Save the changes and exit the text editor.
- Update the package lists with the corrected repository configuration:
```bash
sudo apt update
```

### 2- Adding Flatpack
Flatpak, formerly known as xdg-app, is a utility for software deployment and package management for Linux. It is advertised as offering a sandbox environment in which users can run application software in isolation from the rest of the system.

- Install Flatpak:
```bash
sudo apt install flatpack
```

- Add Flatpak repo to Software Manager:
```bash
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

### 3- Remove Firefox's ESR version and Install the Normal version
The version of Firefox included in the Debian repositories may not always be the latest release. By updating Firefox from Flathub, you can access the most up-to-date features, security patches, and improvements.

- Remove `firefox-esr`:
```bash
sudo apt remove firefox-esr
```

- Open GNOME Software and Search for Firefox, then install it from `Flathub`.
	![Firefox on Flathub](/Linux/assets/firefox-flathub.png)

### 4- Upgrade the version of LibreOffice
LibreOffice version that comes with Debian is completely out-of-date and missing a lot of new features *(the developers recommends to upgrade to the latest version and to stop using version `7.4`)*.

- Search and uninstall all LibreOffice apps from GNOME Software.
- Make sure that you have uninstalled all LibreOffice apps by running the following commands:
```bash
sudo apt-get remove --purge ‘libreoffice*’
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get remove --purge libreoffice\*
```

- Open GNOME Software and search for LibreOffice and install it from Flathub.
	![Installing LibreOffice from Flathub](/Linux/assets/LibreOffice-GNOME.png)

### 5- Install Additional Desktop Environments
Debian offers a wide variety of software packages and supports multiple desktop environments, including GNOME, KDE Plasma, Xfce, LXQt, and more. This allows users to choose the desktop environment that suits their preferences and requirements.

- Run the following command to choose additional Desktop environments to be installed:
```bash
sudo tasksel
```

- Restart the system, when you get to the login screen click on your username, then click on the gear icon down on the right of the screen and choose the desktop environment you want and login.
	![Switching Between Desktop Environments](/Linux/assets/switching-desktop-environment.png)

### 6- Remove All Games
The default installation of popular Debian-based desktop operating systems include many games.
For developers and diskspace conscious users these games are unnecessary.

To remove all the games using a command line one-liner use the following:  
```bash
sudo apt purge gnome-2048 aisleriot atomix gnome-chess five-or-more hitori iagno gnome-klotski lightsoff gnome-mahjongg gnome-mines gnome-nibbles quadrapassel four-in-a-row gnome-robots gnome-sudoku swell-foop tali gnome-taquin gnome-tetravex -y & sudo apt autoremove -y
```

### 7- Install Nvidia Drivers
*(If necessary)*

- Enable non-free software: *(skip this step if you have done the first step)*
	Open GNOME Software, then choose Software Repositories from the top right menu.
	![software repositories](/Linux/assets/software-repo.png)
	Check the non-free boxes:
	![enabling non-free software](/Linux/assets/enabling-non-free-software.png)
- Install Nvidia drivers package:
```bash
sudo apt install nvidia-driver
```

### 8- Add Multimedia Codecs & Install VLC
- Enable non-free software: *(skip this step if you have done the first step)*
	Open GNOME Software, then choose Software Repositories from the top right menu.
	![software repositories](/Linux/assets/software-repo.png)
	Check the non-free boxes:
	![enabling non-free software](/Linux/assets/enabling-non-free-software.png)

- Install Codecs + VLC:
```bash
sudo apt install libavcodec-extra vlc
```

### 10- Setup the `backports` Repository:
Will Include newer versions of applications that Debian has decided to make available on that repository *(e.g. updated kernels)*.

- Create new file `backports.list`:
```bash
sudo nano /etc/apt/sources.list.d/backports.list
```
- Add bookworm version of `backports` by adding this line:
```bash
deb http://deb.debian.org/debian bookworm-backports main
```
- Refresh the package repository by running:
```bash
sudo apt update
```
- If you want to install a package from `back ports` repo in the future:
```shell
sudo apt install -t bookworm-backports $package-name
```
