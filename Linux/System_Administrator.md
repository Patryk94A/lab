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
