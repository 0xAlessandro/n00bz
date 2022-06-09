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





## MISC

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
   - $0  it's the name of the file(0st argument) but in this case it gives a full unrestricted shell
   - $1 is the first argument (filename1)
   - $2 is the second argument (dir1)
   - $9 is the ninth argument
   - ${10} is the tenth argument and must be enclosed in brackets after $9.
   - ${11} is the eleventh argument.
``` 

None worked except for $0 which broke the terminal and allowed to write commands 

![solve](https://i.ibb.co/bg9VW20/solve.png)





# OSINT                                                                                                                       

                  JJJJJJJJJJJ     OOOOOOOOO     HHHHHHHHH     HHHHHHHHHNNNNNNNN        NNNNNNNN     DDDDDDDDDDDDD             OOOOOOOOO     EEEEEEEEEEEEEEEEEEEEEE
                  J:::::::::J   OO:::::::::OO   H:::::::H     H:::::::HN:::::::N       N::::::N     D::::::::::::DDD        OO:::::::::OO   E::::::::::::::::::::E
                  J:::::::::J OO:::::::::::::OO H:::::::H     H:::::::HN::::::::N      N::::::N     D:::::::::::::::DD    OO:::::::::::::OO E::::::::::::::::::::E
                  JJ:::::::JJO:::::::OOO:::::::OHH::::::H     H::::::HHN:::::::::N     N::::::N     DDD:::::DDDDD:::::D  O:::::::OOO:::::::OEE::::::EEEEEEEEE::::E
                    J:::::J  O::::::O   O::::::O  H:::::H     H:::::H  N::::::::::N    N::::::N       D:::::D    D:::::D O::::::O   O::::::O  E:::::E       EEEEEE
                    J:::::J  O:::::O     O:::::O  H:::::H     H:::::H  N:::::::::::N   N::::::N       D:::::D     D:::::DO:::::O     O:::::O  E:::::E             
                    J:::::J  O:::::O     O:::::O  H::::::HHHHH::::::H  N:::::::N::::N  N::::::N       D:::::D     D:::::DO:::::O     O:::::O  E::::::EEEEEEEEEE   
                    J:::::j  O:::::O     O:::::O  H:::::::::::::::::H  N::::::N N::::N N::::::N       D:::::D     D:::::DO:::::O     O:::::O  E:::::::::::::::E   
                    J:::::J  O:::::O     O:::::O  H:::::::::::::::::H  N::::::N  N::::N:::::::N       D:::::D     D:::::DO:::::O     O:::::O  E:::::::::::::::E   
        JJJJJJJ     J:::::J  O:::::O     O:::::O  H::::::HHHHH::::::H  N::::::N   N:::::::::::N       D:::::D     D:::::DO:::::O     O:::::O  E::::::EEEEEEEEEE   
        J:::::J     J:::::J  O:::::O     O:::::O  H:::::H     H:::::H  N::::::N    N::::::::::N       D:::::D     D:::::DO:::::O     O:::::O  E:::::E             
        J::::::J   J::::::J  O::::::O   O::::::O  H:::::H     H:::::H  N::::::N     N:::::::::N       D:::::D    D:::::D O::::::O   O::::::O  E:::::E       EEEEEE
        J:::::::JJJ:::::::J  O:::::::OOO:::::::OHH::::::H     H::::::HHN::::::N      N::::::::N     DDD:::::DDDDD:::::D  O:::::::OOO:::::::OEE::::::EEEEEEEE:::::E
         JJ:::::::::::::JJ    OO:::::::::::::OO H:::::::H     H:::::::HN::::::N       N:::::::N     D:::::::::::::::DD    OO:::::::::::::OO E::::::::::::::::::::E
           JJ:::::::::JJ        OO:::::::::OO   H:::::::H     H:::::::HN::::::N        N::::::N     D::::::::::::DDD        OO:::::::::OO   E::::::::::::::::::::E
             JJJJJJJJJ            OOOOOOOOO     HHHHHHHHH     HHHHHHHHHNNNNNNNN         NNNNNNN     DDDDDDDDDDDDD             OOOOOOOOO     EEEEEEEEEEEEEEEEEEEEEE

                                                                                                                                                          

---

> <h3>John Doe is on the run! Find the city in which he's planning to meet someone! Start your journey by the social media ccount name noobpeople9999. Example flag: n00bz{new_york}</h3>

This are all the information that we have.

Searching this username online will lead you quickly to his instangram account.

![image](https://i.ibb.co/pj9ZW54/n00bpeople-instangram.png)


The bio is very strange so i started trying to search hidden message until I found an oline decoder that suited my case

![image](https://i.ibb.co/0CnTvsf/Tw.png)

<h3>With this information we can proceed with our research, I started looking on various social trying to find something interesting.</h2>
<h3>I found then on Twitter just what we were looking for</h2>

![image1](https://i.ibb.co/61r1Vh9/n00bmasstwitter.png)

<h3>His only tweet contained a link, which when opened downloaded a pcapng file, which contained a few tcp streams</h3>


![image](https://i.ibb.co/g66y4c4/osintchall.png)

<h3>The pcap contained a link that lead us to an image.</h3>
<h2>And here it comes the most important but also most interesting part.
This is the image</h2>

![image](https://i.ibb.co/dB2FdcB/reverse1.jpg)

After searching a little bit with google image reverse, i wasn't able to find anything.
I thought I was doing something wrong until I tried yandex, thanks to it I was able to find out the name of the river and where it was located.
All I had to do was translate the highlighted name into English and put it into the flag format so it became <h3>n00bz{new_kakhova_plavni}</h3>



                                                                                                                                              
                                                                                                                                                                                                                                                                       
                                                                                                                                                        



  

  
  
  
