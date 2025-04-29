LINUX FILE EDITOR
Most common keys:
- i = insert
- Esc
- r = replace
- d = delete
- :q! = quit without saving
- :wq! = quit and save
- dd = delete entire line
- u = undo
- x = delete 1 character
- shift + z + z = :wq! = quit and save
- a = insert mode and start typing
- inside vi editor "/findword"

  Some websites to train VIM:
  www.openvim.com
  www.vimgenius.com
  www.vim-adventures.com

  "SED" COMMAND
- sed 's/kenny/Lenny/g' filename.txt
s = substitute
/g = global
BUT to be able to laso save the inserted thing, you need to use: sed -i
- sed -i 's/kenny/Lenny/g' filename.txt = use -i to save changes

- sed 's/Constanca//g' filename.txt
will replace Constanca with (space, nothing), thus will remove it

- sed '/Seinfeld/d' filename
will delete all lines matching Seinfeld

- sed '/^$/d' filename
cap ^ - anything that starts with
$ anything thath ends = ^$ = meaning nothing it between = empty line

- sed '1d' filename
will delete first line

- sed '1,2d' filename
delete first and second line

-sed 's/\t/ /g' filename
\t = tab

USER ACCOUNT MANAGEMENT
Commands:
- useradds
- groupadd
- userdel
- groupdel
- usermod

FILES:
- /etc/passwd
- /etc/group
- /etc/shadow

Example: useradd -g superheros -s /bin/bash -c "user description" -m -d /home/spiderman spiderman

- id username
- cd /home/ = ls -ltr (dir username) to verify
- groupadd groupname
cat /etc/group
- useradd -r username = deletes also a dir of a user
- group add nonewgroup
cat /etc/group
- groupdel groupname
- usermod -g superheros spiderman = grep spiderman /etc/group
- /etc/passwd
- /etc/group
- /etc/shadow
grep spiderman /etc/passwd


THE /etc/login.defs File
-The chage command -per user = chage [-m mindays][-M maxdays][-d lastday][-I inactive][-E expiredate][-W warndays] user (e.g -m 5 -M 90 -W 10 -I 3)
- File = /etc/login.defs
  - PASS_MAX_DAYS 999999
  - PASS_MIN_DAYS 0
  - PASS_MIN_LEN 5
  - PASS_WARN_AGE 7

Switch Users and SUDO Access
  - su - username = switch user
  - sudo command
  - sudo visudo = edits the sudoers file
  - /etc/sudoers     = open using vim 
  - usermod -aG wheel username = this command adds the specified username to the wheel group, ensure the wheel-group has sudo privileges  

MONITOR USERS
- who = who is logged in and time
- last = all details of every user since day login 1
- w = shows who is logged on and what they are doing
- finger / pinky nowadays = to trace user
- id = info about own self
- id username = info about other users

TALKING TO USERS
- users = to check users that are currently logged in
- wall - broadcast main message to all logged in users (e.g. for system shutdown) ctrl + d = to broadcast the message
- write username = will write message to specific user

LINUX ACCOUNT AUTHENTICATION
- Types accounts - LOCAL and DOMAIN/DIRECTORY accounts
Difference between AD, LDAP, IDM, WinBIND, OpenLDAP etc...
- AD= Microsoft active directory
- IDM = Identity Manager
- WinBand = Used in Linux to communicate with Windows (Samba)
- OpenLDAP (open source LDAP)
- IDM Directory Server
- JumpCloud

SYSTEM UTILITY COMMANDS
- date
- uptime
- hostname
- uname
- which (command) = tells you exact location of the command. You can spectate it
- cal (Calendar) = cal 5 1994, cal 2016 = will show all months of 2016
- bc = calculator (quit to quit)

PROCESSES and JOBS
- Application = Service
- Script = made out of lines of code to do some job
- Process = App generate Processes
- Daemon = Continuos runs in background
- Threads = Service -> Process -> Thread
- Job = Run a service or process at a schedule time

COMMANDS
- systemctl
- ps
- top
- kill
- cron tab
- at

SYSTEMCTL COMMAND
- SYSTEMCTL start start/stop/status servicename.service = The cli tool to interact with systemd
- Systemctl enable
- systemctl restart/reload
- systemctl list-units --all
- systemctl status firewalld.service (test)
  
  To add a service under systemctl management:
  - Create a unit file in /etc/systemd/system/servicename.service
  To Control system with systemctl:
  - systemctl poweroff
  - systemctl halt
  - systemctl reboot

"ps" command
- ps = show processes of the current shell
- ps -e = all running processes
- ps -ef = shows all running processes in full format listing (Most commonly used)
- ps - u username = Shows all processes by username

"top" command
- top = VERY IMPORTANT = display linux processes
- top -u username = shows tasks/ps by user
- top then press c = shows command absolute path
- top then press k = kill process by PID
- top then M and P = To sort all Linux running by Memory usage

"kill" command
- kill [option][PID]
- kill - l = to get a list of all signal names or signal number
Most used:
- kill PID  = kill a process with default
- kill -1   = Restart
- kill -2   = Interrupt from the keyboard just like ctrl +c
- kill -9   = Forcefully kill the process
- kill -15  = kill a process gracefully
- killall   = kill ps and all child
- pkill     = kill by the process name

"crontab" command
- Used to schedule tasks
- crontab -e = Edit the crontab
- crontab -l = List the crontab entries
- crontab -r = Remove the crontab
- cron       = crontab daemon/service
- systemctl status crond = crond service

* * * * * <command to execute> =
first * = minute 0-59
second * = hours 0-23
third * = day of the month 1-31
4th *   = month 1-12
5th *   = day of the week 0-6 Sunday to Saturday

"at" command
- like crontab, this will schedule job, but "ONCE"
- at HH:MM PM = Schedule a job
- atq  = list the at entries
- atrm#  =remove at entries
- atd   = at daemon/service
- systemctl status atd =To manage atd service
- Create at entry by scheduling a task:
    at 4:45PM -> enter echo "this is my first at entry" > at-entry
    ctrl D

ADDITIONAL CRON JOBS
- there are 4 different types of cronjobs
    - Hourly
    - Daily
    - Weekly
    - Monthly
    - TO be found under /etc/cron.________ (directory)
  Timing schedule set in:
  - /etc/anacrontab -- except hourly
