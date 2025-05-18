df = info about some system files
df /home  = info about /home
df -h /home = human readable /home file

df -h /home | grep -v Filesystem        = this will delete the upper colomn

df -h /home | grep -v Filesystem | tr -s ' '       = this will delete and replace all spaces and replace it with only one ' '

df -h /home | grep -v Filesystem | tr -s ' ' | cut -d ' ' -f 4         = this will cut delimiter -d (and what it says (' ' space in this case) and take -f field 4

HOME_FREE = $(df -h /home | grep -v Filesystem | tr -s ' ' | cut -d ' ' -f 4)
echo $HOME_FREE



#!/bin/bash
Files=$(ls *.sh)
chmod u+x $Files

# Files=`ls *.sh`   this will work the same as $(..)
