# Lab Report 3

## find 

**find -empty**

![find-emptyEX1](https://user-images.githubusercontent.com/68180000/199066219-264b6cb2-60ab-4df7-acf4-90e537b186fc.jpg)

find -empty searches for all the files and directories that are emtpy and returns a list of them. This can be useful for users who needed a quick way to locate empty files and directories. 

**find -iname**

![find-inameEX1](https://user-images.githubusercontent.com/68180000/199067927-e7d82dce-ef5b-4bd4-a56b-63a569e5d428.jpg)

In this example I used two commands, first -type and then -iname. -type f specifies that we are looking for a file. -iname is a more specific form of -name that gives us our exact search. This can be useful if you know the name of a file but want the exact path. 

**find -exec**

![-execrmEX1](https://user-images.githubusercontent.com/68180000/199069144-504a25e9-d60a-4c14-aaad-defc55a80b3b.jpg)

First we use find -name to find the specific file. -exec allows you to execute commands on this file. rm will remove the file, but adding -i ensures that the system asks the user before actually doing so. If you enter Y or y, it will delete the file. 

## grep 

**grep -**

**grep -**

**grep -**


## less

**less -**

**less -**

**less -**





Before logging in, I had to copy over the folder since I am using a Windows computer (which does not have some of the commands installed by default). 

![copyingFiles](https://user-images.githubusercontent.com/68180000/197061662-cc1d5baa-b6f5-4276-b5c7-802717406339.jpg)




![counttxtsResults](https://user-images.githubusercontent.com/68180000/197064811-26e0c845-748d-438f-9d34-d720b2c86650.jpg)
I had to log out of the remote to move the file with scp. 

![movingFileCountTxts](https://user-images.githubusercontent.com/68180000/197064930-fe5b3494-ce31-460f-af0a-a578af4a2ee1.jpg)

![countTxtsFileSC](https://user-images.githubusercontent.com/68180000/197065185-cc91f6b9-879c-49de-97d7-8427edb47bfe.jpg)
