# Basic Linux Summary

## Command Line

The Linux command line is a text interface to your computer.

Also known as shell, terminal, console, command prompts and many others, is a computer program intended to interpret commands.

Allows users to execute commands by manually typing at the terminal, or has the ability to automatically execute commands which were programmed in “Shell Scripts”.

### Command Syntax

Commands can be run by themselves, or can accept arguments to alter their behavior.
A typical syntax can look similar to this:

`command [-argument] [--long-argument] file`

### Notes

There are a few important things to keep in mind when using a Linux shell:

- **It is case sensitive**

In a Linux shell, commands, files and directory names are case sensitive meaning that typing `pwd` will print the current working directory and typing `PWD` will return an error similar to `-bash: PWD: command not found`

- **The `/` (forward-slash) is a special character used as directory separator**

The Linux CLI is full of special characters, and we will go into more detail about this topic. For the moment, just keep this in mind.

- **File extensions don't matter**

If you come from a windows background, a file with .exe extension means it is an executable file. In Linux CLI, the file kind is determined automatically. (By reading the file header).

- **Nearly every Linux command supports `--help` argument**

During your journey with the CLI, you will often wonder "What argument do I need to do X?" The answer is just a `--help` away.

## Basic Commands

### 1. ls

List directory contents. If you know windows you would know that the command `dir` is used to list the contents in a directory. In Linux, the `ls` command is used to list out files and directories. Some versions may support color-coding. The names in blue represent the names of directories.

`ls -l | more -` this helps to paginate the output so you can view page by page. Otherwise the listing scrolls down rapidly. You can always use ctrl c to go back to the command line.

Example

```$ ls -l filename
-rwxrwxrwx 1 user user 52143894 Dec  2 08:49 filename
```

### 2. cd

Change the current directory. The forward slash is to be used in Linux. The example is a Linux directory that comes with all versions of Linux.

When you use `ls -l` you will be able to see more details of the contents in the directory

It will list down the

- Permissions associated with the file
- The owner of the file
- The group associated with the file
- The size of the file
- The time stamp
- The name of the file

Example

```~$ cd /var/log
/var/log$ ls -l
total 368
-rw-r--r-- 1 root      root               434 Apr 23  2020 alternatives.log
drwxr-xr-x 1 root      root              4096 Mar 27 09:00 apt
-rw-rw---- 1 root      utmp                 0 Apr 23  2020 btmp
drwxr-xr-x 1 root      root              4096 Apr  8  2020 dist-upgrade
-rw-r--r-- 1 root      root             80231 Mar 27 09:00 dpkg.log
drwxr-sr-x 1 root      systemd-journal   4096 Apr 23  2020 journal
drwxr-xr-x 1 landscape landscape         4096 Apr 14  2020 landscape
-rw-rw-r-- 1 root      utmp            292292 Mar 26 21:49 lastlog
drwxr-xr-x 1 mongodb   mongodb           4096 Mar 27 08:55 mongodb
drwxr-s--- 1 redis     adm               4096 Mar 26 23:57 redis
drwxr-x--- 1 root      adm               4096 Apr 14  2020 unattended-upgrades
-rw-rw-r-- 1 root      utmp                 0 Apr 23  2020 wtmp
```

### 3. grep

Find text in a file. The grep command searches through many files at a time to find a piece of text you are looking for.

`grep PATTERN [FILE]`

Example

```
$ grep 'progress' transaction.log
progress
```

### 4. sudo command

`sudo` - if you just need to run something as a super user, you can use the sudo command. This will allow you to run the command in elevated rights and once the command is executed you will be back to your normal rights and permissions.

Example - `shutdown` command the shutdown command safely turns off the computer system.

`sudo shutdown 2` - shutdown and turns of the computer after 2 minutes
`sudo shutdown -r 2` - shuts down and reboots in 2 minutes
Using ctrl C or `shutdown -c` helps in stopping the shutdown process.

### 5. pwd

One way to identify the directory you are working in is the `pwd` command
It displays the current working directory path and is useful when directory changes are often

Example

```
~$ pwd
/home/user
```

### 6. passwd

This command is used to change the user account password. You could change your password or the password of other users. Note that the normal system users may only change their own password, while root may modify the password for any account.

Example

```
$ passwd user
Changing password for user.
Current password:
New password:
Retype new password:
Password has been changed
```

### 7. mv

To move a file or rename a file you would use the mv command.

Rename file

`$ mv <target_file> <name>`

Move file

`$ mv <target_file> <destination>`

### 8. cp

This command is used for copying files or directory into directory

`$ cp <file_or_directory> <destination>`

### 9. rm

This command is used to remove files in a directory or the directory itself. A directory cannot be removed if it is not empty.

`$ rm <file_or_directory>`

