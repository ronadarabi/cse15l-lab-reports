# Lab Report 3


## Part 1


## Part 2

**Bug 1: reverseInPlace() method**

The reverseInPlace() method is supposed to change the input array to be in reversed order. This is part of the ArrayExamples.java file.

**Failure inducing input:** The test below shows an input of {1,2,3,4} with the expected outcome to be {4,3,2,1}. 
````
@Test 
  public void test1234() {
    int[] sequence = {1,2,3,4}; 
    int[] expected = {4,3,2,1}; 
    ArrayExamples.reverseInPlace(sequence);
    assertArrayEquals(expected, sequence); 
  }
````

**Symptom:** The output was 'arrays first differed at element [2]; expected:<2> but was:<3>. 

**Bug:** After looking at the code for a bit, it became evident that the method only replaces the first half of the array. So for our input of {1,2,3,4} we get {4,3,3,4}. To fix this, I made the for loop only cycle through half of the array, updating both halves each iteration. So in this case, '1' (index 0) gets stored into a temporary variable. '1' (index 0) is then updated to '4' (index 3), and '4' (index 3) is updated to '1' (temp) by using our temporary variable. So now the array is {4,2,3,1}. The same happens for the other two indices to get {4,3,2,1}. 

Here is the revised code: 
````
static void reverseInPlace(int[] arr) {
    for (int i = 0; i < (arr.length)/2; i += 1) { 
      int temp = arr[i]; 
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp; 
    }
  }
````
  

**Connection:** The code begins by replacing the '1' (index 0) with 4 (index 3). It does not store '1' anywhere so this value essentially becomes lost. The same happens with the '2' at index 1 — it is replaced with a '3' (index 2) but is not stored anywhere. So our array is now {4,3,3,4}. We want to update the '3' (index 2) to be a '2' and the '4' (index 3) to be a '1' (but these values are not stored anywhere!). In an attempt to do so, the '3' (index 2) is updated with the other '3' (index 1) and the '4' (index 3) is updated with the other '4' (index 0). 

---

**Bug 2: filter() method**

The filter() method returns a new list that has all the elements of the input list for which the StringChecker returns true, and not the elements that return false, in the same order they appeared in the input list. This is part of the ListExamples.java file. 

**Failure-inducing input:** 


