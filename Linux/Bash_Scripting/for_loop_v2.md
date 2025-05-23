#!/bin/bash

for server in $(cat /servers.txt); do
  ping -c 1 "$server" >/dev/null 2>&1
  if [[ $? -eq 0 }}; then
    echo "$server is alive"
  else
    echo "$server is not responding"
  fi
done


#!/bin/bash
DAYS= "Mon Tue Wed Thu Fri Sat Sun"
i=0
for day in $DAYS; do
  CATALOG="$((++i))-$day"        = ++i and i++ are different, ++i will add 1 to i ; i++ will show i then add1
  echo CATALOG
  mkdir CATALOG
done

#!/bin/bash
kiss=1
MAX_KISS=5
while [[ $kiss -le $MAX_KISS ]]; do
  echo "$kiss fro auntie Helen!"
  kiss=$(($Kiss+1))
done
exit 0

#!/bin/bash
FILE=/etc/hosts
while read line; do
  echo $line
done <$FILE         = take input from $FILE
exit 0

#!/bin/bash
FILE=/tmp/go.txt
while [[ ! -f $FILE]]; do        = -f takes true when no file detected
