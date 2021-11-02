
# Dual_Boot_Chromium_OS
This is method to dual boot any Chromium OS.    
The purpose of this project is to dual-boot latest version of Chromium OS. Chromium has never gave option to dual boot it. So here is the script to do that on a Single hard disk (Not with Second hard disk).



#### Prerequisites         
UEFI based PC (GPT Disk)       
x86_64 based CPU       
Minimum of 16GB free space       
Chromium OS (arnold_build or wayne_os test)        
8GB USB (Not needed if you are dual booting with linux)       
Note: I am not responsible for any data loss. Please follow this guide carefully        

#### Dual Boot Chromium_OS with Windows      
Download latest version of Chromium_OS         
You can download the Latest Version from the Links below                
Create a live USB of linux mint or ubuntu(arch didn't tried yet)         
Open disk manager and shrink any volume of minimum 24GB        
Create new partition format in ntfs        
Now reboot and boot your PC with the live USB        

### Option 1 : Works on debian based distro        

Download the Chromium OS and extract it.       
Download this file( Script) and Extract it.       
Now run the following command (MAKE SURE THAT YOU ENTER THE PARTITION CORRECTLY)          
Right click on an empty area and select Open in terminal         
```bash
  tar zxvf brunch_r91_stable_20210620.tar.gz
```             
Identify the partition you intend to use for multi_install, you can run 
```bash
  lsblk -e7
```  
To see your disks and identify the right one. (If you have not made a partition yet, make one before continuing.)             
Mount the unencrypted NTFS partition on which we will create the disk image to boot from:
```bash
  mkdir -p ~/tmpmount 
```     

```bash
  sudo mount < the destination partition (ntfs) which will contain the disk image > ~/tmpmount 
``` 

Create the ChromeOS disk image:  
```bash                   
sudo bash chromeos-install.sh -src < path to the ChromeOS recovery image > -dst ~/tmpmount/chromeos.img -s < size you want to give to your chromeos install in GB (system partitions will take around 10GB, the rest will be for your data) >
``` 
Copy the Grub config which appeared in the terminal at the end of the process (the text between lines with stars)                          
Paste it in your grub.cfg in Boot/grub                
or                   
Now copy the grub entry, create a new text document and paste it in C drive or any other.              
Reboot your PC and log in to Windows                      
Install Grub2Win                   
Open Grub2Win and click on Manage Boot Menu then Add new Entry then select Custom Code and name it Chromium_OS                          
Now paste the grub entry from the text document and remove the menuentry line including the curly braces The grub entry should start from insmod part....... 
Save the text file and close Grub2Win            
Now reboot your PC and choose Chromium_OS.               



### Option 2 : Works on Linux Mint & Ubuntu            
Download the Chromium OS and extract it.             
Download this file( Script) and Extract it.               
Download multi_install.sh(Thanks to shrikant)                  
Right click on an empty area and select Open in terminal
```bash              
Sudo sh multi_install.sh        
```                               
select the partition on which you want to install Chromium_OS                
Copy the Grub config which appeared in the terminal at the end of the process  (the text between lines with stars)                   
Paste it in your grub.cfg in Boot/grub              
or                            
Same steps as in option 1                  







## 🔗 Links
[![multi_boot](https://img.shields.io/badge/multi_boot-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://drive.google.com/file/d/12A8v-v809bsbZrRjbynSC_S68mHQXtdM/view?usp=drivesdk/)

[![MEGA](https://img.shields.io/badge/script-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://github.com/sebanc/brunch/releases/download/r91-stable-20210620/brunch_r91_stable_20210620.tar.gz/)

[![WAYNE](https://img.shields.io/badge/chromium_option_1-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://wayne-os.com/category/release/)

[![ARNOLD](https://img.shields.io/badge/chromium_option_2-000?style=for-the-badge&logo=ko-fi&logoColor=white)](http://chromium.arnoldthebat.co.uk/)



             
          





               

                   




## FAQ

#### Is dualbooting by this method safe?

Yes, it is absolutely safe unless you mess with boot entry or not compitable CPU

#### Why only 1 partitions are required to dualboot Chromium OS whereas the image has 13 partitions?

These partitions are in loop on selected partition.

#### Updating Chromium OS

You can update Chromium_OS        
Coming Soon

#### Unistall Chromium OS  

The only way is to delete the partitions on which chromium os is installed from disk management in windows and create a new simple volume. (Gparted, if you are using linux)                             
Uninstall Grub2Win (Optional) 

#### If got any error in any option?

Try other option instead   

#### Chromium OS didn't booted?

First try to boot chromium os build from etcher usb.                     
 Try other distro that support your CPU

#### Will I get all the functionality of chromium os?

Yes, you will get everything 

#### I cannot see my internal drives mounted so how can I mount it?

In boot entry after cros_secure cros_debug add options=mount_drives                              
                 
                                                                   
## Contributing
Special Thanks to  
######
Aditya              
Sebanc                 
Shrikant 
                           

