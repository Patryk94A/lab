#!/bin/bash
echo $0    = the command that was run
echo $1     = first argument
echo ${10}    = more then 1 digit
echo '$#'      = how many args were sent to command
echo '$@'      = it allows to recall the list of arguments
echo '$*'      = it recalls as 1list

for param in '$@' do
  echo $param
done          = it itereates thorugh arguments

bash -x ./arg.sh      =  debugging console/view

shift = it shifts to the next element
