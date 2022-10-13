# **Lab Report Week 1**

## Installing VS Code
Fortunately I already had Visual Studio Code installed, but if you do not already have it, then click on this [link](https://code.visualstudio.com/download). Once downloaded the page should look something like this: 

![vscodeScreenshot](https://user-images.githubusercontent.com/68180000/193378761-ea4ee918-e2ac-464c-9753-dfc4d266e3f5.jpg)


## Remotely Connecting
Now time to connect to our remote server! If you are on Windows, check to see if you have a program called OpenSSH. If you do not, use this [link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) to install the OpenSSH client. 

Next, log in with `$ ssh cs15lfa22zz@ieng6.ucsd.edu`, replacing the 'zz' with the two letters specific to your username. For example, my log in would be cs15lfa22mv@ieng6.ucsd.edu. Once logged in this screen pops up: 

![loggedInSC1](https://user-images.githubusercontent.com/68180000/195510827-ef623d6a-8c0b-40ff-b024-9667863a12a6.jpg)
![loggedInSC2](https://user-images.githubusercontent.com/68180000/195510878-a3a40ccc-f805-49d3-946b-4c934ffe7f87.jpg)

## Trying Some Commands 
Once logged in, you can try out a few commands. I first tried the following command, `ls /home/linux/ieng6/cs15lfa22/cs15lfa22nf` to access my lab partner, Chris', file. The output looked like this: 

![nfScreenshot](https://user-images.githubusercontent.com/68180000/195664172-c5a03c38-8224-49cd-a24b-62e5bca6d7b6.jpg)

Other commands include: 

* `cd ~`
* `cd`
* `ls -lat`
* `ls -a`
* `cp /home/linux/ieng6/cs15lfa22/public/hello.txt~/`
* `cat /home/linux/ieng6/cs15lfa22/public/hello.txt`

To log out, press Ctrl + D and then type `exit`.

## Moving files with `scp`
Say you have a file on your computer that you would like to open on the remote computer. We can use the `scp` command on the client computer, your computer. Let's try this out. 

First, make sure the file is created on the client computer. The file I created is named `WhereAmI.java` with a `WhereAmI` class: 

![whereAmISC](https://user-images.githubusercontent.com/68180000/193379755-a2c7ae5a-4c5d-4ba2-9345-1463d4b6c6a1.jpg)

To check if it runs we can use `javac WhereAmI.java` and then `java WhereAmI`. The first command is responsible for the compiling while the second one does the running. 

![whereAmIOut1](https://user-images.githubusercontent.com/68180000/195665036-99cd31a9-08ed-4be5-8582-86f890018f98.jpg)

Then, on the terminal for the client computer (again, this is yours), type in the following `scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/` while again replacing the 'zz' with your specific letters. This will prompt you to enter a password. 

![scpCommand](https://user-images.githubusercontent.com/68180000/195665350-66fed870-3af1-4548-bfa7-62cad3b5aa54.jpg)

To see if it is on the remote computer, use `ssh` to log in and `ls` to search for it. You can then run the `javac WhereAmI.java` and `java WhereAmI` commands to verify that it worked. Notice the different output. 

![whereAmIOut2](https://user-images.githubusercontent.com/68180000/195665599-3546afc7-d69a-4493-b7af-7704576483da.jpg)


## Setting an SSH Key
To save time, we can make it so that we do not have to keep re-entering our passwords. This is a general overview of what the first step looks like: 
![keygenSC](https://user-images.githubusercontent.com/68180000/193380133-5b833564-151c-4058-b5d7-89e2ee3be40e.jpg)

First I typed in `ssh-keygen` and once prompted with 'Enter file', I pressed enter. Since I am using the TA's account, it asked me to overwrite so I pressed `y` for yes. At this point, because this is not my account, I was scared to mess anything up on the TA's account so I got stuck here and unfortunately did not finish the step (I did not have time to go to office hours but will go next week to figure everything out with my account!). However my understanding is that after getting to the screenshot, you should log in on the client computer using `ssh`. Once on server, use `mkdir .ssh` and then type `<logout>`. Back on the client computer, type in `scp` and then, on the same line, use the username and the path as seen in the screenshot. These are the steps I would take on my own account. 

## Optimizing Remote Running
To optimize the remote running, I began typing in the following: 
* `scp WhereAmI.java cs15lfa22ta2@ieng6.ucsd.edu:~/ronasDirectory`
* Password
At this point I did get stuck. I am not sure what happened and think it could have something to do with the commands I ran in the 'Setting an SSH Key' (as I was not entirely sure if what I was doing was correct) or just that generally (as read in the prompt) it is not reliable to use the TA account because sometimes they change passwords (I emailed the TA about this). 

![taLogInSC](https://user-images.githubusercontent.com/68180000/193384232-40ab5200-3213-4df9-919f-0cbc8fe7e93b.jpg)

Ideally though, I would have logged in again using `ssh` and then accessed the `javac WhereAmI.java` and `java WhereAmI` commands using the up-arrow key. 

