# Tutorial: Install - Uninstall Majaro i3 - Common command

## Uninstall clearly Manjaro i3

1. Restart pc and go to **"BIOS/UEFI setting"** section and remove Manjaro from Bootable list
2. Boot to Window, then ***Window+R*** and type **"diskmgmt.msc"**
3. In **Disk Management**, delete the Volume you use to install Manjaro
4. Go to Boot EEFI section of Window and assign hiden letter Z for it (type those code): ***Window+R*** and type **"diskpart"**

   `list disk`
   
   `select disk X` (with X is the disk install ổ Windows)
    
   `list volume`
   
   `select volume Y` (with Y is EFI Volume of Windows [FAT32, 100MB, System])
   
   `assign letter=Z`
   
    `exit`
8. Open cmd (run as admin) and delete Manjaro: `rmdir /S Z:\efi\manjaro`
9. Unassign letter Z (as step 7, but use `remove letter=Z` instead of assign)

## Must-do things when install Manjaro i3
1. Update: `pacman -Syu`
2. Install pkg from **"installlist.txt"** after cd to the directory include txt file

  `sudo pacman -S --needed - < installlist.txt`
 
3. Uninstall Palemoon: `sudo pacman -Rcns palemoon-bin`
4. Download font
5. Install AUR packages from **"yay_install.txt"** using yay: `yay -S $yay_install.txt`
6. Modify **lxapperance** and update file config
7. Change time (Avoid conflict with Window time): `timedatectl set-local-rtc 1`
8. Change background: `nitrogen /home/nplinh/Pictures/Wallpaper` (path link of the directory consist image)
9. Linking zscroll to /bin: 
   - `which zscroll` -> get the path
   - `sudo ln -s <path> /bin`

## Install miniconda and creat env
1. Download the [installer](https://docs.conda.io/en/latest/miniconda.html#linux-installers)
2. Verify your installer hash: `cd \<location> && sha256sum <filename>` with <location> is the location you download the installer, <filename> is the file installer you just downloaded
3. Open terminal then run 'bash <filename>' with <filename> is the file installer you just downloaded
4. Follow the prompts on the installer screens
5. Close and then re-open your terminal, check by run: `conda list`
6. Creat new env: `conda create -n <name> python=<version>` with <name> is the name of env, <version> is the version of python
7. Run `conda activate <name>` with <name> is the name of env

## Tips and some useful command
1. Command with yay
* Update pkg: `yay`
* Remove pkg: `yay -Rs name_of_pkg`
* Clean: `yay -Yc`
* Install list of pakage: `yay -S $(cat file_name.txt)`

2. To run multi-command by bash file
* Creat a .sh file include commands
* `sudo chmod +x bashfile.sh`
* Run bash file: `bash bashfile.sh`
