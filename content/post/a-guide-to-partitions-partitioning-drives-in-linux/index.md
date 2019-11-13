---
author: admin
comments: true
date: 2019-05-16 04:39:06+00:00
layout: post
link: https://chaitanyarahalkar.000webhostapp.com/a-guide-to-partitions-partitioning-drives-in-linux/
slug: a-guide-to-partitions-partitioning-drives-in-linux
title: A Guide to Partitions & Partitioning Drives in Linux
wordpress_id: 43
categories:
- Linux
tags:
- administration
- linux
---

Linux has completely different naming conventions while mounting drives as compared to Windows. /dev/sda,/dev/sdb,/dev/sdc etc. are the conventions in Linux. 

Each drive has its own partition table that describes the layout of partitions of the drive. MBR,GPT etc. are the different partition table standards used.
The MBR partition scheme is quite old and is rarely used due to limitations like-

1. It does not allow the configuration of more than four main partitions. Those partitions are called primary partitions.

2. Disk partitions are limited to 2TB

Every disk can have three kinds of partitions as per the MBR scheme -

* Primary Partitions - Usually for storing OSes

* Logical Partitions - Every primary partition may have multiple logical partitions

* Extended Partitions - A primary partition can be extended with this to overcome the limitation of maximum four primary partitions.
These partitions can be found named with the conventions /dev/sda1,/dev/sda2 etc.

(Enter all the commands mentioned below in root or with a sudoers' user)

#### Mounting drives in Linux

Running `fdisk -l` in root lists out the number of drives that are mounted on the system. `/dev/sda` is usually the hard drive or SSD on which the OS is running. Other external drives can be found ususally at `/dev/sdb`

`df -h` may also help locating external drives.

Whenever an external drive is inserted it is usually automatically mounted. To format a drive it must be unmounted first.

Drives can also be mounted with `mount /dev/sda /mnt` if the drive to be mounted is `/dev/sda` and the mount location is `/mnt`.

#### Formatting drives in Linux

There are two ways to format drives. One is with a graphical interface utility (GParted) or via the terminal.

GParted may be installed with the aptitude package manager supporting OSes by
`apt-get install gparted`

Entering `umount /dev/sdc1` in root if sdc1 is the drive mount point, will unmount the external drive.
Format the drive with the mkfs utility provided with Linux
```bash
    mkfs.ext4 /dev/sdc1 For ext4 file system
    mkfs.vfat /dev/sdc1 For vFat file system
    mkfs.ntfs /dev/sdc1 For NTFS file system
    
```

#### Creating a bootable drive in Linux

The USB drive must be completely formatted before installing. Format the drive to any supported file system. Several GUI based utilities like etcher can be used to format and create bootable drives.
Linux and Unix based systems provide the data duplicator(dd) utility to copy binary data to drives.

```bash
    dd if=/home/linus/file.iso of=/dev/sdc 
    if - The location of the input file
    of - Location of the mounted drive

```
Status of dd can be monitored by

```bash
    grep -l '^dd$ - Returns the process Id of dd
    kill -USR1 process_id - Shows the status 
    
```

After dd has completed transferring the iso to the drive type `sync`.
This is a good practice, since it forces completition of pending disk writes. It flushes the cache.

#### Partitioning Drives In Linux


##### Creating a partition


GParted is an excellent utility to partition drives. It can also be done with its command-line version invoked by `parted`

1.Select the disk to be operated on with `select /dev/sdc` (within the parted console invoked after typing `parted`)if the disk to be parted is at `/dev/sdc`

2.Label the disk with `mklabel name`.


3.Create the partition

```bash    
    mkpart logical - Creates a logical partition
    
```

Enter the start and end location in megabytes. This will indicate the size of the partition. Eg. Start can be 1 and End can be 1000 indicating a partition of 1 Gb

4.The partition can be formatted with any file system with the `mkfs` command as explained above.

##### Removing a partition

1.Invoke the parted utility with `parted`.

2.Select the disk to be operated on with `select /dev/sdc` if the disk to be parted is at `/dev/sdc`

3.`rm 1` will remove the first partition from sdc if it has been selected


##### Resizing a partition

1.Invoke the parted utility with `parted`.

2.Select the disk to be operated on with `select /dev/sdc` if the disk to be parted is at `/dev/sdc`

3. `resizepart` will ask for the new start and end to resize the partition.


##### Recovering a partition

Lost partitions can be recovered by `rescue`. It asks for the start and end point in Mbs. If any lost partition is found,parted will recover the lost partition.

