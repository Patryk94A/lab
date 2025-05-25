#!/bin/bash

function is_weekend()      () doesn't need to be specifie
{
  WEEKDAY=$(date +%w)

  if [[ $WEEKDAY -eq 0 || $WEEKDAY -eq 6 ]]; then
    echo "It is a weekend!"
    return 0
  else
    echo "It is not a weekend... go to work"
    return 1
  fi

MESSAGE=$(is_weekend)

echo "The result is: $MESSAGE"
