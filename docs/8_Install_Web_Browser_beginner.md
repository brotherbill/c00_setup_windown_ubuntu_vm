c:/dev/ubuntu/docs/8_Install_Web_Browser_beginner.md

# Ubuntu VM Setup (Beginner Checklist)

# 8. Install a Web Browser (Beginner)

1. Ubuntu comes with Firefox pre-installed.
2. To install Google Chrome:
   ```bash
   sudo apt update && sudo apt install -y wget
   wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
   sudo apt install -y ./google-chrome-stable_current_amd64.deb
   ```
3. Follow any prompts to complete the installation.

You can use either browser in your VM.