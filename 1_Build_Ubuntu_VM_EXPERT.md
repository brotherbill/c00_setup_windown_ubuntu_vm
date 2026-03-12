c:/dev/ubuntu/1_Build_Ubuntu_VM_EXPERT.md


# Ubuntu VM Setup (Expert Checklist)

---

## 1. Prerequisites
1. Windows 11
2. Admin rights
3. ≥30GB free disk space

---

## 2. Install Oracle VirtualBox
1. Download from [https://www.virtualbox.org/](https://www.virtualbox.org/)
2. Run installer from Downloads
3. Approve UAC prompt (**Yes**)
4. Accept all default options
5. Approve network/USB driver prompts

---

## 3. Create Ubuntu VM
1. Open VirtualBox
2. Click **New**
3. Name: `UbuntuD-VM` (or preferred)
4. Type: `Linux`, Version: `Ubuntu (64-bit)`
5. Memory: `8192 MB` (or `4096 MB` if low on RAM)
6. CPU: `2` (leave at least 2 for Windows)
7. Disk: `50 GB`, `VDI`, `Dynamically allocated`

---

## 4. VM Settings Before First Boot
1. Display > Graphics Controller: `VMSVGA`
2. Display > Video Memory: `128 MB`
3. Enable 3D Acceleration
4. Attach Ubuntu ISO to optical drive
5. Network: `NAT` (or `Bridged`)
6. Shared Clipboard: `Bidirectional`
7. Drag and Drop: `Bidirectional`

---

## 5. Install Ubuntu
1. Start VM
2. Select Ubuntu ISO if prompted
3. Complete installer (language, keyboard, timezone)
4. Select **Erase disk and install Ubuntu** (only affects VM)
5. Create username/password
6. Finish install and reboot VM
7. Remove/detach ISO if prompted

---

## 6. Install Guest Additions
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

## 7. Test Full Screen and Shortcuts
1. Try Host+F (Right Ctrl+F) for full screen
2. Window resizes with no black margins
3. Clipboard and drag/drop work

---

## 8. Install a Web Browser (if needed)
1. Ubuntu comes with Firefox
2. To install Chrome:
   ```bash
   sudo apt update && sudo apt install -y wget
   wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
   sudo apt install -y ./google-chrome-stable_current_amd64.deb
   ```

---

## 9. Install VS Code
1. In terminal:
   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
   sudo install -o root -g root -m 644 packages.microsoft.gpg /usr/share/keyrings/
   sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
   sudo apt update
   sudo apt install -y code
   ```

---

## 10. Install D Language and Dub
1. In terminal:
   ```bash
   sudo apt install -y curl
   curl -fsS https://dlang.org/install.sh | bash -s dmd
   ```
2. Follow script output to add D to PATH (usually: `source ~/dlang/dmd-*/activate`)

---

## 11. Install VS Code Extensions for D
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

## 12. Configure Debugging (F5)
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

## 13. Shell Script for New Projects (with F5 Debugging)
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

## 14. Done Checklist
1. Ubuntu VM boots to desktop
2. Internet works in VM
3. Window resize/full-screen works (no black margins)
4. Clipboard copy/paste works host ↔ guest
5. VS Code launches
6. Dlang compiles and runs
7. F5 debugging works in VS Code
8. new_d_project.sh script creates working D projects

If anything fails, note the exact step and error message.