# Lab Report 5

## `grade.sh` code

```
set -e

CPATH="student-submission/ListExamples.java"
JUNIT=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

rm -rf student-submission
git clone $1 student-submission

if [[ ! -f $CPATH ]]
then 
    echo "ListExamples.java not found. Please resubmit."
    exit 1
fi

set +e

mkdir student-submission/lib
cp lib/* student-submission/lib
cp *.java student-submission 


javac -cp $JUNITPATH ListExamples.java TestListExamples.java 2> output.txt
java -cp $JUNITPATH org.junit.runner.JUnitCore ListExamples TestListExamples 2> output.txt

if [[ $? -ne 0 ]] 
then 
    echo "Submission works."
    exit
else 
    echo "ListExamples.java failed to compile. Please resubmit."
    exit 
fi

```

## Reported grade 

Unfortunately I had issues getting this running in the URL server, so this is something I'm hoping to address in the resubmit (if there is one). Hopefully it is not an issue. 

![submissionPasses15L5](https://user-images.githubusercontent.com/68180000/204349247-711cebec-7e4a-48c1-9fb1-24634575b171.jpg)

This submission is supposed to be almost completely correct, and the feedback reflects as it shows "Submission works." 

![nestedinWrongDir15L5](https://user-images.githubusercontent.com/68180000/204349252-53e7d66d-b494-47b2-8e8b-b0959f78fa2e.jpg)

This submission was in the wrong directory, so the script was not able to locate it, as shown in the feedback. 

![fileNotFound15L5](https://user-images.githubusercontent.com/68180000/204349255-2efb3621-b838-46d7-9b9b-fd52e05aeb7c.jpg)

The name of this submission was incorrect and did not match the path, so the script was also not able to locate this. 

## Trace

I'll be looking at the last screenshit, the submission with incorrect file name. First I call ```bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-filename```. The script runs through everything and then hits the if-statement. This if-statement is checking to see if the file's name does not match what we expect. In this case it does not match, so the script follows through to the body, which is to tell the user that ```ListExamples.java not found. Please resubmit```. The script then exits with code 1.


(Since that example is fairly short, suppose that the file name was correct as in screenshot one. Then the script carries on until it gets to the next if-statement. This one is checking that the code is not 0, and since it is not, it spits out ```Submission works.```. If it was, then it would ask the user to resubmit since the code could not compile. 
