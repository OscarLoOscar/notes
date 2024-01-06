[```markmap
## 1. Primitive Conversion
- 1.1 Upcasting
  - 1.1 Upcasting(Implicit Conversion / Promotion)![](https://miro.medium.com/v2/resize:fit:733/1*GA514JG3qrheTzf4d8DpXA.png)
- 1.2 Downcasting

## 2. String Method
- 2.1 isBlank()
- 2.2 isEmpty()
- 2.3 substring
  - 2.3.1 substring(int startIndex)
  - 2.3.2 substring(int startIndex, int endIndex)
- 2.4 toLowerCase()
- 2.5 toUpperCase()
- 2.6 replace(char oldChar, char newChar)
- 2.7 replace(CharSequence target, CharSequence replacement)
- 2.8 contains(CharSequence sequence)
- 2.9 endsWith(String suffix)
- 2.10 startsWith(String prefix)
- 2.11 trim()
- 2.12 equals()
- 2.12 equalsIgnoreCase()
- 2.13 indexOf(char ch)
- 2.14 indexOf(String str)
- 2.15 lastIndexOf(char ch)
- 2.16 lastIndexOf(String str)
- 2.17 concat(String str)
- 1.18 compareTo(String str)

## 3. Wrapper Classes
- 3.1 
  - 3.1.1 Wrapper Class

  - 3.2 AutoBoxing, UnBoxing
    - ```java
      // AutoBoxing
      Integer autoBoxed = 100; // primitive to Wrapper
      // UnBoxing
      int autoUnboxed = autoBoxed; // Wrapper to primitive

  - 3.2.1 Comparisons 
    - use equals() instead of == 

## 4. Array and Collection
- 4.1 Array
  - 4.1.1 1D Array
    - ```java
      // Declaration and initialization of a one-dimensional array
      int[] intArray = new int[5]; // An array of integers with a length of 5

      // Accessing and modifying array elements
      intArray[0] = 10;
      intArray[1] = 20;
      intArray[2] = 30;
      intArray[3] = 40;
      intArray[4] = 50;
  - 4.1.2 2D Array
    - ```java
      // Declaration and initialization of a two-dimensional array
      int[][] twoDArray = new int[3][3]; // A 3x3 array of integers 
      // Accessing and modifying two-dimensional array elements
      twoDArray[0][0] = 1;
      twoDArray[0][1] = 2;
      twoDArray[0][2] = 3;
      // ... similar for other rows and columns

- 4.2 Collection
  - 4.2.1 List 
    - 4.2.1.1 ArrayList
      - ```java
        // Declaration and initialization of an ArrayList
        ArrayList<String> stringList = new ArrayList<>();

        // Adding elements to the ArrayList
        stringList.add("Apple");
        stringList.add("Banana");
        stringList.add("Orange");

        // Accessing elements in the ArrayList
        String firstElement = stringList.get(0); // "Apple"

        // Iterating through the ArrayList
        for (String fruit : stringList) {
            System.out.println(fruit);
        }
    - 4.2.1.2 LinkedList
      - ```java
        // Declaration and initialization of a LinkedList
        LinkedList<Integer> integerList = new LinkedList<>();

        // Adding elements to the LinkedList
        integerList.add(10);
        integerList.add(20);
        integerList.add(30);

        // Accessing elements in the LinkedList
        int firstElement = integerList.getFirst(); // 10

        // Iterating through the LinkedList
        for (int number : integerList) {
            System.out.println(number);
        }
  - 4.2.2 Set
    - ```java
      - add()
      - remove()
      - contains()
      - size()
    - ```java
      // Declaration and initialization of a Set (HashSet)
      Set<String> stringSet = new HashSet<>();

      // Adding elements to the Set
      stringSet.add("Red");
      stringSet.add("Green");
      stringSet.add("Blue");
      stringSet.remove("Red");

      // Checking if an element exists in the Set
      boolean containsBlue = stringSet.contains("Blue"); // true 
      stringSet.size(); // 2
  - 4.2.3 Map
    - ```java
      - put(K key , V value)
      - get(Object key)
      - remove(Object key)
      - containsKey(Object key)
      - containsValue(Object Value)
      - isEmpty()
      - size()
      - keySet()
      - values()
      - entrySet()
    - ```java
      // Declaration and initialization of a Map (HashMap)
      Map<String, Integer> ageMap = new HashMap<>();

      // Adding key-value pairs to the Map
      ageMap.put("John", 25);
      ageMap.put("Jane", 30);
      ageMap.put("Bob", 22);
      ageMap.remove("Jane");

      // Accessing values using keys
      int johnsAge = ageMap.get("John"); // 25
      boolean keyExist = map.containsKey("John"); //true
      boolean valueExist = map.containsValue(3); //false

  - 4.2.4 Queue
    - 4.2.4.1 Deque
      - ```java
        - addFirst(E element)
        - addLast(E element)
        - removeFirst(E element)
        - removeLast(E element)
        - pollFirst()
        - pollLast()
        ...
      - ```java
        // Declaration and initialization of a Deque (ArrayDeque)
        Deque<String> deque = new ArrayDeque<>();

        // Adding elements to the front and back of the Deque
        deque.addFirst("First");
        deque.addLast("Last");

        // Accessing elements in the Deque
        String firstElement = deque.getFirst(); // "First"
        String lastElement = deque.getLast(); // "Last"

        // Iterating through the Deque
        for (String element : deque) {
            System.out.println(element);
        }
    - 4.2.4.2 PriorityQueue
      - Nature Order
        - ```java
          // Declaration and initialization of a PriorityQueue
          PriorityQueue<Integer> priorityQueue = new PriorityQueue<>();

          // Adding elements to the PriorityQueue
           priorityQueue.add(3);
           priorityQueue.add(1);
           priorityQueue.add(2);

          // Accessing and removing elements based on priority
          int highestPriorityElement = priorityQueue.poll(); // 1

          // Iterating through the PriorityQueue
           for (int element : priorityQueue) {
                System.out.println(element);
          }
      - Custom Priority
        - ```java
           PriorityQueue<Integer> priorityQueue2 = new PriorityQueue<>(b > a ? 1:-1);
           priorityQueue.add(30);
           priorityQueue.add(10);
           priorityQueue.add(22);
          
          for (int element : priorityQueue) {
                System.out.println(element); //30,22,10
          }


  - 4.2.5 Stack
    - ```java
      Stack<String> stack = new Stack<>();
      stack.push("apple");
      stack.push("banana");
      String top = stack.pop(); // banana , pop() => 彈走無回頭
      String top = stack.peek(); //apple , peek() => 觀察
      boolean exist = stack.contains("orange"); //false

## 5. Useful Java Class      
- Java Class
  - 5.1 StringBuilder
  - 5.2 Math
  - 5.3 BigDecimal
  - 5.4 LocalDate
  - 5.5 Random
  - 5.6 Scanner
