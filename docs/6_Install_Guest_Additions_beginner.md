c:/dev/ubuntu/docs/6_Install_Guest_Additions_beginner.md

# Ubuntu VM Setup (Beginner Checklist)

# 6. Install Guest Additions (Beginner)

1. Open a terminal in Ubuntu.
2. Run:
   ```bash
   sudo apt update
   sudo apt install -y build-essential dkms linux-headers-$(uname -r)
   ```
3. In VirtualBox menu: Devices > Insert Guest Additions CD Image.
4. In the terminal, run:
   ```bash
   sudo mkdir /media/cdrom
   sudo mount /dev/cdrom /media/cdrom
   sudo /media/cdrom/VBoxLinuxAdditions.run
   ```
5. Reboot the VM.

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