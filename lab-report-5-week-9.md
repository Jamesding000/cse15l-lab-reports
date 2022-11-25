# Lab Report 5 - Week 8
## Code from `grade.sh` file
```
set -e

rm -rf student-submission

# Clone the repository of the student submission, and suppress any output
git clone $1 student-submission &>/dev/null

cd student-submission

# Check that the student code has the correct file submitted
if [ ! -e ListExamples.java ]
then
    echo "ListExamples.java is not found!"
    exit 0
fi

# copy my test into the student-submission directory
cd ..
cp TestListExamples.java student-submission/TestListExamples.java
cd student-submission

# turn off set -e and compile the file
set +e

javac -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar *.java 2> error.txt

# If the compilation exit with exitcode other than 0, then there's a compilation error.
if [ ! $? -eq 0 ]
then
    echo "Compile Error!"
    exit 1
fi

# run the program
java -cp .:../lib/hamcrest-core-1.3.jar:../lib/Junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > TestResults.txt

# If test results contains "OK", then all test passed. 
if grep "OK" TestResults.txt &>/dev/null
    then
        echo "All Tests Passed"
    else
    # Otherwise, print the number of failures, and the name of the failed tests to the console.
        grep "Tests run" TestResults.txt
        echo "Failed : "
        grep ") " TestResults.txt
fi

```


## Examples of running the `grade.sh` file
---
- Example 1 -  this submission has the same code as the starter code from lab 3. There's a bug in the `filter` method in `ListExamples.java`. Run `grade.sh` using the following commands:
```
bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-lab3
```

<img width="825" alt="截屏2022-11-24 下午3 36 57" src="https://user-images.githubusercontent.com/100378969/203874901-c1e3ef87-e25a-4c3f-bf70-b40278387161.png">


- Example 2 -  this submission has a syntax error of a missing semicolon so that  Run `grade.sh` using the following commands:
```
bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-compile-error
```


<img width="879" alt="截屏2022-11-24 下午3 37 24" src="https://user-images.githubusercontent.com/100378969/203874904-ce5d438f-902a-460f-be16-a0f97c420244.png">

- Example 3 -  this submission has a great implementation saved in a file with the wrong name. Run `grade.sh` using the following commands:
```
bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-filename
```

<img width="844" alt="截屏2022-11-24 下午3 37 54" src="https://user-images.githubusercontent.com/100378969/203874908-68d91f90-0de7-46b4-9e97-3444df8965aa.png">

---

## Trace the code in Example 3

`rm -rf student-submission`  -- remove student-submission directory from the current directory, it doesn't have stdout or stderr, and its exit code is 0 because this directory is found in the current working directory


`git clone $1 student-submission &>/dev/null` -- clone the repository into local machine, it has no stdout or stderr because it has been redirected to /dev/null directory, which will be later discarded. Exit code is 0.

`cd student-submission` -- No stdout nor stderr, and exit code is 0.

`if [ ! -e ListExamples.java ]` -- this if condition check if a file called "ListExample.java" is not found in the directory. In this case, the file is found, and the codes inside the then block are not executed. Exit code is 0.

`then` -- this line is not executed

`echo "ListExamples.java is not found!"` -- this line is not executed

`exit 0`  -- this line is not executed

`fi` -- indicates that the if block ends here. No stdout or stderr, and exit code is 0.

`cd ..` -- No stdout nor stderr, and exit code is 0.

`cp TestListExamples.java student-submission/TestListExamples.java` -- No stdout nor stderr, and exit code is 0.

`cd student-submission` -- No stdout nor stderr, and exit code is 0.

`set +e` -- No stdout nor stderr, and exit code is 0.

`javac -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar *.java 2> error.txt` -- compile all .java files in the directory, and redirect any stderr to the file called error.txt. In this case, because all files compile succesfully, there's no stdout or stderr and the exit code is 0.

`if [ ! $? -eq 0 ]` -- this if statement check if any of .java file doesn't compile successfully. In this case, this statement is false, because the exit code of the previous line is 0.

`then` -- No stdout nor stderr, and exit code is 0.

`echo "Compile Error!"` -- No stdout nor stderr, and exit code is 0.

`exit 1` -- No stdout nor stderr, and exit code is 0.

`fi` -- indicates that the if block ends here. No stdout or stderr, and exit code is 0.

`java -cp .:../lib/hamcrest-core-1.3.jar:../lib/Junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > TestResults.txt` -- Run TestListExample using the classpath of junit test, and redirect the stdout to a file called TestResults.txt. Thus, this line has no stdout nor stderr, and the exit code is 1 because one of the tests failed.

`if grep "OK" TestResults.txt &>/dev/null` -- check if all tests passed, so that the file should contain "OK". In this case, it is false because there's one failed test. There's no stdout or stderr because they has been redirected to /dev/null and discarded.

`then` -- this line is not executed

`echo "All Tests Passed"` -- this line is not executed
    
`else` -- No stdout nor stderr, and exit code is 0.

`grep "Tests run" TestResults.txt` -- If there're failed tests, I use grep to print the line that contains "Test run" to the console, which is the stdout. There's no stderr and the exit code is 0.

`echo "Failed : "` -- stdout is "Failed : ", no stderr and the exit code is 0.
        
`grep ") " TestResults.txt` -- stdout is the line in TestResults.txt that contains " )". There's no stderr, and the exit code is 0.

`fi` -- No stdout nor stderr, and exit code is 0.