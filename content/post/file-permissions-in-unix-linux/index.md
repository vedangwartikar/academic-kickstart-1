---
author: admin
comments: true
date: 2019-06-05 01:15:35+00:00
layout: post
link: https://chaitanyarahalkar.000webhostapp.com/file-permissions-in-unix-linux/
slug: file-permissions-in-unix-linux
title: File Permissions in Unix/Linux
wordpress_id: 71
categories:
- Computers
- Linux
tags:
- cli
- commands
- linux
- permissions
- unix
---




### File Permissions


Unix & Linux provides Read\(r\),Write(w) and Execute(x) permissions to any file on the system.
If you `ls -l` every file with its permissions will be shown.

The system is divided into three types - User,Group and others. The r,w,x permissions are assigned to each type. This is well explained by the diagram shown below:

![Permissions](https://chaitanyarahalkar.000webhostapp.com/wp-content/uploads/2019/06/permissions.jpg)


* Owner permissions − The owner's permissions determine what actions the owner of the file can perform on the file.


* Group permissions − The group's permissions determine what actions a user, who is a member of the group that a file belongs to, can perform on the file.


* Other (world) permissions − The permissions for others indicate what action all other users can perform on the file.

The chmod command helps to assign permissions or remove existing permissions. Permissions can be assigned in two ways -

1.By using the letters r,w,x & a,o,u with the symbols +, - & =.
2. Using octal numbers.
Let us create a sample file and apply some root privileges to it.


Enter into root by typing `su` and entering the root password.

`echo "Test File " >> only_root.txt`

Check the default permissions for the file by typing `ls -l only_root.txt`. This produced:

```bash   
    -rw-r--r--  1 linus staff 0 Jan 1 08:28 only_root.txt
   

```


We will be adding readonly permissions to this file.
`chmod a-w only_root.txt`

Let us split the command.
* chmod - Used to assign permissions. 
* a-w - a indicates 'all' minus is remove and w is write. So it is the shorthand notation for remove write permissions from all. Similarly to add a permission we can use the plus symbol.

only_root.txt - Is the file
Some examples of this shorthand notation:

* a+rwx - Add read,write and execute permissions to all

* u=x - Assign execute permission to the current user.

* o-wx - Remove write-execute permissions from other users.

* g+rw - Add read-write permissions to the group that the user belongs to.

The other mentioned way was is the octal number system. Check out the table given below:

![Octal System](https://chaitanyarahalkar.000webhostapp.com/wp-content/uploads/2019/06/octal.png)

The chmod command also accepts this method to assign permissions.
Some examples are illustrated below:

The very popluar permission set that is seen is

`chmod 755 only_root.txt`

Let us break it into parts

* 7 - Read,write & Execute permissions to the user

* 5 - Read & Execute permission to the group of the user

The way to remember this number system is referring to the binary equivalent of the octal number.

![Octal permissions](https://chaitanyarahalkar.000webhostapp.com/wp-content/uploads/2019/06/octal-permission.png)

A set bit indicates that the permission exists and a clear bit indicates that it is removed.
Similar permissions can be assigned to directories as well.

##### SUID & SGID Permissions

setuid and setgid are Unix and Linux access right flags that allow users to run an executable having the permissions of executing the binary,restricted to some other user or group.

setuid allows execution access to a specific user
and setgid does the same for a group.

Usually it is used to allow local users to execute some privileged binaries belonging to the root user.
For example, the root user may have some privileged executables like curl,wget etc. and the root user may set the access right flags to allow any other trusted local user to use these executables.

These permissions are usually set with the chmod command.

`chmod ug+s /usr/bin/wget`

Running this command in root will allow local users and groups to execute the binary. In short we have lowered the privileges for this binary executable by setting the SUID & SGID bit.






