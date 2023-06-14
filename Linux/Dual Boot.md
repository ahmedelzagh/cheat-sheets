# Dual Boot Windows and Linux

## Introduction

Dual booting is the process of installing and running two different operating systems on a single computer, allowing you to choose which one to use when you power on your system. This documentation will guide you through the steps required to set up a dual boot configuration with Windows and Linux on your computer.

## Prerequisites

Before you begin, make sure you have the following:

1. A computer with sufficient disk space to accommodate both operating systems.
2. Installation media for Windows and the Linux distribution you want to install (e.g., Ubuntu, Fedora).
3. Backup any important data on your computer to prevent data loss during the installation process.

## Step 1: Prepare Installation Media

1. Obtain a Windows installation disc or create a bootable USB drive with the Windows installation files.
2. Download the ISO file for the Linux distribution you want to install and create a bootable USB drive using tools like Rufus or Etcher.

## Step 2: Partition Your Hard Drive and Install Windows

1. Boot your computer from the Windows installation media.
2. During the Windows installation process, you will be prompted to select a partition for installation.
3. Shrink your existing Windows partition to make space for the Linux installation. Specify the desired size for the new partition.
4. Leave the unallocated space on your disk for the Linux installation.
5. Continue with the Windows installation, following the on-screen instructions to complete the process, including setting up user accounts and configuring preferences.

## Step 3: Install Linux

1. Boot your computer from the Linux installation media.
2. Select the option to install Linux and choose the unallocated space on your disk for the installation.
3. Follow the on-screen instructions to install Linux, including configuring the partition layout, selecting the desired desktop environment, and creating a username and password.

## Step 4: Configure Dual Boot Options

1. After installing Linux, restart your computer. You will typically boot directly into Linux.
2. To access Windows, you need to configure the boot loader. If using Ubuntu or a similar distribution, you can use the `grub` bootloader.
3. Open a terminal in Linux and run the following command to update the `grub` configuration:
```shell
sudo update-grub
```
4. Restart your computer, and you should see a boot menu with options to boot into either Linux or Windows.

## Step 5: Managing the Dual Boot

1. When you start your computer, the boot menu will appear, allowing you to choose the operating system to boot into.

2. Select the desired operating system using the arrow keys and press Enter.

3. In case you want to change the default operating system or adjust the timeout duration for the boot menu, you can modify the `grub` configuration file located in `/etc/default/grub`, and change the number at the entry `GRUB_DEFAULT`.  
	*Here, for example, you specify 0 if the default selection in your grub boot loader should be the first entry. For example, for the 5th entry, enter 4 instead.*
4. Save the change, close the file and return to the terminal. Now enter the command `sudo grub-mkconfig -o /boot/grub/grub.cfg` and press the Enter key.
	
5. Now enter the command `sudo grub-mkconfig -o /boot/grub/grub.cfg` and press the Enter key.

6. Remember to regularly update both operating systems to ensure security and software updates.

## Conclusion

By following these steps, you can successfully set up a dual boot configuration with Windows and Linux on your computer. This allows you to enjoy the benefits of both operating systems and choose the one that best suits your needs when starting your computer. Remember to back up your data regularly and exercise caution when modifying disk partitions to avoid data loss.

# Removing Linux from Dual Boot Completely

To remove Linux from a dual boot configuration completely, you need to remove the Linux partitions and restore the Windows bootloader as the default. Here are the steps to remove Linux:

**Note: Before proceeding, make sure to back up any important data from both your Windows and Linux installations. Removing Linux will delete all the data on its partitions.**

## Step 1: Boot into Windows

Restart your computer and boot into Windows.

## Step 2: Delete Linux Partitions

- Press `Win + X` on your keyboard and select "Disk Management" from the menu.
- Identify the partitions related to Linux. They may have file systems like ext4 or swap.
- Right-click on each Linux partition and select "Delete Volume." Confirm the deletion when prompted.

## Step 3: Restore Windows Bootloader

- Open Command Prompt as an administrator.
- Run the following command to restore the Windows bootloader:
 ```powershell
 bootrec /fixmbr
 ```
- This command repairs the Master Boot Record (MBR) and removes the Linux bootloader from the boot sequence.

*If you encounter the error `bootrec` is not recognized as an internal or external command, operable program or batch file," it means that the command is not available on your system.
In such cases, you can try using the Windows installation media to repair the bootloader. Here's an alternative step to restore the Windows bootloader:*

## Alternative Step 3: Use Windows Installation Media to Repair Bootloader

- Insert the Windows installation media (DVD or USB drive) and restart your computer.
- Boot from the installation media.
- Select your language preferences and click "Next."
- On the installation screen, click on "Repair your computer" or "Troubleshoot" (depending on the Windows version).
- Select "Startup Repair" or "Automatic Repair" from the available options.
- Follow the on-screen instructions to let the repair process run.
- Once the repair is complete, restart your computer.

After completing the alternative step, the Windows bootloader should be restored, and your system will boot directly into Windows.

Remember to back up your data and proceed with caution while performing any system changes to avoid any unintended data loss.

## Step 4: Remove Linux Entry from Boot Menu (Optional)

- Open Command Prompt as an administrator.
- Run the following command to view the current boot configuration:
```powershell
bcdedit
```
- Look for an entry with a description mentioning Linux or GRUB.
- Use the following command to delete the Linux entry:
```powershell
bcdedit /delete <Linux Entry ID>
```
Replace `<Linux Entry ID>` with the actual identifier of the Linux entry.

## Step 5: Restart Your Computer

After completing the above steps, restart your computer to ensure that it boots directly into Windows without displaying the Linux boot menu.

Following these steps will remove Linux from your dual boot configuration and restore Windows as the sole operating system on your computer. Remember to back up your data and proceed with caution to avoid any unintended data loss.