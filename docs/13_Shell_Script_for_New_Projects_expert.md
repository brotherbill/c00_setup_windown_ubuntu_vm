c:/dev/ubuntu/docs/13_Shell_Script_for_New_Projects_expert.md

# Ubuntu VM Setup (Expert Checklist)

# 13. Shell Script for New Projects (Expert)

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
