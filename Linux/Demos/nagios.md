Install and Configure Nagios - monitoring system

Step 1: Install Required Packages
dnf install httpd php gcc glibc glibc-common gd gd-devel make net-snmp unzip wget

Step 2: Create Nagios User and Group
useradd nagios
groupadd nagcmd
usermod -a -G nagcmd nagios
usermod -a -G nagcmd apache

Step 3: Download and Extract Nagios Core
cd /tmp
wget -O nagios-4.5.4.tar.gz https://go.nagios.org/l/975333/2024-08-14/6dqd8
tar xzf nagios-4.5.4.tar.gz
cd nagios-4.5.4

Step 4: Configure Nagios Core
dnf install openssl-devel
./configure --with-command-group=nagcmd

Step 5: Install Nagios Core
make all
make install
make install-commandmode
make install-init
make install-config
make install-webconf

Step 6: Download, Install Nagios Plugins and Disable the Firewall
cd /tmp
wget https://nagios-plugins.org/download/nagios-plugins-2.4.11.tar.gz
tar xzf nagios-plugins-2.4.11.tar.gz
cd nagios-plugins-2.4.11
./configure --with-nagios-user=nagios --with-nagios-group=nagios
make
make install
systemctl stop firewalld
systemctl disable firewalld

Step 7: Create Nagios Web Interface Password and Start and Enable Services
htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin
systemctl start httpd
systemctl enable httpd
systemctl start nagios
systemctl enable nagios
systemctl status nagios

Step 8: configure hosts in Nagios
cd /usr/local/nagios/etc/objects/
ls -ltr
vi localhost.cfg
vi hosts.cfg

define host {
  use linux-server
  host_name CentosServer
  alias My First Server
  address 192.168.100.162
  max_check_attempts 5
  check_period 24x7
  notification_interval 30
  notification_period 24x7
}

define service {
  use generic-service
  host_name CentosServer
  service_description PING
  check_command check_ping!100.0,20%!500.0,60%
  max_check_attempts 5
  normal_check_interval 5
  retry_check_interval 1
  check_period 24x7
  notification_interval 30
  notification_period 24x7
}

Step 9: Update Nagios Configuration
cd /usr/local/nagios/etc/
vi nagios.cfg
cfg_file=/usr/local/nagios/etc/objects/hosts.cfg

Step 10: Verify, Restart and Run Nagios
cd /usr/local/nagios/etc/
vi nagios.cfg
cfg_file=/usr/local/nagios/etc/objects/hosts.cfg
http://192.168.100.161/nagios
