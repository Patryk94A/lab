PROG=../usr/bin/zip

echo ${PROG}  => you can use {...} to put variable inside, but you don't have to
../usr/bin/zip

echo ${PROG%}/*}    => % to get rid of something at the end of sentence
../usr/bin        /* = everything that is after /

echo ${PROG%%/*}    => %% to get rid of the longest end that fits /*
..

echo ${PROG#*/}      => this will delete the shortest,but from LEFT
usr/bin/zip

echo ${PROG##*/}      => this will delete the longest that fits it
zip

echo ${PROG:7:3}      => go 7 characters to right and take 3 next characters
bin

echo ${PROG::3}        => i go 0 characters to right and take 3 characters
../

echo ${PROG:2}          => go 2 characters to right and take all the rest
/usr/bin/zip
