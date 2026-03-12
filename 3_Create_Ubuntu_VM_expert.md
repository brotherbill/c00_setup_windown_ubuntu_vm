# Ubuntu VM Setup (Expert Checklist)

# 3. Create Ubuntu VM (Expert)

## Virtual machine name and operating system (first wizard page)

1. Ensure folders exist: `C:\dev\ubuntu\iso\` and `C:\dev\ubuntu\vms\`
2. Download latest Ubuntu LTS ISO from https://ubuntu.com/download/desktop and place in `C:\dev\ubuntu\iso\`
3. Open **Oracle VirtualBox**
4. Click **New**
5. Name: `UbuntuD-VM` (or preferred)
6. VM Folder: `C:\dev\ubuntu\vms\`
7. ISO Image: select from `C:\dev\ubuntu\iso\`
8. Type: `Linux`, Version: `Ubuntu (64-bit)` (auto-detected)
9. Uncheck **Proceed with Unattended Installation**
10. Click **Next**

## Specify virtual hardware (second wizard page)

1. Base Memory: **4096–8192 MB** (do not exceed half system RAM)
2. CPUs: **2** (leave at least half for Windows)
3. Disk Size: **50 GB**
4. Leave **Use EFI** unchecked
5. Click **Next**

## Summary (third wizard page)

1. Click **Finish**

---

You have created a new Ubuntu Virtual Machine (VM).
