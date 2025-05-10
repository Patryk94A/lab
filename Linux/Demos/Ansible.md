INSTALL and Configure Ansible
### Important to put username and IPADDRESS of the another server/Machine (had some trouble getting error at /etc/ssh otherwise)
### Very nice to see it installing 2 things at two different machines at the same time

STEP 1: Install and verify Ansible
rpm -qa | grep ansible
dnf install ansible
ansible -version

Step 2: Configure ansible hosts file
vi /etc/ansible/hosts
[webservers] (uncomment it)
localhost ansible_connection=local

Step 3: Verify the configuration settings
ansible -m ping webservers

Step 4: Generate SSH key pair
vi /etc/nginx/nginx.conf
vi /etc/nginx/conf.d/myfirstlinuxos.conf
ssh-keygen -t rsa -b 2048 (enter at each prompt)
ssh-copy-id username@ipaddress  (username of the another computer and IP address of the another computer)
ssh username@IPAddress
exit
vi /etc/ansible/hosts
[webservers]
CentosServer ansible_host=IPADDRESS ansible_user=username
ansible -m ping webservers
ansible -m ping all

Step 5: Create the ansible Playbook to Install Apache server
vi install_httpd.yml

# Ansible Playbook to Install Apache Server on Two Machines MyFirstLinuxMachine and MySecondLinuxMachine
---
- hosts: webservers
  become: yes
  become_user: root
  tasks:
    - name: Install httpd package
      dnf:
        name: httpd
        state: present

ansible-playbook install_httpd.yml --ask-become-pass
