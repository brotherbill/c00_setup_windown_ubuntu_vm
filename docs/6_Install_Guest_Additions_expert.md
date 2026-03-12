c:/dev/ubuntu/docs/6_Install_Guest_Additions_expert.md


# Ubuntu VM Setup (Expert Checklist)

# 6. Install Guest Additions (Expert)

1. Log in to Ubuntu VM.
2. (Optional) Full screen: Right-Ctrl+C, Right-Ctrl+F
3. (Optional) Hide Dock: Settings > Appearance > Auto-hide Dock
4. Open terminal:
   ```bash
   sudo apt update
   sudo apt install -y build-essential dkms linux-headers-$(uname -r)
   ```
5. VirtualBox menu: Devices > Insert Guest Additions CD Image
6. In terminal:
   ```bash
   sudo mkdir /media/cdrom
   sudo mount /dev/cdrom /media/cdrom
   sudo /media/cdrom/VBoxLinuxAdditions.run
   ```
7. Reboot VM:
   ```bash
   sudo reboot
   ```

---

# Shared Folders (Host ↔ Guest)

## Windows Host
1. VirtualBox Manager > Settings > Shared Folders
2. Add folder: set path, name (e.g., shared), check Auto-mount & Make Permanent

## Ubuntu Guest
1. Shared folder auto-mounts at `/media/sf_<name>` (e.g., `/media/sf_shared`)
2. If not visible, add user to vboxsf:
   ```bash
   sudo usermod -aG vboxsf $USER
   ```
   Log out/in or reboot to apply
3. Access shared files in `/media/sf_<name>`

---

Enables full screen, clipboard, drag-and-drop, and shared folder support.
