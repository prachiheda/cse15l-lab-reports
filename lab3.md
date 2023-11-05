# Lab 3 Report

## Part 1

For this section, I am working with the reverseInPlace method, in the ArrayExamples file. 

### Failure inducing input: 
```
@Test 
public void testReverseInPlace2() {
    int[] input1 = { 1,2,3,4,5 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 5,4,3,2,1 }, input1);
}
```
### Non-failure inducing input: 
```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
```
### Symptom: 
![Image](lab3ss1.png)

### Before and after fixed reverseInPlace method: 
Before: 
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
}
```
After:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i]; 
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length-i-1] = temp; 
    }
}
```
We need to have another variable temp, and only iterate halfway through the array, and swap values on either side. Otherwise, the method is overwriting the original elements of the array as it iterates through it. This leads to all elements in the array becoming the last element of the original array.




