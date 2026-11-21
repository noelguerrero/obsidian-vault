
### Basic Linux Command

|Command|Description|Syntax|Example Command|
|---|---|---|---|
|`mv`|**Moves a file or folder to another location, or renames it.** Think of it as the "Cut & Paste" or "Rename" command.|`mv <source> <destination>`|`mv report.txt Documents/`|
|`chmod`|**Changes who can read, write, or execute a file.** Often used to make a script executable.|`chmod <permissions> <file>`|`chmod 755 script.sh`|
|`chown`|**Changes who owns a file or folder.** Useful when another user or root owns a file and you need to transfer ownership.|`chown <owner>:<group> <file>`|`sudo chown noel:noel file.txt`|
|`dd`|**Copies data exactly from one place to another, byte by byte.** Commonly used to create bootable USB drives or clone disks. Be careful—it can overwrite data.|`dd if=<input> of=<output>`|`sudo dd if=ubuntu.iso of=/dev/sdb`|
|`pwd`|**Shows the folder (directory) you are currently working in.** It tells you "Where am I?" in the terminal.|`pwd`|`pwd`|
|`ps`|**Shows the programs (processes) that are currently running on your computer.** Useful for troubleshooting or checking if an application is active.|`ps [options]`|`ps aux`|
|`su`|**Switches to another user account, usually the root (administrator) account.** You'll need that user's password.|`su [username]`|`su root`|
|`sudo`|**Runs a command with administrator (root) privileges.** You'll usually use this when installing software or changing system settings.|`sudo <command>`|`sudo apt update`|
|`grep`|**Searches for specific words or text inside a file or command output.** Great for finding information quickly.|`grep <pattern> <file>`|`grep "error" logfile.txt`|
|`ifconfig`|**Displays information about your network connections**, such as IP addresses. It can also configure network interfaces. _(Older command; `ip address` is now recommended.)_|`ifconfig [interface]`|`ifconfig`|
|`apt-get`|**Downloads, installs, updates, or removes software packages** on Ubuntu and other Debian-based Linux systems.|`apt-get <action> <package>`|`sudo apt-get install nginx`|
|`iwconfig`|**Shows information about your wireless (Wi-Fi) network adapter**, such as the connected network and signal strength.|`iwconfig [interface]`|`iwconfig`|
|`shutdown`|**Turns off, restarts, or schedules your computer to shut down.**|`shutdown <option>`|`sudo shutdown -r now`|
|`passwd`|**Changes a user's password.** If no username is provided, it changes your own password.|`passwd [username]`|`passwd noel`|
|`cat`|**Displays the contents of a text file in the terminal.** It can also combine multiple files into one output.|`cat <file>`|`cat notes.txt`|
|`man`|**Opens the manual (help page) for a command.** Use it when you want to learn what a command does or see all of its options.|`man <command>`|`man grep`|

****
### File Directory Commands

| Command | Description                                           | Syntax                      | Example Command            |
| ------- | ----------------------------------------------------- | --------------------------- | -------------------------- |
| `ls`    | Lists the files and folders inside a directory.       | `ls [options] [directory]`  | `ls -l`                    |
| `cd`    | Changes your current directory (folder).              | `cd <directory>`            | `cd Documents`             |
| `mkdir` | Creates a new directory (folder).                     | `mkdir <directory>`         | `mkdir Projects`           |
| `cp`    | Copies a file or folder from one location to another. | `cp <source> <destination>` | `cp file.txt Documents/`   |
| `mv`    | Moves or renames a file or folder.                    | `mv <source> <destination>` | `mv report.txt Documents/` |
| `rm`    | Deletes a file or folder.                             | `rm <file>`                 | `rm notes.txt`             |
| `grep`  | Searches for text in a file or command output.        | `grep <pattern> <file>`     | `grep "error" log.txt`     |
| `cat`   | Displays the contents of a text file.                 | `cat <file>`                | `cat notes.txt`            |
| `pwd`   | Display your current directory                        | `pwd`                       | `pwd`                      |

**Additional Option Used in File directory**:
- `-l` it display the file size, permission, ownership, date of creation, and more
- `-a` show all files
- `>` - redirect, its use when you place or replace a text in a file
- `>>` - append, its use when you add a text to specific file.
- `-r` - recursive, it is paired with `rm` to delete a specific directory and everything inside of it.

**Syntax that encountered in File directory**
- `ls -l` - to see all the details of the file or folder
- `ls -la` - to display all the files, including the hidden files.
- `echo Hello World > text.txt` - it create a hello world text in the text.txt file.
	- note: if the file is not exist, it automatically creates one.
- `ls -l text.txt` - to show if a file is exist
- `cat text.txt` - to display the contents if the specific file.
- `echo Add another text >> text.txt` - to add a text to specific file.
- `rm -r folder1` - it deletes the `folder1` and everything inside of it.
- `mv text.txt cyops_folder1` - move a file to specific folder.
- `mv textNameBefore.txt textNameAfter.txt` - rename a file.
****
### Navigating at the Directory
- `cd` - back
- `cd .` goes to the current directory.
- `cd ..` goes back / goes to the parent directory
- `cd [path]` - goes to the specific path, 
	- ex: `cd ~/downloads/folder_1`
- `cp` - use to copy and paste a specific file.
	- syn: `cp [file] [path]`, ex: `cp text.txt folder1/` 
- `rm` - use to delete a file or folder/directory
	- syn: `rm [fileName]` ex: `rm text.txt`
****
### Terminal Codes that i encounter
- `ls` - to show directory
- `sudo apt update` - check if there is an new package available.
- `sudo apt upgrade` - install the new package
- `echo [string/text] > [filename]` - to output/upload a text to a specific file.
	- ex: `echo Hello World > text.txt`

****
### `man` Terminal Codes

- `man man` - to display manual of the command line
- `man cp` - To display the manual of `cp` commands
Note: `cp` is a command use to copy a file and paste to another location.
- `man ls` - manual for `ls` command

****
