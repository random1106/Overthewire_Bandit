# Overthewire_Bandit

Welcome to the GitHub walkthrough for the Bandit Wargame! This repository is designed to guide you through the levels of Bandit. 
Bandit is structured as a series of progressively challenging levels, starting from Level 0 and culminating in Level 34. 
Each level presents unique tasks that will help you build essential skills in navigating the Linux command line, 
working with files, and understanding basic security concepts. By successfully completing each level, you'll unlock the next, 
gaining valuable knowledge and experience along the way.

This walkthrough provides detailed instructions, tips, and solutions for each level, making it easier for you to understand the concepts 
and techniques required to progress.

## Level 0 -> 1

1. `ssh bandit0@bandit.labs.overthewire.org -p 2220`
   
Here, `-p` specifies the port number of the secure shell connection to the target server. 
Use the password `bandit0` to login.

2. Use `ls` to find all the files in the current directory. We find `readme`. 

3. Use `cat readme` to find the password to the next level.

Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## Level 1 -> Level 2

1. Use `ssh` to login with the password of the previous step.

2. Use `ls`, we find a file with name `-`.

3. Use cat ./- to handle the filename issue, and you will find the password.

Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Level 2 -> Level 3

1. Use `ssh` to login with the password of the previous step.

2. Use `ls`, we find the file named `spaces in this filename`.

3. Use `cat "spaces in this filename"`, and you will find the password.

Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Level 3 ->  Level 4

1. Use `ssh` to login with the password of the previous step.

2. Use `ls`, then use `cd inhere` to enter the directory.

3. Enter the `inhere` folder, use `ls -la` again, we find the file `...Hiding-From-You`.

4. Use `cat ...Hiding-From-You`, and you will find the password.

Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## Level 4 -> Level 5

1. Use `ssh` to login with the password of the previous step.

2. Use `ls`, then use `cd inhere` to enter the directory. We find `-file00` ... `-file09`.

3. Use `file ./*` (the ./ is used for escaping `-` in the filenames),

![image](https://github.com/user-attachments/assets/91c4a6f1-1aa4-4c68-b577-7e367b7934b3)

4. Use `cat ./file07` open the ASCII text file and obtain the password.

Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Level 5 -> Level 6

1. Use `ssh` to login with the password of the previous step.

2. `cd inhere`

3. We want to find the files that is human-readable, size 1033 bytes and non-executable.

`find -type f -size 1033c | file -f- | grep -i 'text'`

Here `-type f` seraches for the file instead of directory, `-size 1033c` specifies the size of the file, the `-f-` flag specifies the input is a list of files, `grep -i 'text'` filters the human-readable file.

![image](https://github.com/user-attachments/assets/a1bc4d4b-f253-493e-9a43-f3dcb418c942)

4. Open the file and find the password.

Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Level 6 -> Level 7

1. Use `ssh` to login with the password of the previous step.

2 `find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`

Here `-user` and `-group` specify the user and group name. `2>/dev/null` discards the error message.

![image](https://github.com/user-attachments/assets/1ed9f02c-5e6c-47e6-a4e2-b530f6e2badb)

3. Use `cat /var/lib/dpkg/info/bandit7.password` and find the password.

Password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## Level 7 -> Level 8

1. Use `ssh` to login with the password of the previous step.

2. `cat data.txt | grep -i "millionth"

![image](https://github.com/user-attachments/assets/5cf2a52a-0641-455f-b320-be8baeba49cb)

Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## Level 8 -> Level 9

1. Use `ssh` to login with the password of the previous step.

2. Use `ls`, we find `data.txt`. Use `sort data.txt | uniq -u`

Here `sort` sorts the txt file according to rows, `uniq -u` only prints unique lines.

![image](https://github.com/user-attachments/assets/5e0d8e9d-d4e3-44f7-9d71-df74c5a0cd90)

Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Level 9 -> Level 10





















