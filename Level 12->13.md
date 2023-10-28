# Level 12->13

1) ls - it shows daa.txt exists in directory
2) cat data.txt - we get to know that it is hex coded
3) mkdir /tmp//akshaj - to create a folder inside tmp
4) cp data.txt /tmp/akshaj - to copy data of data.txt into akshaj 
5) cd /tmp/akshaj
6) ls - it shows data.txt
7) mv data.txt hexdump.txt - to rename the file
8) file hexdump.txt - it shows that the file is ASCII text
9) xxd -r hexdump.txt > binary.txt - to reverse coding of hex into binary
10) file binary - we find that it is in gzip compress format
11) mv binary.txt binary.gz
12) gzip -d binary.gz - to decrypt gzip compressed binary file
13) file binary - it shows that it is bzip2 compressed
14) mv binary binary.bz2
15) bzip2 -d binary.bz2
16) file binary - shows it is gzip compressed
17) mv binary binary.gz
18) gzip -d binary.gz
19) file binary - shows : POSIX tar archive (GNU)
20) POSIX tar archive (GNU) -  this gives the idea that now we will have to use tar command
21) mv binary binary.tar
22) tar xf binary.tar - To extract a tar archive, use the --extract (-x) option followed by the archive name : tar -xf archive.tar
23) ls - it shows binary.tar , data5.bin , hexdump.txt
24) file data5.bin - tells us that POSIX tar archive (GNU)
25) mv data5.bin data.tar
26) tar xf data.tar
27) ls - data6.bin, data.tar
28) file data6.bin - bzip2 compressed
29) mv data6.bin data6.bz2
30) bzip2 -d data6.bz2
31) file data6 - POSIX tar archive (GNU)
32) mv data6 data6.tar
33) tar xf data6.tar
34) ls - data6.tar , data8.bin ...
35) file data8.bin - gzip compressed
36) mv data8.bin data8.gz
37) gzip -d data8.gz
38) file data8 - ASCII encoded
39) cat data8
40) shows password - wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
# password 13 - wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
commands - ls,cat,mkdir,cd
cp - to copy
mv - to rename
file
xxd- creates a hex dump of a given file or standard input
gzip- gzip command compresses files
bzip2- bzip2 command in Linux is used to compress and decompress the files
tar - The Linux ‘tar’ stands for tape archive, which is used to create Archive and extract the Archive files.

reference - https://www.geeksforgeeks.org/gzip-command-linux/ ,   https://linuxize.com/post/how-to-create-and-extract-archives-using-the-tar-command-in-linux/#:~:text=The%20most%20common%20uses%20of,to%20add%20to%20the%20archive. , searched for way of using other commands.  


# Level 13-14

1) ls - shows one file : sshkey.private
2) cat - /etc/bandit_pass/bandit14 - tried it but couldnt get the access
3) ssh -i - The -i flag allows login with the private key.
4) so we use ssh -i command
5) ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
6)  it lets us login into bandit14 server directly

commands - ls , ssh ( -i ).

reference - https://docs.rackspace.com/docs/logging-in-with-an-ssh-private-key-on-linuxmac

# Level 14-15

1) ls
2) man telnet
3) cat /etc/bandit_pass/bandit14 - bcuz in last level it was told that : The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14.
4) so got password of 14 - fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
5) telnet localhost 30000 - to connect to localhost port 30000
6) now i enter the password of bandit14 - fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
7) i get the correct password for bandit 15 - jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

# password level 14 - fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
# password level 15 - jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

commands - ls,cat
telnet(localhost ) - In Linux, the telnet command is used to create a remote connection with a system over a TCP/IP network. For example, we are connecting our system with the localhost. Execute the command as follows: telnet localhost  .

reference - https://www.javatpoint.com/linux-telnet-command

# Level 15-16
1) man openssl
2) openssl s_client -connect localhost:30001
3) Then I paste password - jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
4) I get output as Corrrect!
JQttfApK4SeyHwDlI9SXGR50qclOAil1


# password 16 - JQttfApK4SeyHwDlI9SXGR50qclOAil1

