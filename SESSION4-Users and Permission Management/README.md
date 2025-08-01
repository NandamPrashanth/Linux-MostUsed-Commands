# Session 4 - Users and Permission Management

User management is a critical part of any Linux-based operating system, including Rocky Linux. It allows system administrators to control access to the system, manage user permissions, and ensure the security of the environment.

In this session we will learn **User management Overview** and **Essential commands for User Management** such as **Creating a user**, **Creating a user with home directory**, **Setting users password**, **Checking existing users info**, **Deleting a user without removing their home directory**, **Deleting a user with their home direcctory**.

Then we will learn **Managing user group** and we will cover **Creating a user group**, **adding users to group**, **removing a user from group**, **checking user group membership**, **changing user login name**, ****

# User management Overview

In Linux, every user has an associated user account, which defines the user's ability to access the system and its resources. User accounts are managed using a set of command-line tools.

**User account:** Defines who a person is on the system and what permissions they have.

**Groups:** A collection of users who are assigned similar permissions to resources.

**Permissions:** Control what users can do with files, directories, and programs.

1. For creating a user  
**sudo useradd username**
2. creating a user with home directory  
**sudo useradd -m john**
3. Setting users password  
**sudo passwd username**
4. Checking existing user details  
**cat /etc/passwd | grep username**
5. To delete a user without removing their home directory  
**sudo userdel username**  
6. To delete a user with their home directory
**sudo userdel -r username**
7. To create a group  
**sudo groupadd groupname**
8. Adding user to a group  
**sudo usermod -aG groupname username**
9. Removing a user from group  
**sudo gpasswd -d username groupname**
10. Checking user group membership  
**groups username**
11. Changing user login name  
**sudo usermod -l new_username old_username**
12. To verify a created group  
**cat /etc/group**
13. To verify which group a specific user belongs to  
**groups username**

To switch into a created user directory  

sudo su - username

WHILE PERFOMRING ANY ACTION THAT NEED ROOT PERMISSION THEN YOU CAN ADD YOUR USER TO %SUDO OR %WHEEL WHICH EVER PRESENT IN YOU /ETC/SUDOERS AND TO DO THAT YOU NEED TO USE usermod -aG groupname username
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# What are Permissions in Linux?  
Permissions control who can do what with a file or folder. In Linux, every file or folder has three types of permissions:  
**Read (r)** – Can view the contents.

**Write (w)** – Can modify or delete.

**Execute (x)** – Can run the file as a program/script.

# Three Types of Users  
Every file/folder has permissions for three types of users:

User Type	Meaning  

**Owner**	The person who created the file.
**Group**	A group the file belongs to.
**Others**	Everyone else.


#  Check File Permissions  

Use the ls -l command:  
ls -l filename  

Example output:  
-rwxr-xr-- 1 alice staff 1234 Aug 1 12:00 myfile.txt  

-rwxr-xr-- → The permission string

First character: - (file), d (directory)

rwx → Owner (can read, write, execute)

r-x → Group (can read, execute)

r-- → Others (can read only)

# Change Permissions with chmod  

Use chmod to change permissions.  

chmod u+x script.sh      # Give execute to owner  
chmod g-w myfile.txt     # Remove write from group  
chmod o+r file.txt       # Give read to others  

You can also use numbers:  

| Symbol | Number |
| ------ | ------ |
| `r`    | 4      |
| `w`    | 2      |
| `x`    | 1      |

Example:  

chmod 755 myfile.txt  

Means:

7 (owner): 4+2+1 = rwx

5 (group): 4+0+1 = r-x

5 (others): 4+0+1 = r-x

Examples:  

touch test.txt  

chmod 600 test.txt   # Only owner can read/write  

chmod 644 test.txt   # Everyone can read, only owner can write  

chmod 777 test.txt   # Be careful! Everyone can do everything!  


Try ls -l after each change and observe.  



# Change Owner or Group  

Use chown to change the file owner:  

chown newowner filename  

Use chgrp to change the group:  

chgrp newgroup filename  


























