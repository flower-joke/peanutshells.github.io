---
title: Java Exception Handling
Date: 2017-02-27
---

Exceptions can be caught using a combination of the try and catch keywords.
A try/catch block is placed around the code that might generate an exception. 
Syntax: 
```
try {
  //some code
} catch (Exception e) {
  //some code to handle errors
}
```
A catch statement involves declaring the type of exception you are trying to catch. If an exception occurs in the try block, the catch block that follows the try is checked. If the type of exception that occurred is listed in a catch block, the exception is passed to the catch block much as an argument is passed into a method parameter.
The Exception type can be used to catch all possible exceptions.

The example below demonstrates exception handling when trying to access an array index that does not exist: 
```
public class MyClass {
  public static void main(String[ ] args) {
    try {
      int a[ ] = new int[2];
      System.out.println(a[5]);
      } catch (Exception e) {
      System.out.println("An error occurred");
    }
  }
}
//Outputs "An error occurred" 
```
Without the try/catch block this code should crash the program, as a[5] does not exist.
Notice the (Exception e) statement in the catch block - it is used to catch all possible Exceptions.

## throw
The throw keyword allows you to manually generate exceptions from your methods. Some of the numerous available exception types include the `IndexOutOfBoundsException`, `IllegalArgumentException`, `ArithmeticException`, and so on. 
For example, we can throw an ArithmeticException in our method when the parameter is 0. 
```
int div(int a, int b) throws ArithmeticException {
if(b == 0) {
  throw new ArithmeticException("Division by Zero");
} else {
  return a / b;
}
} 
```
The throws statement in the method definition defines the type of Exception(s) the method can throw. 
Next, the throw keyword throws the corresponding exception, along with a custom message.
If we call the div method with the second parameter equal to 0, it will throw an ArithmeticException with the message "Division by Zero".
Multiple exceptions can be defined in the throws statement using a comma-separated list.

```
/* two sum non-zero based */
public class Solution {
    public int[] twoSum(int[] numbers, int target) {
        Map<Integer, Integer> tsMap = new HashMap<Integer, Integer>();
        for(int i = 0; i< numbers.length; i++){
            if(tsMap.containsKey(target - numbers[i])){ 
                return new int[] {tsMap.get(target-numbers[i])+1, i+1}; 
            }
            tsMap.put(numbers[i], i);
        }
        throw new IllegalArgumentException("no two sum solution");
    }
}
```
<a href = "https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html">HashMap(Java Platform SE8)</a>
```
public HashMap(int initialCapacity)
Constructs an empty HashMap with the specified initial capacity and the default load factor (0.75).
Parameters:
initialCapacity - the initial capacity.
Throws:
IllegalArgumentException - if the initial capacity is negative.
```

