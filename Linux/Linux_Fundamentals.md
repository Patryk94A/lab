COMMANDS SYNTAX:
Command typically have the syntax: 
Command - 'ls' options - '-' arguments - 'ltr'

FILE PERMISSIONS:
r - read
w - write
x - execute = running a program

(rwx): Each permission can be controlled at three levels.

u - user = yourself
g - group = can be people in the same project
o - other= everyone on the system

-rwxrwxrwx 
first rwx - (u)user
second rwx - (g)group
third rwx - (o)other

chmod - to change permission
chmod u-w 'filename' = minus is to remove at user lever write permission
a-r a= all
chmod a+rw 'filename' = + add read and write at user level permission
a+rwx = add all permissions to all levels

chmod ugo+r 'filename'
chmod 444 'filename'

NUMBER         PERMISSON             SYMBOL
0            No Permission           ---
1            Execute                 --x 
2            Write                   -w- 
3            Execute + Write         -wx
4            Read                    r--
5            Read + Execute          r-x
6            Read + Write            rw-
7            Read + Write + Execute  rwx

chmod 764 'filename'
7 = User (rwx)
6 = Group (rw-)
4 = Other (r--)

FILE OWNERSHIP:
-There are 2 owners of a file or directory
  - User and Group
-Command to change file ownership
  - chown and - chgrp
    - chown = changes the ownership
    - chgrp = changes the group ownership
r- recursive

drwxrwxrwx 137 root root ....etc

etc is owned by root 
Group is owned by root aswel


ACCESS CONTROL LIST (ACL)

Commands to assign and remove ALL permissions:
setfacl  - set file acl
getfacl  - get file acl

1) To add permission for user:
   setfacl -m u:user:rwx /path/to/file
2) To add permissions for a group
   setfacl -m g:group:rw /path/to/file
3) To allow all files or directories to inherit ACL entries from the directory it is within
   setfacl -dm "entry" /path/to/dir
4) To remove a specific entry
   setfacl -x u:user /path/to/file(for specific user)
5) To remove all entries
   setfacl -b path/to/file (Forallusers)

Note:
- As you assign the ACL permission to a file directory it adds + sign at the end of the permission
- Setting W permission with ACL does not allow to remove a file

HELP COMMANDS
- whatis command
- command --help
- man command

ADDING TEXT TO FILES
- vi
- Redirect command output > or >>
- ech > or >>

- cat -> read the content of the file
  echo "Jerry first line..." > jerry  = add/readd
  echo "Jerry second line..." >> jerry + append


INPUT AND OUTPUT REDIRECTS
- Input(stdin) - 0
- Output(Stdout) - 1
- Error(stderr) - 2
  ls - l /root 2> errofile
  telnet localhost 2> errorfile

STANDARD OUTPUT TO A FILE (TEE)
"tee" = to store and view at the same time (from T-Splitter)
echo "David Puddy..." | tee elianefile ===>>> will create a new file "elianefile" and show/echo message

echo "David second message...: | tee -a elianefile ===>>> will append to the file

wc-c file will count the characters

PIPE
ls - l | tail -1 = will get the last one result

FILE MAINTENENCE COMMANDS
- cp = copy
- rm = remove
- mv = move
- mkdir = make dir
- rmdir or rm-r or rm-rf (forcefully) =remove direcotry
- chgrp = changes group ownership
- chown = changes ownership
- chown username:username dir = changes both chgrp and chown at the same time

FILE DISPLAY COMMANDS
- cat = view all content
- more
- less
- head -1 = view first line (-3 then first 3 lines)
- tail -3 = view last 3 lines (-1 last one line)

FILTERS/TEXT PROCESSORS COMMANDS
- cut = cut the output
- awk
- grep and egrep
- sort
- uniq
- wc

CUT
cut -c1 filename   = gives first character
cut -c1,2,4       = first, second, foruth characters
cut -c1-3         = characters 1 -> 3
cut -d: -f 6 /etc/passw      = delimiter : (used to separate field); -f filter/field; 6 at sixth position
ls-l | cut -c1-10            = will show 1 to 10 characters starting from the left from ls-l command
