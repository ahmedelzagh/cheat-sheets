# Installing FreeBSD w some essential services set up 

**1. Download the FreeBSD 13.1 bootonly ISO image**

-   Go to the FreeBSD download page ([https://www.freebsd.org/where.html](https://www.freebsd.org/where.html))
-   Scroll down to the "FreeBSD 13.1-RELEASE" section
-   Download the "bootonly" ISO image for your architecture (e.g., amd64)

**2. Create a new virtual machine on your hypervisor**

-   Choose the appropriate settings for your system (e.g., RAM, disk space, network, etc.)
-   Attach the FreeBSD ISO image to the virtual machine

**3. Boot the virtual machine from the FreeBSD ISO image**

-   Follow the prompts to begin the installation process
-   Choose the appropriate settings for your system (e.g., keyboard layout, disk partitioning, etc.)

**4. Install FreeBSD 13.1**

-   When prompted, select "Standard" installation
-   Follow the prompts to install the base system

**5. Post-installation steps to setup essential services**

-   Update the system packages and ports collection to ensure that you have the latest security patches and software updates:
    -   `freebsd-update fetch install`
    -   `pkg update`
-   Install and configure the OpenSSH server:
    -   `pkg install openssh`
    -   Edit the `/etc/ssh/sshd_config` file to enable SSH login and configure other options as needed (e.g., port, protocol version, etc.)
    -   Start the OpenSSH service: `service sshd start`
-   Install and configure the PF firewall:
    -   `pkg install pf`
    -   Edit the `/etc/pf.conf` file to configure the firewall rules
    -   Enable and start the PF service:
        -   Add `pf_enable="YES"` to the `/etc/rc.conf` file
        -   Start the PF service: `service pf start`
-   Create a new sudo user (if desired):
    -   `adduser` to create a new user
    -   `visudo` to edit the sudoers file and grant the new user sudo access