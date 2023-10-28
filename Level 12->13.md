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
# password - wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
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

1) 

