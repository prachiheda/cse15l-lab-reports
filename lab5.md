# Lab 5

## Part 1 - Debugging Scenario 

1. Student post: I created my grade.sh file for week 9 lab, but I am having some issues with running JUnit on the student submissions. I tested my grade.sh file on https://github.com/ucsd-cse15l-f22/list-methods-corrected, which is a repo that SHOULD pass all tests. However, this is my output:
![Image](lab5ss1.png)

This is what is in the compilation_output.txt file:

```
TestListExamples.java:1: error: package org.junit does not exist
import static org.junit.Assert.*;
                       ^
TestListExamples.java:2: error: package org.junit does not exist
import org.junit.*;
^
TestListExamples.java:24: error: cannot find symbol
  @Test(timeout = 500)
   ^
  symbol:   class Test
  location: class TestListExamples
TestListExamples.java:33: error: cannot find symbol
  @Test 
   ^
  symbol:   class Test
  location: class TestListExamples
TestListExamples.java:49: error: cannot find symbol
    @Test 
     ^
  symbol:   class Test
  location: class TestListExamples
TestListExamples.java:30: error: cannot find symbol
    assertEquals(expected, merged);
    ^
  symbol:   method assertEquals(List<String>,List<String>)
  location: class TestListExamples
TestListExamples.java:46: error: cannot find symbol
    assertEquals(expectedOutput, actualOutput);
    ^
  symbol:   method assertEquals(List<String>,List<String>)
  location: class TestListExamples
TestListExamples.java:63: error: cannot find symbol
        assertEquals(expectedOutput, actualOutput);
        ^
  symbol:   method assertEquals(List<String>,List<String>)
  location: class TestListExamples
8 errors
```

It seems like there is an issue with accessing JUnit. But I am unsure where to start as there are no hints in the compilation_output.txt file as to what is wrong in my grade.sh file. For reference, here is my grade.sh code: 

```
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission
echo 'Finished cloning'

if [ -e student-submission/ListExamples.java ]; then
    echo 'Expected file found. Proceeding with compilation and testing.'
    # Move student code and grading tests to grading-area
    cp -r student-submission/*.java grading-area/
    cp -r TestListExamples.java grading-area/
    # Change to grading-area directory
    cd grading-area
    javac -cp $CPATH *.java > compilation_output.txt 2>&1

    # Check the compilation status
    if [ $? -eq 0 ]; then
        echo 'Compilation successful. Proceeding with testing.'
        # Run JUnit tests and redirect the output to test_output.txt
        java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > test_output.txt 2>&1

        # Check the test results using grep
         passed_tests=$(grep -o "OK ([0-9]\+ tests)" test_output.txt | grep -o "[0-9]\+")
         echo $passed_tests

        # Print the number of passed tests
        echo "Number of passed tests: $passed_tests"

        # Calculate the grade based on the number of passed tests
        if [ "$passed_tests" == "3" ]; then
            echo 'Grade: A'
        elif [ "$passed_tests" == "2" ]; then
            echo 'Grade: B'
        elif [ "$passed_tests" == "1" ]; then
            echo 'Grade: C'
        else
            echo 'Grade: F'
        fi

    else
        echo 'Error: Compilation failed. See compilation_output.txt for details.'
        exit 1  # Exit the script with an error code
    fi

else
    echo 'Error: Expected file not found in the student submission.'
    exit 1  # Exit the script with an error code
fi
```

2. TA response: Hi! Yes, looks like JUnit is not being accessed in your grade.sh file. Have you checked the directories where you compile tests versus where the JUnit class path is? (Hint, I mean the variable CPATH in your grade.sh file). You can check this out by using echo pwd at a few key points in your grade.sh file.

3. 

