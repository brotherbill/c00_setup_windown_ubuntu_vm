c:/dev/ubuntu/docs/4_VM_Settings_Before_First_Boot_expert.md


# Ubuntu VM Setup (Expert Checklist)

# 4. VM Settings Before First Boot (Expert)

1. Open VirtualBox, select **Ubuntu VM,** **Settings**.
2. Switch to **Expert Mode**.

**General > Features**

- Shared Clipboard: **Bidirectional**
- Drag-and-Drop: **Bidirectional**

**Display > Screen**
	- Video Memory: **128 MB**
	- Graphics Controller: **VMSVGA**
	- **Enable 3D Acceleration**

**Storage**
	- Ensure **Ubuntu ISO** is attached to IDE controller, from Step 3

**Network**
	- Attached to:  **NAT** (or Bridged if needed)

Use these settings for best integration and performance. Adjust as needed.
