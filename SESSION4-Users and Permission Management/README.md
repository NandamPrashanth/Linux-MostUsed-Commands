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
**sudo useradd <username>**
2. creating a user with home directory  
**sudo useradd -m john**
3. Setting users password  
**sudo passwd <username>**
4. Checking existing user details
**cat /etc/passwd | grep <username>**
5. To delete a user without removing their home directory  
**sudo userdel <username>**
6. To delete a user with their home directory
**sudo userdel -r <username>**
7. To create a group
**sudo groupadd <groupname>**
8. Adding user to a group  
**sudo usermod -aG <groupname> <username>**
9. Removing a user from group
**sudo gpasswd -d <username> <groupname>**
10. Checking user group membership
**groups <username>**
11. Changing user login name
**sudo usermod -l <new_username> <old_username>**


