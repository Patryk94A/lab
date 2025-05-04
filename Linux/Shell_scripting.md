What is Shell?
 - It is like a container.
 - Interface between users and kernel/OS
 - CLI is a shell
Find your shell
 - echo $0
 - Available Shells "cat/etc/shells"
 - Your shell? /etc/passwd
Types of Linux Shells
- Gnoe = GUI
- KDE = Same GUI
- sh
- bash (Most used)
- csh and tcsh
- ksh
SHELL SCRIPTING
What is a shell script?
 - A shell script is an executable file containing multiple shell commands that are executed sequentally. The file can contain:
     - shell (#!/bin/bash)
     - Comments (#comments)
     - Commands (echo, cp, grep, etc...)
     - Statememnts (if, while, for, etc.....)
 - Shell script has to have exe permissions ( - rwx r-x r-x)
 - Shell script has to be called from absolute path (e.g. /home/userdir/script.bash)
 - If called from current location then ./script.bash

BASIC SHELL SCRIPTS
vi output-screen (to open that file in vi)
#!/bin/bash
echo Hello World!

!!! Very important it must have x-permissions
!!! Run it by ./output-screen

BASIC SCRIPT #2
a = Imran (varialbe a)
b = Patryk (variable b)

echo "my first name is $a"
echo "My surname is $b)

read name = to get input of user

a = `hostname` = (tick as this is variable that does something)
$a = to call that variable

BASIC SCRIPT #3
IF-then script

#!/bin/bash
count=1
if [ $count -eq 100 ]
then
  echo Count is 100
else
  echo Sorry is not 100
fi (to finish the if, opposite of if)

BASIC SCRIPT #4
#!/bin/bash

clear
if [ -e /home/pnowak/error.txt ]
  then
  echo "File exist"
  else
  echo "File does not exist"
fi 

BASIC SCRIPT #5
For loop Scripts 
#!/bin/bash

for i in 1 2 3 4 5
do
echo "Welcome $1 times"
done

BASIC SCRIPT #6
#!/bin/bash

for i in eat run jump play
do
echo See Imran $i
done

BASIC SCRIPT #7
do-while Scripts

while [condition]
do
  cmd1
  cmd2
  cmd3
done

BASIC SCRIPT #8
CASE STATEMENT SCRIPTS
if option a is selected = do this
if option b is selected = do this
if option c is selected = do this


#!/bin/bash
echo
echo Please chose one of the options below
echo (we do echo to leave 1 line empty)
echo 'a = Display Date and Time'
echo 'b = List file anddirectories'
echo 'c = List users logged in'
echo'd = check System uptime'
echo

read choices

case $choice in 
  a) date ;;
  b) ls ;;
  c) who ;;
  d) uptime ;;
  *) echo invalid choice - Bye ;;
esac
