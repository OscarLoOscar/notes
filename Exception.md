# Exception Handling
[exception](https://hackmd.io/@oscarlo/exception)

---

## 8. Exception Handling
- 8.1 What is an Exception?
  - An exception is an event that occurs during the execution of a program that disrupts the normal flow of instructions.
- 8.2 try-catch Blocks
  - ```java
    // Example of try-catch block to handle an exception
    try {
        // Code that may cause an exception
        int result = 10 / 0; // ArithmeticException
    } catch (ArithmeticException e) {
        // Handling the exception
        System.out.println("Error: " + e.getMessage());
    }
- 8.3 finally Block
  - ```java
    // Example of try-catch-finally block
    try {
        // Code that may cause an exception
        int result = 10 / 0; // ArithmeticException
    } catch (ArithmeticException e) {
        // Handling the exception
        System.out.println("Error: " + e.getMessage());
    } finally {
        // Code in the finally block always executes, with or without an exception
        System.out.println("Finally block executed");
    }
- 8.4 Throws Clause
  - ```java
    // Example of a method with a throws clause
    public void exampleMethod() throws MyCustomException {
        // Code that may throw a custom exception
        throw new MyCustomException("Exception thrown from exampleMethod");
    }
- 8.5 Custom Exceptions
  - ```java
    // Example of a custom exception class
    public class MyCustomException extends Exception {
        public MyCustomException(String message) {
            super(message);
        }
    }
    
    // Example of throwing and catching a custom exception
    try {
        // Code that may throw a custom exception
        throw new MyCustomException("This is a custom exception");
    } catch (MyCustomException e) {
        // Handling the custom exception
        System.out.println("Custom Exception: " + e.getMessage());
    }
