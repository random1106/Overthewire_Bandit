# Overthewire_Bandit

Welcome to the GitHub walkthrough for the Bandit Wargame! This repository is designed to guide you through the levels of Bandit. 
Bandit is structured as a series of progressively challenging levels, starting from Level 0 and culminating in Level 34. 
Each level presents unique tasks that will help you build essential skills in navigating the Linux command line, 
working with files, and understanding basic security concepts. By successfully completing each level, you'll unlock the next, 
gaining valuable knowledge and experience along the way.

This walkthrough provides detailed instructions, tips, and solutions for each level, making it easier for you to understand the concepts 
and techniques required to progress.

I am using Kali Linux Virtual Machine for this entire task. 

## Level 0 -> 1

`ssh bandit0@bandit.labs.overthewire.org -p 2220`
   
Here, `-p` specifies the port number of the secure shell connection to the target server. 
Use the password `bandit0` to login.

Use `ls` to find all the files in the current directory. We find `readme`. 

Use `cat readme` to find the password to the next level.

The password to next level is
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## Level 1 -> Level 2

Use `ssh` to login with the password of the previous step.

Use `ls`, we find a file with name `-`.

Use cat ./- to handle the filename issue, and you will find the password.

The password to next level is
263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Level 2 -> Level 3

Use `ssh` to login with the password of the previous step.

Use `ls`, we find the file named `spaces in this filename`.

Use `cat "spaces in this filename"`, and you will find the password.

The password to next level is
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Level 3 ->  Level 4

Use `ssh` to login with the password of the previous step.

Use `ls`, then use `cd inhere` to enter the directory.

Enter the `inhere` folder, use `ls -la` again, we find the file `...Hiding-From-You`.

Use `cat ...Hiding-From-You`, and you will find the password.

The password to next level is
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## Level 4 -> Level 5

Use `ssh` to login with the password of the previous step.

Use `ls`, then use `cd inhere` to enter the directory. We find `-file00` ... `-file09`.

Use `file ./*` (the ./ is used for escaping `-` in the filenames),

