
![](https://hackmd.io/_uploads/SyEyldeRh.png)
QUERY|Desc
|-|-|
|基礎查詢|-|
SELECT |字段列表
FROM |TABLE名
|條件查詢|-|
WHERE|條件
|分組查詢|-|
GROUP BY|分組組名
HAVING|分組後條件
排序查詢|-
ORDER BY|排序
分頁查詢|-
LIMIT|分頁





改結構
:::success
ALTER TABLE 'name' ADD 'column name' type (length);
ALTER TABLE student ADD 'dept' VARCHAR(20);
:::

改名改type
:::success
ALTER TABLE 'name' CHANGE 'old name ' new name
 type (length)
 
 ALTER TABLE stucent CHANGE 'dept' department VARCHAR(30);
:::

DELETE Column
:::success
ALTER TABLE 'name' DROP 'colunm'

ALTER TABLE student DROP department;
:::

改TABLE名
:::success
RENAME TABLE 'old name' TO new name;

RENAME TABLE 'student' TO stu;
:::

數據插入
:::success
INSERT INTO 'table name' (colunm1,column 2,...) VALUES (1,2,...);
INSERT INTO 'table name' (value1,value2,..);

INSERT INTO student (sid,name,gender) VALUES (v1,v2,v3);
INSERT INTO student (v1,v2,v3);
:::

數據修改
:::success
UPDATE 'name' SET 'cloumn=value',...;
UPDATE 'name' SET 'cloumn=value',... WHERE condition ;

UPDATE student SET address = 'sth';
UPDATE student SET address = 'sth' WHERE id = 001;
UPDATE student SET address = 'sth', B = b , WHERE id = 002;
:::

數據刪除
:::success
1.DELETE FROM 'table' WHERE condition; -> delete內容

2.TRUNCATE TABLE 'name'； ->類似DROP TABLE , 先DROP再CREATE

3.TRUNCATE 'name';

DELETE FROM student WHERE id = 1004;
DELETE FROM student;
TRUNCATE TABLE student;
TRUNCATE student;
:::


### MySQL Constraint
* NOT NULL - 指示某列不能存儲 NULL 值。
* UNIQUE - 保證某列的每行必須有唯一的值。
* PRIMARY KEY - NOT NULL 和 UNIQUE 的結合。確保某列（或兩個列多個列的結合）有唯一標識，有助於更容易更快速地找到Table中的一個特定的記錄。
* FOREIGN KEY - 保證一個Table中的數據匹配另一個Table中的值的參照完整性。
* CHECK - 保證列中的值符合指定的條件。
* DEFAULT - 規定沒有給列賦值時的默認值。

#### PRIMARY KEY
:::success
CREATE TABLE emp1(
id INT PRIMARY KEY,
name VARCHAR(20)
);
:::
:::success
CREATE TABLE emp2(
id INT,
name VARCHAR(20),
CONSTRAINT pk_tableName PRIMARY KEY(id)
);
:::
:::success
3.
CREATE TABLE emp4(
id INT,
...
);
ALTER TABLE emp4 ADD PRIMARY KEY(id);
:::

:::success
ALTER TABLE emp1 DROP PRIMARY KEY;
:::

#### AUTO_INCREMENT
:::success
CREATE TABLE student(
id INT PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(20)
)AUTO_INCREMENT=100; -> define the start number yourself
:::

#### NOT NULL
:::success
CREATE TABLE USER(
ID INT NOT NULL
);
:::

#### DEFAULT
:::success
指定column默許值
:::

#### ZEROFILL
:::success
ZEROFILL默認為int(10)
小於(10)，係前面補上相應的零
自動加上UNSIGNED（無符號）屬性，有符號-128～＋127，無符號0~256
:::

#### UNIQUE
:::success
不能重覆，唯一
CREATE TABLE user(
id INT,
NAME VARCHAR(20),
PHONE_NUMBER VARCHAR(20)UNIQUE
);

ALTER TABLE user ADD CONSTRAINT UNIQUE_PN UNIQUE(PHONE_NUMBER);
:::

:::warning
SELECT * 
FROM 
WHERE
GROUP BY
HAVING
ORDER BY (DESC)
LIMIT
:::

![](https://hackmd.io/_uploads/r1kb-yQT2.png)


| Operation | Rows | Columns | Table |
|---|---|---|---|
| `DELETE` | Can specify a WHERE clause to delete specific rows. | Can specify which columns to delete. | Does not delete the table itself. |
| `TRUNCATE` | Cannot specify a WHERE clause. | Deletes all columns in the table. | Deletes the table itself. |
| `DROP` | Cannot specify a WHERE clause. | Does not delete any columns. | Deletes the table itself. |

Here are some additional details about each operation:

 **DELETE:** The `DELETE` operation can be used to delete ==specific== rows from a table. The ==WHERE clause is used== to specify which rows to delete. The `DELETE` operation does not delete the table itself.
**TRUNCATE:** The `TRUNCATE` operation deletes ==All== rows from a table. It cannot be used with a WHERE clause. The `TRUNCATE` operation also ==deletes the table's auto-increment value==, so the next row inserted into the table will have an auto-increment value of 1.
 **DROP:** The `DROP` operation ==deletes a table from the database==. It cannot be used with a WHERE clause. The `DROP` operation also deletes the table's data and structure.

In general, the `TRUNCATE` operation is faster than the `DELETE` operation, because it does not have to iterate over each row in the table to delete it. However, the `TRUNCATE` operation ==cannot be used with a WHERE== clause, so it cannot be used to delete specific rows.

The `DROP` operation is the most destructive operation, because it deletes the table itself, including its data and structure. The `DROP` operation should only be used when you are sure that you no longer need the table.

### INSERT INTO SELECT
:::success
INSERT INTO table2 (field1,field2,...) SELECT value1,value2...FROM table1
:::

### Function
count()
sum()
min()
ma()
avg()
group_concat()

### PARTITION BY
:::success
將data分拆成多組
:::

![](https://hackmd.io/_uploads/HkyN-9rT2.png)
![](https://hackmd.io/_uploads/rkPHb9ST2.png)


### <font color="#008000">插入數據</font>

INSERT INTO 語句用於向Table中插入新記錄。
#### 插入完整的行

:::success
INSERT INTO user
VALUES (10, 'root', 'root', 'xxxx@163.com');
:::
#### 插入行的一部分
:::success
INSERT INTO user(username, password, email)
VALUES ('admin', 'admin', 'xxxx@163.com');
:::
#### 插入查詢出來的數據
:::success
INSERT INTO user(username)
SELECT name
FROM account;
:::

### <font color="#008000">更新數據</font>

UPDATE 語句用於更新Table中的記錄。
:::success
UPDATE user
SET username='robot', password='robot'
WHERE username = 'root';
:::

### <font color="#008000">刪除數據</font>
DELETE 語句用於刪除Table中的記錄。
TRUNCATE TABLE 可以清空Table，也就是刪除所有行。

#### 刪除Table中的指定數據
:::success
DELETE FROM user
WHERE username = 'robot';
:::
#### 清空Table中的數據
:::success
TRUNCATE TABLE user;
:::

### <font color="#008000">查詢數據</font>
SELECT 語句用於從數據庫中查詢數據。
DISTINCT 用於返回唯一不同的值。它作用於所有列，也就是說所有列的值都相同才算相同。
LIMIT 限制返回的行數。可以有兩個參數，第一個參數為起始行，從 0 開始；第二個參數為返回的總行數。
ASC ：升序（默認）
DESC ：降序

#### 查詢單列
:::success
SELECT prod_name
FROM products;
:::
#### 查詢多列
:::success
SELECT prod_id, prod_name, prod_price
FROM products;
:::
#### 查詢所有列
:::success
SELECT *
FROM products;
:::
#### 查詢不同的值
:::success
SELECT DISTINCT
vend_id FROM products;
:::
#### 限制查詢結果
:::success
-- 返回前 5 行
SELECT * FROM mytable LIMIT 5;
SELECT * FROM mytable LIMIT 0, 5;
-- 返回第 3 ~ 5 行
SELECT * FROM mytable LIMIT 2, 3;
:::

### <font color="#008000">子查詢</font>
子查詢是嵌套在較大查詢中的 SQL 查詢。子查詢也稱為內部查詢或內部選擇，而包含子查詢的語句也稱為外部查詢或外部選擇。

* 子查詢可以嵌套在 SELECT，INSERT，UPDATE 或 DELETE 語句內或另一個子查詢中。

* 子查詢通常會在另一個 SELECT 語句的 WHERE 子句中添加。

* 您可以使用比較運算符，如 >，<，或 =。比較運算符也可以是多行運算符，如 IN，ANY 或 ALL。

* 子查詢必須被圓括號 () 括起來。

* 內部查詢首先在其父查詢之前執行，以便可以將內部查詢的結果傳遞給外部查詢。執行過程可以參考下圖：

![](https://hackmd.io/_uploads/SyKc6DOT2.jpg)


#### 子查詢的子查詢

```
SELECT cust_name, cust_contact
FROM customers
WHERE cust_id IN (SELECT cust_id
                  FROM orders
                  WHERE order_num IN (SELECT order_num
                                      FROM orderitems
                                      WHERE prod_id = 'RGAN01'));
```                                      
        
### <font color="#008000">WHERE</font>
* WHERE 子句用於過濾記錄，即縮小訪問數據的範圍。
* WHERE 後跟一個返回 true 或 false 的條件。
* WHERE 可以與 SELECT，UPDATE 和 DELETE 一起使用。
* 可以在 WHERE 子句中使用的操作符
 
|運算符|描述|
|-|-|
|=|	等於
|<>|不等於。註釋：在 SQL 的一些版本中，該操作符可被寫成 !=
|>|	大於
|<|	小於
|>=|大於等於
|<=|小於等於
|BETWEEN|	在某個範圍內
|LIKE|	搜索某種模式
|IN|	指定針對某個列的多個可能值

#### SELECT 語句中的 WHERE 子句
:::success
SELECT * FROM Customers
WHERE cust_name = 'Kids Place';
:::

#### UPDATE 語句中的 WHERE 子句
:::success
UPDATE Customers
SET cust_name = 'Jack Jones'
WHERE cust_name = 'Kids Place';
:::

#### DELETE 語句中的 WHERE 子句
:::success
DELETE FROM Customers
WHERE cust_name = 'Kids Place';
:::

### <font color="#008000">IN 和 BETWEEN</font>
* IN 操作符在 WHERE 子句中使用，作用是在指定的幾個特定值中任選一個值。
* BETWEEN 操作符在 WHERE 子句中使用，作用是選取介於某個範圍內的值。


#### IN 示例
:::success
SELECT *
FROM products
WHERE vend_id IN ('DLL01', 'BRS01');
:::

### BETWEEN 示例
:::success
SELECT *
FROM products
WHERE prod_price BETWEEN 3 AND 5;
:::

### <font color="#008000">AND、OR、NOT</font>
* AND、OR、NOT 是用於對過濾條件的邏輯處理指令。
* AND 優先級高於 OR，為了明確處理順序，可以使用 ()。
* AND 操作符表示左右條件都要滿足。
* OR 操作符表示左右條件滿足任意一個即可。
* NOT 操作符用於否定一個條件。

#### AND 示例
:::success
SELECT prod_id, prod_name, prod_price
FROM products
WHERE vend_id = 'DLL01' AND prod_price <= 4;
:::
#### OR 示例
:::success
SELECT prod_id, prod_name, prod_price
FROM products
WHERE vend_id = 'DLL01' OR vend_id = 'BRS01';
:::
#### NOT 示例
:::success
SELECT *
FROM products
WHERE prod_price NOT BETWEEN 3 AND 5;
:::

### <font color="#008000">LIKE</font>
* LIKE 操作符在 WHERE 子句中使用，作用是確定字符串是否匹配模式。
* 只有字段是文本值時才使用 LIKE。
* LIKE 支持兩個通配符匹配選項：% 和 _。
* 不要濫用通配符，通配符位於開頭處匹配會非常慢。
* % 表示任何字符出現任意次數。
* _ 表示任何字符出現一次。


#### % 示例
:::success
SELECT prod_id, prod_name, prod_price
FROM products
WHERE prod_name LIKE '%bean bag%';
:::
#### _ 示例
:::success
SELECT prod_id, prod_name, prod_price
FROM products
WHERE prod_name LIKE '__ inch teddy bear';
:::

### <font color="#008000">連接（JOIN）</font>
### JOIN乘數
* 如果一個 JOIN 至少有一個公共字段並且它們之間存在關係，則該 JOIN 可以在兩個或多個Table上工作。
* 連接用於連接多個Table，使用 JOIN 關鍵字，並且條件語句使用 ON 而不是 WHERE。
* JOIN 保持基表（結構和數據）不變。
* JOIN 有兩種連接類型：內連接和外連接。
* 內連接又稱等值連接，使用 INNER JOIN 關鍵字。在沒有條件語句的情況下返回笛卡爾積。
* 自連接可以看成內連接的一種，只是連接的Table是自身而已。
自然連接是把同名列通過 = 測試連接起來的，同名列可以有多個。
* 內連接 vs 自然連接
內連接提供連接的列，而自然連接自動連接所有同名列。
* 外連接返回一個Table中的所有行，並且僅返回來自次表中滿足連接條件的那些行，即兩個Table中的列是相等的。外連接分為左外連接、右外連接、全外連接（Mysql 不支持）。
左外連接就是保留左Table沒有關聯的行。
右外連接就是保留右Table沒有關聯的行。
* 連接 vs 子查詢
連接可以替換子查詢，並且比子查詢的效率一般會更快。

![](https://hackmd.io/_uploads/HkcOldupn.jpg)


### <font color="#008000">內連接（INNER JOIN）</font>
:::success
SELECT vend_name, prod_name, prod_price
FROM vendors INNER JOIN products
ON vendors.vend_id = products.vend_id;
:::
### <font color="#008000">自連接</font>
:::success
SELECT c1.cust_id, c1.cust_name, c1.cust_contact
FROM customers c1, customers c2
WHERE c1.cust_name = c2.cust_name
AND c2.cust_contact = 'Jim Jones';
:::
### <font color="#008000">自然連接（NATURAL JOIN）</font>
:::success
SELECT *
FROM Products
NATURAL JOIN Customers;
:::
### <font color="#008000">左連接（LEFT JOIN）</font>
:::success
SELECT customers.cust_id, orders.order_num
FROM customers LEFT JOIN orders
ON customers.cust_id = orders.cust_id;
:::
### <font color="#008000">右連接（RIGHT JOIN）</font>
:::success
SELECT customers.cust_id, orders.order_num
FROM customers RIGHT JOIN orders
ON customers.cust_id = orders.cust_id;
:::
### <font color="#008000">組合（UNION）</font>
## UNION 加數
* UNION 運算符將兩個或更多查詢的結果組合起來，並生成一個結果集，其中包含來自 UNION 中參與查詢的提取行。
* UNION 基本規則
所有查詢的列數和列順序必須相同。
每個查詢中涉及Table的列的數據類型必須相同或兼容。
通常返回的列名取自第一個查詢。
* 默認會去除相同行，如果需要保留相同行，使用 UNION ALL。
* 只能包含一個 ORDER BY 子句，並且必須位於語句的最後。
* 應用場景
在一個查詢中從不同的Table返回結構數據。
對一個Table執行多個查詢，按一個查詢返回數據。

#### 組合查詢
:::success
SELECT cust_name, cust_contact, cust_email
FROM customers
WHERE cust_state IN ('IL', 'IN', 'MI')
UNION
SELECT cust_name, cust_contact, cust_email
FROM customers
WHERE cust_name = 'Fun4All';
:::
### <font color="#008000">JOIN vs UNION</font>
JOIN vs UNION
JOIN 中連接Table的列可能不同，但在 UNION 中，所有查詢的列數和列順序必須相同。
UNION 將查詢之後的行放在一起（垂直放置），但 JOIN 將查詢之後的列放在一起（水平放置），即它構成一個笛卡爾積。

### <font color="#008000">數值</font>
|type|大小|Range|格式|
|-|-|-|-|
DATE|3|1000-01-01 / 9999-12-31|YYYY-MM-DD|
TIME|3|'-828:59:59' / '838:59:59'|HH:MM:SS|
YEAR|1|1901 / 2155|YYYY|
DATETIME|8|1000-01-01 00:00:00 / 9999-12-31 23:59:59| YYYY-MM-DD HH:MM:SS|
TIMESTAMP|4|1970-01-01 00:00:00 / 2038-01-19 03:14:07| YYYYMMDD HHMMSS|
### <font color="#008000">函數</font>
|函數|Defination|
|-|-|
|AddDate()|	增加一個日期（天、周等）
|AddTime()|	增加一個時間（時、分等）
|CurDate()|	返回當前日期
|CurTime()|	返回當前時間
|Date()|	返回日期時間的日期部分
|DateDiff()|	計算兩個日期之差
|Date_Add()|高度靈活的日期運算函數
|Date_Format()|	返回一個格式化的日期或時間串
|Day()|返回一個日期的天數部分
|DayOfWeek()|	對於一個日期，返回對應的星期幾
|Hour()|返回一個時間的小時部分
|Minute()|返回一個時間的分鐘部分
|Month()|返回一個日期的月份部分
|Now()|返回當前日期和時間
|Second()|返回一個時間的秒部分
|Time()|返回一個日期時間的時間部分
|Year()|返回一個日期的年份部分
|IntevalDay()|表示一段時間間隔，INTERVAL 間隔值 單位，INTERVAL 1 
|AVG()|返回某列的平均值
|COUNT()|返回某列的行數
|MAX()|返回某列的最大值
|MIN()|返回某列的最小值
|SUM()|返回某列值之和


### <font color="#008000">函數</font>
排序和分組
### <font color="#008000">函數</font>
ORDER BY
ORDER BY 用於對結果集進行排序。
ASC ：升序（默認）
DESC ：降序
可以按多個列進行排序，並且為每個列指定不同的排序方式
指定多個列的排序方向
:::success
SELECT * FROM products
ORDER BY prod_price DESC, prod_name ASC;
:::
### <font color="#008000">GROUP BY</font>
* GROUP BY 子句將記錄分組到匯總行中。
* GROUP BY 為每個組返回一個記錄。
* GROUP BY 通常還涉及聚合：COUNT，MAX，SUM，AVG 等。
* GROUP BY 可以按一列或多列進行分組。
* GROUP BY 按分組字段進行排序後，ORDER BY 可以以匯總字段來進行排序。

#### 分組
SELECT cust_name, COUNT(cust_address) AS addr_num
FROM Customers GROUP BY cust_name;

#### 分組後排序
SELECT cust_name, COUNT(cust_address) AS addr_num
FROM Customers GROUP BY cust_name
ORDER BY cust_name DESC;
### <font color="#008000">HAVING</font>
* HAVING 用於對匯總的 GROUP BY 結果進行過濾。
* HAVING 要求存在一個 GROUP BY 子句。
* WHERE 和 HAVING 可以在相同的查詢中。
* HAVING vs WHERE
WHERE 和 HAVING 都是用於過濾。
HAVING 適用於匯總的組記錄；而 WHERE 適用於單個記錄。
#### 使用 WHERE 和 HAVING 過濾數據
```sql
SELECT cust_name, COUNT(*) AS num
FROM Customers
WHERE cust_email IS NOT NULL
GROUP BY cust_name
HAVING COUNT(*) >= 1;
```
### <font color="#008000">LIMIT</font>
:::success
SELECT ... FROM ... LIMIT N
N：表示查詢幾多條data
:::
:::success
SELECT ... FROM ... LIMIT M,N
M:由第幾條開始查，計算方法(M-1)
:::

### <font color="#008000">10 - VIEW</font>
#### 定義
視圖是基於 SQL 語句結果集的可視化表格。
視圖是==虛擬的表格==，本身不包含數據，因此不能進行索引操作。
對視圖的操作與普通表格相同。

作用
簡化複雜的 SQL 操作，例如復雜的連接操作。
僅使用實際表格的部分數據。
通過僅為用戶授予訪問視圖的權限，保障數據的安全性。
更改數據的格式和表示。

#### 創建視圖
```sql=
-- Creating a sample orders table
CREATE TABLE orders (
  order_id INT PRIMARY KEY,
  customer_id INT,
  order_date DATE,
  total_amount DECIMAL(10, 2)
);

-- Inserting sample data into the orders table
INSERT INTO orders (order_id, customer_id, order_date, total_amount)
VALUES
  (1, 101, '2023-08-01', 150.00),
  (2, 102, '2023-08-02', 200.00),
  (3, 101, '2023-08-03', 300.00),
  (4, 103, '2023-08-04', 100.00),
  (5, 102, '2023-08-05', 250.00);
```
```sql=
-- Creating a sample customers table
CREATE TABLE customers (
  customer_id INT PRIMARY KEY,
  customer_name VARCHAR(50)
);

-- Inserting sample data into the customers table
INSERT INTO customers (customer_id, customer_name)
VALUES
  (101, 'Alice'),
  (102, 'Bob'),
  (103, 'Charlie');

```
:::success
Now, let's create a view named order_details that combines data from the orders table and the customers table to show order details with customer names.
:::
```sql=
-- Creating a view to show order details with customer names
CREATE VIEW order_details AS
SELECT o.order_id, c.customer_name, o.order_date, o.total_amount
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id;
```
```sql=
-- Querying the order_details view
SELECT * FROM order_details;

```
#### 刪除視圖
```sql=
Copy code
DROP VIEW order_details;
```

### <font color="#008000">INDEX</font>

#### 作用
通過索引可以更加快速高效地查詢數據。
用戶無法直接看到索引，它們僅用於加速查詢。

#### 注意
更新包含索引的表格需要更多時間，因為索引本身也需要更新。因此，最好只在常常被搜索的列（以及表格）上創建索引。

#### 創建索引
```sql=
-- Creating a sample products table
CREATE TABLE products (
  product_id INT PRIMARY KEY,
  product_name VARCHAR(50),
  category VARCHAR(20)
);

-- Inserting sample data into the products table
INSERT INTO products (product_id, product_name, category)
VALUES
  (1, 'Laptop', 'Electronics'),
  (2, 'Smartphone', 'Electronics'),
  (3, 'Shirt', 'Clothing'),
  (4, 'Shoes', 'Footwear'),
  (5, 'Book', 'Books');

```

#### 創建唯一索引
```sql=
-- Creating a unique index on the category column
CREATE UNIQUE INDEX idx_unique_category ON products(category);
```
```sql=
-- Query using the index for faster execution
SELECT * FROM products WHERE category = 'Electronics';
```
#### 刪除索引
```sql=
DROP INDEX idx_category ON products;
```
:::info
|	|Unique Index|	Non-Unique Index|
|-|-|-|
|| Ensures uniqueness of values in indexed column(s).<br>- Prevents duplicate values.<br>- Enforces data integrity.	| Does not enforce uniqueness; duplicates allowed.<br>- Improves query performance.|
||Typically used for primary keys or unique constraints.<br>- One unique index per table for enforcing primary key.<br>- Multiple unique indexes for unique constraints.	| Used to speed up searches on frequently queried columns.<br>- Multiple non-unique indexes possible.|
|Usage|	 Primary keys, business identifiers.<br>- Ensures uniqueness in indexed column(s).	|- Optimize SELECT operation speed.<br>- Does not guarantee uniqueness.
:::
:::info
||使用 View 的好處|	View 與 Table 的比較|
|-|-|-|
概述|	View是基於 SQL 查詢的結果集的可視化虛擬表格。| Table是數據庫中的實際數據存儲單元。|
用途|	- 簡化複雜的查詢操作。 <br>- 將復雜的聯結操作封裝為View，減少編寫重複的代碼。 <br>- 隱藏底層數據結構，提供更簡單、更具可讀性的數據訪問方式。| - 存儲實際數據。 <br>- 提供主要數據操作，如插入、更新、刪除記錄。 <br>- 表格內的數據具有持久性。|
數據存儲|	- View本身不存儲數據，而是基於查詢生成的。 <br>- 不佔用物理存儲空間。| - 表格實際存儲數據記錄。 <br>- 佔用物理存儲空間。|
數據更新|	- 對View的修改不會直接影響底層數據表，只是影響查詢結果。 |- 對Table的修改會直接影響存儲的數據。|
安全性|	- 可以限制用戶只能訪問特定列的數據，保護敏感數據。 <br>- 隱藏底層表的結構，減少數據暴露風險。 |- 數據可以根據Table的權限直接控制。 <br>- 表內的數據可能更容易受到直接訪問的威脅。|
性能|	- 可以提供預先計算的數據結果，加速查詢操作。| <br>- 基於VIew的查詢可以減少複雜的 JOIN 操作。 - 表格的查詢性能取決於索引和數據量。 <br>- 複雜的查詢可能需要手動編寫 JOIN 操作。|
示例|	假設有一個名為 "銷售訂單" 的VIew， 匯總了訂單信息和客戶名稱。通過查詢該View， 可以直接獲得訂單和客戶的信息。|假設有一個名為 "產品" 的Table，存儲了產品的詳細信息，如名稱、價格和庫存數量。|
:::

### <font color="#008000">事務處理</font>

* 不能回滾 SELECT 語句，回滾 SELECT 語句也沒有意義；也不能回滾 CREATE 和 DROP 語句。
* MySQL 默認是隱式提交，每執行一條語句就將其視為一個事務並提交。出現 START TRANSACTION 語句時，隱式提交關閉；執行 COMMIT 或 ROLLBACK 語句後，事務會自動關閉，恢復隱式提交。
* 通過設置 autocommit=0 可以取消自動提交，直到 autocommit=1 才會提交；autocommit 標記針對每個連接，而不是服務器。

### 指令
* START TRANSACTION：標記事務的起始點。
* SAVEPOINT：創建保存點。
* ROLLBACK TO：回滾到指定的保存點；如果沒有設置保存點，則回滾到 START TRANSACTION 語句處。
* COMMIT：提交事務。

```sql=
-- 開始事務
START TRANSACTION;

-- 轉賬操作：從賬戶A減去100，添加到賬戶B
UPDATE accounts SET balance = balance - 100 WHERE account_id = 'A';
UPDATE accounts SET balance = balance + 100 WHERE account_id = 'B';

-- 檢查餘額是否足夠
SELECT balance INTO @balance_a FROM accounts WHERE account_id = 'A';
IF @balance_a < 0 THEN
  -- 餘額不足，回滾事務
  ROLLBACK;
ELSE
  -- 餘額足夠，提交事務
  COMMIT;
END IF;
```


### <font color="#008000"> ROW_NUMBER()</font> 
```sql=
ROW_NUMBER() OVER (
    [PARTITION BY expr1, expr2,...]
    ORDER BY expr1 [ASC | DESC], expr2,...
)
```

:::success
First, the PARTITION BY clause divides the result set returned from the FROM clause into partitions.

The PARTITION BY clause is optional. If you omit it, the whole result set is treated as a single partition.

Then, the ORDER BY clause sorts the rows in each partition. 
Because the ROW_NUMBER() is an order sensitive function, the ORDER BY clause is required.

Finally, each row in each partition is assigned a sequential integer number called a row number. The row number is reset whenever the partition boundary is crossed.
:::
![](https://hackmd.io/_uploads/r1s9YrKRn.png)

---

```sql=
SELECT
ROW_NUMBER()OVER(
ORDER BY SALARY)
row_number,
first_name,
last_name,
salary
FROM employees;
```
![](https://hackmd.io/_uploads/B1pwqBFC3.png)

---
### APPROACH 1 :
```sql=
SELECT * FROM (
SELECT
ROW_NUMBER() OVER (ORDER BY SALARY)ROW_NUM,
FIRST_NAME,
LAST_NAME,
SALARY
FROM
EMPLOYEES
)AS NEW_TABLE
WHERE ROW_NUM > 10 AND ROW_NUM <=20;
```

### APPROACH 2 : 
```sql=
WITH NEW_TABLE AS(
SELECT 
ROW_NUMBER OVER (
ORDER BY SALARY)
ROW_NUMBER,
FIRST_NAME,
LAST_NAME,
SALARY
FROM 
EMPLOYEES
)
SELECT * FROM NEW_TABLE
WHERE ROW_NUM > 10 AND ROW_NUM<=20;
```
![](https://hackmd.io/_uploads/rJFboHFR3.png)

---

```sql=
-- finding the highest salary per department
SELECT 
DEPARTMENT_NAME,
FIRST_NAME,
LAST_NAME,
SALARY
FROM
    (
        SELECT 
            DEPARTMENT_NAME,
            ROW_NUMBER() OVER(
                PARTITION BY DEPARTMENT_NAME
                ORDER BY SALARY DESC) ROW_NUM,
            FIRST_NAME,
            LAST_NAME,
            SALARY
        FROM 
            EMPLOYEE E
            INNER JOIN 
            EMPLOYEE E2
                ON E.DEPARTMENT_ID = E2.DEPARTMENT_ID
    )AS NEW_TABLE
WHERE
    ROW_NUM =1;
```
![](https://hackmd.io/_uploads/r1hnCrK0h.png)


## ManyToMany
![](https://hackmd.io/_uploads/SJDmKGHzp.png)
```sql=
CREATE TABLE books (
  book_id INT PRIMARY KEY,
  title VARCHAR(255) NOT NULL
);

```
```sql=
CREATE TABLE authors (
  author_id INT PRIMARY KEY,
  name VARCHAR(255) NOT NULL
);

```
```sql=
CREATE TABLE book_authors (
  book_id INT,
  author_id INT,
  PRIMARY KEY (book_id, author_id),
  FOREIGN KEY (book_id) REFERENCES books (book_id),
  FOREIGN KEY (author_id) REFERENCES authors (author_id)
);

```
```sql=
-- Insert some books
INSERT INTO books (book_id, title) VALUES (1, 'Book 1');
INSERT INTO books (book_id, title) VALUES (2, 'Book 2');

-- Insert some authors
INSERT INTO authors (author_id, name) VALUES (1, 'Author A');
INSERT INTO authors (author_id, name) VALUES (2, 'Author B');

-- Create associations in the junction table
INSERT INTO book_authors (book_id, author_id) VALUES (1, 1); -- Author A wrote Book 1
INSERT INTO book_authors (book_id, author_id) VALUES (1, 2); -- Author B also wrote Book 1
INSERT INTO book_authors (book_id, author_id) VALUES (2, 2); -- Author B wrote Book 2
```

```java=
import javax.persistence.*;
import java.util.HashSet;
import java.util.Set;

@Entity
public class Author {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;

    @ManyToMany(mappedBy = "authors")
    private Set<Book> books = new HashSet<>();
```
```sql=
import javax.persistence.*;
import java.util.HashSet;
import java.util.Set;

@Entity
public class Book {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String title;

    @ManyToMany
    @JoinTable(name = "book_author",
        joinColumns = @JoinColumn(name = "book_id"),
        inverseJoinColumns = @JoinColumn(name = "author_id"))
    private Set<Author> authors = new HashSet<>();


}

```