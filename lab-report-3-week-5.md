# Lab Report 3

## find -type

**Example 1** 

```[cs15lfa22mv@ieng6-203]:911report:194$ find -type f```

```
./chapter-1.txt
./chapter-10.txt
./chapter-11.txt
./chapter-12.txt
./chapter-13.1.txt
./chapter-13.2.txt
./chapter-13.3.txt
./chapter-13.4.txt
./chapter-13.5.txt
./chapter-2.txt
./chapter-3.txt
./chapter-5.txt
./chapter-6.txt
./chapter-7.txt
./chapter-8.txt
./chapter-9.txt
./preface.txt
```

This a basic example of the command. find -type f specifies that we are looking specifically for a file. We are currently in 911report, so the command will return all files in that directory in alphabetical order. 

**Example 2**

```[cs15lfa22mv@ieng6-203]:~:197$ find -type f -iname "chapter-1.txt"```

```
./technical/911report/chapter-1.txt
```

-iname is a more specific form of -name that gives us our exact search. Here I was looking for the exact file chapter-1.txt. This is useful if you know the name of a file but want its exact path. 

**Example 3**

```[cs15lfa22mv@ieng6-203]:911report:202$ find -type f -name "*.txt" -exec grep 'flight to Boston' {} \;```

```
    When he checked in for his flight to Boston, Atta was selected by a computerized prescreening system known as CAPPS (Computer Assisted Passenger Prescreening System), created to identify passengers who should be subject to special security measures. Under security rules in place at the time, the only consequence of Atta's selection by CAPPS was that his checked bags were held off the plane until it was confirmed that he had boarded the aircraft. This did not hinder Atta's plans.
```

With this command we search through all files in 911report with the format .txt. -exec essentially means 'execute' and grep allows us to search for the String "flight to Boston". The command returns the line block containing that phrase. 


## find -exec

**Example 1**

```[cs15lfa22mv@ieng6-203]:~:204$ find -name "DraftRecom-PDF.txt" -exec rm -i {} \;```

```
rm: remove regular file './technical/government/Alcohol_Problems/DraftRecom-PDF.txt'? n
```

First we used -name to find the specific file. -exec allows you to execute commands on this file. rm will remove the file, but adding -i ensures that the system asks the user before actually doing so. Typing in Y or y will carry through with the removal (in this case I did not remove the file). 

**Example 2** 

```[cs15lfa22mv@ieng6-203]:911report:207$ find -iname "chapter-1.txt" -exec md5sum {} \;```

```
ab88505cef824e722ba5ab715eaca0c1  ./chapter-1.txt
```

This command calculates the md5sum on chapter-1.txt file in 911report. md5sum is the sum of 128-bit MD5 hashes, which is returned alongside the path of the inputted file. 

**Example 3**

```[cs15lfa22mv@ieng6-203]:911report:208$ find -type f -exec ls -s {} \; | sort -n | head -5```

```
12 ./preface.txt
52 ./chapter-10.txt
76 ./chapter-11.txt
84 ./chapter-2.txt
88 ./chapter-8.txt
```

This command returns the top 5 smallest files in the directory 911report. head -5 indicates that we are looking for the top 5 while sort -n indicates that we are looking for the smallest files. preface-txt is the smallest of the five, meaning it has the lowest number of bytes. 


## find -size

**Example 1**

```[cs15lfa22mv@ieng6-203]:911report:219$ find -size -200M```

```
.
./chapter-1.txt
./chapter-10.txt
./chapter-11.txt
./chapter-12.txt
./chapter-13.1.txt
./chapter-13.2.txt
./chapter-13.3.txt
./chapter-13.4.txt
./chapter-13.5.txt
./chapter-2.txt
./chapter-3.txt
./chapter-5.txt
./chapter-6.txt
./chapter-7.txt
./chapter-8.txt
./chapter-9.txt
./preface.txt
```

I used this command to find files in 911 report smaller than 200M, which turns out to be all the files in 911report.

**Example 2**

```[cs15lfa22mv@ieng6-203]:911report:228$ find -type f -name "*.txt" -size +105k -exec rm -i {} \;```

```
rm: remove regular file './chapter-1.txt'? n
rm: remove regular file './chapter-12.txt'? n
rm: remove regular file './chapter-13.2.txt'? n
rm: remove regular file './chapter-13.3.txt'? n
rm: remove regular file './chapter-13.4.txt'? n
rm: remove regular file './chapter-13.5.txt'? n
rm: remove regular file './chapter-3.txt'? n
rm: remove regular file './chapter-6.txt'? n
rm: remove regular file './chapter-7.txt'? n
rm: remove regular file './chapter-9.txt'? n
```

This example is similar to example one in find -exec, but this time we are deleting files over 105k. For each one, it asks me to confirm (all of which I said no to). 

**Example 3**

```[cs15lfa22mv@ieng6-203]:911report:231$ find -size +105k -size  -125k```

```
./chapter-1.txt
./chapter-13.2.txt
```

Finally, this command returns all files in between 105 and 125k. 
    
