#!/bin/bash

./setup.sh
RESULT=$?

if [[ $RESULT -eq 0 ]]; then
  echo "App is installed"
else
  echo "App installation failed, exit code $RESULT"
  exit 1
fi

x=10
y=20
[ $x -lt 100 ] && [ $y -gt 0 ]
echo $?
0

user=yoda   (doesn't exist)
grep $USER /etc/passwd>/dev/null && "$USER is present"        = first sentence is false and the second wont be shown

variable = wawel
if [ -z "variable" ]; then ...      

[ -z "$Variable" ] && echo "$Variable "Variable" is not defined" && exit 1
it goes from left to right so if first sentence is not right (1) it doesn't go further




