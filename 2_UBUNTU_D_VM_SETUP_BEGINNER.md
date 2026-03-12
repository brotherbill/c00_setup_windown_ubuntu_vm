c:/dev/ubuntu/UBUNTU_D_SETUP_BEGINNER.md
# Ubuntu D Programming Environment Setup (Beginner Guide)

This guide will walk you through every step to set up an Ubuntu virtual machine for D programming, with full VS Code integration and debugging. Each step is broken down for beginners.

---

## 1. Prepare Your Windows PC
- Make sure you have admin rights and at least 30GB free disk space.

## 2. Download and Install VirtualBox
- Go to https://www.virtualbox.org/ and download the latest version for Windows.
- Run the installer and accept all default options.
- Allow any network or USB drivers if prompted.

## 3. Download Ubuntu ISO
- Visit https://ubuntu.com/download/desktop and download the latest LTS version (e.g., Ubuntu 22.04 LTS).
- Save the ISO file somewhere easy to find (like your Downloads folder).

## 4. Create a New Virtual Machine
- Open VirtualBox and click **New**.
- Name: UbuntuD (or any name you like).
- Type: Linux. Version: Ubuntu (64-bit).
- Memory: 4096–8192MB (4–8GB). Do not use more than half your total RAM.
- Hard disk: Create a virtual hard disk now. Size: 30GB or more.
- Click **Create**.

## 5. Adjust VM Settings for Best Experience
- Select your VM, click **Settings**.
- System > Processor: 2 or more CPUs (leave at least 2 for Windows).
- Display > Screen: Video Memory 128MB. Enable 3D Acceleration.
- Network: Bridged Adapter (for internet access).
- General > Advanced: Shared Clipboard and Drag'n'Drop: Bidirectional.

## 6. Install Ubuntu in the VM
- Start the VM. When prompted, select the Ubuntu ISO you downloaded.
- Follow the installer prompts. Use default partitioning.
- Set a username and password you will remember.

## 7. Install Guest Additions (for full screen, clipboard, drag/drop)
- After Ubuntu is running, open a terminal:
  sudo apt update && sudo apt install -y build-essential dkms linux-headers-$(uname -r)
- In VirtualBox menu: Devices > Insert Guest Additions CD Image.
- In the terminal:
  sudo mkdir /media/cdrom
  sudo mount /dev/cdrom /media/cdrom
  sudo /media/cdrom/VBoxLinuxAdditions.run
- Reboot the VM.

## 8. Test Full Screen and Shortcuts
- To enter full screen: Press **Right Ctrl + F** (Right Ctrl is the default Host key).
- If full screen doesn't work, make sure Guest Additions are installed.

## 9. Install a Web Browser (if needed)
- Ubuntu comes with Firefox. To install Chrome:
  sudo apt update && sudo apt install -y wget
  wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
  sudo apt install -y ./google-chrome-stable_current_amd64.deb

## 10. Install VS Code
- Download and install VS Code:
  wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
  sudo install -o root -g root -m 644 packages.microsoft.gpg /usr/share/keyrings/
  sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
  sudo apt update
  sudo apt install -y code

## 11. Install D Language and Dub
- Install DMD and Dub:
  sudo apt install -y curl
  curl -fsS https://dlang.org/install.sh | bash -s dmd
- Follow the script's output to add D to your PATH (usually: source ~/dlang/dmd-*/activate)

## 12. Install VS Code Extensions for D
- Open VS Code.
- Press Ctrl+Shift+X to open Extensions.
- Search for and install:
  - "code-d" (D language support)
  - "Native Debug" (for GDB integration)
- Or run in terminal:
  code --install-extension webfreak.code-d
  code --install-extension webfreak.debug

## 13. Configure Debugging (F5)
- Open your D project in VS Code.
- If not auto-generated, create a .vscode/launch.json file:

```
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
- Replace <your_executable> with your binary name.

## 14. Create a Shell Script for New Projects
- Create a file called new_d_project.sh with the following content:

```
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
- Make it executable:
  chmod +x new_d_project.sh

---

You now have a complete D programming environment on Ubuntu, ready for F5 debugging in VS Code!
