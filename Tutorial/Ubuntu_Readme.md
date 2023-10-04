# Git quick setup
Check [git_tutorial](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys)
1. Set up global env:
   - `git config --global user.name "deLini1612"`
   - `git config --global user.email "ling.npl.1612@gmail.com"`
   - `git config --list` to check env
2. Check for existing SSH key:
   - `ls -al ~/.ssh`
3. Generating a new SSH key:
   - `ssh-keygen -t ed25519 -C "ling.npl.1612@gmail.com"`
   - Enter for all questions
   - `eval "$(ssh-agent -s)"`
   - `ssh-add ~/.ssh/id_ed25519`
4. Add SSH key to your account on Github:
   - `cat ~/.ssh/id_ed25519.pub` and copy contents of the id_ed25519.pub file displayed in the terminal to your clipboard
   - Following [tutorial](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
5. Testing your SSH connection:
   - `ssh -T git@github.com
   -  type `yes`
   - If this message "Hi deLini1612! You've successfully authenticated, but GitHub does not provide shell access." is prompt --> success 

# Theme, Icon, Font installtion

# zsh installation

# Conda installation

# Questasim installation

# Vivado installation
1. Install some packet
   ```
   sudo apt-get update -y
   sudo apt-get install -y libtinfo5
   sudo apt-get install build-essential
   sudo apt-get install lib32stdc++6
   sudo apt-get install make
   ```
2. Download file setup vivado
   - Go to (vivado download site)[https://www.xilinx.com/support/download.html] and select the appropriate version of Vivado
   - Login to your account and download file (extract it if it a zip file)
   - Grant permissions for the installation file to be downloaded and run it. Using those command:
       ```
       cd [your_downloaded_file_path]
       sudo chmod +x [fileName]
       sudo ./[fileName]
       ```
3. Install Vivado:
   - Click ***ignore*** in welcome page if you don't want to update your version to latest verdion
   - Click ***next*** until "***Slect Edition to install***" page then choose ***Vivado HL Design Edition***
   - Choose all options in "***Vivado HL Design Edition***" page and install it (have to wait for very long time)
4. Add PATH and download driver install file
   - Open your `~/.bashrc` (or `~/.zshrc`) then add the following path and save (modify the version with your version)
       ```
       export PATH=$PATH:/tools/Xilinx/Vivado/2019.2/bin
       source /tools/Xilinx/Vivado/2019.2/settings64.sh
       
       ```
   - To install driver cable:
       ```
       cd /tools/Xilinx/Vivado/[your_version]/data/xicom/cable_drivers/lin64/install_script/install_drivers
       sudo ./install_drivers
       ```
5.Install and load License
You can see [this video](https://www.youtube.com/watch?v=1uJzjvgTQUk&t=715s) or [Vivado site](https://docs.xilinx.com/r/en-US/ug973-vivado-release-notes-install-license/Create-and-Generate-a-License-Key-File) for tutorial
- View machine configuration and network card address. You can use `ip a` or `ifconfig` command
- Visit [this link](https://www.xilinx.com/getlicense) to get the lisence
- Choose all lisence then choose ***Generate License***
- In "***2. SYSTEM INFORMATION***" section, select your Ethernet card address (if it not have pre-populated system information, just add a host)
    - run Vivado License Manager on the machine that serves as the license host to get the correct ID
- Click next, Review your selections, and click Next
- When you finish generating the licenses, you receive a confirmation message summarizing your licensing activity then get lisence file (in yoyr email)
- In Vivado Lisence Manager: choose ***Load lisence*** then choose ***Copy Lisence*** and browse the lisence file you just download

6. **DONE!!!**. Now you can run vivado just by running `vivado` command
