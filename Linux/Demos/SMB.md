• Install samba packages
  # Become root user
  # yum install samba samba-client samba-common
  
• Enable samba to be allowed through firewall (Only if you have firewall running)
  # firewall-cmd --permanent --zone=public --add-service=samba
  # firewall-cmd –reload

• To stop and disable firewall or iptables
  # systemctl stop firewalld
  # systemctl stop iptables
  # systemctl disable firewalld
  # systemctl disable iptables

• Create Samba share directory and assign permissions
  # mkdir -p /samba/morepretzels
  # chmod a+rwx /samba/morepretzels
  # chown -R nobody:nobody /samba

• Also, you need to change the SELinux security context for the samba shared
directory as follows: (Only if you have SELinux enabled)
  # chcon -t samba_share_t /samba/morepretzels

• If you want to disable SELinux, follow these instructions
  # sestatus To check the SELinux status)
  # vi /etc/selinux/config
Change SELINUX=enforcing
To
SELINUX=disabled
# reboot

• Modify /etc/samba/smb.conf file to add new shared filesystem (Make sure to
create a copy of smb.conf file)
Delete everything from smb.conf file and add the following parameters

[global]
  workgroup = WORKGROUP
  netbios name = centos
  security = user
  map to guest = bad user
  dns proxy = no
[Anonymous]
  path = /samba/morepretzels
  browsable = yes
  writable = yes
  guest ok = yes
  guest only = yes
  read only = no
  
• Verify the setting
  # testparm
  
• Once the packages are installed, enable and start Samba services
  # systemctl enable smb
  # systemctl enable nmb
  # systemctl start smb
  # systemctl start nmb
  
• Mount on Windows client
  o Go to start
  o Go to search bar
  o Type \\192.168.1.95 (This is my server IP, you can check your Linux
  CentOS IP by running the command ifconfig)

• Mount on Linux client
  Become root
  # yum -y install cifs-utils samba-client
  Create a mount point directory
  # mkdir /mnt/sambashare
  Mount the samba share
  # mount -t cifs //192.168.1.95/Anonymous /mnt/sambashare/
  # Entry without password



Secure Samba Server

• Create a group smbgrp & user larry to access the samba server with proper
authentication
  # useradd larry
  # groupadd smbgrp
  # usermod -a -G smbgrp larry
  # smbpasswd -a larry
  New SMB password: YOUR SAMBA PASS
  Retype new SMB password: REPEAT YOUR SAMBA PASS
  Added user larry

• Create a new share, set the permission on the share:
  # mkdir /samba/securepretzels
  # chown -R larry:smbgrp /samba/securepretzels
  # chmod -R 0770 /samba/securepretzels
  # chcon -t samba_share_t /samba/securepretzels
  
• Edit the configuration file /etc/samba/smb.conf (Create a backup copy first)
  # vi /etc/samba/smb.conf
  Add the following lines
[Secure]
    path = /samba/securepretzels
    valid users = @smbgrp
    guest ok = no
    writable = yes
    browsable = yes
    
  • Restart the services
  # systemctl restart smb
  # systemctl restart nmb
