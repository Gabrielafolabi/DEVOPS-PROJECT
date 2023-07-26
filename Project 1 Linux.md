## LINUX COMMAND
LINUX is an operating system or a kernel distributed under an open-source license. Its functionality list is quite like UNIX. The kernel is a program at the heart of the Linux operating system that takes care of fundamental stuff, like letting hardware communicate with software

On this project i will be showing some useful Linux Command to perform some specific tasks

### 1. Sudo Command:

sudo (Super User DO) command in Linux is generally used as a prefix for some commands that only superusers are allowed to run. If you prefix any command with “sudo”, it will run that command with elevated privileges or in other words allow a user with proper permissions to execute a command as another user, such as the superuser.

example of sudo command
#### sudo apt upgrade : 
sudo apt upgrade command is asking our Linux machine to go browse lists of updated packages and look for any software that can be upgraded, if there are some, then the latest version of those software packages are installed in our computers.


<img width="377" alt="sudo_upgrade" src="https://github.com/gallant001/DEVOPS-PROJECT/assets/35296784/c8dc8fd4-f18e-4f3d-9f66-c2b448445b3e">


### 2 pwd Command :

This command is used to show the path of your current working directory. Here , my working directory is /home/vboxuser, as seen on the screenshot.


<img width="353" alt="pwd" src="https://github.com/gallant001/DEVOPS-PROJECT/assets/35296784/5efe761b-b2ea-49b4-8516-b35fc1a7ab29">

### 3 ls Command: 
ls : This command lists files and directories within a system.

ls -R : List all the files in the sub directories

ls -a : Show hidden files in addition to the visible ones

ls -lh :Shows the file sizes in easily readable format such as MB, GB, TB.

ls -t : Sort files and directories by their last modification time, displaying the most recently modified ones first.

ls -l : Long format that displays detailed information about files and directories.

see below screenshots:

<img width="344" alt="ls" src="https://github.com/gallant001/DEVOPS-PROJECT/assets/35296784/0b10ac4d-50d7-4a3d-86e8-60df4f636e61">

<img width="323" alt="ls 2" src="https://github.com/gallant001/DEVOPS-PROJECT/assets/35296784/428bc9f4-505f-4533-aa50-700437f19845">

### 4. cd Command:
This command is known as change directory. It is used to navigate through the linux directories. That is, to move efficiently from the current working directory to different directories.

We use `..` this as an argument in `cd` command which is used to move to the parent directory of current directory, or the directory one level up from the current directory.


<img width="347" alt="cd" src="https://github.com/gallant001/DEVOPS-PROJECT/assets/35296784/01560d02-522d-4823-a80a-58358d54b6d7">

### 5. Cat Command: 
This Cat(concatenate) command reads data from the file and gives its content as output.


<img width="356" alt="cat" src="https://github.com/gallant001/DEVOPS-PROJECT/assets/35296784/c4087cb5-e72b-461a-8ffa-712deb5721da">


### 6. cp Command:
The cp command is used to copy files or directories from one location to another. When copying the file, specify the soure of the file or directories you want to
, Also the destination or location you want to copy the file to.

see below example: I am copying "Learning_Linux" file from Desktop to "DevOps_Folder/AYotemi" 



<img width="362" alt="image" src="https://github.com/gallant001/DEVOPS-PROJECT/assets/35296784/4987297d-db39-48e2-a4c8-a882a011803c">

