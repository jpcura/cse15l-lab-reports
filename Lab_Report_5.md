**LAB REPORT 5**
**_Julian Curatolo_**

* Student Post
  - Hi, I am trying to run `test.sh` to test the `ListExamples.java` file. When I do so I get this error. I think it may have something to do with how the two sorted arrays are added in my `merge` method.
  - <img width="356" alt="image" src="https://github.com/jpcura/cse15l-lab-reports/assets/146609257/b4ca77ae-3413-49b3-bc9c-68c2f7402484">

* TA Post
  - It looks like the cause of the error is near line 28 of `ListExamples.java`. Use `vim` to look at that line or open it in an editor.
    Check to see that the indexes you are adding with are within bound.

* Student Response
  - <img width="488" alt="image" src="https://github.com/jpcura/cse15l-lab-reports/assets/146609257/b1fea9db-fa1d-4bd0-b60a-2155703834aa">
  - This is line 28 of my `ListExamples.java` file. It looks like the error is coming when checking the condition of the if statement.
  - I see that the condition for the while loop uses an `||` logical operator.
  - This means that as long as one of the indexes in inbound the loop will continue to run.
  - This is what is causing the error and it should be changed to `&&` so that the loop only runs while both indexes are within bounds.
 

* Information about the set up:
file Structure (from lab7):


```
lab7
  ListExamples.java  
  ListExamplesTests.java  
  test.sh  
```


ListExamples.java contents:  


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
      index2 += 1;
    }
    return result;
  }


}
```



ListExamplesTests.java contents:  


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
    while(index1 < list1.size() || index2 < list2.size()) {
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
      index2 += 1;
    }
    return result;
  }


}
[jcuratolo@ieng6-201]:lab7:251$ cat ListExamplesTests.java
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

test.sh contents: 


```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
```


Command line to trigger bug:  


`bash test.sh`  


Description of what to edit to fix the bug:   


- Change line 27 in  `ListExamples.java`
- Update the `while` loop condition from `index1 < list1.size() || index2 < list2.size()` to `index1 < list1.size() && index2 < list2.size()`



**PART 2**  
I learned how to use the `jdb` bugger and find it useful that I can stop while my code is running to check variables. I also did not know how to use github before. Now I know how to used it to commit changes to a file form the command line as well as work collaborativley with a group on the same file. 

