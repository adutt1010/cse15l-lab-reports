# Lab Report - 5

## 1. The Post

### Title : Question regarding bug in Lab 7

### Description :
In the `lab7` folder, I tried running `test.sh` in order to run the tests. When I ran the tests, I ended up getting an error message stating that one of the tests had failed. The test that failed was `testMerge2()`. I have attached the screenshot of the symptom.
![image](images/symptomlr5.png)

I believe that the error is caused from the method `merge(List<String> list1, List<String> list2)`. I believe that there may be an infinite while loop but I don't know where and why it occurs.
Any help would be appreciated.

## 2. TA response
 
Good job, you have succesfully narrowed down the error to one of the while loops. I would suggest going to `ListExamples.java`, and analyzing the last `while` loop, you may find some errors there.

Hint: The third `while` performs operations using the second list. Compare this to the second while loop, which performs operations using the first list, and try to find the error based on 
how the second while loop is designed. Try using the second while loop as a road map.


## 3. The information received from TA

I went into `ListExamples.java`, and tried analyzing the various `while` loops. I saw the similarity between the second and third `while` loop, and tried changing `index1` in the third `while` loop to `index2`. The error was caused because the iterator being used for the second list was `index2`, however instead of incrementing `index2`, `index1` was being incremented. Here is the screenshot of the succesful test run. 

![image](images/successlr5.png)


## 4. Information required for understanding the setup

- Repository structure 

lab7

- lab7
  - ListExamples.java
  - ListExamplesTest.java
  - test.sh
  - lib
    - hamcrest-core-1.3.jar
    - junit-4.13.2.jar


- Contents of ListExamples.java before fixing the bug:

```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      // change index1 below to index2 to fix test
      index1 += 1;
    }
    return result;
  }


}
```

- Contents of ListExamplesTests.java

```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;
import java.util.ArrayList;


public class ListExamplesTests {
      @Test(timeout = 500)
      public void testMerge1() {
    		    List<String> l1 = new ArrayList<String>(Arrays.asList("x", "y"));
		        List<String> l2 = new ArrayList<String>(Arrays.asList("a", "b"));
          assertArrayEquals(new String[]{ "a", "b", "x", "y"}, ListExamples.merge(l1, l2).toArray());
      }
	
	      @Test(timeout = 500)
       public void testMerge2() {
		           List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
		           List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
		           assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l1, l2).toArray());
        }
		
}
```

- Contents of test.sh
```
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ListExamplesTests
```
- The command line I ran to trigger the bug was `bash test.sh`.This ran the commands in the `test.sh` file, which contained two commands
```
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ListExamplesTests
```

- To fix the bugs, you must edit the code in the last `while` loop in the file `ListExamples.java`. In the last `while` loop, at line 44, you should change `index1` to `index2`. If you run the tests now, you will see that all the tests pass.


## Reflection

In the second half of this quarter I learned how to use vim. I believe this is a huge asset and can be used for text file editiing. I believe that this is a huge component in CSE 30. I also became extremely comfortable with github in the second half learning how to fork repositories and push changes. This would be incredibly useful when working on projects comprising of teams of multiple people. We even learned how to debug using jdb. This enables us to isolate bugs by going through the program line by line. Even the autograder we ran helped in my understanding. I always wondered how TA's grade us in classes like CSE 11 and 12, and now I have a basic understanding of how it works. I wish to become a tutor in the CSE department and this will be extremely helpful if I become one.
