c:/dev/ubuntu/docs/6_Install_Guest_Additions_beginner.md

# Ubuntu VM Setup (Beginner Checklist)

# 6. Install Guest Additions (Beginner)

1. Log in with your user name and password.

   1. Click on user name, such as: **Brother Bill**
   2. Enter your password, then press **Enter**

2. Scale to full screen

   1. Press Right-Ctrl + C
   2. Press Right-Ctrl + F

3. Remove left column of apps

   1. Open **Settings** app
   2. 

4. Open a terminal in Ubuntu.

   - With VM having the focus, press Windows key, then type "Terminal", and click the Terminal app.
5. Run the following commands to make sure your system has the tools needed to install Guest Additions:
   ```bash
   sudo apt update
   
   sudo apt install -y build-essential dkms linux-headers-$(uname -r)
   ```
   - The first command updates your list of available software. The second command installs software needed for Guest Additions to work properly.
   - You may be asked for your password after typing `sudo`. Type it carefully (you won’t see it as you type) and press Enter.
6. In the VirtualBox menu at the top of your VM window, click **Devices** > **Insert Guest Additions CD Image**.
   - This will insert a virtual CD into your Ubuntu VM with the Guest Additions installer.
7. In the terminal, run these commands to install Guest Additions:
   ```bash
   sudo mkdir /media/cdrom
   
   sudo mount /dev/cdrom /media/cdrom
   
   sudo /media/cdrom/VBoxLinuxAdditions.run
   ```
   - The first command creates a folder to access the CD. The second command mounts the CD so Ubuntu can read it. The third command runs the installer.
   - If you see any errors about "modprobe vboxsf failed", you can ignore them for now.
8. Reboot the VM to finish the installation.
   - You can reboot by clicking the power icon in the top-right corner and choosing Restart, or by running:
   ```bash
   sudo reboot
   ```

---

# Add Shared Folders Between Windows and Ubuntu

## On the Windows (Host) Side
1. In VirtualBox Manager, select your Ubuntu VM (do not start it yet).
2. Click **Settings** > **Shared Folders**.
3. Click the folder icon with a plus (+) sign to add a new shared folder.
4. For **Folder Path**, browse and select a folder on your Windows system you want to share (e.g., `C:\Users\YourName\SharedVM`).
5. For **Folder Name**, enter a simple name (e.g., `shared`).
6. Check **Auto-mount** and **Make Permanent**.
7. Click **OK** to save.

## On the Ubuntu (Guest) Side
1. Start your Ubuntu VM.
2. If you used **Auto-mount**, the shared folder should appear automatically in `/media/sf_shared` (replace `shared` with your folder name if different).
3. If you do not see the folder, you may need to add your user to the `vboxsf` group:
   ```bash
   sudo usermod -aG vboxsf $USER
   ```
   Then log out and log back in, or reboot the VM.
4. Access your shared files in `/media/sf_shared`.

---

This enables full screen, clipboard, drag-and-drop, and shared folder support.