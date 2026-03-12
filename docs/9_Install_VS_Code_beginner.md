c:/dev/ubuntu/docs/9_Install_VS_Code_beginner.md

# Ubuntu VM Setup (Beginner Checklist)

# 9. Install VS Code (Beginner)

1. Open a terminal in Ubuntu.
2. Run the following commands one at a time:
   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
   sudo install -o root -g root -m 644 packages.microsoft.gpg /usr/share/keyrings/
   sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
   sudo apt update
   sudo apt install -y code
   ```
3. Launch VS Code from the applications menu or by typing `code` in the terminal.