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
the old array, and we then went through each value of our original array and substituted it with the values of the new array from the last index.



