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

![sshkeygen2](https://user-images.githubusercontent.com/68180000/195667299-e6074f56-4aa7-416d-b7d5-131e356a9ced.jpg)

First I typed in `ssh-keygen -t ed25519` (this is because I am on Windows) and once prompted with 'Enter file', I pressed enter. After getting the keyart, I then logged in to the server using `ssh`, and once on the server, used `mkdir .ssh` since .ssh is the directory we stored the file in. I then logged out of the server, back to the client computer. Then enter the path shown in the screenshot and your username. Mine looked like this `scp \Users\ronad/.ssh/id_ed25519.pub cs15lfa22mv@ieng6.ucsd.edu:~/.ssh/authorized_keys`.

This is me logging in without password: 
![loggedInSC3](https://user-images.githubusercontent.com/68180000/195680977-c8eeec95-7fd9-42b3-921a-1ca339dd71d8.jpg)


## Optimizing Remote Running
To optimize the remote running, I began typing in what is shown in the screenshots: 

![scpSC](https://user-images.githubusercontent.com/68180000/195696774-d105aef3-9cd7-461d-bc1c-9a2b9e53d70c.jpg)

![lsSC](https://user-images.githubusercontent.com/68180000/195696670-7c07fd60-a106-407a-bc9e-015f523f56b4.jpg)

![multipleFiles](https://user-images.githubusercontent.com/68180000/195696513-acabd5a1-18c6-44e4-9c0f-7b520e5644ed.jpg)

This ran the WhereAmI.java file (which had been updated with a hello!). 
