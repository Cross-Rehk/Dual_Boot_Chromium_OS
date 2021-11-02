# Dual_Boot_Chromium_OS
This is method to dual boot any Chromium OS.
The purpose of this project is to dual-boot latest version of Chromium OS. Chromium has never gave option to dual boot it. So here is the script to do that on a Single hard disk (Not with Second hard disk).



Prerequisites
UEFI based PC (GPT Disk)
x86_64 based CPU
Minimum of 16GB free space
Chromium OS (arnold_build or wayne_os test)
8GB USB (Not needed if you are dual booting with linux)
Note: I am not responsible for any data loss. Please follow this guide carefully

Dual Boot Chromium_OS with Windows
Download latest version of Chromium_OS
You can download the Latest Version from
        1. https://wayne-os.com/category/release/
Create a live USB of linux mint or ubuntu(arch didn't tried yet)
Open disk manager and shrink any volume of minimum 24GB
Create new partition format in ntfs
Now reboot and boot your PC with the live USB

Option 1 : Works on debian based distro

Download the Chromium OS and extract it.
Download this file(    ) and Extract it.
Now run the following command (MAKE SURE THAT YOU ENTER THE PARTITION CORRECTLY)
Right click on an empty area and select Open in terminal
tar zxvf script.tar.gz
Identify the partition you intend to use for Brunch, you can run lsblk -e7 to see your disks and identify the right one. (If you have not made a partition yet, make one before continuing.)
Mount the unencrypted ext4 or NTFS partition on which we will create the disk image to boot from:
mkdir -p ~/tmpmount
sudo mount < the destination partition (ext4 or ntfs) which will contain the disk image > ~/tmpmount
Create the ChromeOS disk image:
sudo bash chromeos-install.sh -src < path to the ChromeOS recovery image > -dst ~/tmpmount/chromeos.img -s < size you want to give to your chromeos install in GB (system partitions will take around 10GB, the rest will be for your data) >
Copy the Grub config which appeared in the terminal at the end of the process (the text between lines with stars)

Paste it in your grub.cfg in Boot/grub
or
Now copy the grub entry, create a new text document and paste it in C drive or any other. 
Reboot your PC and log in to Windows
Install Grub2Win
Open Grub2Win and click on Manage Boot Menu then Add new Entry then select Custom Code and name it Chromium_OS
Now paste the grub entry from the text document and remove the menuentry line including the curly braces The grub entry should start from insmod part....... and end at cros_debug
Save the text file and close Grub2Win
Now reboot your PC and choose Chromium_OS.



Option 2 : Works on Linux Mint & Ubuntu
Download the Chromium OS and extract it.
Download this file(    ) and Extract it.
Download multi_install.sh(Thanks to shrikant)
Right click on an empty area and select Open in terminal
Sudo sh multi_install.sh
select the partition on which you want to install Chromium_OS
Copy the Grub config which appeared in the terminal at the end of the process (the text between lines with stars)

Paste it in your grub.cfg in Boot/grub
or 
same steps as in option 1







Updating Chromium OS
You can update Chromium_OS
Coming Soon





Unistall Chromium OS

The only way is to delete the partitions on which chromium os is installed from disk management in windows and create a new simple volume. (Gparted, if you are using linux)
Uninstall Grub2Win (Optional)






FAQ (Frequently Asked Questions)
Is dualbooting by this method safe?
Yes, it is absolutely safe unless you mess with your partitions

Why only 1 partitions are required to dualboot Chromium OS whereas the image has 13 partitions?
These partitions are in loop on selected partition.

#Linux (Beta) dosen't work in my system after doing this, so what should i do now?
#Make sure to disable crostini-use-dlc from chrome://flags and retry. If that dosen't work then try downgrading to older version of cloudready. If you have dgpu then switch it to igpu

If got any error in any option?
try other option instead

Chromium OS didn't booted?
first try to boot chromium os build from etcher usb.
try other distro that support your CPU

Will I get all the functionality of chromium os?
Yes, you will get everything

Why Filesystem-verity is disabled and cloudready recommends reinstalling, so should i reinstall?
As we are manually installing cloudready, filesystem verity will be disabled. Just click "I understand" and tick the check box to never display it again.

I cannot see my internal drives mounted so how can I mount it?
in boot entry after cros_secure cros_debug add options=mount_drives


special Thanks to 
Sebanc
Shrikant
