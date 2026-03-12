c:/dev/ubuntu/docs/5_Install_Ubuntu_beginner.md

# Ubuntu VM Setup (Beginner Checklist)


# 5. Install Ubuntu (Beginner)

**Note:** Installation steps may change over time since the date this lesson was created. If you notice small differences, just go with the flow and follow the prompts. If you encounter major changes or something confusing, let me know and I’ll update the lesson for you.


1. Launch **Oracle VirtualBox** if it is not already open.
  - Double-click the VirtualBox icon on your desktop or find it in your Start menu.

2. Start the Ubuntu VM.
  - Click the green Start arrow in VirtualBox to power on your Ubuntu VM, or simply double-click the Ubuntu VM in the list to start it.

3. You will see *** Try or Install Ubuntu**.  

   1. Click **Enter** to install Ubuntu.
   2. This may take a while and you may seem a fully black screen.  This is expected.
   3. Click the **Install Ubuntu** icon at the bottom-center of the window.
   4. Finally, you will see **Welcome to Ubuntu**

4. Open the Installer icon on the bottom-right of the window, or double-click the Installer icon.

   1. Click **Next** at the end of each wizard step.

   2. It displays: **Preparing Ubuntu**

   3. Choose your language: **English**
      1. You may choose English to follow the course, or choose your own language

   4. Select you **keyboard layout**

   5. Connect to the **Internet**
      1. I have an Ethernet connection, so selected: **Use wired connection**
      2. If you use **Wi-Fi**, follow the instructions.

   6. How would you like to install Ubuntu?
      1. Select: **Interactive installation**

   7. What apps would you like to install to start with?
      1. Select: **Default selection**

   8. Install recommended proprietary software?
      1. Don't select either.  **Next**

   9. How do you want to install Ubuntu?
      1. Select **Erase disk and install Ubuntu** (*this only affects the VM*).
         1. This option will only erase the virtual hard disk inside your VM, not your real computer. It is safe to choose this for a new VM.

   10. Create your account 
       1. Enter **Your name**.  I entered: **Brother Bill**
       2. Enter **Your computer's name**.  I entered: **Ubuntu-VM**
       3. Enter **Your username**.  I entered: **bb**
          1. This will be on every Terminal prompt by default, so keep it short.
       4. Enter **Password** and **Confirm password**
          1. Be sure to **remember** your username and password. Write them down somewhere safe so you don’t lose them. (Don’t actually use a Post-it note on your keyboard—choose a secure place!)
       5. Keep checked: **Require my password to log in**
          1. Although this is in a VM, and it may be convenient to not need to enter your password to log in, this may develop a bad habit, where your real projects don't require a password to log in.
       6. Click **Next**
   11. Select your timezone
       1. Mine is in Eastern timezone.  Set your timezone for your location on the planet.
   12. Review your choices.  Click: **Install**
5. Click **Restart now**

6. If Ubuntu asks you to "Please remove the installation medium, then press Enter":

- 1. At the top of the VirtualBox window, click the **Devices** menu.
    2. Hover over **Optical Drives**.
    3. If the menu item for Ubuntu .iso file has a checkmark on it, then click on it to toggle the checkmark to off, to detach the iso.  Otherwise, click escape to close the menu.

       1. If you get a dialog box asking: "Unable to eject the virtual optical disk `C:\dev\ubuntu\iso\ubuntu-24.04.4-desktop-amd65.iso` from the machine **Ubuntu**.

          Would you like to try to force ejection of this disk?

          Click **Force Unmount**
    4. The menu will close. Now, click inside the VM window and press **Enter** on your keyboard.
    5. Ubuntu should now finish restarting and boot from the virtual hard drive.

You should now see a log in screen for your Log in name, such as Brother Bill.

Use **Right-Ctrl + C** to scale to screen and **Right-Ctrl + F** to toggle full screen.

If you get stuck, note the step and error, and ask for help.