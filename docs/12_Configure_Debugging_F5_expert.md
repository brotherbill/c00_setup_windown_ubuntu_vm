c:/dev/ubuntu/docs/12_Configure_Debugging_F5_expert.md

# Ubuntu VM Setup (Expert Checklist)

# 12. Configure Debugging (F5) (Expert)

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
