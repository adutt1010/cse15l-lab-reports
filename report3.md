## Part 1: Bugs
### A failure inducing output
```
@Test 
public void testReverseInPlace() {
    int[] input1 = {1, 2, 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3, 2 , 1}, input1);
}
```
### An input that doesn't induce a failure
```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
```

### Symptom:
#### Input: {1, 2, 3}
![image](https://github.com/adutt1010/cse15l-lab-reports/assets/146874656/33d66bbf-6007-47cb-9373-cb714827f825)

#### Input: { 3 }
![image](https://github.com/adutt1010/cse15l-lab-reports/assets/146874656/657c8e95-0066-4511-af67-8f174789dc35)

### Bug
#### Before
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

#### After
```
  static void reverseInPlace(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0;i < arr.length;i++) {
      newArray[i] = arr[i];
    }
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
  }
```
In the previous code, the values for the first half of the array were replaced, but in the second half, the values were swapped incorrectly, because the values we were supposed to replace
the second half with were gone because they were removed when the first half of the array was replaced. In the updated code, we created a second array that was used to store the values of 
the old array, and we then went through each value of our original array and substituted it with the values of the new array from the last index. This way the values that are supposed to be
 supposed to be entered into the array.

## Part 2: Researching Commands
### ```grep```
> **Source: ChatGPT**
#### `-i` command
**Example 1:**
```
$ grep -i "study"  biomed/1468-6708-3-1.txt
        events [ 10 ] . In this paper we study whether BMI at
          Study design: The Cardiovascular Health
          Study
          The Cardiovascular Health Study (CHS) is a
          population-based longitudinal study of 5,888 adults aged
        from EVGFP) in the first seven years of the study, adjusted
        CHS Cardiovascular Health Study
```
- The `-i` command is used to perfrom a case-insensitive search for patterns in the file thats given. This is useful for perfoming searches for patterns efficiently as case does not matter.
- In this case I entered the word `"study"` as input and you can see that it gave an output of instances where study appears in both upper-case and lower-case.

**Example 2:**
```
$ grep -i "winter"  biomed/1468-6708-3-1.txt biomed/1468-6708-3-1.txt biomed/1468-6708-3-1.txt
```
- It can also be used for checking patterns through multiple files.
- In this case I used to it to search for places where the word `"winter"` shows up and since there are no instances of winter it does not give us an output.

#### `-c` command
**Example 1:**
```
$ grep -c "study"  biomed/1468-6708-3-1.txt
3
```
- The `-c` command is used to count the number of lines in which the patter occurs. This is useful when dealing with large files and you want to determine the frequency of certain wrods in  a file.
- In this case I entered `"study"`, and it shows me that it occurs on 3 lines.

**Example 2:**
```
$ grep -c -e "study" -e "bio"  biomed/1468-6708-3-1.txt
3
```
- It can also be used to check for multiple patterns using `-e`. It checks the file and sees lines that have any of the patterns. This is useful to optimize counting efficiency such that you dont have to repeatedly search for singular patterns at a time.
- In this case it checks for both `"study"` and `"bio"`, and counts lines which have any of the two patterns.

#### `-n` command
**Example 1:**
```
$ grep -n "study"  biomed/1468-6708-3-1.txt
34:        events [ 10 ] . In this paper we study whether BMI at
50:          population-based longitudinal study of 5,888 adults aged
194:        from EVGFP) in the first seven years of the study, adjusted
```
- The `-n` command is used to display the line numbers of lines that correspont to a pattern and the parts of the lines that correspond to the patters. It is useful when you are searching for specific keywords in the text and the information around them, and don't have the time to search for them manually.
- In this case I enter `"study"` as the input and it returned the lines containing the pattern and the portion of the line that corresponds to `"study"`.

**Example 2:**
```
$ grep -n -c "report" 911report/chapter-1.txt
56

```
- Here we combine the `-n` and `-c` command line arguments to get the number of times a patthern appears in the file, in this case the patter I wanted to check was `"report"`. This can be useful when you want to find the frequency of certain words in the file for statistical purposes.

#### `-r` command
**Example 1:**
```
$ grep -r "torch"
biomed/ar328.txt:        cryptorchidism.
government/Media/Legal_Aid_attorney.txt:welding torch at sculpting steel.
plos/journal.pbio.0020047.txt:        Creative human beings are the torch-bearers of civilization. How does their creativity
```
- The `-r` command is used to conduct a recursive search for a pattern through all files in a directory. It diplays the instances of it's occurence in the files. This can be useful when there are a large number of files, and you need to find a pattern in the files, and the context of it's occurence.
- In this case I entered the pattern `"torch"` and it displayed it's occurences in the directory.

**Example 2:**
```
$ grep -r --include="*.txt" "torch" 
biomed/ar328.txt:        cryptorchidism.
government/Media/Legal_Aid_attorney.txt:welding torch at sculpting steel.
plos/journal.pbio.0020047.txt:        Creative human beings are the torch-bearers of civilization. How does their creativity
```
- Here I used the `-r` command and the `--include` command to only search certain files, in this case that was `.txt` files. This can be useful when a directory contains multiple files of different types, and you only want to limit your search to a certain type of files.



## Acknowledgement of ChatGPT usage
I used ChatGPT for a portion of this lab report. The area I used ChatGPT for was Part 2 of this lab report. My prompts for ChatGPT, and the output it gave me was:-
- **Prompt:** find command-line options
- **Output:**
```
The grep command in Unix and Unix-like operating systems is used for searching and manipulating text. It's a powerful tool for pattern matching within files or input streams. grep has a variety of command-line options to customize its behavior. Here are some commonly used grep command-line options:

-i (or --ignore-case): Ignore case distinctions in both the search pattern and input files.

-v (or --invert-match): Invert the sense of matching, showing lines that do not match the given pattern.

-r (or --recursive): Recursively search directories and their subdirectories for matching files. This is often used for searching through directory trees.

-l (or --files-with-matches): Print only the names of files that contain matching lines, rather than the actual matching lines.

-n (or --line-number): Prefix each line with the line number within its input file.

-c (or --count): Display only the count of matching lines in each file, rather than the lines themselves.

-w (or --word-regexp): Match whole words only. For example, if you search for "word," it won't match "subword."

-A (or --after-context): Show N lines of trailing context after a match. For example, -A 3 will display the line containing the match and the three lines that follow it.

-B (or --before-context): Show N lines of leading context before a match. For example, -B 2 will display the line containing the match and the two lines that precede it.

-E (or --extended-regexp): Interpret the pattern as an extended regular expression, which allows for more advanced pattern matching.

-F (or --fixed-strings): Treat the pattern as a fixed string, not a regular expression. Useful when you want to search for a specific string without special characters being interpreted.

-m (or --max-count): Stop after finding N matching lines. This is useful when you want to limit the number of matches.

-q (or --quiet): Quiet mode. It suppresses output and is typically used in scripts to check for the existence of a pattern without displaying matching lines.

These are some of the most commonly used options with the grep command. You can combine multiple options to customize the search behavior to suit your needs. For more detailed information and additional options, you can refer to the grep manual page by running man grep in your terminal.
```
- After using it to find multiple command-line options for grep, I chose 4 of the command-line options and used those in my Lab-report.


I also used ChatGPT to find an additional command-line option for `-r`,as I had reached a little bit of a road block.
- **Prompt:** 
