test -f /etc/passwd = does this file exist and is it normal file?
0 = true
1= false

test -f /etc
1 = etc is not a normal file

[ -f /etc/passwd ]     = spaces required
echo $?
0

[ -f /etc ]
echo %?
1

[[ -f /etc/passwd ]]
echo$?
0

[[ -f /etc ]]
echo $?
1

test is a external command whereas [[ .. ]] Internal and [ .. ] also
a='a'
b='b'

test $a=$a
echo $?
0 (true)

test $a=$b
echo $?
1

[ $a \> $b ]      = there needs to be backslash '\', otherwise it won't read it as greater sign
echo $?
1

[ '1' = '01' ]         = it seems to be string insite '... ' so it itsn't equal
echo $?
1

x=10
y=100

test $x -lt $y        = lower then
0

[ $x -eq $x ]      = equal
0

[ $x -eq $y ]        
1

[[ $x -ne $y ]]      = not equal
0

[ 'a' -eq 'a' ]        = works only on digits not strings
error 

