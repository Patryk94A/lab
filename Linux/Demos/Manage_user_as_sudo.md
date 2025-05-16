I was wandering how it workt in real life/pro environment. How do users get sudo privileges. Are they added like i have learned from the course to the wheel group? Or is there other way they do that?
So basically what i was tought:
at /etc/sudoers => i needed to check if wheel is uncommended.
\/
usermod -aG wheel username => to add user to wheel group to be able to sudo with that user..
\/
then i could check using
vi /etc/group    OR
grep wheel /etc/group    OR
getent group wheel      -->> this one seems to be very useful and recommended in profesional and networked environment.

In case i wanted to remove a user from a group i would go with:
gpasswd -d username groupname   ==>> standard and safe way to remove a user from a group. -d is to remove any user from any group under /etc/group



THEN i have was thinking that it should go using a sudo group that i can add users to it and then they have sudo privileges:
So i asked COPILOT for assistance..
he gave me 2 aswers:
We can create a new group by: groupadd name_pf_group

1. Not recommended for large environment.
   sudo visudo (which visudo => /usr/sbin/visudo to check where it is stored)
   then i add:
   %groupname ALL=(ALL) ALL   (% means it is a group)(instead of groupname i put actual groupname that i want that have sudo privilages)

2. This option is recommended for a large environment.
   Create a dedicated file in /etc/sudoers.d/groupname
   sudo visudo -f /etc/sudoers.d/groupname
   \/
   then add:
   %groupname ALL=(ALL) ALL  (% means it is a group)(instead of groupname i put actual groupname that i want that have sudo privilages)
   (visudo -f opens or create a file in a safe editor that checks for syntax errors before saving.)
