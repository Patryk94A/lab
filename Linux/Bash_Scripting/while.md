#!/bin/bash
FILE=/tmp/go.txt
while [[ ! -f $FILE ]]; do
  echo -n '.'
  sleep 1
done
echo "File $FILE Exists!"
exit 0

[[ ! -f $FILE ]] = -f $FILE only this checks if $FILE exists and outputs true when it does, but with ! it outputs true when it doesn't exist
When we create /tmp/go.txt it outputs false and goes further.

#!/bin/bash
while true; do
  echo -n '.'
  sleep 1
  if [[ -f $FILE ]]; then
    break        = breaks the loop
  fi
done    




$!/bin/bash
YEAR=2030
MONTHS=12
DAYS=31
BASEDIR=/tmp
m=1

while [[ $m -le $MONTHS ]]; do
  d=1
  while [[ $d -le $DAYS ]]; do
    Dir="$BASEDIR/$YEAR/$m/$d"
    echo $DIR
    mkdir -p $DIR
    d=$((d+1))
  done
  m=$((m+1))
done

    
