# Module 2 - Operating Systems & Linux Basics

### Demo 1 - Setup VirtualBox & Linux Virtual Machine

After installing Oracle VirtualBox on my local Windows machine, I then installed a Linux Ubuntu VM, preparimg the VM container first and then downloading the Ubunto ISO and mapping the ISO image to my VM to allow me to install the OS.

Got my bi-directional clipboard working by installing Virtual Box extension pack/ Guest Additions (was a little challenging to get this working but figured it out in the end). Even s, every so often the clipboard function stops working and I have to run this command to get it working again: pkill VBoxClient && VBoxClient --clipboard

I also installed VS Code on my Ubuntu instance, my running the following commands:

1. sudo apt update
2. sudo apt install software-properties-common apt-transport-https wget -y


### Demo 2 - Basic Linux commands

pwd = Show current directory
ls = list folders
cd <directory>= change folder
mkdir <directory> = make folder
touch <filename> = create file
rm <filename> = remove file
rm -r <directory> = remove folder
clear = clears terminal
cd ~ = return to home directory
mv <filename> <new filename> = rename file
cp -r <dirname> <new_dirname> = Copy dirname to new dirname
ls -R <directory> = show directory and contents
Ctrl + c = kill command
history = display previous commands
ls -a = show all (including hidden)
cat <filename> = display the file content
sudo = allows regular users to run programs with the security privileges of the superuser or root
sudo adduser <user> = add new user
sudo addgroup <group> = add new group

FYI bash_history file stores terminal history

### Demo 3 - Package Manager - Installing Software on Linux

Summary: Package Managers are included in every Linux distribution. Their job is to download, install and update software from a repository. On Ubuntu, APT package Manager is available. APT-GET and APT are both package managers, APT is more modern and not always installed but easier to use and installs software as it should be on Linux (distributed and smaller size as dependencies shared across applications). Note: always update the package index before upgrading or installing new packages, using **sudo apt update**. Alternative software install options are Ubuntu Software Centre (includes a GUI) and Snap Package Manager, also known as Snappy. If you cannot install your apps using any of these options you may need to add a repository (especially for very new apps/versions).

1. Installed Jave on Ubuntu VM (VirtualBox) using: sudo apt install openjdk-25-jre-headless (to remove you can use sudo apt remove openjdk-25-jre-headless)
2. Installed IntelliJ IDEA from App Center
3. Installed VS Code using snap using: sudo snap install --classic code
   
### Demo 4: Vi & Vim Text Editor

Built in text editors in Linux - Vim is richer. Useful for quick small adjustments when currently working in CLI. Faster to create/edit at the same time. Useful when there is no visual text editor on a remote server. Also useful when working with GIT and with Kubernetes Config files. 

1. Installed Vim using: sudo apt install vim
2. Edited files using vim <filename>
3. Used Command mode (default) for navigating, searching etc. and Insert mode - enter/edit text. Use "i" for Insert. Use "Esc" to get back to Command mode, followed by typing :wq (write/quit) or :q! (quit without save).
4. Create new file using vim <new filename>
5. In Command mode can delete a line by typing "dd" = Delete entire line or "d10" = Delete next 10 lines
6. Type A = Jump to end of line and switch to Insert mode
7. Type 0 = Jump to start of the line
8. Type /pattern in Command mode to search/find text
9. Type :%s/old/new = Replace old with new throughout the file


### Demo 5: Users & Permissions - Part 1 & 2

Don't run services using root! Run them with service account users - best practice. For Linux, should use use multi-user set up for servers - only set permissions required for each user, and easier to track actions by user - traceability. Group users into groups and apply permissions at group level. User info stored in /etc/passwd

1. cat etc/passwd
2. sudo adduser <username> = create new user
3. sudo passwd <username> = change password of a user
4. su <username> = login as username
5. su = login as root
6. sudo groupadd <groupname> = create new group
7. sudo usermod [OPTIONS] <username> = Modify user account, e.g sudo usermod -g devops tom (changes the primary group of tom to devops)
8. 
### Demo 3 - Package Manage - Installing Software on Linux

