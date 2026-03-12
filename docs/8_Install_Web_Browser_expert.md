c:/dev/ubuntu/docs/8_Install_Web_Browser_expert.md

# Ubuntu VM Setup (Expert Checklist)

# 8. Install a Web Browser (Expert)

1. Ubuntu comes with Firefox
2. To install Chrome:
   ```bash
   sudo apt update && sudo apt install -y wget
   wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
   sudo apt install -y ./google-chrome-stable_current_amd64.deb
   ```
