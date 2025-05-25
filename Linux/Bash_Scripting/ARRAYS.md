CITIES=(Bologna Roma Venezia Milano Firence Napoli)

echo $CITIES
Bologna

echo ${CITIES[0]}
Bologna

echo ${CITIES[1]}
Roma

echo ${CITIES[2]}
Venezia

echo ${CITIES[-1]}
Napoli

echo ${CITIES[-2]}
Firence

echo ${CITIES[@]}
Bologna Roma Venezia Milano Firence Napoli

echo ${!CITIES[@]}
012345

for city in ${CITIES[@]}; do
  echo $city
done

echo ${#CITIES[@]}
6

CITIES += (PALERMO)
Bologna Roma Venezia Milano Firence Napoli PALERMO


echo ${#CITIES[@]}
7 = there are 7 elements in the array

echo ${CITIES[@]:2:4}  = go from 0 to 2 from left and take 4 cities
Venezia Milano Firence Napoli



#!/bin/bash
USERS=()
NAME=''
while [[ $NAME != 'exit' ]]; do
  read -p 'Enter username or 'exit' to finish: ' NAME
  if [[ $NAME != 'exit' ]]; then
    Users += ($NAME)
  fi
done

echo ${USERS[@]}
for NAME in ${USERS[@]}; do
  echo "Creating user $NAME...."
  useradd $NAME
done
exit 0

