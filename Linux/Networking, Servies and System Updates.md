NETWORK FILES AND COMMANDS
- Interface Detection
- Assigning IP Address
- Interface configuration files
    - /etc/nsswitch.conf
    - /etc/hosts
    - /etc/sysconfig/network
    - /etc/sysconfig/network-scripts/ifconfig-nic
    - /etc/resolv.config

enp0s3 -> /etc/NetworkManager/system-connections/enp0s3.nmconnection
BOOTPROTO = dhcp
- /etc/resolv.conf = DNS

NETWORK
ip a = ifconfig
ping
ifup or ifdown
netstat
nslookup
tcpdump -i enp0s3 = listening to every coming in and goin out

NIC INFORMATION
- ethtool (ethtool 'enp0s3')

NEW NETWORK UTILITIES
- nmcli = network manager CLI
- nmtui = network manager text user interface
- nm-connectin-editor = Graphical management
- GNOME settings

DOWNLOAD FILES OR APPS
- wget(worldwide get)
- wget link/package .... tar.gz = to install that package

CURL and PING COmmands
- curl www.google.com
- curl - o https://exact-link-to-download
- ping www.google.com
- nslookup = DNS

SS -command
- Protocol = Kind of language, Set of rules that ensures data is sent successfully between two computers over the internet
- TCP - Transmission Control Protocol Sync -> ; Sync ackn <- ; Ackn ->
- UDP (User datagram Protocol) Request <- ; Response -> ;Response -> ;Response -> ;
  - Sending data over Internet without checking if it arrives correctly.
      - fastest but less reliable
      - live streaming
- ss -t = tcp
- ss -u = udp
- ss -x = unix
   
UNIX
- it is a way for programs on the same computer to talk to each other
    - Uses a special file for message exchange
    - Used in databases, web servers and local system services without internet
FTP - FILE TRANSFER PROTOCOL
- Protocol to transfer file from server A to server B
- Default FTP Port = 21

SCP - SECURE COPY PROTOCOL
- Similair to FTP, but it adds security and authentication
- Default SCP Port = 22 (Same as SSH)
  scp filename username@IP.address:/path/to/file

RSYNC - REMOTESynchronization
- highly efficent and versatile
    - Incremental backup: Only changes are transfered
    - Compression: Data can be compressed during transfer
    - SSH support
- default rsync Port = 22 (same as SSH)

Demo:
- tar cvf backup.tar . = to backup current file/folder into backup.tar
- rsync -azvh
- rsync -avz backup.tar username@IP.address:/path/to/file

SYSTEM UPDATES AND REPOS:
- dnf = it handles downloading and installing packages.
      - (yum- centos and redhat) - Older package manager, now replaced by dnf
      - (apt-get -ubuntu) The package manager for Debian-baes systems like Ubuntu
- dnf install package
- dnf remove package
- dnf update    = Update all installed packages
- rpm = redhat package manager = Used to install, update and remove packages on RHEL-based systems
- rpm -qa | grep package name = to check if package is installed 
- rpm -e package = remove a package
- rpm -i package.rpm = To install a package

SYSTEM UPGRADE /PATCH MANAGEMENT
Types:  - Major version 7,8,9
        - Minor Centos 8,1; 8,2; 8,3
- Major upgrade can't be done with dnf command
- Minor can be done with  = dnf update command
dnf update -y
dnf upgrade = will delete packages
update = will preserves packages

- /etc = all packages and configuration files are under /etc
- wget https://link.from.internet.rpm -->> rpm -ivh link.from.internet.rpm to install it
- rpm -qi package = to get all info about it

- which command = to check full path of a command
/usr/bin/clear
rpm -qf /usr/bin/clear = this will provide full package name of that command

ROLLBACK UPDATES AND PATCHES
- Rollback a package or patch
      - yum install <package-name>
      - yum history undo <id>
- Rollback an update
      - NOT recommenden to go back from ( e.g. 7.1 to 7.0)
  - yum update
  - yum upgrade
  - yum history undo <id>
- yum history = to get all history

SSH and TELNET
- Telnet =  Un-secured connection betweem PC's
- SSH = Secured
- 2 ways to check status:
  - 1. ps -ef | grep sshd
    2. systemctl status sshd
DNS - DOMAIN NAME SYSTEMS
- PTR record ( IP to Hostname )
- A Record (Hostname to IP)
- CName Record ( Hostname to Hostname)
Files:
- /etc = all configuration directories
- /etc/named.conf
- /var/named
Service
- systemctl restart named