commands - openssl ( s_client, -connect)
openssl - OpenSSL is a cryptography software library or toolkit that makes communication over computer networks more secure. It is generally used for Transport Layer Security(TSL) or Secure Socket Layer(SSL) protocols.
s_client - The s_client command implements a generic SSL/TLS client which connects to a remote host using SSL/TLS. It is a very useful diagnostic tool for SSL servers.
- connect - This specifies the host and optional port to connect to.

reference - https://www.openssl.org/docs/man1.0.2/man1/openssl-s_client.html

# Level 16-17

1) nmap -sV localhost -p 31000-32000
2) we get -
31046/tcp open  echo
31518/tcp open  ssl/echo
31691/tcp open  echo
31790/tcp open  ssl/unknown
31960/tcp open  echo

3) here ssl connections are only 2 and amongst them one is ssl/echo which will just give us what we input so it norrows us down to ssl/unknown port
4) openssl s_client -connect localhost:31790 - connecting to that ssl port
5) now we write the password for this level that is - JQttfApK4SeyHwDlI9SXGR50qclOAil1
6) we get a RSA private key -
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW                                                                                                  JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX                                                                                                  x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD                                                                                                  KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl                                                                                                  J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd                                                                                                 d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC                                                                                                  YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A                                                                                                  vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama                                                                                                  +TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT                                                                                                  8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx                                                                                                  SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd                                                                                                  HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt                                                                                                  SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A                                                                                                  R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi                                                                                                  Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg                                                                                                  R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu                                                                                                  L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni                                                                                                  blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU                                                                                                  YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM                                                                                                  77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b                                                                                                  dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3                                                                                                  vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=

7) cd /tmp/bandit7 - now going inside bandit17
8) ls - it shows that bandit17key.private file exits which is the rsa key
9) so its the private key for next bandit17 server
10) simply using ssh -i  command we connect to bandit17 server
11) ssh -i bandit17key.private bandit17@bandit.labs.overthewire.org -p 2220
12) yes - for key fingerprint

# rsa pvt key - 
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW                                                                                                  JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX                                                                                                  x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD                                                                                                  KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl                                                                                                  J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd                                                                                                 d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC                                                                                                  YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A                                                                                                  vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama                                                                                                  +TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT                                                                                                  8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx                                                                                                  SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd                                                                                                  HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt                                                                                                  SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A                                                                                                  R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi                                                                                                  Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg                                                                                                  R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu                                                                                                  L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni                                                                                                  blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU                                                                                                  YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM                                                                                                  77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b                                                                                                  dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3                                                                                                  vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=

commands - cd,ls
nmap - Nmap is Linux command-line tool for network exploration and security auditing.
openssl,ssh.

referance - https://www.geeksforgeeks.org/nmap-command-in-linux-with-examples/

# Level 17-18

1) ls - shows files passwords.old and passwords.new exist
2) diff passwords.old passwords.new - to find the difference between the files
3) the output was - 42c42                                                                                                                                         < p6ggwdNHncnmCNxuAt0KtKVq185ZU7AW                                                                                                                               ---                                                                                                                                                                > hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg

4) as we wrote passwords.new in diff command in the second place hence the password  is also printed in the second half.

# password 18 - hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg

commands - ls, diff - to find difference between files

reference - https://www.geeksforgeeks.org/diff-command-linux-examples/

# Level 18-19

First i thought as we arent able to lgin using ssh , is there any other commandd to get into a server.
But then i found out that we can remotely access a server using ssh command itself 
learnt about in the reference link given below

1) ssh bandit18@bandit.labs.overthewire.org -p 2220 ls - it asks for the password of bandit18 and then shows that readme file exists.
2) ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme - it asks for the password of bandit18 and then gives us the password for bandit19

# password 19 - awhqfNnAbc1naukrpqDYcF95h7HoMTrC

commands - ssh ( ls, cat).
reference - https://www.hostinger.in/tutorials/ssh/basic-ssh-commands

# Level 19-20



