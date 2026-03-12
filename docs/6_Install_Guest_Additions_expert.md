c:/dev/ubuntu/docs/6_Install_Guest_Additions_expert.md

# Ubuntu VM Setup (Expert Checklist)

# 6. Install Guest Additions (Expert)

1. Open terminal in Ubuntu:
   ```bash
   sudo apt update
   sudo apt install -y build-essential dkms linux-headers-$(uname -r)
   ```
2. In VirtualBox menu: Devices > Insert Guest Additions CD Image
3. In terminal:
   ```bash
   sudo mkdir /media/cdrom
   sudo mount /dev/cdrom /media/cdrom
   sudo /media/cdrom/VBoxLinuxAdditions.run
   ```
4. Reboot VM

---

# Shared Folders (Host ↔ Guest)

## Windows Host
- VirtualBox Manager > Settings > Shared Folders
- Add folder: set path, name (e.g., shared), check Auto-mount & Make Permanent

## Ubuntu Guest
- After boot, shared folder auto-mounts at `/media/sf_<name>` (e.g., `/media/sf_shared`)
- If not visible, add user to vboxsf:
   ```bash
   sudo usermod -aG vboxsf $USER
   ```
- Log out/in or reboot to apply
- Access shared files in `/media/sf_<name>`
