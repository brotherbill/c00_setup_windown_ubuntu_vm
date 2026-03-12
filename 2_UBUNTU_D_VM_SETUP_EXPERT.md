c:/dev/ubuntu/UBUNTU_D_VM_BABY_STEPS.md
# Ubuntu VM for D Programming (Baby Steps)

This guide is for beginners. Follow each checklist step in order. Do not skip steps. If you get stuck, note the exact step and error.

---

## 1. Prepare Windows 11
1. Confirm you have admin rights
2. Free space: at least 30GB

---

## 2. Check Virtualization Support
1. Press `Ctrl+Shift+Esc` (Task Manager)
2. Go to **Performance** tab
3. Click **CPU**
4. Find **Virtualization**
   - [ ] If **Enabled** → continue
   - [ ] If **Disabled** → enable VT-x/AMD-V in BIOS, then return

---

## 3. Install VirtualBox
1. Download from https://www.virtualbox.org/
2. Install with default options
3. Reboot if prompted

---

## 4. Download Ubuntu ISO
1. Go to https://ubuntu.com/download/desktop
2. Download latest LTS (e.g., Ubuntu 22.04 LTS)
3. Save to easy path (e.g., `C:\ISO\ubuntu.iso`)

---

## 5. Create the Virtual Machine
1. Open VirtualBox
2. Click **New**
3. Name: `UbuntuD-VM`
4. Type: `Linux`
5. Version: `Ubuntu (64-bit)`
6. Memory: `8192 MB` (use `4096 MB` if low on RAM)
7. CPU: `2` (leave at least 2 for Windows)
8. Disk: `50 GB`, `VDI`, `Dynamically allocated`

---

## 6. VM Settings Before First Boot
1. Display > Graphics Controller: `VMSVGA`
2. Display > Video Memory: `128 MB`
3. Display > Enable 3D Acceleration
4. Storage > Attach Ubuntu ISO to optical drive
5. Network > Adapter 1: `NAT` (or `Bridged` for direct network)
6. General > Advanced: Shared Clipboard: `Bidirectional`
7. General > Advanced: Drag and Drop: `Bidirectional`

---

## 7. Install Ubuntu
1. Start the VM
2. Select Ubuntu ISO if prompted
3. Follow installer: language, keyboard, timezone
4. Select **Erase disk and install Ubuntu** (only affects VM)
5. Create username/password
6. Finish install and reboot VM
7. Remove/detach ISO if prompted

---

## 8. Install Guest Additions (for full screen, clipboard, drag/drop)
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

## 9. Test Full Screen and Shortcuts
1. Try Host+F (Right Ctrl+F) for full screen
2. Window should resize with no black margins
3. Clipboard and drag/drop should work

---

## 10. Install a Web Browser (if needed)
1. Ubuntu comes with Firefox
2. To install Chrome:
   ```bash
   sudo apt update && sudo apt install -y wget
   wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
   sudo apt install -y ./google-chrome-stable_current_amd64.deb
   ```

---

## 11. Install VS Code
1. In terminal:
   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
   sudo install -o root -g root -m 644 packages.microsoft.gpg /usr/share/keyrings/
   sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
   sudo apt update
   sudo apt install -y code
   ```

---

## 12. Install D Language and Dub
1. In terminal:
   ```bash
   sudo apt install -y curl
   curl -fsS https://dlang.org/install.sh | bash -s dmd
   ```
2. Follow script output to add D to PATH (usually: `source ~/dlang/dmd-*/activate`)

---

## 13. Install VS Code Extensions for D
1. Open VS Code
2. Press Ctrl+Shift+X (Extensions)
3. Search for and install:
   - `code-d` (D language support)
   - `Native Debug` (for GDB integration)
4. Or run in terminal:
   ```bash
   code --install-extension webfreak.code-d
   code --install-extension webfreak.debug
   ```

---

## 14. Configure Debugging (F5)
1. Open your D project in VS Code
2. If not auto-generated, create `.vscode/launch.json`:
   ```json
   {
     "version": "0.2.0",
     "configurations": [
       {
         "name": "Debug D Program",
         "type": "gdb",
         "request": "launch",
         "target": "./bin/<your_executable>",
         "cwd": "${workspaceFolder}",
         "preLaunchTask": "dub build"
       }
     ]
   }
   ```
3. Replace `<your_executable>` with your binary name

---

## 15. Shell Script for New Projects (with F5 Debugging)
1. Create `new_d_project.sh`:
   ```bash
   #!/bin/bash
   set -e
   if [ -z "$1" ]; then
     echo "Usage: $0 <project_name>"
     exit 1
   fi
   dub init "$1" executable
   cd "$1"
   mkdir -p .vscode
   cat > .vscode/launch.json <<EOF
   {
     "version": "0.2.0",
     "configurations": [
       {
         "name": "Debug D Program",
         "type": "gdb",
         "request": "launch",
         "target": "./$1",
         "cwd": "${workspaceFolder}",
         "preLaunchTask": "dub build"
       }
     ]
   }
   EOF
   echo "Project $1 created and configured for F5 debugging in VS Code."
   ```
2. Make it executable:
   ```bash
   chmod +x new_d_project.sh
   ```

---

## 16. Done Checklist
1. Ubuntu VM boots to desktop
2. Internet works in VM
3. Window resize/full-screen works (no black margins)
4. Clipboard copy/paste works host ↔ guest
5. VS Code launches
6. Dlang compiles and runs
7. F5 debugging works in VS Code
8. new_d_project.sh script creates working D projects

If anything fails, note the exact step and error message.
