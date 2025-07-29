# Session 2 – Linux File System and Navigation

In this session we will learn What is **File System** , **File System Components** , **Hierarchical Tree Structure in Linux** and commands which we use in day to day life in File System.

And later we will see how to Navigate in between files. And how to **Print Working Directory**, **Change Directory** , **List Directory Contents** , **Special Directory Symbols**, and then we will see scenario based exapmles.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# WHAT IS FILE SYSTEM?

A **File System** is a method used by an Operating System ( **OS**) to organize, store,  retrieve and manage data on storage devices like hard driver's, SSDs and USB drivers.

# FILE SYSTEM COMPONENTS

| Component        | Description                                                        |
| ---------------- | ------------------------------------------------------------------ |
| **Files**        | Actual data (documents, executables, logs, etc.)                   |
| **Directories**  | Containers that organize files (like folders in Windows)           |
| **Metadata**     | Information about files (size, creation date, permissions, etc.)   |
| **Mount Points** | Locations in the directory tree where storage devices are attached |
| **Inodes**       | Unique identifiers for each file, storing metadata and location    |


# EXAMPLE :  Think of a File System like a LIBRARY

* **Librarian** = Opearting System (organizes and retrieves things for you)
* **Library catalog** = metadata (tells you where a book is, who wrote it, when it was added)
* **Shelves** = directories
* **Books** = files

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Hierarchical Tree Structure in Linux

## What is aHierarchical File System?
A hierarchical file system is one where files are organized in a **tree-like structure:**

* The root of the tree is the topmost directory called /.
* Branches and leaves of the tree represent directories (folders) and files.
* Each directory can have subdirectories, forming nested levels.

The entire Linux file system starts from /, regardless of where files are physically stored (hard disk, SSD, USB, network).

# TREE STRUCTURE DIAGRAM

```bash
/
├── bin       → Essential system binaries
├── boot      → Boot loader files (kernel, grub)
├── dev       → Device files
├── etc       → System-wide configuration files
├── home      → User directories
│   ├── USER1
│   └── USER2
├── lib       → Essential shared libraries
├── media     → Auto-mounted external devices
├── mnt       → Temporary mount points
├── proc      → Virtual filesystem for processes
├── root      → Home directory of root user
├── sbin      → System administration binaries
├── tmp       → Temporary files
├── usr       → Secondary hierarchy (user-installed software)
│   ├── bin
│   ├── lib
│   └── share
└── var       → Variable data like logs and spools
```


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Explanation of Key Directories

| Directory | Description                    | Notes                                                    |
| --------- | ------------------------------ | -------------------------------------------------------- |
| `/`       | Root directory                 | Parent of all directories                                |
| `/bin`    | Essential user binaries        | Basic commands (`ls`, `cp`, etc.)                        |
| `/boot`   | Bootloader, kernel files       | Critical for system startup                              |
| `/dev`    | Device files                   | Everything is treated as a file in Linux — even hardware |
| `/etc`    | Configuration files            | System-wide settings (e.g., `passwd`, `ssh/`)            |
| `/home`   | User home directories          | Each user gets a folder (`/home/username`)               |
| `/lib`    | System libraries               | Shared libraries used by binaries in `/bin` and `/sbin`  |
| `/media`  | External drives                | Auto-mount point for USB/CDs                             |
| `/mnt`    | Manual mount points            | Temporarily mount filesystems                            |
| `/proc`   | Process information            | Virtual file system to view system & process info        |
| `/root`   | Root user's home directory     | Not to be confused with `/`                              |
| `/sbin`   | System binaries for root/admin | e.g., `ifconfig`, `shutdown`                             |
| `/tmp`    | Temporary files                | Deleted after reboot or session                          |
| `/usr`    | User programs and libraries    | Like `Program Files` in Windows                          |
| `/var`    | Variable files                 | Logs, mail, spool directories                            |



# Why /usr, /bin, /sbin — Why So Many?

Linux follows the Unix Filesystem Standard (FHS):

*/bin and /sbin = Needed for minimal boot environment
*/usr/bin, /usr/sbin = User-installed software (safe to mount later)
*/lib, /usr/lib = Libraries (like DLLs in Windows)
*/opt = Optional third-party apps


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# NAVIGATION ABSOLUTE AND RELATIVE  PATH

This is a foundational concept in Linux file system navigation, and it's critical for Engineers to understand how to move through directories confidently.

# What is a path is LINUX

A PATH in Linux defines how to reach a **file or a directory** from **certain location in the File System.**

* There are two types of path
  
**Absolute Path** : Always from the root `/`    example:  `/home/student/Documents` 
**Relative Path** : From your current directory example:  `Documents/notes.txt`     |


 # ABSOLUTE PATH (If a path starts with a forward slash /, it is an absolute path.)

 An Abosolute path always starts from a root directory / and it shows the complete path to destination.

 * For an Example
```bash

   /
└── home
    └── student
        └── Documents
            └── world.txt

```

Now absolute path to world.txt is: /home/student/Documents/world.txt

 **Even if you’re in /var or /tmp or any other, this path will still take you to the file 'world.txt'.**

# RELATIVE PATH (If a path does NOT start with /, it's a relative path.)

Relative Path is relative to **YOUR CURRENT LOCATION** or ***CURRENT WORKING DIRECTORY**
Uses symbols like . (current dir) and .. (parent dir)

 * For an Example
   You are in below path

   /home/student

   * And now you want to access

   /home/student/Documents/notes.txt

   * Use this relative path:

   cd Documents

   And then youll be able to access notes.txt


# COMMANDS USED DAY RO DAY LIFE
```bash
* pwd — Print Working Directory
Useful to confirm where you are, especially in scripts or after running multiple cd commands.

* cd — Change Directory
  cd ~          # Go to home
  cd ..         # Up one level
  cd -          # Go back to previous location

* ls — List Directory Contents
  ls
  ls -l         # Long listing (permissions, owner, size)
  ls -a         # Show hidden files (.bashrc)
  ls -lh        # Human-readable sizes

* Special Directory Symbols
  Symbol	Meaning	Example
  .	Current directory	./script.sh
  ..	Parent directory	cd ..
  ~	Home directory	cd ~
  /	Root directory	cd /
```
# Examples

*Scenario 1: Find and Open Log File
Goal: Navigate to and view /var/log/syslog

cd /var/log
ls -lh
less syslog

*Scenario 2: Traverse Into a Deep Folder
Path: /home/student/course/linux/week1/notes

cd ~/course/linux/week1/notes

*Scenario 3: Jump Between Two Folders

cd ~/projects/linux
cd /etc
cd -   # Go back to ~/projects/linux

*Scenario 4: Check Files

cd /media
ls
cd usb
ls -l
   
* Auto-Completion
Use the TAB key to auto-complete file/folder names.

cd /etc/def[TAB]   ➝ /etc/default/

* Command History
Use Up Arrow (↑) or history to recall previous commands.

* clear and Ctrl + L
Clear the screen to reduce clutter.

* Combine Navigation

cd ~/Documents/linux && ls -lh

* Useful Navigation Aliases (Optional for Teaching)

alias ..="cd .."
alias ...="cd ../.."
alias ll="ls -l"
alias cls="clear"





  




   





