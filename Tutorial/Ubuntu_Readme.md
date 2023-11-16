# Table of contents
1. [Git quick setup](#git-quick-setup)
2. [Theme, Icon installtion](#theme-icon-installtion)
3. [zsh installation](#zsh-installation)
4. [Install ibus-bamboo for Vietnamese typing](#install-ibus-bamboo-for-vietnamese-typing)
5. [Install free-typing-error vscode](#install-free-typing-error-vscode)
6. [Conda installation](#conda-installation)
7. [Questasim installation and crack](#questasim-installation-and-crack)
8. [Vivado installation](#vivado-installation)

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
   - `ssh -T git@github.com`
   -  type `yes`
   - If this message "Hi deLini1612! You've successfully authenticated, but GitHub does not provide shell access." is prompt --> success 

# Theme, Icon installtion
- **Theme**: Nordic
- **Icon**: Papirus
- Tutorial youtube [link](https://www.youtube.com/watch?v=2BLLMc4C_PA)
- Download theme:
   1. `sudo apt install gnome-tweaks`
   2. Download zip theme file from [website](https://www.gnome-look.org/). Here we will use Nordic-darker version of [Nordic](https://www.gnome-look.org/p/1267246/)
   3. Create a `.themes` folder in home, then extract the zip theme file to it
- Download icon: Here I will use papirus icon
   1. `sudo add-apt-repository ppa:papirus/papirus`
   2. `sudo apt install papirus-icon-theme`
- Modify dock
   1. `sudo apt install dconf-editor`
   2. Inside dconf-Editor, you can find the dock panel settings by navigating to this schema: _**org > gnome > shell > extensions > dash-to-dock**_

# zsh installation
- Install zsh
   - `sudo apt-get update`
   - `sudo apt-get install zsh -y`
   - Check for the installation: `which zsh`
- Install oh-my-zsh:
   - Install curl: `sudo apt-get install git curl`
   - `sudo curl -L http://install.ohmyz.sh | sh`
- Install and enable Custom theme:
   - Edit the `.zshrc` file as follow: `ZSH_THEME="gallois"`
- Install zsh-autosuggestions
   - `git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions`
   - Add the plugin to the list of plugins inside `~/.zshrc`:
     ```
      plugins=(git
      	zsh-autosuggestions
      	)
     ```
- Set zsh as default terminal: `chsh -s $(which zsh)`

# Install ibus-bamboo for Vietnamese typing
- Install ibus-bamboo
   ```
   sudo add-apt-repository ppa:bamboo-engine/ibus-bamboo
   sudo apt-get update
   sudo apt-get install ibus ibus-bamboo --install-recommends
   ibus restart
   ```
- Then reboot and go to **Setting -> Region & Language -> Choose + -> Vietnamese -> Vietnamese (Bamboo)** to set ibus-bamboo as default typing tool

# Install free-typing-error vscode
- Simply download `.deb` directly from [website](https://code.visualstudio.com/) instead of from snap
- Open downloaded `.deb` file then install it

# Miniconda installation
- Download the installer from [here](https://docs.conda.io/projects/miniconda/en/latest/)
- Make the miniconda installation script executable then run it (choose yes is asked):
  ```
  chmod +x Miniconda3-latest-Linux-x86_64.sh
  ```
- Close and reopen your bash --> Successful

# Questasim installation and crack
- Download zip file questasim (I put in on [onedrive](https://husteduvn-my.sharepoint.com/:u:/g/personal/linh_np206203_sis_hust_edu_vn/EdDv81QSagBApJ9eqKavY4cBGwYQ5YLptkPu2gEICqtLcw?e=R8oZFp)) then extract it
- Navigate to `Mentor Graphics QuestaSim 10.7c Linux64` folder, then run:
  ```
  chmod +x install.linux64
  ./install.linux64
  ```
- Then install it in GUI app:
   - Click Install to install it. Then, click Browse to select target location
   - Select both of releases
   - Select All Platforms
   - Select all products
   - Finally, Agree and Install → Exit
- Crack questasim:
   - Copy 3 files (MentorKG.exe, MGLS.DLL, Patch_DownLoadLy.iR.bat) from folder `Crack/Others/2` and Paste in `../questasim/linux_x86_64`
   - Install wine frome [here](Install wine: https://wiki.winehq.org/Ubuntu)
   - Open Terminal in linu_x86_64, then run `wine Patch_DownLoadLy.iR.bat`
        > Note: Install everything if have request
   - Remove comment 2 first lines in LICENSE.TXT
   - Add path of your `questasim/` folder to 2nd line as example `VENDOR mgcld /home/delini/questasim/questasim` then Save as `LICENSE.dat` into folder `/questasim`
   - Add path to `~/.zshrc` as the following then `source ~/.zshrc` 
     ```
     export PATH=$PATH:/home/delini/questasim/questasim/bin/
     export LM_LICENSE_FILE=/home/delini/questasim/questasim/LICENSE.dat
     ```
  - Download SFK from [here](http://stahlworks.com/downloads.html): file SFK for Linux (i686 64 bits executable)
  - Move file `sfk-linux-64.exe` into `/questasim` then `chmod +x sfk-linux-64.exe`
  - Run sfk (install everything if have request)
    ```
    sudo wine ./sfk-linux-64.exe rep -yes -pat -bin /5589E557565381ECD00000008B5508/31C0C357565381ECD00000008B5508/ -bin /5589E557565381ECD8000000E8000000005B81C3/33C0C357565381ECD8000000E8000000005B81C3/ -bin /41574989FF415641554154554889CD534489C3/33C0C389FF415641554154554889CD534489C3/ -dir /home/delini/questasim/questasim
    ```
   - Then Ctrl + C to interupt process → done
   - Install LSB `sudo apt install lsb` then run `sudo ./linux_x86_64/mgls/bin/lmgrd -c ./LICENSE.dat`
   - **Possible error and how to fix**
      1. Can’t make directory usr/tmp/.flexlm, errno: 2(No such file or directory)
        > `sudo ln -s /tmp /usr/tmp`
      2. (lmgrd) Failed to open the TCP port number in the license
        > Open file LICENSE.dat and replace 27001 to 27002 (if still failed, 2700(3, 4, 5, …))
      3. Cannot open lock file. errno=11 (/var/tmp/lockmgcld): Resource temporarily unavailable
        > ```
        > cd /var/tmp
        > ls
        > sudo mv lockmgcld lockmgcld.bak
        > ```
        > Open LICENSE.dat and replace 27001 to 27002 (if still failed, 2700(3, 4, 5, …))
- Create an alias in `~./zshrc` to use alias (instead of remember such a long command), for example
  ```
  alias get_vsim="cd /home/delini/questasim/questasim && sudo ./linux_x86_64/mgls/bin/lmgrd -c ./LICENSE.dat"
  ```

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
7. **Reload** license: Do step 5 again when you need to reload license
