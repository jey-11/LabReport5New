# LabReport5New
**1)** The original post from a student with a screenshot showing a symptom and a description of a guess at the bug/some sense of what the failure-inducing input is. (Don’t actually make the post! Just write the content that would go in such a post)<br>

Dear TA,<br>
    I have been working on my merge method within ListExamples.java. The failure-inducing input would probably be the arrays I passed in, when I added the arrays I get an error stating that the heap is not large enough. <br>
    Best, <br>
    Student <br>
![Image](Lab5_2.png)<br>

**2)** A response from a TA asking a leading question or suggesting a command to try (To be clear, you are mimicking a TA here.)<br>

Hello Student,<br>
  Based on your problem and provided code it seems that there is a problem when you are adding to your new merged array. I would recommend going through the conditions used to add to the array, there is likely a problem there.<br>
   Best,<br>
   TA<br>
   
**3)** Another screenshot/terminal output showing what information the student got from trying that, and a clear description of what the bug is.<br>
there was a line of code in TestExamples.java that compared the values incorrectly and caused the error. <br>
![Image](Lab5_3.png)<br>
![Image](Lab5_1.png)<br>

**4)** At the end, all the information needed about the setup including:
- The file & directory structure needed: list-examples-grader which contatins grade.sh and an implementation of ListExamples.java
- The contents of each file before fixing the bug:
```
  class ListExamples {
      public static void main(String[] args){
        ArrayList<String> list1 = new ArrayList<>(Arrays.asList("a", "b", "c"));
        ArrayList<String> list2 = new ArrayList<>(Arrays.asList("c", "d", "e"));
        System.out.println(ListExamples.merge(list1,list2).toString());
      }
      static List<String> merge(List<String> list1, List<String> list2) {
        List<String> result = new ArrayList<>();
        int index1 = 0, index2 = 0;
        while(index1 < list1.size() && index2 < list2.size()) {
          if(list1.get(index1).compareTo(list2.get(index2)) > 0) {
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
          index1 += 1;
        }
        return result;
      }
  }
``` 
within grade.sh
```
  javac ListExamples.java
  java ListExamples
```

- The full command line (or lines) you ran to trigger the bug `javac ListExamples.java` `java ListExamples` was called within the bash script
- A description of what to edit to fix the bug: I had to change the comparison sign from > to < 
