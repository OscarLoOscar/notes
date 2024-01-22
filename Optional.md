---
title: Optional<T>
source: https://cloud.tencent.com/developer/article/2360289?areaId=106001
---

[Optional](https://hackmd.io/@oscarlo/optional)

# Optional\<T\>

使用 Optional 封裝可能為 null 的類別，提高代碼的可讀性和健壯性（在執行過程中處理錯誤，以及在遇到輸入、運算等異常時仍能維持正常運行的能力）。避免空指針異常（NullPointerException）。

優點：
- 可以避免空指針異常，提高代碼的健壯性和可讀性。
- 可以減少顯式的空值檢查和 null 的使用，使代碼更簡潔和優雅。
- 可以利用函數式編程的特性，實現更靈活和高效的邏輯處理。
- 可以提高代碼的可測性，方便進行單元測試和集成測試。

## Optional 創建

- of(T value)：創建非空對象。
  - ```java
    // 創建非空的 Optional 對象
    Optional<String> nonNullOptional = Optional.of("Hello");
    ```
- empty()：創建空對象。(指住地址object，object裝住null。本身不是null)
  - ```java
    // 創建一個空的 Optional 對象
    Optional<String> emptyOptional = Optional.empty();
    ```
- ofNullable(T value)：創建可能為空的對象。
  - ```java
    // 創建一個可能為空的 Optional 對象
    Optional<String> nullableOptional = Optional.ofNullable("Hello");
    ```

## Optional 方法

- isEmpty()：判斷是否為空，返回 boolean。
- isPresent()：判斷對象是否有值。
- get()：如果對象不為空，返回值；否則拋出 NoSuchElementException。
  - ```java
    // 使用 isPresent 和 get 方法
    Optional<String> name = Optional.ofNullable("Tom");
    if (name.isPresent()) {
        System.out.println("Hello, " + name.get());
    } else {
        System.out.println("Name is not available");
    }
    // 輸出：Hello Tom
    ```
- ifPresent(Consumer<? super T> action)：如果對象不為空，執行指定的動作；否則什麼都不做。
  - ```java
    // 使用 ifPresent(Consumer<? super T> action)
    Optional<String> name = Optional.ofNullable("Tom");
    name.ifPresent(s -> {
        System.out.println("Hello, " + name.get());
    });
    // 輸出：Hello Tom
    ```
- orElse(T other)：如果對象為空，返回指定的其他值。
  - ```java
    // 使用 orElse(T other)
    Optional<String> name = Optional.ofNullable(null);
    String greeting = "Hello, " + name.orElse("Guest");
    System.out.println(greeting);
    // 輸出：Hello Guest
    ```
- orElseGet(Supplier<? extends T> supplier)：如果對象為空，返回由指定供應商生成的值。
  - ```java
    // 使用 orElseGet(Supplier<? extends T> supplier)
    Optional<String> name = Optional.ofNullable(null);
    String greeting = "Hello, " + name.orElseGet(() -> "Guest");
    System.out.println(greeting);
    // 輸出：Hello Guest
    ```
- orElseThrow(Supplier<? extends X> exceptionSupplier)：如果對象為空，則拋出由指定供應商生成的異常。
  - ```java
    // 使用 orElseThrow(Supplier<? extends X> exceptionSupplier)
    Optional<String> name = Optional.ofNullable(null);
    String greeting = "Hello, " + name.orElseThrow(() -> new NullPointerException("null"));
    // 拋出 java.lang.NullPointerException: null 異常
    ```
- map(Function<? super T,? extends U> mapper)：如果對象不為空，對其進行映射操作。
  - ```java
    // 使用 map(Function<? super T,? extends U> mapper)
    Optional<String> name = Optional.ofNullable("Tom");
    String greeting = "Hello, " + name.map(s -> s.toUpperCase()).get();
    System.out.println(greeting);
    // 輸出：Hello TOM
    ```
- flatMap(Function<? super T,? extends Optional<? extends U>> mapper)：如果對象不為空，對其進行 flatMap 操作。
  - ```java
    // 使用 flatMap(Function<? super T,? extends Optional<? extends U>> mapper)
    Optional<String> name = Optional.ofNullable("Tom");
    String greeting = name.flatMap(s -> Optional.of("Hello " + s)).get();
    System.out.println(greeting);
    // 輸出：Hello Tom
    ```
- filter(Predicate<? super T> predicate)：根據指定條件過濾對象。
  - ```java
    // filter(Predicate<? super T> predicate)
    Optional<String> name = Optional.ofNullable("Tom");
    String greeting = "Hello " + name.filter(s -> !s.isEmpty()).get();
    System.out.println(greeting);
    // 輸出：Hello Tom
    ```

- Java 9 新增
  - isPresentOrElse(Consumer<? super T> action, Runnable emptyAction)：如果對象不為空，執行指定的動作；否則執行指定的空動作。
    - ```java
      // Java 9 新增 isPresentOrElse(Consumer<? super T> action, Runnable emptyAction)
      Optional<Integer> optional = Optional.of(1);
      optional.ifPresentOrElse(
          x -> System.out.println("Value: " + x),
          () -> System.out.println("Not Present.")
      );

      optional = Optional.empty();
      optional.ifPresentOrElse(
          x -> System.out.println("Value: " + x),
          () -> System.out.println("Not Present.")
      );
      // 輸出：Value: 1
      // 輸出：Not Present.
      ```
  - or(Supplier<? extends Optional<? extends T>> supplier)：如果對象為空，返回由指定供應商生成的 Optional 對象。
    - ```java
      // Java 9 新增 or(Supplier<? extends Optional<? extends T>> supplier)
      Optional<String> optional = Optional.of("Hello ");
      Supplier<Optional<String>> supplier = () -> Optional.of("Tom");
      optional = optional.or(supplier);
      optional.ifPresent(x -> System.out.println(x));

      optional = Optional.empty();
      optional = optional.or(supplier);
      optional.ifPresent(x -> System.out.println(x));
      // 輸出：Hello 
      // 輸出：Tom
      ```
  - stream()：將 Optional 對象轉換為 Stream。
    - ```java
      // stream()
      List<Optional<String>> list = Arrays.asList(
          Optional.empty(),
          Optional.of("A"),
          Optional.empty(),
          Optional.of("B")
      );

      // 使用 stream() 方法過濾列表，只保留非空的值
      List<String> filteredList = list.stream()
              .flatMap(Optional::stream)
              .collect(Collectors.toList());

      System.out.println(filteredList);
      // 輸出 [A, B]
      ```




- 