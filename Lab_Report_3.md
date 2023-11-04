**Part 1 - Bugs**
* A failure-inducing input for the buggy program
  ```
   @Test
  public void testRevereInPlace2(){
  int[] input1 = {1, 2, 3, 4};
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{4, 3, 2, 1}, input1);
  }
  ```
* An input that doesn't induce a failure
  ```
  @Test
  public void testReverseInPlace3(){
  int[] input1 = {1};
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[] {1}, input1);
  }
  ```
  
* The symptom

  <img width="481" alt="image" src="https://github.com/jpcura/cse15l-lab-reports/assets/146609257/8814c314-ddec-4dd2-9048-bd0824c3f8fb">
  

* The bug

```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

changed to:

```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    int[] newarr = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newarr[i] = arr[arr.length - i - 1];
      
    }
    for (int i = 0; i < arr.length; i += 1){
      arr[i] = newarr[i];
    }
  }
```

Why the fix addresses the issue: The bug was that `reverseInPlace(int[] arr)` would replace the contents in the original array so that after iterating through half, the original contents of the second half would not get reversed and instead the new contents would get copied over. The fix is creating `newarr[int]` which first copies the contents of the original array in reverse order without overwriting `arr[int]`. The contents in `newarr[int]` can then be copied into `arr[int]`.



**Part 2 - Research Commands**
`grep`

