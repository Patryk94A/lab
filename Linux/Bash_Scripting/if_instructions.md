#!/bin/bash

INSTALLDIR=/var/lib/finbook
ERROR_CONFLICT_DETECTED=100
ERROR_INSTALDIR_EMPTY=102
ERROR_EXTERNAL_COMMAND_FAIL=102

if [[ -z $INSTALLDIR ]]; then 
  echo "INSTALLDIR cannot be empty...."
  exit $ERROR_INSTALLDIR_EMPTY
fi

if [[ -d $INSTALLDIR ]]; then     = -d= file exist and is directory
  echo "Directory $INSTALLDIR already exist"
elif [[ -e $INSTALLDIR ]]; then       = -e is there anything that exists and is a file, dir, device...
  echo "Path $INSTALLDIR already exists, but it is not a dir. Aborting Installation!"
  exit $ERROR_CONFLICT_DETECTED
else
  echo "Creating directory $INSTALLDIR"
  mkdir $INSTALLDIR
  Result=$?
  if [[ $Result -ne 0 ]]; then
    echo "Error ($Result) while creating..."
    exit $ERROR_EXTERNAL_COMMAND_FAIL
  fi
fi

exit 0