`$ rm -r <directory>` - removes all the contents in a directory and the directory as well.

### 10. mkdir

This command is used to make a directory

`$ mkdir <name>`

### 11. chmod

To change mode of a file system object. Files can have `r` - read, `w` - write and `x` - execute permissions.

Syntax

`chmod mode FILE`

| Octal Notation | Permission                                                            | Symbolic Presentation |
| -------------- | --------------------------------------------------------------------- | --------------------- |
| 0              | No Permission                                                         | ---                   |
| 1              | Execute Permission Only                                               | --x                   |
| 2              | Write Permission Only                                                 | -w-                   |
| 3              | Write and Execute Permissions (1+2)=3                                 | -wx                   |
| 4              | Read Permission Only                                                  | r--                   |
| 5              | Read and Execute Permissions (1+4)=5                                  | r-x                   |
| 6              | Read and Write Permissions (2+4)=6                                    | rw-                   |
| 7              | Read, Write and Execute Permissions, Means Full Permissions (1+2+4)=7 | rwx                   |

### 12. chown

This command is used to change the ownership of a file/folder or even multiple files/folders for a specified user/group.

Syntax

`$ chown <owner_name> <file_name>`

Example

`$ chown user1 script.sh`

### 13. cat

cat command allows you to create single or multiple files, view contents of file, concatenate files and redirect output in terminal or files. The output will show the entire contents of the file(s).

Example

```
$ cat file.txt
This is a fluffy cat
```

### 14. echo

This command is used to display a text or a string to the standard output or a file.

Example

```
$ echo "This is a phrase"
This is a phrase
```

### 15. wc

The wc (word count) command in Linux operating system is used to find out the number of new lines, word count, byte and characters count in a file specified by the file arguments.

Syntax

`wc [options] <filename>`

Example

```
$ wc -l readme.txt
120 readme.txt
```

- `wc -l` : Prints the number of lines in a file.
- `wc -w` : prints the number of words in a file.
- `wc -c` : Displays the count of bytes in a file.
- `wc -m` : prints the count of characters from a file.
- `wc -L` : prints only the length of the longest line in a file.

### 16. man

This command is used to view the on-line reference manual pages for commands/programs.

`$ man mkdir`

Output

```
MKDIR(1)                    User Commands                   MKDIR(1)

NAME
mkdir - make directories

SYNOPSIS
mkdir [OPTION]... DIRECTORY...

DESCRIPTION
Create the DIRECTORY(ies), if they do not already exist.

       Mandatory arguments to long options are mandatory for short options too.

       -m, --mode=MODE
              set file mode (as in chmod), not a=rwx - umask

       -p, --parents
              no error if existing, make parent directories as needed

       -v, --verbose
              print a message for each created directory

       -Z     set SELinux security context of each created directory to the default type

       --context[=CTX]
              like -Z, or if CTX is specified then set the SELinux or SMACK security context to CTX

       --help display this help and exit
```

### 17. history

This command is used to show previously used commands or to get information about the commands executed by a user.

```
$ history
man mkdir
chown user1 script.sh
cd /home/user/Downloads
touch text.txt
```

### 18. touch

he `touch` command is used to update the timestamps on existing files and directories as well as to create new, empty files.

`$ touch text.txt`

If the file already exists, touch will change the file's last access and modification times to the current time.

### 19. apt

Advanced Package Tool or APT is a package management system used by Debian-based distributions.

There are several command-line package management tools in Debian distributions, with `apt` and `apt-get` being the most used ones.

`$ apt update` - Update package index
`$ apt upgrade` - Update installed packages
`$ apt install package_name` - Install packages
`$ apt remove package_name` - Remove packages

### 20. top

The `top` (table of processes) command shows a real-time view of running processes in Linux and displays kernel-managed tasks. The command also provides a system information summary that shows resource utilization, including CPU and memory usage.

Output

```
top - 22:32:24 up 28 min, 0 users, load average: 0.52, 0.58, 0.59
Tasks: 4 total, 1 running, 3 sleeping, 0 stopped, 0 zombie
%Cpu(s): 3.3 us, 2.3 sy, 0.0 ni, 93.9 id, 0.0 wa, 0.6 hi, 0.0 si, 0.0 st
MiB Mem : 15741.3 total, 6575.3 free, 8942.0 used, 224.0 buff/cache
MiB Swap: 19199.9 total, 18941.0 free, 258.8 used. 6668.7 avail Mem

PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
1 root 20 0 8940 324 284 S 0.0 0.0 0:00.04 init
9 root 20 0 8940 220 180 S 0.0 0.0 0:00.00 init
10 suisei 20 0 18084 3608 3496 S 0.0 0.0 0:00.13 bash
121 suisei 20 0 18908 2136 1516 R 0.0 0.0 0:00.00 top
```