![image](https://github.com/user-attachments/assets/91c4a6f1-1aa4-4c68-b577-7e367b7934b3)

Use `cat ./file07` open the ASCII text file and obtain the password.

The password to next level is 
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Level 5 -> Level 6

Use `ssh` to login with the password of the previous step.

`cd inhere`

We want to find the files that is human-readable, size 1033 bytes and non-executable.

`find -type f -size 1033c | file -f- | grep -i 'text'`

Here `-type f` seraches for the file instead of directory, `-size 1033c` specifies the size of the file, the `-f-` flag specifies the input is a list of files, `grep -i 'text'` filters the human-readable file.

![image](https://github.com/user-attachments/assets/a1bc4d4b-f253-493e-9a43-f3dcb418c942)

Open the file and find the password.

The password to next level is 
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Level 6 -> Level 7

Use `ssh` to login with the password of the previous step.

`find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`

Here `-user` and `-group` specify the user and group name. `2>/dev/null` discards the error message.

![image](https://github.com/user-attachments/assets/1ed9f02c-5e6c-47e6-a4e2-b530f6e2badb)

Use `cat /var/lib/dpkg/info/bandit7.password` and find the password.

The password to next level is 
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## Level 7 -> Level 8

Use `ssh` to login with the password of the previous step.

`cat data.txt | grep -i "millionth"

![image](https://github.com/user-attachments/assets/5cf2a52a-0641-455f-b320-be8baeba49cb)

The password to next level is 
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## Level 8 -> Level 9

Use `ssh` to login with the password of the previous step.

Use `ls`, we find `data.txt`. Use `sort data.txt | uniq -u`

Here `sort` sorts the txt file according to rows, `uniq -u` only prints unique lines.

![image](https://github.com/user-attachments/assets/5e0d8e9d-d4e3-44f7-9d71-df74c5a0cd90)

The password to next level is 
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Level 9 -> Level 10

`cat data.txt | grep -a =====` 

Here data.txt is a binary file, we need to add `-a` option so 
that `grep` can process as if it were text

![alt text](image.png)

The password to next level is 
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## Leve 10 -> Level 11

`cat data.txt | base64 -d`

Here the option `-d` is used to decode the base64 encoding.

![alt text](images/image-1.png)

The password to next level is 
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

## Level 11 -> Level 12

`cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'`

Here since we want to rotate the letter by 13 position, 
we need to rotate a → n, b → o, ..., n → a, o → b and similarly 
for the capitalized letter. By using `tr`, we complete 
this rotation.

![alt text](images/image-2.png)

The password to next level is 
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## Level 12 -> Level 13

Since we are only allow to write in `tmp` folder, we first 
make a folder inside.

`mktemp -d`

The temp directory is /tmp/tmp.Sqb3z4WIof

![alt text](images/image-3.png)

`cp /home/bandit12/data.txt /tmp/tmp.Sqb3z4WIof`

Enter the temp folder, inspect the file, it is a hex dump.

![alt text](images/image-4.png)

We can use `xxd -r` to decode the hexdump. 

`xxd -r data.txt > decode.txt`

We check the file type using

`file decode.txt`

![alt text](images/image-5.png)

Let us uncompress the file using gunzip, before that, we need 
to modify the extension to `.gz`

`mv decode.txt data2.bin.gz && gunzip data2.bin.gz`

We get a new file `data2.bin`. 

![alt text](images/image-6.png)

`mv data2.bin data2.bin.bz2 && bzip2 -d data2.bin.bz2`

![alt text](images/image-7.png)

Check the file type, and repeat the previous steps. 

![alt text](images/image-8.png)

This time we get a tar archive.

`mv data5.bin data4.bin.tar && tar -xvf data5.bin.tar`

`-v` means verbose. `-x` is for extraction. 
`-f` uses archive file or device ARCHIVE.

![alt text](images/image-9.png)

We get `data5.bin`

![alt text](images/image-10.png)

Repeat the previous step

`mv data5.bin data5.bin.tar && tar -xvf data5.bin.tar`

![alt text](images/image-11.png)

We get `data6.bin`

![alt text](images/image-12.png)

Repeat the previous step

`mv data6.bin data6.bin.bz2 && bzip2 -d data6.bin.bz2`

![alt text](images/image-14.png)

Repeat the previous step

`mv data6.bin data6.bin.tar && tar -xvf data6.bin.tar`

We get `data8.bin`

![alt text](images/image-15.png)

Repeat

`mv data8.bin data8.bin.gz && gunzip data8.bin.gz`

We get the password

![alt text](images/image-16.png)

The password to next level is 
FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

## Level 13 -> Level 14

There is a ssh private key in the level 13

![alt text](images/image-17.png)

We copy the ssh private key to our local machine as `sshkey.private`

We need to set the key to be only readable to the owner

`chmod 400`

![alt text](images/image-18.png)

We use the private key to log in to level 14

`ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220`

![alt text](images/image-19.png)

Success. We can retrieve the password for level 14 by 

`cat /etc/bandit_pass/bandit14`

![alt text](images/image-20.png)

The password to next level is 
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

## Level 14 -> Level 15

Log in to level 14, use

`nc -nv 127.0.0.1 30000`

Here 127.0.0.1 is the ip for localhost, `-n` flag disables the 
DNS resolution, `-v` is the verbose mode. 

After connecting, submit the password of level 14, we retrieve the password for Level 15.

![alt text](images/image-21.png)

The password to next level is 
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

## Level 15 -> Level 16

`openssl s_client -connect 127.0.0.1`

Enter the password of the current level after the 'Read R BLOCK', we get 

![alt text](images/image-22.png)

The password to next level is kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

## Level 16 -> Level 17

`nmap 127.0.0.1 -p 31000-32000 -sV`

![alt text](images/image-24.png)

`openssl s_client 127.0.0.1 31518`

![alt text](images/image-25.png)

Something seems wrong ... Let us try the other port with ssl service

`openssl s_client 127.0.0.1 31790`

We Enter the password and retrieve the ssh private key

![alt text](images/image-26.png)

Store it in a local file `sshkey.private` 

make it not accessible by others.

`chmod 400 sshkey.private`

Then we use 

`ssh -i sshkey.private bandit17@bandit.labs.overthewire.org -p 2220`

to log into the next level. 

We can retrieve the password in `/etc/bandit_pass` once we logged in.

The passowrd is EReVavePLFHtFlFsjn3hyzMlvSuSAcRD

## Level 17 -> Level 18

`diff passwords.new passwords.old`

< indicates the difference in the first file, while > indicates the difference in the second file.

![alt text](images/image-27.png)

The password to the next level is x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

## Level 18 -> Level 19

When using ssh to log in, the session immediately finishes. 

So we attach the command `cat readme` right after the ssh

`ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme`

This retrieves the password.

![alt text](images/image-28.png)

The password to the next level is cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8

## Level 19 -> Level 20

We try to run command via `bandit20-do` 

`./bandit20-do id`

![alt text](images/image-29.png)

This tells us when running command using `./bandit20-do`, the effective user is `bandit20`. Therefore, we can extract the password via 

`./bandit20-do cat /etc/bandit_pass/bandit20`

![alt text](images/image-31.png)

The password to the next level is 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO

## Level 20 -> Level 21

On level 20, we find an executable file named suconnect with SUID. This means that if we can execute it, we can run it as the root user.

![alt text](images/image-32.png)

According to the problem, this file makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

So we use `nc -nlvp 4444` to set up a listener. 

Then log in through another terminal, do `.\suconnect 4444`

![alt text](images/image-34.png)

As expected, we see a connection on the listener.

![alt text](images/image-33.png)

We input the password of level 20 and retrieve the password of level 21. 

![alt text](images/image-35.png)

The password to the next level is EeoULMCra2q0dSkYj561DX7s1CpBuOBt

## Level 21 -> Level 22

According to the instruction, we look at /etc/cron.d folder. We have read permission to `cronjob_bandit22`, open it.

![alt text](images/image-36.png)


The cron file runs `usr/bin/cronjob_bandit22.sh`, for which we have read permission.

![alt text](images/image-39.png)

Read the file. 

![alt text](images/image-37.png)

It seems the file will read the password of level 22 and write it to a file in `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`. We read this file and find the password.

![alt text](images/image-38.png)

The password to the next level is tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q

## Level 22 -> Level 23

Go to `/etc/cron.d` and open `cronjob_bandit23`

![alt text](image-41.png)

base on the output, we know this file will be executed by user `bandit23` every minute. Let us browse the content. 

![alt text](image-42.png)

So the user `bandit23` run the file and write the password of level 23 to a file whose name is encrypted in the `tmp` folder.

We can find the name by running the command with `$myname = bandit23`

![alt text](images/image-40.png)

Open the file `/tmp/8ca319486bfbbc3663ea0fbe81326349`, we find the password. 

![alt text](image-44.png)

The password to the next level is 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga

## Level 23 -> Level 24

Open the file `cronjob_bandit24` in the directory `/etc/cron.d`. This file will be run by user `bandit24` every minute. 

![alt text](images/image-45.png)

In particular, it will delete every file in `/var/spool/bandit24/foo`. And if the owner of the file is `bandit23`, if will run it, then delete.

![alt text](images/image-46.png)

We write a `script.sh` the in tmp folder `/tmp/tmp.cYY5SQP0B0`

```
#!/bin/bash

cat /etc/bandit_pass/bandit24
```

`chmod a+x`

We copy it to `/var/spool/bandit24/foo` and hope this to be executed. However, we receive no response from our screen. This is because the `cronjob_bandit24.sh` will redirect the output to `/dev/null`

![alt text](images/image-47.png)

So we change our script. We open a netcat listener on port 4444, and paste the `script.sh` to `/var/spool/bandit24/foo` with the following content

```
#!/bin/bash

cat /etc/bandit_pass/bandit24 | nc 127.0.0.1 4444
```

![alt text](images/image-48.png)

The password to the next level is gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8

## Level 24 -> Level 25


