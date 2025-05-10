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

HOSTNAME / IP LOOKUP
- nslookup
- dig

NTP NETWORK TIME PROTOCOL
- Time sync
- File = /etc/ntp.conf
- Service = systemctl restart ntpd
- Command = ntpq
- systemctl enable ntpd = to enable service to start at boot
- NTP Port = 123

CHRONYD (NEW NTP)
- Time synchonization
- Package name = chronyd
- Configuration file = /etc/chronyd.conf
- log file = /var/log/chrony
- service = systemctl start/restart chronyd
- Program command = chronyc.

NEW SYSTEM UTILITY COMMAND (TIMEDATECTL)
- timedatectl = to check time status
- timedatectl list = time zones
- timedate ctl set-ntp true/false

MAIL TRANSFER AGENT
- STORAGE, PROCESSING AND DELIVERY OF EMAILS
- Postfix; -Sendmail (old); exim; Spam assassin; open stmpd; courier; zimbra
- /etc/postfix/
- /etc/postfix/main.cf.
- systemctl restart postfix
- Doesn't have 'd' deamon, but it works as it

    S-nail = write and send emails on terminal
    Postfix = handles emails on the server
  HOW TO SEND EMAILS
  mail -s "mail setup" ia@test.com (enter)
  
  Type body of the email (ctrl d

  Confirm to send an email y/n

WEB SERVER (httpd)
- Service = httpd
- Files = /etc/httpd/conf/httpd.conf
- /var/www/html/index.html

Service = systemctl restart httpd
          systemctl enable httpd

INSTALLING, CONFIGURING and MANAGING NGINX
- Powerful, high performance WEB server that helps websited to handle a large number of visitors efficiently
- Webserver = can be used as reverse proxy, load balancer, mail proxy and http cache
  lsof -i :80 = to check port :80
- vi /etc/nginx/nginx.conf
- sestatus
- tail -f /var/log/nginx/error.log  ==>> to check logs why it failed
- setsebool -P httpd_can_network_connect 1

CENTRAL LOGGER (RSYSLOG)
- PURPOSE = GENERATE LOGS OR COLLECT LOGS FROM OTHER SERVERS
- Service or package name = rsyslog
- Configuration file = /etc/rsyslog.conf
- Service: systemctl restart rsyslog    systemctl enable rsyslog

LINUX OS HARDENING
1. USER ACCOUNT =
    - cat /etc/passwd => all the users that we have in our system
    - chage -l username = check password details
    - cat /etc/shadow
    - cat /etc/login.defs = default PASS settings
    - cd /etc/pam.d ==>>more system auth... commands/field to be studied
2. REMOVE UN-WANTED PACKAGES
   - rpm -wa | wc -l ==>> rpm -e packagename
3. STOP UNUSED SERVICES
4. CHECK ON LISTENING PORTS
   - lsof    /netstat -tunlp
5.1 SECURE SSH CONFIGURATION
    - cd /etc/ssh/ => more sshd_config
    - #PermitROOTLogin yes -> no = uncomment - You first need to login as user and can't login as root right away
5.2 firewall-config = GUI
    - firewall-cmd --help
    - iptables = cd /etc/firewalld -> firewalld.conf
5.3 SElinux -> Sestatus to check status
5.4 Change listening services port numbers
5.5 Keep your OS upto date (sec Patching)
    - man checkpolicy
    - Signup to Redhat/CENTOS when new update come up to get notify

OPENLDAP INSTALLTION
- OpenLDAP Service = slapd
      systemctl start/enable slapd
- Config files
      /etc/openldap/slapd.d

TRACEROUTE 
- The journey that a packet of information undertakes from its source to its destination. 'data loss to locate'
- Example
      - traceroute www.google.com
      - netstat -rnv = to check my gateway
HOW TO OPEN A IMAGE FILE
- rpm IMAGEMAGICK

CONFIGURE AND SECURE SSH
 HARDWARE => KERNEL => SHELL => UTILITIES
ssh = secure shell => provides you with an interface to the linux system. It takes in your commands and translate them to kernel to manage hardware.
- openSSH is a package/software
- its daemon service is sshd
- SSH port is 22
Configure idle timeout Interval. Avoid having an unattended SSH session, you can set an idle timeout interval.
- /etc/ssh/sshd_config
- clientAliveinterval 600
- clientalivecountMax 0
- Systemctl restart sshd
    cp /etc/ssh/ssh_config-origin /etc/ssh/ssh_config ===>>> Make backup to easy copy it back
    Disbale root login
      - /etc/ssh/ssh_config
      - PermitRootLogin
  Disbale Empty password
      - Permitemptypasswords
  Limit Users SSH Access
      - Allow users user1 user2 ....
  User a different port

SSH-keys - Access remote server without a password
Cockpit-app

FIREWALL
- 2 types; software and hardware
- 2 tools; Iptables = for older Linux
           firewalld = for newer versions
1. tables= allows you to process packets in a specific way. 4 different types: filter, mangle, nat, raw
2. chains are attached to tables. chains allow you to inspect traffic at various points.
    3 main different chains
   - Input
   - Forward
   - Output
   These allow you to filter traffic by adding rules to them
    - Rule = if traffic is coming from 192.168.1.35 then go to defined target.
3. Targets = decides what happens next
- Accept
- reject
- drop = drop without sending any response

    Output of iptables -L
Chain INPUT (Policy ACCEPT)
target prot opt source        destination
target= target
prot= tcp, udp, icmp, all
opt= IP options.. rarely used
source= The source IP or subnet of the traffic or anywhere
destination= The destination IP or subnet of the traffic or anywhere

FIREWALLD
- firewalld-cmd
      - predefined: NFS, NTP, HTTPD
      - Table, Chains, Rules, Targets
- firewall-and --list-all
- firewall-cmd --get-services
- firewall-cmd --reload
  PRACTICAL EXAMPLES
- firewall-cmd --get-zones
- firewall-cmd --get-active-zones
- firewall-cmd --zone=public --list-all OR firewall-cmd --list-all

/usr/lib/firewalld/services/allservices.xml
cp any .xml file and change the service and port number = to add 3rd party service

- to add a service (http)
    - firewall-cmd --add-service=http
    - firewall-cmd --remove-service=http
- to add or remove a service permanently
    - firewall-cmd --add-service=http --permanently
    - firewall-cmd --remove-service=http --permanently
- to add port
    - to add port
          - firewall-cmd --add-port=1110/tcp
  - to reject incoming traffic from an IP address
firewall-cmd --add-rich-rule = 'rule family' ="ipv4" source address= "IP" reject'
### d + $ = to remove the rest of the line

to block and unblock ICMP traffic
    - firewall-cmd --add-icmp-block-inversion
to block outgoing traffic to specific website
- host -t a www.facebook.com = find IP address
firewall-cmd --direct--add-rule ipv4
filter OUTPUT 0-d 31.13.71.36 -j DROP

TUNE SYSTEM PERFORMANCE
- TUne is for system tuning Linux system performance d is for daemon
- rpm -qa | grep tuned
      - tuned-adm
      - tuned-adm active    = check active profile
      - tuned-adm list      = list of profiles
      - tuned-adm list "profile-name" = change adm profile name
      - tuned-adm recommand = gives recommenden profile
      - tuned-adm off        = set it off
- nice and renice => 40 levels of prio
      -20 (highest) to 19 (lowest)
- Top command to check level of nice
- Nice value is a user-space and prio PR is the process's actual prio that use by Linux kernel. In Linux system prio are 0 to 139 in which 0 to99 for real time and 100 to 139 for users.
  To view using ps-command
      - ps axo pid,comm,nice,cls --sort=-nice
      - nice -n # process-name (# = number)
      - renice -n # process-name
      - renice -n 12 PID

RUN CONTAINERS
- Imaged- containers can be created through images and containers can be converted to images
- pods - Group of containers deployed together on the host. In the podman logo there are 3 seals grouped together as a pod.
- podman -v == podman is docker but from RHEL
- man podman / podman --help
- podman info = to search a specific image in repo
- podman search httpd
- podman images
- podman pull docker.io/library/httpd = to download available images
- podman ps = running containers
- podman stop container-name
