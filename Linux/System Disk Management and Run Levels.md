SYSTEM RUN LEVELS (0 to 6)
Main Run Level
0 - shutdown
1 - Single users mode, aliased as s or S
6 - Reboot
other:
2 - Multiuser mode without networking
3 - Multiuser mode wit networking
5 - Multiuser mode without networking and GUI
[init 0]
who -r to check what run level is current running

COMPUTER BOOT PROCESS
BIOS | BASIC input/output system executes MBR
Basic input/output Settings (firmware interfaced) POST = Power-Onself-test started
\/
MBR | Master BOOT Record, executes GRUB (contains info about GRUB)
Information saved in the first sector of a hard disk that indicates where the GRUB 2 is located so it can be loaded in computer
\/
GRUB2 | Grand Unified Bootloader executes Kernel
Loads Linux Kernel /boot/grub2/grub.cfg
\/
KERNEL | Kernel executes/sbin/init
Core of OS system, Loads required drivers from initrd.img. Starts the first OS process (systemd)
\/
Systemd = System daemon (PID#1)
It then starts all the required processes (0 to 6). Run levels Reads = /etc/systemd/system/default.target to bring the system to run-level

The systemd-analyze command
- Analyzes boot performance 
- highlight slow services
- optimizing startup time
    man systemd-analyze
    systemd-analyze blame
    systemd-analyze time
    systemd analyze blame --user
  - /etc/motd
  - /etc/profile.d/moth.sh
      modify sshd_config Print NOTD to no
      restart sshd

STORAGE
Most importand commands:
- df
- fdisk
- df -h

SWAP SPACE
- Is used when the amount of Physical memory is full. If the system need more memory and the RAM is full, inactive pages in memory are moved to the swap space. It should not be a replacemnet for more RAM.
Commands:
- dd
- mkswap
- swapon / swapoff

XFS_INFO
- man xfs_info

RAID = Redundant Array of Independent Disks
- Type of RAID
  - RAID 0
  - RAID 1
  - RAID 5
    RAID 0 ( 5 + 5) = 10G  But what if 1 got destroyed?
    RAID 1 ( 5= 5 ) = 5GB  BUT is slow
    RAID 5 ( 5+= 5+= 5) =12GB

FILE SYSTEM CHECK (fsck and xfs_repair)
- fsck = is used to check and repair Linux filesystem (ext2, ext3, ext3 ...)
- Linux xfs_repair is used to check and repair Linux filesystem for xfs
- fsck errors to be check online
    - df -h = file system check
    - df -T = type of file system

SYSTEM BACKUP
    5 different types of backup
1. System backup
2. App backup
3. Database ackup
4. Filesystem backup
5. Disk backup or disk cloning (dd command)


AND A LOOOTT MORE TO IT is coming....
