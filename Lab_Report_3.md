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
  
  ```
