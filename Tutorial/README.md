# Tutorial: Install - Uninstall Majaro i3 - Common command

## Uninstall clearly Manjaro i3

1. Restart pc and go to **"BIOS/UEFI setting"** section and remove Manjaro from Bootable list
2. Boot to Window, then ***Window+R*** and type **"diskmgmt.msc"**
3. In **Disk Management**, delete the Volume you use to install Manjaro
4. Find **"cmd"** in **Start Menu** and run as admin
5. `bcdedit /enum all` them ***Ctr+F*** and find **"Manjaro"**, copy the code in *identifier* part
6. `bcdedit /delete {thecode}`
7. Go to Boot EEFI section of Window and assign hiden letter Z for it (type those code)

   `diskpart`

   `list disk`
   
   `select disk X` (with X is the disk install ổ Windows)
    
   `list volume`
   
   `select volume Y` (with Y is EFI Volume of Windows [FAT32, 100MB, System])
   
   `assign letter=Z`
   
    `exit`
8. Delete Manjaro: `rmdir /S Z:\efi\manjaro`
9. Unassign letter Z (as step 7, but use `remove letter=Z` instead of assign)
10. Change backgrounf: `nitrogen /home/nplinh/Pictures/Wallpaper` (path link of the directory consist image)

## Must-do things when install Manjaro i3
1. Update: `pacman -Syu`
2. Install pkg from **"installlist.txt"** after cd to the directory include txt file

  `sudo pacman -S --needed - < installist.txt`
 
3. Uninstall Palemoon: `sudo pacman -Rcns palemoon-bin`
4. Download font
5. Install AUR packages using yay: ibus-bamboo
6. Modify **lxapperance** and update file config
7. Change time (Avoid conflict with Window time): `timedatectl set-local-rtc 1`

## Tips and some useful command
1. Command with yay
* Update pkg: `yay`
* Remove pkg: `yay -Rs name_of_pkg`
* Clean: `yay -Yc`

2. To run multi-command by bash file
* Creat a .sh file include commands
* `sudo chmod +x bashfile.sh`
* Run bash file: `bash bashfile.sh`
