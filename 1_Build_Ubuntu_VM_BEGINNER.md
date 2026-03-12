c:/dev/ubuntu/1_Build_Ubuntu_VM_BEGINNER.md
# Ubuntu VM Setup Guide (Beginner)

This guide will help you set up a virtual Ubuntu computer (*called a "virtual machine" or VM*) inside your Windows 11 PC. You’ll use a free program called Oracle VirtualBox. Follow these simple steps:

# Ubuntu VM Setup Guide (Beginner)

This guide will help you set up a virtual Ubuntu computer (*called a "virtual machine" or VM*) inside your Windows 11 PC. You’ll use a free program called Oracle VirtualBox. Follow these simple steps:

## Step 0: What is a VM?

A virtual machine (VM) lets you run Ubuntu inside your Windows computer, like having a second computer inside your main one. It uses some of your disk space and memory, so it may run a bit slower than a real, separate Ubuntu computer.

## Step 1: Get Ready

- Make sure your Windows 11 PC is turned on.
- Log in as a regular user (not an admin). You’ll be asked for an admin password or permission only when needed.
- Check that you have at least 30GB of free space on your hard drive.
- You’ll need an admin password or provide permission when installing software.

## Step 2: Download and Install VirtualBox

1. Open your web browser and visit: [https://www.virtualbox.org/](https://www.virtualbox.org/)

2. Click the **Get Started Download** button.

3. On the next page, click **Windows hosts**. This will download a file called something like `VirtualBox-7.2.6a-172322-Win.exe` (*the version number may be newer*).

4. Open the file you just downloaded (*it’s in your Downloads folder*).


5. When installing an application, Windows may display a User Access Control (UAC) dialog asking:

   “Do you want to allow this app to make changes to your device?”

   - On most personal Windows 11 computers, you can simply click **Yes** to continue.
   - If you are on a corporate or school device and cannot proceed, contact your tech support team for assistance.


   - If you see a message about needing the "Microsoft Visual C++ 2019 Redistributable Package", skip to the next section below.
   - If nothing happens, try pressing **Alt+Tab** to see if its window is hiding behind others.

6. Click **Next** or **OK** to accept all the default options during installation.

7. If you see any prompts about network or USB drivers, click **Install** or **Allow**.

**If everything installs without errors, you’re done with this part!**

---

## If You See a "Microsoft Visual C++ 2019 Redistributable" Error

1. Click **OK** to close the error message.
2. Click **Finish** to close the installer.
3. Click **OK** on any other error messages. Don’t worry—your computer is still fine!

4. Visit: [https://aka.ms/vs/16/release/vc_redist.x64.exe](https://aka.ms/vs/16/release/vc_redist.x64.exe) to download the missing package.

5. Open the file you just downloaded (VC_redist.x64.exe) from your Downloads folder.
6. Check the box to agree to the license, then click **Install**.
7. If Windows asks for permission, click **Yes**.
8. When you see **Setup Successful**, click **Close**. (*If you don’t see this window, check if it’s hiding behind others.*)

9. Restart your computer.
10. Log back in.
11. Try installing VirtualBox again (repeat Step 2 above).

   1. Open your Downloads folder.

   2. Find the VirtualBox installer (*e.g., VirtualBox-7.2.6a-172322-Win.exe  or newer*).

   3. Double-click the installer to start the installation.

   4. If prompted, enter the administrator password or have someone with admin rights approve.
      Or click **Yes** button for User Account Control, in response to question *"Do you want to allow this app to make changes to your device?"* for VirtualBox Installer.

   5. Accept license terms, and all default options during installation.

   6. Allow any network or USB drivers to install if prompted.


## Summary
You have confirmed your machine has enough resources and have successfully downloaded and installed Oracle VirtualBox.

In the next document, we will create an Ubuntu Virtual Machine (VM) and configure it for use.

---

For troubleshooting, see the EXPERT guide.