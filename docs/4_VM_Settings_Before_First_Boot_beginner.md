c:/dev/ubuntu/docs/4_VM_Settings_Before_First_Boot_beginner.md


# Ubuntu VM Setup (Beginner Checklist)

# 4. VM Settings Before First Boot (Beginner)



Before you start your Ubuntu virtual machine (VM), follow these steps to get everything ready:

1. Open **Oracle VirtualBox** (the program you installed earlier).
2. In the list on the left, click once on your **Ubuntu VM** to select it.
3. Click the **Settings** button (it looks like a gear).
4. If you see an option for **Expert Mode**, click it to access additional settings.


Now, change the following settings. These will help your Ubuntu VM work better and make it easier to use with Windows:

**General tab**

1. Click the **General** tab on the left.
2. Click the **Features** tab at the top.
3. Set **Shared Clipboard** to **Bidirectional**. This lets you copy and paste text between Windows and Ubuntu.
4. Set **Drag-and-Drop** to **Bidirectional**. This lets you drag files between Windows and Ubuntu.
   


**Display tab**

1. Click the **Display** tab on the left.
2. Click the **Screen** tab at the top (if it isn't already selected).
3. Set **Video Memory** to **128 MB**. This helps your VM look better and run smoother.
4. Set **Graphics Controller** to **VMSVGA**. This is the best choice for Ubuntu.
5. Check the box for **Enable 3D Acceleration**. This can make graphics faster. If you have problems later, you can turn this off.
   


**Storage tab**

1. Click the **Storage** tab on the left.
2. Under **Controller: IDE**, make sure your Ubuntu ISO file (like **ubuntu-24.04.4-desktop-amd64.iso**) is attached. This is needed to install Ubuntu the first time you start the VM.


**Network tab**

1. Click the **Network** tab on the left.
2. Make sure **Attached to** is set to **NAT**. This is the easiest way to let your VM use the internet. (You can use Bridged mode if you know you need it, but NAT is best for most beginners.)
---


These settings will help your Ubuntu VM run smoothly and work well with your Windows computer. If you are not sure about any setting, just use the recommended values above. You can always change them later if you need to.