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

**grep -win**

![flightToBoston](https://user-images.githubusercontent.com/68180000/199080874-a216610c-3b8a-4675-b033-809c2dd9dc52.jpg)

This command searches in the specific file outlined for the word (in this case words) given. It then returns the block of lines containing this phrase. The phrase I used as an example was "flight to Boston" in chapter-1.txt of 911reports. 

**grep -n**

![boardingFlights](https://user-images.githubusercontent.com/68180000/199081829-5fa2c10c-feb2-4770-9950-e7cd443ed62a.jpg)

I used grep -n to find a line that matches the given input (in my case it was "Boarding the Flights"). It also returns the line number, which was 12. 

**grep -o**

![attaAndOmari](https://user-images.githubusercontent.com/68180000/199082330-2192f1dd-05e8-4955-81d4-2d1f2b1efadd.jpg)

grep -o only prints the parts of the line that match the input. It prints on a new line for each different line in which the input is found. So for example, "Atta and Omari" was the input, and it was found on four different lines, so the phrase printed four times on separate lines. It does not include the line number. 


## less

**less -F**
For this example I typed ```less -F chapter-1.txt``` and got the following output: 

![less-F](https://user-images.githubusercontent.com/68180000/199083080-cae4ae48-cb6e-40a1-b054-c2f798152e9e.jpg)

less -F exits out of less if the file can fit on one page. Since the contents of the file were too long, it did not exit. To exit, I pressed `q`. 

**less -**

**less -**
