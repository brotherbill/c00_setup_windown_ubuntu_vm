c:/dev/ubuntu/docs/13_Shell_Script_for_New_Projects_beginner.md

# Ubuntu VM Setup (Beginner Checklist)

# 13. Shell Script for New Projects (Beginner)

1. Create a file named `new_d_project.sh` with the following content:
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
2. Make the script executable:
   ```bash
   chmod +x new_d_project.sh
   ```

This script helps you quickly set up new D projects with debugging support in VS Code.