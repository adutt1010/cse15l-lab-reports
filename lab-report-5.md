# Lab report 5: Putting it all together

## Step 1: Edstem Post by Student
In `lab7` I ran the tests by running `test.sh`, but one of my tests failed. It was the second test `testMerge2()`. Here is a screenshot of the symptom. I have isolated the error to the 
second method in `ListExamples.java`, and I believe that it is in the last while loop but I am not sure which part it is in and am afraid of messing up the code, and being unable to 
change it. I thought that I would ask for some guidance and help with this.

![image](https://github.com/adutt1010/cse15l-lab-reports/assets/146874656/dc8e8d82-72c3-4a7b-8de1-1b9220ef9dbf)

## Step 2: Response
You are in the right direction, and were able to narrow down the error. In the second while loop, it adds the elements of `list1` onto the list `result`. The third while loop has similar
functionality. If you can find out the use of the third while loop you should be able to find the error in the code. 

Don't be afraid to remove parts of the code, you can always use `Command+z`(Mac user) or `Ctrl+Z`(Windows) to undo and `Command+y`(Mac user) or `Ctrl+y`(Windows user) to redo. 
If you run into an issue where you are unable to undo or redo you can come to 
office hours where we can help you acquire the original code and guide you in the right dircetion. Trial and error is a huge asset and can be used to solve most problems in 
programming.

## Step 3: Implementing TA's guidance
I found the error and fixed the bug by changing `index1` to `index2` in the third while loop in `ListExamples.java`.
![image](https://github.com/adutt1010/cse15l-lab-reports/assets/146874656/c74185eb-1a77-4eb3-86ed-43100dc7c4d8)


## Step 4: Information
- Directory Structure

lab7

lab7 -- ListExamples.java

lab7 -- ListExamplesTest.java

lab7 --  test.sh

lab7 -- lib

lab7 -- lib -- hamcrest-core-1.3.jar

lab7 -- lib -- junit-4.13.2.jar

- ListE
