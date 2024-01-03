## 7. Object-Oriented Programming
- 7.1 Classes and Objects
  - 7.1.1 Defining a Class
    - ```java
      // Class definition
      public class Car {
          // Class members (fields and methods) go here
      }
  - 7.1.2 Creating Objects
    - ```java
      // Creating an object of the Car class
      Car myCar = new Car();
- 7.2 Encapsulation
  - ```java
    // Example of encapsulation using private fields and public methods
    public class Person {
        private String name;
        private int age;
        
        // Getter method for name
        public String getName() {
            return name;
        }
        
        // Setter method for name
        public void setName(String newName) {
            name = newName;
        }
        
        // Getter method for age
        public int getAge() {
            return age;
        }
        
        // Setter method for age
        public void setAge(int newAge) {
            age = newAge;
        }
    }
- 7.3 Inheritance
  - ```java
    // Example of inheritance with a base class (Vehicle) and a derived class (Car)
    public class Vehicle {
        public void start() {
            System.out.println("Vehicle is starting...");
        }
        
        public void stop() {
            System.out.println("Vehicle is stopping...");
        }
    }
    
    public class Car extends Vehicle {
        public void drive() {
            System.out.println("Car is driving...");
        }
    }
- 7.4 Polymorphism
  - ```java
    // Example of polymorphism using method overriding
    public class Animal {
        public void makeSound() {
            System.out.println("Animal makes a sound");
        }
    }
    
    public class Dog extends Animal {
        @Override
        public void makeSound() {
            System.out.println("Dog barks");
        }
    }
    
    public class Cat extends Animal {
        @Override
        public void makeSound() {
            System.out.println("Cat meows");
        }
    }
- 7.5 Enumerations (Enums)
  - ```java
    // Example of using Enums
    public enum Day {
        SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY
    }
    
    // Using the Enum
    Day today = Day.MONDAY;
- 7.6 Abstraction
  - ```java
    // Example of abstraction using abstract classes and methods
    abstract class Shape {
        abstract void draw();
    }
    
    class Circle extends Shape {
        @Override
        void draw() {
            System.out.println("Drawing a circle");
        }
    }
    
    class Square extends Shape {
        @Override
        void draw() {
            System.out.println("Drawing a square");
        }
    }
    
    // Using abstraction
    Shape myCircle = new Circle();
    Shape mySquare = new Square();
    myCircle.draw(); // Output: Drawing a circle
    mySquare.draw(); // Output: Drawing a square
