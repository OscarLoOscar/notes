---
markmap:
  colorFreezeLevel: 2
---

# Java

##  Basic Syntax
### 1. HelloWorld

```js
public class HelloWorld {
public static void main(String[] args) {
System.out.println("Hello, World!");
}
}
```
### 2. Variable and Primitive type
  ####  2.1.1 int
```java
int integerVariable = 10;
```
#### 2.1.2 float/double
```java
float floatVariable = 10.5f;
double doubleVariable = 10.123;
```
#### 2.1.3 char
```java
char charVariable = 'A';
```
[ASCII Code](https://www.ascii-code.com)
#### 2.1.4 boolean
```java
boolean booleanVariableA = true;
boolean booleanVariableB = false;
```
### 3. Operators
#### 3.1.1 + , - , * , / , %
```java
int result = 5 + 3; // addition
int result2 = 7 - 2; // subtraction
int result3 = 4 * 6; // multiplication
int result4 = 8 / 2; // division
int result5 = 10 % 3; // modulus (remainder)
```
### 3.1.2 compare Operators
```java
boolean isEqual = (a == b); // equal to
boolean isNotEqual = (a != b); // not equal to
boolean isGreaterThan = (a > b); // greater than
boolean isLessThan = (a < b); // less than
boolean isGreaterOrEqual = (a >= b); // greater than or equal to
boolean isLessOrEqual = (a <= b); // less than or equal to
```
### 3.1.3 AND , OR , !
```java
boolean andResult = (condition1 && condition2); // logical AND
boolean orResult = (condition1 || condition2); // logical OR
boolean notResult = !condition; // logical NOT
```
#### 3.3.4 位元運算符 XOR (we skip)
## String Basics
### 4.1.1 Sring Creation
```java
String name = "Test";
```
### 4.1.2  Combine with other data types

### 4.1.3 String Methods
#### length()
#### equals()
#### charAt(int index) 

##  Conditions
### 1.1 Conditionals
#### 1.1.1 if
```java
if (condition) {
// code block to be executed if the condition i            s true
}
```
#### 1.1.2 switch
```java
switch (expression) {
case value1:
// code block for value1
break;
case value2:
// code block for value2
break;
// ... more cases
default:
// code block if none of the cases match
}
```
##  Loops
### 2.1 Loop
#### 2.1.1 for loop
```java
for (int i = 0; i < 5; i++) {
// code block to be executed in each iteration
}
```
```java
for(char s : s.toCharArray()){
// code block to be executed in each iteration
}
```
#### 2.1.2 while loop
```java
while (condition) {
// code block to be executed as long as the condition is true
}
```
#### 2.1.3 do-while loop
```java
do {
// code block to be executed at least once, and then as long as the condition is true
} while (condition);
```
### 2.2 Break , Contiune
#### 2.2.1 Break
```java
for(int i = 0 ; i <=100 ; i++){
if( i ==5 )
break;
System.out.println(i);
}
//Output
1
2
3
4  
```
#### 2.2.2 Contiune
```java
for(int i = 0 ; i <11 ; i++){
if(i%2 ==0)
contiune;
System.out.print(i);
}
//Output
1
3
5
7
9
```
