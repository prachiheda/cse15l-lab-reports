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


