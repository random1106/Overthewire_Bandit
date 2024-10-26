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











