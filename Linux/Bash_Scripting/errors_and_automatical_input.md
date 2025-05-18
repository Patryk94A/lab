find /etc -name *.conf > text.txt        
this will redirect it into text.txt

find /etc -name *.conf >> text.txt 
this will add the text to al existing one

find /etc -name *.conf > text.txt 2>find_errors.txt  
the standard exit code has to be redirected elsewhere   find_errors.txt in this case

find /etc -name *.conf > text.txt 2>&!   
all in 1 file

find /etc -name *.conf > text.txt 2>/dev/null
2>/dev/null  => put all errors in this case into "black hole" it will dissapear in there


tell_me.sh
#!/bin/bash

read -p "Enter directory name " DIR
read -p "Enter file name " FILE

echo "directory name $DIR"
echo "file name $FILE"

read -p "Enter file name " FILE    
==>> read works as a input and then save it into variable FILE
echo $FILE
______________________________________________________________
tell_him.sh
#!/bin/bash

./tell_me.sh >> END_OF_INPUT
/etc
passwd
END_OF_INPUT

echo "done!"
exit 0

THIS script will call ./tell_me itself and itself will put whats called in the first script. Automatically.

______________________________________________________________
cat > info.txt
/etc
shadow

./tell_me.sh < info.txt

this will also take input itself from the info.txt and then start the script itself
