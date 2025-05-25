#!/bin/bash

MAKE_REPORT='N'       = takes wrong input
DELETE_REPORT='N'     = takes wrong input
FILE=''              = empty string

-r generate raport
-d delete file before generating
-f file_name where to save it
-h help/instruction 

while [[ $# -gt 0 ]]; do

  case $1 in             = what has to happen in case this comes up (e.g -r)
    -r|--report)
      echo "-report will be created"
      MAKE_REPORT='Y'
      shift
      ;;
    -d|--delete
      echo "-d report will be deleted"
      DELETE_REPORT='Y'
      shift
      ;;
    -h|--help)
      echo "USAGE: 0$ [-r|--report] [-d|--delete] [-f|--file <file_path>]"
      exit 0
      ;;
    -f|--file)
      echo "-f report will be saved in the file $2"
      FILE=$2
      shift          = -f optie
      shift          = value of that option $2
      ;;
    *)
      echo "Unknow option! Use 0$ -h to display help"
      exit1 
      ;;
      
  esac
  
done

[[ -z $FILE ]] && echo "File parameter value is missing..." && exit 1

if [[ $DELETE_REPORT == 'Y' && -f $FILE ]]; then
  echo "Removing file $FILE"
  rm $FILE || exit 1
fi

if [[ $MAKE_REPORT == 'Y' ]]; then
  echo "Generating report in $FILE"
  df >> $FILE || exit 1
fi

exit 
