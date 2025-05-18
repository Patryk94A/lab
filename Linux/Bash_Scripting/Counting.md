x=5
echo %((x++))  => in this case it will show x=5 and then it does ++ so it will show..
5

echo $((x++))
6

echo $((x++))
7

echo $((x++))
8

y=4
echo $((x>y))
1              => 1 is deafult and  means = true

echo $((x<y))
0              => deafult 0 menas = false

echo $((x==y))
0

echo $((x==x))
1
