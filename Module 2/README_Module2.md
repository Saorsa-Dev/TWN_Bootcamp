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
cd [directory]= change folder
mkdir [directory] = make folder
touch [filename] = create file
rm [filename] = remove file
rm -r [directory] = remove folder
clear = clears terminal
cd ~ = return to home directory
mv [filename] [new filename] = rename file
cp -r [dirname] [new_dirname] = Copy dirname to new dirname
ls -R {directory] = show directory and contents
Ctrl + c = kill command
history = display previous commands
ls -a = show all (including hidden)
cat [filename] = display the file content
sudo = allows regular users to run programs with the security privileges of the superuser or root
sudo adduser [user] = add new user
sudo addgroup [group] = add new group

FYI bash_history file stores terminal history

### Demo 3 - Package Manage - Installing Software on Linux

