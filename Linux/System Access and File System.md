/boot => boot loader (grub.cfg)
/root => root user home dir
/dev  => System devices(disk, cdrom, keyboards)
/etc  => Config files (IMPORTANT)
/bin->/usr/bin  => Everyday user commands
/sbin->/usr/sbin  => System/filesystem commands
/opt  => Optional add-on app (NOT OS apps)
/proc  => Running processes(Only exists in memory)
/lib->usr/lib => C programming lib files needed by commands and apps
/tmp => Dir for temp files
/home => Dir for user
/var  => System logs
/run  => System daemons that start very early (e.g systemd and udev) to store temp runtime files like PID files
/mnt  => To mount external file system
/media  => For CDrom mounts

cd -> Change dir
pwd -> print working dir
ls -> list
su -> switch user

drwxr-xr-x.      ==>> d = dir
lrwxr-xr-x.      ==>> l = link to another file
-rwxr-xr-x.      ==>> - = file

File symbols  Meaning
  -               Regular file
  d               directory
  l               link
  c               Special file or device file
  s               socket
  p               Named pipe
  b               block device

Changing password:
Command => passwd userid
while root => passwd to change root password (cd / - root directory su - => switch user to root user)


Creating files and dir:
- touch -> empty files
- cp -> copy exsiting and copy at the destination location
- vi or vim text editor

Creating Directory
- mkdir
- cp -R <source_folder><destination_folder>

Find FIles and Directories
- find
- locate

find. (dot start searching from current working directory)

* if "locate" command does not output any result, then as root run "updatedb"
* Also make sure you have "mlocate" package installed:
  to check = rpm -qa | grep mlocate
  To install = yum install mlocate
*locate uses a prebuilt database, which should be regularly updated, while find iterates over a file system to locate files. Thus locate is much faster than find, but can be inaccurate if the database(can be seen as cache) is not updated.
*toupdate locate run updatedb

WildCards
* - zero or more characters
? - single character
[] - range of characters
{1..9} - goes from 1 till 9

Soft and Hard Links
-inode => Pointer or number of a file on the hard disk
-Soft link => Link will be removed if file is removed or renamed
-Hard link => Deleting renaming or moving the original filewill not affect the hard link
ln => hard link
ln -s => soft link
