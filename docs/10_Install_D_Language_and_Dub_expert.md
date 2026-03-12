c:/dev/ubuntu/docs/10_Install_D_Language_and_Dub_expert.md

# Ubuntu VM Setup (Expert Checklist)

# 10. Install D Language and Dub (Expert)

1. In terminal:
   ```bash
   sudo apt install -y curl
   curl -fsS https://dlang.org/install.sh | bash -s dmd
   ```
2. Follow script output to add D to PATH (usually: `source ~/dlang/dmd-*/activate`)
