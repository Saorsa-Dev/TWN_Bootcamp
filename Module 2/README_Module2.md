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
8.sudo chown <username> <filename> = Change user ownership
9. sudo chown <username>:<groupname> <filename> = Change user/group ownership
10. sudo chgrp <username> <filename> = Change group ownership
11. r read / w write / x execute / - none -- characters represent file/folder permissions
12. sudo chmod -x api = remove execute permissions on api folder
13. sudo chmod g-w <filename> = remove write (w) permission from group (g) on file
14. sudo chmod g+x <filename> = add execute (x) permission to group (g) on file
15. sudo chmod u+x <filename> = add execute permissions to user (u) on file
16. sudo chmod o+x <filename> = add execute permissions to other (o) users on file
17. sudo chmod a-x <filename> = remove execute permissions to all (a) users on file
18. sudo chmod g=rwx <filename> = add read/write/execute permissions to group on filename

### Demo 6: Pipes & Redirects 

Every program has the concept of input/output. Output of one program/command can become the input of another program/command, using the | (pipe) command -- called "piping"

1. cat /var/log/syslog | less = send contents of the syslog directory to the less program
2. history | less
3. history | grep sudo = globally search the results of hoitory for regular expression (grep) in the word sudo and print out result
4. history | grep sudo | less = piping can keep going between programs
5. ls /usr/bin | grep java = search for app called java in the /usr/bin directory
6. Redirects - redirect results of command execution into a file, for example, using the greater than symbol: history | grep sudo > sudo-commands.txt
7. Use >> syntax to append existing file, not overwrite which is the default with >
8. Useful use case: collecting logs of program printing to command line, can send to file to store/share for later analysis
9. Every program has 3 built-in streams: STDIN (0); STDOUT (1); STDERR (2)

### Demo 7: Shell Scripting Part 1 - Intro to Shell Scripting

Shell scripts have file extension .sh. Shell is a program that interprets and executes the various commands that we type in the terminal and translates them so the OS kernel can understand them.

1. sh (Bourne Shell) - /bin/sh
2. Bash (Bourne again shell) - /bin/bash - improved version of sh, default shell program for most Unix systems
3. Bash is both a shell program and scripting language - bash and shell used interchangeably
4. Shebang - file header is #!/bin/bash (location of required shell - needs to be installed to work) -- shebang shortened for sharp-bang
5. To execute the script, the syntax is ./setup.sh (must have execute permission on file)

### Demo 8: Shell Scripting Part 2 - Basic Concepts & Syntax

1. variable_name=value = Assigns value to  variable
2. Refer to variable like so: echo "using file $file_name to configure something"
3. config_files=$(ls config) -- storing output of other commands as variables
4. Use of Conditionals to alter control flow/handle different conditions/results, e.g. execute program only if condition is true. Referred to as if-then-else statements:
   if [ -d "config" ]
   then
      echo "reading config directory contents"
      config_files =$(ls config)
   else
      echo "config dir not found. Creating one..."
      mkdir config
   fi
5. Passing parameters/ arguments to a script, e.g. ./setup.sh setup-scripts admin -- where admin is a parameter value accepted by the script
6. Reading user input in script, e.g.
   read -p "Please enter password: " user-pwd (-p = prompt)
   echo "Thanks for providing your password, $user_pwd"
7. $* -- represents all variables as a single string
8. $# -- total number of variables
9. Shell loops -- use whenever you are working with a list of items, called a for loop. Operates on a list of items, repeats set of commands for every item in list. E.g.
   for param in $*
      do
         echo $param
      done
10. While loop - executes set of commands repeatedly until condition is met (need a break command to exit loop or will run forever)
    while condition
    do
       statement(s) to be executed while command is true
    done

### Demo 9 - Shell Scripting Part 3 -  Basic Concepts & Syntax

1. Use functions to reuse more complex logic in your code
   function <name> () {
      list of commands
   }
2. Must call the function to use them
3. You can accept parameters in functions using $1, $2 etc., which you can assign to variables in the function
4. Can comment out lines in your shell script using # symbol - good to describe what your code is doing with comments
5. Best practices with functions:
   - Don't use too many parameters
   - Apply Single Responsibility Principle: function should do just one thing
   - Declare variables with a meaningful name for positional parameters within your function
6. Booleans - a data type that can have only two values, true or false. True or false are keywords in Bash and will recognized as boolean values
7. Functions can return value, using keyword return
8. $? - captures value returned by last command




