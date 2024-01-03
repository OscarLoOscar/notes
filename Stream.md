

# Java Stream 

## 2. 基本操作

### 2.1 forEach
```java
List<String> myList = Arrays.asList("Apple", "Banana", "Orange");
myList.stream().forEach(System.out::println);
//output
Apple
Banana
Orange
```
### 2.2 filter
```java

List<String> filteredList = myList.stream()//
                                .filter(s -> s.startsWith("A"))//
                                .collect(Collectors.toList());
//output
[Apple]
```
### 2.3 map
```java
List<String> upperCaseList = myList.stream()//
                                   .map(String::toUpperCase)//
                                   .collect(Collectors.toList());
//output
[APPLE, BANANA, ORANGE]
```
### 2.4 flatMap
```java
 
List<List<String>> nestedList = Arrays.asList(//
    Arrays.asList("One", "Two"),//
    Arrays.asList("Three", "Four"),//
    Arrays.asList("Five", "Six")//
);

List<String> flatList = nestedList.stream()//
                                 .flatMap(Collection::stream)//
                                 .collect(Collectors.toList());
//output
[One, Two, Three, Four, Five, Six]
```
### 2.5 distinct
```java
 
List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 4, 4, 5);
List<Integer> distinctNumbers = numbers.stream()//
                                       .distinct()//
                                       .collect(Collectors.toList());
//output
[1, 2, 3, 4, 5]
```
### 2.6 sorted
```java
List<Integer> sortedNumbers = numbers.stream()//
                                     .sorted()//
                                     .collect(Collectors.toList());
//output
[1, 2, 2, 3, 4, 4, 5]
```
## 3. map() 和 flatMap() 比較
### 3.1 map()
使用 map() 時，每個輸入元素都會被映射成一個輸出元素。
結果是一對一的映射。
```java
List<Integer> squaredNumbers = numbers.stream()//
                                     .map(n -> n * n)//
                                     .collect(Collectors.toList());
//output
[1, 4, 4, 9, 16, 16, 25]

```
### 3.2 flatMap()
使用 flatMap() 時，每個輸入元素可以映射為零個、一個或多個輸出元素。
結果是一對零、一或多的映射。
```java
List<List<Integer>> nestedNumbers = Arrays.asList(//
  Arrays.asList(1,2,3),//
  Arrays.asList(4,5),//
  Arrays.asList(6,7,8)
);

List<Integer> flatNumbers  = nestedNumbers.stream()//
.flatMap(Collection::stream)//
.collect(Collectors.toList());
//output
[1, 2, 3, 4, 5, 6, 7, 8]
```