# Lab 5

## Part 1 - Debugging Scenario 

1. I created my grade.sh file for week 9 lab, but I am having some issues with running JUnit on the student submissions. I tested my grade.sh file on https://github.com/ucsd-cse15l-f22/list-methods-corrected, which is a repo that SHOULD pass all tests. However, this is my output:

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


