c:/dev/ubuntu/docs/3_Create_Ubuntu_VM_beginner.md

# Ubuntu VM Setup (Beginner Checklist)

# 3. Create Ubuntu VM (Beginner)

This step guides you through creating a new virtual machine in VirtualBox for Ubuntu.

**Virtual machine name and operating system**  (*first wizard page*)

1. Create folder paths: `C:\dev\ubuntu\iso\` and `C:\dev\ubuntu\vms\`
2. Download the Ubuntu ISO image:
   - Visit https://ubuntu.com/download/desktop
   - Click **Download** of the latest LTS version (e.g., Ubuntu 22.04 LTS)
     - As I am running on Intel or AMD 64-bit architecture, I select that Download button.
     - A new browser window will Thank you for downloading and invite you to sign up for their newsletter.  You may do so if you choose.  The course does not require this.
   - Open the Downloads folder, then copy the file to `C:\dev\ubuntu\iso\` 
3. Open **Oracle VirtualBox**.
4. Click **New** icon.
   1. A New Virtual Machine wizard will display.

5. Enter VM Name such as: **Ubuntu**.
6. For VM Folder, set: `C:\dev\ubuntu\vms\`
   1. Click on drop down arrow, then select: **Other...**
   2. Select: `C:\dev\ubuntu\vms`, then click **Select Folder** button.

7. ISO Image
   1. Click on drop down arrow, then select: **Other...**
   2. Set folder path to: `C:\dev\ubuntu\iso\`

8. OS is set to **Linux** and you can't change it.
9. OS Version is set to **Ubuntu (64-bit)** and you can't change it.
10. Uncheck **Proceed with Unattended Installation**.
11. Click **Next**
    

**Specify virtual hardware**  (*second wizard page*)

****

1. Set Base Memory to **4096–8192 MB** (4–8 GB). 
   1. Do not use more than half your total RAM.

2. Set Number of CPUs to at least **2** (*leave at least half for Windows*).
3. Set Disk Size to **50 GB**.
4. Keep **Use EIF** unchecked.
5. Click **Next**.
   

**Summary**  (*third wizard page*)

1. Click **Finish**.
   

##### Congratulations, you have just created a new Ubuntu Virtual Machine (VM)