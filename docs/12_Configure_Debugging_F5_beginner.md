c:/dev/ubuntu/docs/12_Configure_Debugging_F5_beginner.md

# Ubuntu VM Setup (Beginner Checklist)

# 12. Configure Debugging (F5) (Beginner)

1. Open your D project in VS Code.
2. If not auto-generated, create a `.vscode/launch.json` file with the following content:
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
3. Replace `<your_executable>` with your program's binary name.

This enables F5 debugging for your D projects.