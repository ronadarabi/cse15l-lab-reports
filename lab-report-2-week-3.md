# Lab Report 3


## Part 1

Below is the code for the SearchEngine: 
````
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Search implements URLHandler {
    ArrayList<String> searching = new ArrayList<>();

    public String handleRequest(URI url) {
        String error = "Invalid input. Please try again.";
        
        // Display full list. If list is empty, tell user what to do
        if (url.getPath().equals("/")) {
            String all = ""; 
            if (searching.size() == 0) { 
                return String.format("Your list is empty! 
                \nTry adding with /add?s=<word to add>.
                \nTry searching with /search?s=<characters to search>");
            } else { 
                for (int i = 0; i < searching.size(); i++) { 
                    all += searching.get(i) + "\n"; 
                }
                return "Here is your current list: \n\n" + all; 
            }
        // User wants to add. Check there is 's', if not send error
        // If there is, add to ArrayList and tell user it has been added
        } else if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) { 
                searching.add(parameters[1]); 
                return parameters[1] + " added!";
            } 
            return error;
        // User wants to search. Check for 's', if no 's' send error
        // If there is an 's', loop through ArrayList
        // Find Strings that contain substring. If there are none, tell user.
        // Display all Strings in list format
        } else if (url.getPath().contains("/search")) { 
            String[] parameters = url.getQuery().split("=");
            String passed = "";
            if (parameters[0].equals("s")) { 
                for (int i = 0; i < searching.size(); i++) { 
                    if (searching.get(i).contains(parameters[1])) { 
                        passed += searching.get(i) + "\n"; 
                    }
                }
                if (passed.equals("")) { 
                    return "No strings found.";
                }
                return passed; 
            }
            return error; 
        // If user inputs anything else, return error
        } else { 
            return error;
        }
    } 
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Search());
    }
}

````

This is what shows as you open the host link. We are looking at the first if-statement, which checks for '/'. Since our list is empty, the site prompts the user to add and then search. Since this is not an add or search command (it is just the default), there are no arguments. This will not change until at least one word has been added.
![startingSC](https://user-images.githubusercontent.com/68180000/195934555-47a8d5cd-e6a0-4f73-87ca-ed74988772ac.jpg)



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

**Symptom:** The output was 'arrays first differed at element [2]; expected:<2> but was:<3>'. 

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
  

**Connection:** The original code begins by replacing the '1' (index 0) with '4' (index 3). It does not store '1' anywhere so this value essentially becomes lost. The same happens with the '2' at index 1 — it is replaced with a '3' (index 2) but is not stored anywhere. So our array is now {4,3,3,4}. We want to update the '3' (index 2) to be a '2' and the '4' (index 3) to be a '1' (but these values are not stored anywhere!). In an attempt to do so, the '3' (index 2) is updated with the other '3' (index 1) and the '4' (index 3) is updated with the other '4' (index 0), so our "updated" array is {4,3,3,4}.

---

**Bug 2: filter() method**

The filter() method returns a new list that has all the elements of the input list for which the StringChecker returns true, and not the elements that return false, in the same order they appeared in the input list. This is part of the ListExamples.java file. Before testing filter(), I created a class that implements the StringChecker interface. It returns true if the String's length is over 5: 
````
class LengthOver5 implements StringChecker { 
    public boolean checkString(String s) { 
        return s.length() > 5; 
    }
}
````

**Failure-inducing input:** The test below shows an input of ["hello", "candy", "structure", "herald", "trees"]. We expect ["structure", "herald"] as our output. 

````
@Test
    public void over5() { 
        List<String> input = Arrays.asList("hello", "candy", "structure", "herald", "trees"); 
        List<String> expected = Arrays.asList("structure", "herald"); 
        assertArrayEquals(expected.toArray(), ListExamples.filter(input, new LengthOver5()).toArray());
        
    }
````

**Symptom:** The test failed because the method returned a list with "herald" at index 0 when it should be "structure". This means that the method is not returning a list with kept elements in the order they appeared in the input. 

**Bug:** At the line where the code adds each kept element to the new list, it is actually adding each new element to the front of the list. 

Here is the revised code: 

````
static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }
````

**Connection:** Since the original code was adding elements using .add(index, element), with the index set to 0, it kept adding elements to the front of the list. This means that "structure", which shows up in the input first, is added to the front of the list (at this point the list is empty so it is just ["structure"]). Eventually StringChecker checks "herald" and adds it to the new list ('result') like so: result.add(0, "herald"). This pushes "herald" to the front of the list and moves "structure" one index over so the list is ["herald", "structure"], which is why the test failed. The fixed code above adds each new element to the end of the list, and since the for-loop iterates from the beginning of the input list to end, the method will return the list in the correct order. 
