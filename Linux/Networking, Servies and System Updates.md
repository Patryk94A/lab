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

