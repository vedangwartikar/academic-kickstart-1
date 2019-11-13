---
author: admin
comments: true
date: 2019-06-01 14:04:37+00:00
layout: post
link: https://chaitanyarahalkar.000webhostapp.com/the-virtual-file-system/
slug: the-virtual-file-system
title: The Virtual File System
wordpress_id: 48
categories:
- Linux
tags:
- filesystem
- linux
---




### File Systems In Linux


Linux works on the concept of virtual file systems. Everything on a Linux/Unix system is a file.
Here is a brief look at the file system structure -

![Linux File System](https://chaitanyarahalkar.000webhostapp.com/wp-content/uploads/2019/06/lfs.png)

This directory structure is followed in all Linux distributions which is similar to a Unix file system. Whenever a Linux system boots,this virtual file system is mounted. Each directory in this tree has its own significance.

* /bin - The bin directory stores all the Linux command binaries. The default commands like ls,cd,mkdir etc have their binaries located in this folder.

* /boot - This directory stores all the boot related information. The Linux kernel can be found here with usually the name `vmlinuz`. A separate subdirectory for GRUB can also be found here if it is installed.

* /dev - Here all the external devices are mounted. It also contains ttys,null,urandom,random devices which are internal devices used in several situations.

* /etc - Here all the configuration files are stored for different programs. A well known file - hosts can be found here. FTP,SSH and several applications store their configuration files here.

* /home - Here all the documents and personal files of different users on the system are stored. /home may have sub directories for each user.

* /lib - This directory has all the library files used by the Kernel or the system while booting. It has shared library images (Shared Object files & dependencies)

* /media - This directory is now no longer used. It is kept for backward compatibility to older systems having floppy or CD drivers. The CDs and floppies inserted into the drives were mounted here. Instead they can now be mounted in the /mnt directory.

* /mnt - This directory is used to mount external drives or even ISO mounts. Other Linux Virtual File systems can also be mounted here.

* /opt - Add on software package files are installed in this folder. Some softwares use this folder to place its libraries and dependencies here. It also has /bin, /doc , /include directories reserved for the system administrator.

* /root - A separate directory is provied for the root user. All the documents and root files are stored here. Other non-privileged users are not allowed access to this directory as well as all the other directories mentioned.


* /sbin - This directory contains all the system binaries. Binaries for programs like systemctl,service etc. can be found here.

* /tmp - This is a directory used to store temporary files. The system creates several temporary files which are deleted once the system is powered off. Ususally incomplete download files can be found here. Sometimes temporary mounts are also created here.

* /srv - This directory has site-specific data served by the system. Usually files related to services are stored here. Eg. ftp,rsync related files are stored here.

* /usr - It is one of the major directories in Linux. It has various sub-directories like bin(User binaries),include(All the C headers are stored here),share(Architecture independent data),local(Local system files) etc.

* /var - This directory has variable data files. It has several sub directories like cache(Applications' cache data),lib,opt(Variable /opt data),tmp(Temporary system files),log(System logs),lock(Lock files),cron(Crontab configuration file),backups etc.

File systems are also used on numerous storage devices that use different kinds of media. NTFS,HFS+,APFS,ExFAT etc. are some of the well known file systems designed by proprietary companies. Linux uses Extended File Systems. ext4 is the latest file system used on Linux based distributions. It is backward compatible with its older generations ext3,ext2 & ext. ext4 allows volumes upto size 1EiB (Exbibyte) and files with sizes upto 16 TiB (Tebibytes).






