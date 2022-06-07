Hi everyone, I'm 0x Alessandro.
During the period from Sat, 04 Jun. 2022, 13:00 UTC to Mon, 06 Jun. 2022, 13:00 UTC I participated in the ctf organized by https://ctf.n00bzunit3d.xyz/
I was in Cubi di Rubick team and we qualified first in high school and 7th in Open.
We have solved a total of 30 challenges and this is the writeup of the challenges that I found most interesting


![image](https://media.discordapp.net/attachments/983355827127738408/983355895536832542/unknown.png)









                                     _______  _______ ___.            _______________________________
                                ____ \   _  \ \   _  \\_ |__ ________ \_   ___ \__    ___/\_   _____/
                               /    \/  /_\  \/  /_\  \| __ \\___   / /    \  \/ |    |    |    __)  
                              |   |  \  \_/   \  \_/   \ \_\ \/    /  \     \____|    |    |     \   
                              |___|  /\_____  /\_____  /___  /_____ \  \______  /|____|    \___  /   
                                   \/       \/       \/    \/      \/         \/               \/    



MISC

                                /$$$$$  /$$$$$$  /$$$$$$ /$$      
                               |__  $$ /$$__  $$|_  $$_/| $$      
                                  | $$| $$  \ $$  | $$  | $$      
                                  | $$| $$$$$$$$  | $$  | $$      
                             /$$  | $$| $$__  $$  | $$  | $$      
                            | $$  | $$| $$  | $$  | $$  | $$      
                            |  $$$$$$/| $$  | $$ /$$$$$$| $$$$$$$$
                             \______/ |__/  |__/|______/|________/
                                      
                                      
                                      


I allow only numbers and special characters, surely you can't escape this jail! nc challs.n00bzunit3d.xyz 32281
In this challenge we were only given one remote host to connect to.


![netcat](https://i.ibb.co/2h6HCxW/Immagine-2022-06-06-171011.png)

As we can see only numbers and some special characters were allowed,so I had to find a way to get out of jail and be able to write commands in the terminal.

I started trying different kind of things such as
```
$$  ---> used to reference the process ID of bash shell itself
$!  ---> bash script parameter is used to reference the process ID of the most recently executed command in background.
$# ---> expands to a number of positional parameters in decimal.
$- ---> is used to get current option flags specified during the invocation, by the set built-in command or set by the bash shell itself. Though this bash parameter is rarely used.
$_ ---> used to reference the absolute file name of the shell or bash script which is being executed as specified in the argument list.
```
but without success.
Then i found on a webiste something interesting:
```
   - $0 is the name of the script itself (script.sh)
   - $1 is the first argument (filename1)
   - $2 is the second argument (dir1)
   - $9 is the ninth argument
   - ${10} is the tenth argument and must be enclosed in brackets after $9.
   - ${11} is the eleventh argument.
``` 

None worked except for $0  which broke the terminal and allowed to write commands 

![solve](https://i.ibb.co/bg9VW20/solve.png)
