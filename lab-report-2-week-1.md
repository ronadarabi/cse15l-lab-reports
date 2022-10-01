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

## Moving files with `scp`

## Setting an SSH Key

## Optimizing Remote Running
