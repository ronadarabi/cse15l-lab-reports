# **Lab Report Week 1**

## Installing VS Code
Fortunately I already had Visual Studio Code installed, but if you do not already have it, then click on this [link](https://code.visualstudio.com/download). Once downloaded the page should look something like this: 

![vscodeScreenshot](https://user-images.githubusercontent.com/68180000/193378761-ea4ee918-e2ac-464c-9753-dfc4d266e3f5.jpg)


## Remotely Connecting
Now time to connect to our remote server! If you are on Windows, check to see if you have a program called OpenSSH. If you do not, use this [link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) to install the OpenSSH client. 

Next, log in with `$ ssh cs15lfa22zz@ieng6.ucsd.edu`, replacing the 'zz' with the two letters specific to your username. Even though I had reset my password in advance, I was not able to successfully log in with my username and instead had to use the TA email and password. Once logged in this screen pops up: 

![loggedInSC](https://user-images.githubusercontent.com/68180000/193379049-0a07d8ef-a9bb-4cbe-91d2-2744a1a07108.jpg)

Because I used the TA log in, I created a directory to work in with the command `mkdir ronasDirectory`. 

## Trying Some Commands 
Once logged in, you can try out a few commands. First, I accessed this directory using `cd ronasDirectory`. From there, I used the following command, `ls /home/linux/ieng6/cs15lfa22/cs15lfa22nf` to access my lab partner, Chris', file. The output looked like this: 

![outputSC](https://user-images.githubusercontent.com/68180000/193379461-26876d04-7bfb-47ed-b8ce-a41101cf09fa.jpg)

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

To check if it runs we can use `javac WhereAmI.java` and then `java WhereAmI`. The first command is responsible for the compiling while the second one does the running. Then, on the terminal for the client computer (again, this is yours), type in the following `scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/` while again replacing the 'zz' with your specific letters. This will prompt you to enter a password. 

To see if it is on the remote computer, use `ssh` to log in and `ls` to search for it. You can then run the `javac WhereAmI.java` and `java WhereAmI` commands to verify that it worked. 

## Setting an SSH Key
To save time, we can make it so that we do not have to keep re-entering our passwords. 

## Optimizing Remote Running
