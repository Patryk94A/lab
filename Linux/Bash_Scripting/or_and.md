empty=' '
not_empty='abc'

test -z $empty ( using -z we are checking if a file is empty and if it is we put true, in this case empty is empty so it gives 0 true)
echo $?
0

test -z $notempty (in this case it isn't empty si it gives 1, not true)
echo $?
1

test 10 -gt 1 -a 100 -gt 99      = -gt =greater then; -a = and
echo $?
0

test 10 -gt 1 -o 100 -lt 99      -gt = greater then; -o = or; -lt = lower then
echo $?
0

[ 10 -gt 1 -a 100 -lt 99 ]
echo$?
1

[ 10 -gt 1 -o 100 -lt 99 ]
echo $?
0

[[ 10 -gt 1 -a 100 -lt 99 ]]
error
[[ 10 -gt 1 && 100 -lt 99 ]]        = && = AND when using double brackets [[ ... ]]
echo $?
1

[[ 10 -gt 1 -o 100 -lt 99 ]]
ERROR
[[ 10 -gt 1 || 100 -lt 99 ]]      || = OR when using double brackets [[ .. ]]
echo $?
0
