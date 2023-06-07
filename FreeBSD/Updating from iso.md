# How to update from another .iso file

Example:
converting a FreeBSD server installed using `FreeBSD-13.1-RELEASE-amd64-disc1.iso` to have all services included in `FreeBSD-13.1-RELEASE-amd64-dvd1.iso`

The `FreeBSD-13.1-RELEASE-amd64-disc1.iso` image provides a minimal installation of FreeBSD, while the `FreeBSD-13.1-RELEASE-amd64-dvd1.iso` image provides a full installation of FreeBSD, with additional packages and software.

To convert a FreeBSD server installed using the `FreeBSD-13.1-RELEASE-amd64-disc1.iso` image to have all the packages and software provided by the `FreeBSD-13.1-RELEASE-amd64-dvd1.iso` image, you can follow these steps:

1.  Mount the `FreeBSD-13.1-RELEASE-amd64-dvd1.iso` image:
    ```bash
    mkdir /mnt/dvd # mount -t cd9660 /dev/cd0 /mnt/dvd
    ```
2.  Edit the `/usr/local/etc/pkg/repos/FreeBSD.conf` file to include the DVD as a package repository. Add the following line to the file:
    ```
    file:///mnt/dvd/packages/13.1-RELEASE
    ```
3.  Update the package repository:
    ```bash
    pkg update
    ```
4.  Install the packages from the DVD:
```bash
    pkg install -y dvd1
```

This will install all the packages and software that come with the `FreeBSD-13.1-RELEASE-amd64-dvd1.iso` image on your server. Keep in mind that this will take up additional disk space and may require more resources.