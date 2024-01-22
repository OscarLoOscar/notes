# java bookmark
```java
 @Override // documentation，唔可以亂放
  public String toString() { // 本身有toString method，但做手腳出第二D野
    return "[" + this.color + " " + super.name //
        + "" + super.height//
        + "" + super.weight//
        + "" + super.age + "]";
  }
  ```

  
```java
  @Override           //記//
  public boolean equals(Object o){
    if(this==o) //adress
    return true;
    if(!(o instanceof Policy)){
      return false;
      Policy policy = (policy o);
      return this.policyNo.getPolicyNo().equals(policy.getPolicyNo().getPolicyNo());
    }
  }
```
```java
//downcast記得instanceOf - runtime exception
public class UncheckException { //係簽名throws多次
  public static double divide(double a, double b) throws ArithmeticException {// unchecked,從來唔會throws runtime exception
    if (b == 0) {
      return -1;
    }
    return a / b;// pass 0 will game over
  }
//extend Exception原因： 想攞多次exception
//唔try catch就簽名throws

```
```java
  public Driver(String name) {
    if (name == null || "".equals(name)) { // name.equal()都得，但null會死，""係STRING，所以call到method
      this.name = "N/A";
    } else {
      this.name = name.trim(); // avoid to have space
    }
```
```java
     @Override
  public int compare(Member4 o1, Member4 o2) {
    int result = o1.getClass().getName().compareTo(o2.getName()); // -1,0,1
    if (result == 0) {
      result = o1.getJoinDate().compareTo(o2.getJoinDate());
    }
    return result;
  }
}
```
```java
 @Override           //記//
  public boolean equals(Object o){
    if(this==o) //adress
    return true;
    if(!(o instanceof Policy)){
      return false;
      Policy policy = (policy o);
      return this.policyNo.getPolicyNo().equals(policy.getPolicyNo().getPolicyNo());
    }
  }

```java
      // return new ArrayList<>(Arrays.asList("-1"));
    return staffs.stream() //
        .map(e -> e.getEmail()) //
        .collect(Collectors.toList());
```

```java
  @Override // 靚method
  public boolean equals(Object obj) {
    if (obj == this)
      return true;

    if (!(obj instanceof Triangle))
      return false;

    Triangle t = (Triangle) obj;// downcasting, no runtime error here,coz i already ensure by instanceof
    if (this.base == t.base
        && this.height == t.height
        && super.getArea() == t.getArea()) {
      return true;
    }
    return false;
  }
  ```
//
```java
    itemList.stream()
        .filter(s -> s.getPrice() < 13.0)
        .map(Item::toString)
        .forEach(System.out::println);//.stream()既print方式
            strings.forEach(s -> System.out.println(s));

        ```
//
```java
        class bookComparator implements Comparator<Book> {
    public int compare(Book o1, Book o2) {
        return Double.compare(o1.getPrice(), o2.getPrice());
    }
  }
    

    Animal (String name) {
this.name = name;
hashcounter++; //有可能出現duplicate
}
String getName () {
return this.name;
}
public static void addAnimal (Animal animal) {
hashmap.put (hashcounter, animal);
}
```
```java
  List<Car6> car = new ArrayList<>();
    car.add(new Car6(null, "Yellow"));
    car.add(new Car6(null, "Black"));
    car.add(new Car6(null, "Black"));
    Car6[] carArr =  Car6.stream()
        // .filter(e -> e != null)
        .toArray(e -> new Car6[e]);
        ```

Java Stream是Java 8中引入的一種新特性，可以讓開發人員以更簡潔的方式來處理集合中的元素。Java Stream提供了一種流式處理集合元素的方式，可以進行過濾、映射、排序、統計等操作，並且可以通過並行處理來提高程序的執行效率。

以下是一些Java Stream的常用方法和示例：

1. 過濾（Filter）：使用filter方法可以將符合條件的元素抽取出來，例如：

```
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> evenNumbers = numbers.stream()
                                    .filter(n -> n % 2 == 0)
                                    .collect(Collectors.toList());
```

上述示例中，使用filter方法過濾出所有偶數，最終得到一個只包含偶數的List。

2. 映射（Map）：使用map方法可以將一個集合中的元素映射成另一種形式，例如：

```
List<String> words = Arrays.asList("hello", "world");
List<Integer> wordLengths = words.stream()
                                  .map(String::length)
                                  .collect(Collectors.toList());
```

上述示例中，使用map方法將每個單詞轉換成它的長度，最終得到一個包含單詞長度的List。

3. 排序（Sort）：使用sorted方法可以將一個集合中的元素按照指定的方式進行排序，例如：

```
List<Integer> numbers = Arrays.asList(5, 3, 1, 4, 2);
List<Integer> sortedNumbers = numbers.stream()
                                      .sorted()
                                      .collect(Collectors.toList());
```

上述示例中，使用sorted方法將數字按照升序排序，最終得到一個升序排列的List。

4. 統計（Reduce）：使用reduce方法可以對一個集合中的元素進行統計操作，例如：

```
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
int sum = numbers.stream().reduce(0, Integer::sum);
```

上述示例中，使用reduce方法對所有數字進行求和操作，最終得到所有數字的總和。

5. 收集（Collect）：使用collect方法可以將Stream中的元素收集到一個集合中，例如：

```
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
Set<Integer> evenNumbers = numbers.stream()
                                    .filter(n -> n % 2 == 0)
                                    .collect(Collectors.toSet());
```

上述示例中，使用collect方法將所有偶數收集到一個Set中。

以上是Java Stream的一些常用方法和示例，希望對你有所幫助。如果你想深入了解Java Stream，可以參考官方文檔或相關書籍。

704 Binary Search
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length -1;
       while(left <= right){
            int mid = (left+right)/2;
           if(nums[mid] == target){
               return mid;
           }else if(nums[mid] > target){
                   right = mid - 1;
                  
           }else if(nums[mid] < target){
                   left = mid +1;
                  
                   } 
                          System.gc();
           }
        
              return -1;    
       }
       }
    
