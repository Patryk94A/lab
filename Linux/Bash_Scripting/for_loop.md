for i in {1..5}; do
  echo $!
done

for i in {1..5}; do
  for j in {1..5}; do
    echo "$i x $j = (($i*$j))"
  done
done

for file in files/*.txt; do
  echo $file
done

DAYS="Mon Tue Wed Thu Fri Sat Sun"
for day in $DAYS; do
  echo $day
done

$DAYS without ".." is going to show
Mon
Tue
Wed...

$DAYS with ".." will show 
Mon Tue Wed...


